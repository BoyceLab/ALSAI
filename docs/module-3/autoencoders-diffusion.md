# Autoencoders & Diffusion Models

!!! abstract "Module 3 · Lesson 8"
    **Deep dives into variational autoencoders and diffusion models — tools increasingly used in biomedical imaging.**

## Variational Autoencoders (VAEs)

A VAE encodes training images into a **latent space** — a mathematical construct where similar images cluster together. It captures each image as a distribution (mean + variance) rather than a fixed point, enabling interpolation and controlled generation.

### Key Capabilities

| Capability | Description | ALS Application |
|------------|-------------|-----------------|
| **Image generation** | Sample from latent space to create new images | Synthetic training data |
| **Representational learning** | Find images similar to a reference | Pathology image search |
| **Data imputation** | Fill in missing data based on surrounding distribution | Handling incomplete imaging datasets |
| **Anomaly detection** | Images outside learned distribution are flagged | Detecting novel pathology patterns |
| **Interpolation** | Generate intermediate states between two conditions | Disease progression visualization |

!!! tip "ALS Application"
    A VAE trained on spinal cord pathology images could detect anomalous motor neuron degeneration patterns that fall outside the distribution of healthy tissue — potentially useful for early disease detection models.

---

## Diffusion Models

Diffusion models learn by gradually adding random noise to an image (forward diffusion), then learning to reverse that process (reverse diffusion). Repeated over thousands of steps, this teaches the model the underlying structure of realistic images.

### Why Diffusion Models Are Now State-of-the-Art

| Feature | GAN | VAE | Diffusion |
|---------|-----|-----|-----------|
| Output quality | High | Medium | **Highest** |
| Training stability | Problematic (mode collapse) | Stable | Stable |
| Text conditioning | Limited | Limited | **Excellent** |
| Compositional control | Limited | Limited | **Excellent (ControlNet)** |
| Relative compute cost | Medium | Low | Medium-low |

### Biomedical Imaging Applications

- **MRI resolution enhancement** — Upsample low-resolution scans to improve diagnostic quality
- **Microscopy denoising** — Remove noise from fluorescence or electron microscopy images
- **Augmented training sets** — Generate additional training examples for rare pathology classifiers
- **Image-to-image translation** — Convert a low-quality scan into high-resolution for downstream AI tasks
- **Synthetic patient imaging** — Generate privacy-preserving synthetic imaging datasets for sharing

!!! info "ControlNet for Research"
    ControlNet is a form of stable diffusion that gives you fine-grained control over generated images — specifying pose, structure, and composition. For research applications, this could allow generation of synthetic pathology images with specific controlled characteristics (e.g., specific degrees of motor neuron degeneration).

---

[← Image Generation](image-generation.md) | [Next: Symbolic AI →](../module-4/symbolic-ai.md)
