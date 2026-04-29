---
title: "How Stripe Detects Fraudulent Transactions Within 100ms"
date: 2026-04-28
source_url: https://blog.bytebytego.com/p/how-stripe-detects-fraudulent-transactions
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter]
tags: [ML, fraud-detection, Stripe, neural-networks, MoE-architecture, systems]
saved_at: 2026-04-28
---

## Summary

ByteByteGo dives deep into Stripe Radar's evolution from Wide & Deep (XGBoost + DNN ensemble) to "Shield NeXt," a ResNeXt-inspired multi-branch DNN architecture inspired by "Network-in-Neuron." The architectural shift reduced model training time by over 85% (to under 2 hours) while matching XGBoost's accuracy contributions — enabling a 3x faster model release cadence. Radar evaluates 1,000+ signals per transaction in under 100ms, achieving 99.9% accuracy across billions of payments.

## Key Highlights

- Shield NeXt: multi-branch DNN replacing Wide & Deep; 85%+ training time reduction; trains in <2 hours
- 90% of Stripe network cards seen across multiple merchants — unique cross-network fraud signal
- Embeddings enable geographic fraud transfer: patterns detected in Brazil auto-apply to US
- 10x increase in training data still produced meaningful accuracy gains; 100x version in progress
- Precision-recall tradeoff: 33% of consumers stop shopping after a single false decline
- Manual review queues let merchants reshape their precision-recall curve with business knowledge
- Risk Insights UI shows merchants top fraud signals, IP/address distance maps, and email auth rates

## Why It Matters

Stripe's journey from XGBoost ensemble to DNN-only architecture is a blueprint for teams facing the operations vs. accuracy tradeoff — proving that architectural simplification can enable 3x faster iteration without sacrificing model quality.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-stripe-detects-fraudulent-transactions)
