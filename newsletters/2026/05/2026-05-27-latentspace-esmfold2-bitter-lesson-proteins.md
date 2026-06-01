---
title: "ESMFold2: The Bitter Lesson is Coming for Proteins — Alex Rives, BioHub"
date: 2026-05-27
source_url: https://www.latent.space/p/esmfold2
source: Latent.Space
type: newsletter
newsletter: Latent.Space
topics: [newsletter, genai-llm]
tags: [ESMFold2, BioHub, protein-folding, AlphaFold, world-model, SAE, mech-interp, scaling-laws, biology, open-source, programmable-biology]
saved_at: 2026-06-01
---

## Summary

Latent.Space podcast episode with Alex Rives (Head of Science, BioHub) on the release of ESMFold2 — an open scientific engine for protein structure prediction and design, released under MIT license. ESMFold2 demonstrates that vanilla BERT-like transformers trained on large, diverse protein sequence data can beat specialized models like AlphaFold3 on some of the hardest protein problems (especially antibodies), validating the "Bitter Lesson" for biology. BioHub simultaneously released ESMC (world model, 2.8B sequences) and an atlas of 6.8 billion proteins with 1.1 billion predicted structures — exceeding AlphaFold DB in scale.

## Key Highlights

- **ESMFold2** achieves SOTA on protein interactions and antibodies — AlphaFold3 uses MSAs (multi-sequence alignments) as an inductive bias that hurts antibody generalization; ESM skips MSAs entirely
- **Scale hypothesis confirmed**: ESM doubled down on unsupervised training on diverse sequences after AlphaFold2 released; inference time scaling also working across five cancer/immunology targets
- **World Model for proteins**: ESMC is a semantic, compositional, generalizing world model; ESMFold2 is the structure-prediction "head" attached to it; MIT licensed
- **Atlas**: 6.8 billion proteins + 1.1 billion predicted structures released publicly; exceeds AlphaFold DB in scale
- **Mechanistic interpretability**: SAEs applied to ESMC extract hierarchical protein features (secondary structure → supersecondary motifs → full domain identifiers → functional motifs like disulfide bonds, disordered regions) — discovers unknown biology
- **Programmable biology analogy**: cell nucleus = storage, ribosome = JIT compiler, SAE features = functions, signaling pathways = workflows → "we are moving toward programmable biology"
- Evidence of wet-lab validation: Alex discusses validating predicted molecules in the lab for cancer and immunology targets

## Why It Matters

ESMFold2 is the strongest signal yet that the Bitter Lesson — scale + diverse data + simple objectives beats hand-crafted inductive biases — generalizes from language to protein biology, potentially unlocking a new era of model-guided drug and therapeutic design.

---
[Source: Latent.Space](https://www.latent.space/p/esmfold2)
