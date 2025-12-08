
### 📌 Zero-Shot Paradigm Overview

We adopt a **zero-shot learning (ZSL)** framework where the model learns to map EEG activity into a **shared embedding space** that aligns with both **image** and **text** semantic features.

The core mapping is performed by a learned encoder:

$$
f_\theta : \mathbb{R}^{561} \rightarrow \mathbb{R}^d
$$

Where:

- **561** = dimensionality of the EEG vector (after time-window flattening)  
- **θ** = trainable parameters of the EEG encoder  
- **d** = size of the shared embedding space (e.g., 16 / 32 / 64), treated as a *hyperparameter*  

---

### 🔄 Full Workflow

1. **EEG trial**  
   → preprocessed + flattened vector $x \in \mathbb{R}^{561}$

2. **EEG encoder**  
   → mapped to embedding  
   $$ z = f_\theta(x) \in \mathbb{R}^{d} $$

3. **Prototype comparison**  
   Compare $z$ to class prototypes from:
   - Visual embeddings (PCA-reduced CORnet-S features)  
   - Text embeddings (CLIP-Text features)

4. **Zero-shot decision rule**  
   The predicted class is the prototype with highest cosine similarity:

   $$
   \hat{y} = \arg\max_{c \in \mathcal{C}} 
   \cos\bigl(z, \; p_c \bigr)
   $$

Where $p_c$ is the semantic prototype for class $c$.

---

## Paradigm overview

**High-level idea**

- Use EEG to predict where a stimulus should land in a **shared semantic embedding space**.
- Build **class prototypes** in that space from image + text features (no EEG).
- Do **zero-shot classification** by matching EEG embeddings to the nearest prototype.
- Then add **incremental few-shot updates** when a small number of EEG trials from new classes become available.

You can think of the full pipeline as:

1. **Input:** single EEG trial  
   $$x \in \mathbb{R}^{561}$$  
   (17 channels × 33 timepoints after windowing/flattening).
2. **Encoder:**  
   $$z = f_\theta(x) \in \mathbb{R}^d$$  
   where \( d \) is the shared embedding dimension (hyperparameter).
3. **Class prototypes** (precomputed):  
   - Visual prototype: mean of image features per class  
   - Text prototype: mean of text features per class  
   - Optionally combine them: e.g. simple average or learned fusion.
4. **Zero-shot prediction:** compare \( z \) to all class prototypes via cosine similarity; pick the closest.
5. **Few-shot update:** when we get some labelled EEG for a new class, slightly update \( f_\theta \) and/or the prototype for that class.

---

## Diagram (to redraw nicely later)

I’d draw something like this in the report:

- **Left block:** “EEG trial (subject-specific, 17 channels, 70–400 ms)”  
  ↓  
- **Box:** “EEG encoder \( f_\theta \) (ML model)”  
  ↓  
- **Node:** “Shared embedding space \( \mathbb{R}^d \)”  
  ↘ compare to “Image prototype”  
  ↘ compare to “Text prototype”  
  ↓  
- **Right block:** “Nearest class prototype → predicted object label”

Underneath, you can add a second phase:

- “New class with K labelled EEG trials” → “few-shot update of \( f_\theta \) / prototype” → “improved performance for that class”.

This makes the hybrid **zero-shot + incremental few-shot** paradigm visually obvious.

---

## Formal problem setup

### Data

For a fixed subject \( s \):

- EEG features (seen classes):
  - $$X^{\text{eeg}}_{\text{seen}} \in \mathbb{R}^{N_{\text{seen}} \times 561}$$  
  - Labels: $$y_{\text{seen}} \in \{1,\dots, C_{\text{seen}}\}^{N_{\text{seen}}}$$

- EEG features (unseen classes):
  - $$X^{\text{eeg}}_{\text{unseen}} \in \mathbb{R}^{N_{\text{unseen}} \times 561}$$  
  - Labels: $$y_{\text{unseen}} \in \{C_{\text{seen}}+1,\dots, C_{\text{total}}\}^{N_{\text{unseen}}}$$

- Visual embeddings per trial (CORnet-S PCA):
  - $$X^{\text{img}} \in \mathbb{R}^{N_{\text{total}} \times 100}$$

- Text embeddings per trial (CLIP text):
  - $$X^{\text{text}} \in \mathbb{R}^{N_{\text{total}} \times 512}$$

For each class \( c \) we define **prototypes** in their native spaces:

- Visual:
  $$
  v_c = \frac{1}{|I_c|} \sum_{i \in I_c} x^{\text{img}}_i
  $$
- Text:
  $$
  t_c = \frac{1}{|T_c|} \sum_{i \in T_c} x^{\text{text}}_i
  $$

We then project them into a **shared space** \( \mathbb{R}^d \):

