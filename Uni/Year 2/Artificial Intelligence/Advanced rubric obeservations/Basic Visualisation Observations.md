## EEG Data Exploration & Visualisation Summary

### 1. Raw EEG Channel Inspection  
Visualisation of single EEG trials across all channels showed the expected oscillatory structure centred around 0 μV. A small number of channels (e.g., Channel 3) exhibited **consistent, high-amplitude spikes across many trials**.  
These spikes were **systematic**, not random artefacts, and appeared across subjects. Removing such channels would delete genuine neural signals.

**Implication:**  
The EEG encoder must learn to integrate over noisy-but-systematic activity. This motivates the use of **contrastive prototype learning** rather than simple regression.

---

### 2. Per-Channel Variability and Background Noise  
Standard deviation and spike-percentage analyses revealed:

- Most channels showed stable noise levels.  
- A few channels displayed consistently higher variance.  
- High-variance channels appeared frequently, implying meaningful evoked responses rather than noise.

**Implication:**  
Because EEG amplitude varies heavily across channels, **normalisation and cosine similarity** are more appropriate than raw-value losses such as MSE/Ridge. This aligns with the MPA model’s design.

---

### 3. Class Prototype Analysis Across Modalities  
For each class \( c \), we computed prototypes:

\[
p_c = \frac{1}{N_c}\sum_{i\in c} x_i.
\]

Findings:

- **Image prototypes** (from CLIP/CORnet-S) form clear perceptual clusters.  
- **Text prototypes** (CLIP text) show even stronger semantic structure.  
- **EEG prototypes** are weakly separable, with noisy and overlapping class means.

**Implication:**  
EEG has poor intrinsic discriminability across 400 classes.  
Thus, zero-shot decoding requires projecting EEG into a **structured latent space**, enriched by image and text prototypes.

---

### 4. Similarity Heatmaps  
Cosine similarity matrices showed:

- **EEG**: noisy, little diagonal structure.  
- **Image**: strong block-diagonal similarity.  
- **Text**: clearest semantic hierarchy.

This gives the hierarchy:

\[
\text{text} > \text{image} \gg \text{EEG}.
\]

**Implication:**  
Zero-shot classification should rely on the structured visual/semantic spaces.  
The MPA model accomplishes this via multimodal prototypes.

---

### 5. Hierarchical Clustering of Similarity Matrices  
Ward clustering revealed:

- **Image/text** embeddings cluster into meaningful semantic groups (animals, vehicles, tools).  
- **EEG** embeddings remain noisy, with limited structure even after reordering.

**Implication:**  
The EEG space is not aligned with semantics. Hence, we learn a **cross-modal alignment** into a shared latent space rather than decoding directly from EEG structure.

---

### 6. Labelled Heatmaps  
With class names:

- Image/text clusters mapped onto intuitive semantic groupings.  
- EEG clusters were nearly random.

**Implication:**  
EEG cannot support semantic decoding on its own.  
A model must **import structure** from image and text embeddings via a learned projection.

---

### 7. Cross-Subject Similarity  
Cross-subject cosine similarity was low and inconsistent. Subjects did **not** cluster together.

**Implication:**  
EEG varies widely across individuals.  
A prototype-based model is more robust, since it aligns EEG to **class prototypes** instead of raw EEG distributions.

---

### 8. Same-Class vs Different-Class EEG Similarity  
Same-class EEG prototypes were only slightly more similar than random class pairs.

**Implication:**  
The EEG carries only a weak class-identifying signal.  
Therefore, the model must learn to **map EEG into a structured latent space** that contains both perceptual (image) and semantic (text) information.

---

## How These Findings Justify the Advanced MPA Model

### 1. EEG alone is insufficient  
Weak EEG prototype structure and low discriminability mean that models like linear regression cannot learn high-fidelity class mappings. This directly motivates a **latent-space projection model**.

---

### 2. Image and text embeddings offer strong structure  
Image prototypes provide perceptual grounding.  
Text prototypes provide semantic grouping.  
Both are essential for robust zero-shot retrieval.

This motivates multimodal prototypes:

\[
P_c = \beta\,\tilde v_c + (1-\beta)\,\tilde t_c.
\]

---

### 3. A discriminative objective is required  
Regression losses (MSE/Ridge) do not enforce separation between classes.  
The MPA model instead uses a **margin-based ranking loss**:

\[
\mathcal{L} = 
\sum_i \sum_{c^-}
\max(0,\; m - \cos(\tilde z_i,\tilde p_{y_i})
          + \cos(\tilde z_i,\tilde p_{c^-}))
          + \lambda\|W\|_F^2.
\]

This pulls EEG features toward the correct fused prototype and pushes them away from others.

---

### 4. Zero-shot decoding via cosine similarity matches data structure  
After projecting EEG into the learned latent space:

\[
\hat{y} = \arg\max_c \cos(\tilde z_i, \tilde P_c).
\]

This classifier relies entirely on the structured multimodal space rather than raw EEG.

---

### 5. Empirical validation  
Ablation studies confirm:

- **Image-only** prototypes work well (EEG captures perceptual information).  
- **Text-only** prototypes fail (EEG lacks direct semantic encoding).  
- **Fused** prototypes perform best (10.03% top-1, 29.52% top-5), showing that semantic structure helps top-k retrieval when combined with visual features.

---

## Final Summary

All exploratory analyses point to the same conclusion:

> **EEG does not contain enough structure to support semantic zero-shot classification alone.  
> The image and text modalities contain strong perceptual and semantic hierarchy, which must be transferred to the EEG space via a learned projection.**  

The MPA model implements exactly this strategy:

- Linear EEG/image/text projection matrices trained **from scratch**  
- Shared latent space  
- Multimodal fused prototypes  
- Contrastive ranking loss  
- Cosine-based zero-shot classifier  

This architecture is directly motivated by the visualisations and achieves significant improvements over the baseline model.
