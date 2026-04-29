# Preference-Aligned Abstractive Summarization for Mongolian Cyrillic Script
**Graduation Research | E-Society Laboratory, Ritsumeikan University**

## 📌 Overview
This research addresses the critical gap in Natural Language Processing (NLP) for the Mongolian Cyrillic script. Specifically, it focuses on overcoming the limitations of Large Language Models (LLMs) when processing low-resource, agglutinative languages.

### **The Problem**
*   **Tokenization Failure:** Standard multilingual models (like mT5) suffer from excessive subword segmentation in Mongolian, breaking the semantic connection between root words and suffix chains.
*   **Exposure Bias:** Supervised Fine-Tuning (SFT) often leads to repetitive or "hallucinative" summaries that lack factual grounding.

---

## 🛠 Proposed Methodology (Four-Module Architecture)
The system adapts a multilingual foundation into a preference-aligned summarizer through a specialized pipeline:

1.  **Module 1: Monolingual Adaptation (monT5)**
    *   Reduced the mT5-Large vocabulary (250k tokens) to a specialized 40k Mongolian subset using **Vocabulary Pruning**.
2.  **Module 2: Three-Phased SFT Strategy**
    *   Sequential fine-tuning of the encoder, decoder, and bias parameters to stabilize learning on synthetic and natural datasets.
3.  **Module 3: Semantic Reward Modeling**
    *   Developed a **Semantic Judge** based on Sentence-BERT (SBERT) using Cross-lingual Knowledge Distillation and Triplet Loss optimization.
4.  **Module 4: Reinforcement Token Optimization (RTO)**
    *   A hybrid alignment algorithm combining token-wise dense signals (DPO-based) and sentence-wise sparse signals to identify and correct morphological errors.

![System Architecture Overview](assets/overview)

---

## 📊 Key Results
The **monT5-RTO** model achieved superior performance across nearly all metrics, validating the effectiveness of token-wise alignment for morphologically complex languages.

| Model | ROUGE-1 | ROUGE-L | BERTScore | Semantic Judge |
| :--- | :---: | :---: | :---: | :---: |
| Baseline (SFT) | 14.39 | 13.99 | 59.78 | 2.2471 |
| Baseline + PPO | 18.62 | 17.47 | 63.68 | 2.7864 |
| Baseline + DPO | 21.18 | 19.68 | **65.63** | 2.8336 |
| **monT5 + RTO (Proposed)** | **21.33** | **19.88** | 65.57 | **2.8464** |

---

## 🔐 Status of Thesis & Implementation
Due to the proprietary nature of the datasets curated from Mongolian news portals (baabar.mn) and the specific algorithmic implementations of the RTO strategy, the full documentation is protected.

*   **Codebase:** The system architecture is designed for full reproducibility. The implementation scripts reside within the private research environment.
*   **Full Thesis:** The complete **50-page graduation thesis**, containing exhaustive mathematical formulations, data cleaning procedures, and hyperparameter configurations, is **available strictly upon request for interview and professional evaluation purposes.**

### **Contact for Full Research Access**
If you are an employer or researcher interested in the full technical details of this project, please reach out directly:
*   **Name:** Khurtsbayar Biligsaikhan
*   **Email:** [biligeekhurtsbayar@gmail.com](mailto:biligeekhurtsbayar@gmail.com)