- Visual projection:  
  $$g_\phi : \mathbb{R}^{100} \to \mathbb{R}^d$$
- Textual projection:  
  $$h_\psi : \mathbb{R}^{512} \to \mathbb{R}^d$$

Class prototypes in shared space:

- Visual prototype:
  $$
  \tilde{v}_c = g_\phi(v_c) \in \mathbb{R}^d
  $$
- Text prototype:
  $$
  \tilde{t}_c = h_\psi(t_c) \in \mathbb{R}^d
  $$

Optionally, a fused prototype:

- Simple average:
  $$
  p_c = \frac{1}{2}(\tilde{v}_c + \tilde{t}_c)
  $$
- Or weighted:
  $$
  p_c = \alpha \tilde{v}_c + (1-\alpha)\tilde{t}_c, \quad \alpha \in [0,1]
  $$

### EEG encoder

You already wrote the core definition:

- EEG encoder:
  $$
  f_\theta : \mathbb{R}^{561} \to \mathbb{R}^d
  $$
Where:
- \( x \in \mathbb{R}^{561} \) is one flattened EEG trial (17 channels × 33 timepoints)
- \( \theta \) are the learnable parameters
- \( d \) is a hyperparameter (e.g. \( d \in \{16,32,64,128\} \))

The EEG embedding is:

- $$
  z = f_\theta(x) \in \mathbb{R}^d
  $$

### Zero-shot classification rule

Given an EEG trial \( x \) from an unseen class, we compute:

- $$
  z = f_\theta(x)
  $$
- Cosine similarity to each prototype:
  $$
  \text{sim}(z, p_c)
  = \frac{z^\top p_c}{\|z\| \, \|p_c\|}
  $$

**Zero-shot prediction:**

- $$
  \hat{y}_{\text{ZS}}(x) = \arg\max_{c \in \mathcal{C}_{\text{unseen}}} \text{sim}\big(f_\theta(x), p_c\big)
  $$

### Training objectives

There are two phases:

1. **Projection training (aligning image & text)**  
   - Optional if you want to **learn** \( g_\phi, h_\psi \) instead of using something simple:
   - You can use a contrastive loss:
     $$
     \mathcal{L}_{\text{proj}}(\phi,\psi)
     = \sum_{(i,j)}
       \ell\big(
         \text{sim}(g_\phi(x^{\text{img}}_i), h_\psi(x^{\text{text}}_j)),
         \mathbf{1}[y_i = y_j]
       \big)
     $$
   - Where \( \ell \) encourages high similarity for same-class pairs and low similarity otherwise.

2. **EEG encoder training on seen classes**

   A simple **prototype regression + classification** objective:

   - Prototype target in shared space:
     $$
     p_{y_i} \in \mathbb{R}^d
     $$
   - Regression loss (make EEG embedding close to its class prototype):
     $$
     \mathcal{L}_{\text{reg}}(\theta)
     = \sum_i \big\| f_\theta(x^{\text{eeg}}_i) - p_{y_i} \big\|_2^2
     $$
   - Or a **prototype-based softmax loss**:
     - Logits:
       $$
       s_c(x) = \text{sim}\big(f_\theta(x), p_c\big)
       $$
     - Cross-entropy:
       $$
       \mathcal{L}_{\text{CE}}(\theta)
       = - \sum_i \log \frac{
       \exp(s_{y_i}(x_i))
       }{
       \sum_{c \in \mathcal{C}_{\text{seen}}} \exp(s_c(x_i))
       }
       $$

   Combined objective (for seen classes):

   - $$
     \mathcal{L}_{\text{seen}}(\theta)
     = \lambda_{\text{reg}} \, \mathcal{L}_{\text{reg}}(\theta)
     + \lambda_{\text{CE}} \, \mathcal{L}_{\text{CE}}(\theta)
     $$

### Incremental few-shot phase

When a new class \( c^\* \in \mathcal{C}_{\text{unseen}} \) gets \( K \) labelled EEG trials:

- Add these trials to a small **few-shot set**:
  - $$\{(x^{\text{eeg}}_k, y_k = c^\*)\}_{k=1}^K$$
- Option A: **Update prototype only** (fast, low-risk):
  - $$
    p_{c^\*}^{\text{new}}
    = \beta p_{c^\*}^{\text{old}}
    + (1-\beta)
      \frac{1}{K}\sum_{k=1}^K f_\theta(x^{\text{eeg}}_k)
    $$
- Option B: **Light fine-tuning of \( f_\theta \)** on a small batch:
  - Minimize:
    $$
    \mathcal{L}_{\text{few-shot}}(\theta)
    = \mathcal{L}_{\text{CE}}(\theta\ \text{on current seen} + \text{few-shot examples})
    $$
  - With small learning rate, few epochs, and strong regularisation.

This is your **hybrid paradigm**: zero-shot base → incremental few-shot adaptation.

