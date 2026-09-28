# Structure-Aware Topological Gating (SATG) Framework for Mammographic Lesion Analysis

[![Audit-First Protocol](https://img.shields.io/badge/Audit--First-Gates%200--4%20PASSED-success.svg)](#audit-gates-verification-matrix)
[![Dataset](https://img.shields.io/badge/Dataset-CBIS--DDSM%20%7C%20INbreast-blue.svg)](#dataset-specifications)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Official implementation and audit trail for the **Structure-Aware Topological Gating (SATG)** deep fusion framework for breast mass classification in digital mammography.

---

## 📌 Audit-First Verification Matrix

| Gate | Audit Scope | Status | Audit Artifact | Key Verified Parameters |
| :--- | :--- | :---: | :--- | :--- |
| **Gate-0** | Environment & Data Integrity | `PASSED` | `audit/gate0_environment_data_audit.json` | 691 train / 201 test patients; >10,649 DICOMs; INbreast PH-only AUC=0.6164 [0.5055, 0.7219] |
| **Gate-1** | Patient & Lesion Partitioning | `PASSED` | `audit/gate1_manifest_split_audit.json` | Key: `(patient_id, abnormality_id)`; 1,318 train / 378 test rows; Leakage = 0.0% |
| **Gate-2** | Topological Extraction Stability | `PASSED` | `audit/gate2_topological_extraction_audit.json` | Sublevel filtration; $H_0/H_1$ persistent homology representations |
| **Gate-3** | Subspace SVCCA Regularization | `PASSED` | `audit/gate3_alignment_svcca_audit.json` | 11 active TDA dimensions; Ledoit-Wolf shrinkage=0.0569; Cond=102.98; $H_1$ lifetime $r=0.2785$ |
| **Gate-4** | Independent Test Cohort Inference | `PASSED` | `audit/gate4_test_evaluation_audit.json` | 378 test rows; 201 unique patients; deterministic evaluation protocol |

---

## 🔬 Method Overview

The **SATG** framework integrates multi-scale persistent homology features with deep representations via regularized canonical gating to prevent attribution collapse on subtle spiculated margins.

---

## 🛠️ Verified Dependencies
- `ripser==0.6.15`
- `persim==0.3.8`
- `gudhi==3.13.0`
