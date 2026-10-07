# Honours-Project-Final-Yesr-Project
# Does Skill-Level Inference Improve Resume-to-Job Matching? An Evidence-Grounded Evaluation of Large Language Models

This repository contains the implementation, configuration files, and evaluation code for my SOC10101 Honours Project in Computer Science (AI) at Edinburgh Napier University.

## Project Evolution and Title Change
This project was originally initialized and presented under the title:
* **Original Title:** Skills Predictions from Resume and Matching with Job Posting using Large Language Models

To better reflect the academic scope, controlled experimental design, and the scientific evaluation of the pipeline, the title has been updated to:
* **Current Title:** Does Skill-Level Inference Improve Resume-to-Job Matching? An Evidence-Grounded Evaluation of Large Language Models

---

## Project Overview
The objective of this research is to evaluate whether inferring implicit skills from a resume using a large language model (LLM) improves candidate-to-job ranking performance, or if it primarily introduces evaluation noise. 

While candidates frequently possess underlying capabilities not explicitly stated in their CVs, unconstrained LLM inference can lead to hallucinations. This project implements a controlled experiment comparing traditional semantic matching and explicit skill matching against an LLM-based inference pipeline. To test the validity of inferred skills, the pipeline introduces a verification step requiring the model to extract direct textual evidence from the resume before mapping the skill to the European Skills, Competences, Qualifications and Occupations (ESCO) framework.

---

## Research Questions
* **RQ1:** How accurately does an LLM infer skills which a resume supports but does not state?
* **RQ2:** Does adding inferred skills improve candidate ranking compared with both baselines?
* **RQ3:** How reliably does the quoted evidence for each inferred skill support it?
* **RQ4:** Which kinds of errors does the LLM make when inferring skills?

---

## Controlled Experimental Setups
The system evaluates four matching pipelines on identical resume and job description pairs to isolate the performance impact of skill inference and verification:

* **B1 (Baseline 1):** Full-document semantic similarity scored via cosine similarity on sentence embeddings.
* **B2 (Baseline 2):** Explicit skill matching, extracting written skills from the resume and mapping them directly to job requirements.
* **B3 (Experimental Setup 1):** Explicit skills combined with unconstrained LLM-inferred skills, running without an evidence constraint.
* **B4 (Experimental Setup 2):** Explicit skills combined with verified LLM-inferred skills, strictly retaining concepts that pass the textual quote verification check.

The primary algorithmic evaluation centers on an ablation study between B3 and B4 to measure the utility of the evidence-checking mechanism.

---

## Evaluation Methodology
* **Skill Inference Performance:** Evaluated using standard Precision, Recall, and F1-score against hand-annotated subsets.
* **Ranking Quality:** Scored using Information Retrieval metrics including Mean Average Precision (MAP), Mean Reciprocal Rank (MRR), nDCG@10, and Recall@10.
* **Statistical Significance:** Setup variations are compared using a paired Wilcoxon signed-rank test on per-job ranking scores, accompanied by a paired bootstrap 95% confidence interval and effect size estimations.

---

## Repository Structure
* `notebooks/` - Jupyter Notebooks detailing the data preprocessing, text embedding generation, and pipeline executions for setups B1 through B4.
* `prompts/` - Structured system and few-shot prompt templates used for reproducible LLM skill inference and quote extraction.
* `data/` - Templates and mock profiles for development. True evaluation datasets are omitted to comply with dataset licensing and privacy restrictions.
* `results/` - Evaluation outputs, statistical test logs, and categorized error analysis profiles.

---

## Project Metadata
* **Student:** Al Sifat Siddiki (Student ID: 40735842)
* **Programme:** BSc Computer Science (AI)
* **Supervisor:** Dr Md Zia Ullah
* **Second Marker:** Dr Dimitra Gkatzia
* **Institution:** Edinburgh Napier University
* **Target Submission Date:** 20 April 2027
