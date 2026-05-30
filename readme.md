# Clinical Dataset Anomaly Detector (Medical AI Auditing)

This repository provides an automated pipeline to audit clinical and medical datasets for structural anomalies, data fabrication signatures, and distribution shifts. Inspired by recent investigations into unverified, simulated, or "dubious" datasets used to train public machine learning models for diseases like stroke and diabetes, this tool helps researchers ensure data authenticity before training clinical AI models.

## 🔍 The Problem
In medical data science, many public open-source datasets contain synthetic mathematical patterns, lack proper clinical provenance, or exhibit structural anomalies that indicate they were artificially fabricated. Models trained on such data learn artificial correlations rather than true biological signals, rendering them dangerous if deployed on real patients.

---

## 🛠️ Features
The tool conducts three structural diagnostic tests to identify unauthentic or manipulated datasets:

1. **Missing Data Completeness Check**: Real-world electronic health records (EHR) naturally contain missing entries due to fragmented clinical workflows. A dataset with exactly 0% missing fields across thousand of entries is flagged as highly suspicious for synthetic generation.
2. **Sequential Distribution Shift Detection**: Detects abrupt mathematical jumps or structural drops in clinical variables (e.g., Blood Glucose, Blood Pressure) relative to patient IDs. This identifies cases where distinct synthetic batches or unaligned data pools were stitched together.
3. **Oversampling & Duplicate Check**: Identifies exact row duplication often caused by naive implementation of data-augmentation algorithms (like SMOTE) to unnaturally bloat clinical datasets.

---

## 🚀 Getting Started

### Prerequisites
Ensure you have Python 3.8+ and the following packages installed:
```bash
pip install pandas numpy matplotlib