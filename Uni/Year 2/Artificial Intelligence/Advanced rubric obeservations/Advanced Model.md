0. Quick recap of the improvement B

Baseline A (what you already have):

Two independent ridge models:

EEG → image embedding (100-D)

EEG → text embedding (512-D)

Zero-shot classification done separately via nearest image or text prototype.

Advanced model B (what we’ll build now):

Learn a shared $d$-dimensional multimodal space.

Learn linear projections for all three modalities:

$W_E : \mathbb{R}^{561} \to \mathbb{R}^d$ (EEG)

$W_I : \mathbb{R}^{100} \to \mathbb{R}^d$ (image)

$W_T : \mathbb{R}^{512} \to \mathbb{R}^d$ (text)

For class $c$:

$z^I_c = W_I V_c$ (image prototype in shared space)

$z^T_c = W_T T_c$ (text prototype)

Multimodal prototype $P_c = \alpha z^I_c + (1-\alpha) z^T_c$.

Train $W_E, W_I, W_T$ from scratch with a cosine alignment loss so that

$f_\theta(x) = W_E x$ is close to both $z^I_c$ and $z^T_c$ for EEG from class $c$.

That gives you a single “EEG → multimodal latent space → nearest prototype” pipeline, which is clearly a methodological improvement over the ridge baselines.