---

## Data splits and protocol

You can describe the splits like this (subject-specific):

- **Seen classes**:
  - Use all trials belonging to \( \mathcal{C}_{\text{seen}} \).
  - Split as:
    - $$70\%$$ training  
    - $$15\%$$ validation  
    - $$15\%$$ test (for supervised EEG performance on seen classes).
- **Unseen classes**:
  - Completely **disjoint** class set \( \mathcal{C}_{\text{unseen}} \).
  - For **pure zero-shot** evaluation:
    - Hold out all unseen-class EEG until test time.
  - For **few-shot** experiments:
    - From each unseen class, sample:
      - K labelled trials per class for few-shot training (e.g. \( K \in \{1,5,10\} \)).
      - The rest of the unseen trials stay as a **held-out test set**.

In table form (for the report):

| Split         | Classes               | EEG labels used?      | Purpose                               |
|---------------|-----------------------|------------------------|----------------------------------------|
| Train         | \( \mathcal{C}_{\text{seen}} \)   | Yes                    | Train \( f_\theta \), \( g_\phi \), \( h_\psi \) |
| Val           | \( \mathcal{C}_{\text{seen}} \)   | Yes                    | Tune hyperparameters (e.g. \( d \), loss weights) |
| Test (seen)   | \( \mathcal{C}_{\text{seen}} \)   | Yes                    | Evaluate supervised EEG classification on seen classes |
| Zero-shot test| \( \mathcal{C}_{\text{unseen}} \) | No during training     | Evaluate pure zero-shot EEG→prototype mapping |
| Few-shot train| \( \mathcal{C}_{\text{unseen}} \) | K trials per class     | Incrementally adapt to new classes    |
| Few-shot test | \( \mathcal{C}_{\text{unseen}} \) | No (held-out)          | Evaluate improved performance after few-shot update |

This hits the rubric’s requirement to **“correctly define and justify training/validation/test split”** and makes the zero-shot + few-shot protocol clear.

---

## Real-world motivation (short version)

You can summarise the motivation like this:

- **Annotation cost:**  
  - Collecting many labelled EEG trials for every possible object class is unrealistic.  
  - Using **image and text embeddings** allows us to **reuse vision/language models** trained on millions of images/captions.
- **Zero-shot benefit:**  
  - Once the encoder learns to map EEG into this shared space, we can recognise **novel classes without any EEG training data** for them — only their image/text embeddings are needed.
- **Few-shot benefit:**  
  - In practice, we might get a **small number of EEG trials** per new class (e.g. during calibration).  
  - Incremental few-shot updates allow us to adapt the model to subject-specific neural patterns while still leveraging the strong structure from the vision/text prototypes.
- **Subject-specific focus (limitation + justification):**  
  - All modelling is done **per subject**, because cross-subject EEG alignment is non-trivial (different head shapes, noise, electrode contact, etc.).  
  - You can explicitly state this as a **scope choice**:  
    - “In this coursework I focus on a strong per-subject model; extending to cross-subject generalisation would require additional alignment methods and is left as future work.”

This ties your data exploration + visualisation directly to a **coherent, advanced paradigm** that matches the rubric.



+---------------------------------------------------------------+
|                          EEG Trial                            |
|                 (70–400 ms → 27–60 samples)                   |
+---------------------------------------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                     EEG Preprocessing                         |
|  - Bandpass filtering                                          |
|  - Epoch trimming                                              |
|  - Reshape channels × time → 561-D vector                      |
+---------------------------------------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                   EEG Encoder  fθ  (MLP / Linear)             |
|                Maps EEG → d-dimensional embedding             |
|                   fθ(x_EEG) ∈ ℝ^d                             |
+---------------------------------------------------------------+
                                |
                                v
+===============================================================+
||               Shared Latent Space  ℝ^d                      ||
||      (d is tunable: 8, 16, 32, 64, chosen via analysis)     ||
+===============================================================+
        |                                    |
        |                                    |
        |                                    |
        v                                    v
+-----------------------+        +------------------------------+
| Image Embeddings      |        | Text Embeddings              |
| CORnet-S → PCA (100D) |        | CLIP text encoder (512D)     |
| Per-class averaging   |        | Per-class averaging          |
+-----------------------+        +------------------------------+
        |                                    |
        +--------------------+---------------+
                             v
+---------------------------------------------------------------+
|               Multimodal Class Prototypes  {z_i}              |
|     Combine image + text embeddings → project into ℝ^d        |
+---------------------------------------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                     Cosine Similarity                         |
|             sim( fθ(x_EEG),  z_i )   for each class i         |
+---------------------------------------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|               Zero-Shot Classification Output                 |
|               ŷ = argmax_i   sim(fθ(x_EEG), z_i)              |
+---------------------------------------------------------------+
cod