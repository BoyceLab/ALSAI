# Generative Image AI

!!! abstract "Module 3 · Lesson 7"
    **How AI generates synthetic images — and its growing applications in biomedical research.**

## Three Core Approaches

=== "GAN"
    **Generative Adversarial Network**

    A **generator** creates fake images; a **discriminator** learns to tell real from fake. They compete, each improving the other, until the generator produces highly realistic images.

    Best for: Synthetic data generation, super-resolution, image-to-image translation

=== "VAE"
    **Variational Autoencoder**

    Encodes images into a compressed **latent space** (capturing mean, variance, and noise), then decodes back to generate new images from that space. Allows smooth interpolation between concepts.

    Best for: Representational learning, anomaly detection, similarity search

=== "Diffusion"
    **Diffusion Models**

    Learns to progressively add and remove noise from images. State-of-the-art quality. Powers DALL-E, Stable Diffusion, and MidJourney.

    Best for: Text-to-image generation, resolution enhancement, controllable synthesis

---

## GANs for Biomedical Research

GANs are particularly relevant for ALS research because they can generate **synthetic training data** when real data is scarce — a common challenge in rare disease research.

### Synthetic Data Generation

!!! tip "ALS Research Example"
    A model classifying neuromuscular junction morphology might have only 200 labeled images. GANs could generate 2,000 synthetic variations — capturing the statistical properties of real data — dramatically improving the classifier's recall performance on novel samples.

### Other Biomedical Applications

| Application | Description |
|-------------|-------------|
| **Super-resolution** | Enhance microscopy or MRI images to improve feature detection |
| **Background removal** | Remove artifacts or noise from imaging data |
| **Image translation** | Convert between modalities (T1 to T2 MRI) when one is unavailable |
| **Data augmentation** | Generate variations to prevent overfitting in classification models |
| **Anomaly detection** | Flag images that deviate from learned normal distributions |

---

## A Brief History of Generative Image AI

```
1975  Utah Teapot          → First rule-based 3D generative image
2006  Deep Belief Networks → Early attempts at generating digits
2012  Conv. Deep Belief    → First recognizable face generation
2014  VAE & GAN introduced → Higher-quality facial generation
2018  StyleGAN             → Photorealistic synthetic faces
2020  ImageGPT / DALL-E    → Text-to-image generation begins
2022  Stable Diffusion     → High-quality open-source text-to-image
2023  ControlNet           → Controllable pose and composition
```

---

[← Why LLMs Appear Smart](../module-1/why-llms-appear-smart.md) | [Next: Autoencoders & Diffusion →](autoencoders-diffusion.md)
