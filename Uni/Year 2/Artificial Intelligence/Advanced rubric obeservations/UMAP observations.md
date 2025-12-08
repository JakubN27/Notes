## Observations from Multimodal UMAP Visualisations

### 1. UMAP on Full Multimodal Space (EEG + Image + Text)
- The fused space ($X = [\text{EEG} \,\|\, \text{image} \,\|\, \text{text}]$) produces a **single coherent manifold**, indicating that the three modalities share enough structure for joint embedding.
- However, **per-class clusters are weak or absent**. Points from the same class scatter widely.  
  → This directly reflects the **high intra-class variability** of EEG responses and confirms that raw EEG does **not naturally align** with semantic or visual embeddings.

### 2. UMAP of Multimodal Class Prototypes
- Reducing each class to its mean prototype dramatically changes the structure:  
  - The manifold becomes **cleaner, less noisy, and more class-consistent**.
  - Clusters become visible at a macro level, although still not perfectly separated.
- This supports the idea that **EEG is highly noisy at the trial level**, but **averages carry meaningful class structure**.

### 3. Per-modality Prototype UMAPs (EEG vs Image vs Text)
- **Image prototypes** form the cleanest clusters → expected since CORnet-S produces highly structured representations.
- **Text prototypes** show moderate clustering → CLIP text features encode semantics but with weaker visual grounding.
- **EEG prototypes** are the least structured → weak inherent separability highlights the difficulty of zero-shot EEG classification.

### 4. Interpretation Across All UMAPs
- All three modalities embed into **roughly similar low-dimensional shapes**, but **alignment is not automatic**.  
  This empirically validates the need for a **learned mapping** $f_\theta(\text{EEG}) \rightarrow \mathbb{R}^d$ instead of assuming natural alignment.
- The visualisations highlight two key ML problems:
  1. **EEG has much higher noise and trial-level variability** than images/text.  
  2. **Cross-modal spaces differ in scale, structure, and granularity**, preventing naïve cosine matching.

### 5. Takeaway for Paradigm Design
- These visualisations justify an **alignment-based paradigm**, where we learn a function
  $$
  f_\theta: \text{EEG} \rightarrow \mathcal{Z}
  $$
  mapping EEG into the **shared multimodal space** $\mathcal{Z}$.
- They also justify treating embedding dimension as a **tunable hyperparameter**, due to the different structural properties across modalities.
- Most importantly, they motivate the use of:
  - **prototype-level reasoning**  
  - **projection into a shared latent space**  
  - **zero-shot or few-shot decoding**  
  as more reliable strategies than raw supervised classification on EEG alone.
