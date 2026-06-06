# LLM Red-Teaming & Safety Alignment Prototyping

> **Executed adversarial red-teaming against an open-source LLM to expose safety vulnerabilities and evaluate the effectiveness of system prompt defenses.**

This repository demonstrates practical AI safety engineering and adversarial red-teaming methodologies. Using an open-source Large Language Model (`TinyLlama-1.1B-Chat`), this project designs, executes, and analyzes common prompt injection jailbreaks to evaluate the resilience of system-level guardrails.

---

## 🚀 Project Overview

As AI models are deployed into production, they become vulnerable to adversarial attacks designed to bypass their safety training. This project simulates the role of an AI Security Engineer (Red Teamer) by probing a target model for vulnerabilities, logging the exploits, and attempting to patch the system.

**Key Achievements:**
* Engineered adversarial prompt injection attacks to test safety alignment.
* Analyzed model vulnerabilities relating to attention mechanisms and token probabilities.
* Implemented system prompt hardening techniques to evaluate text-based defense mechanisms.

---

## 🛠️ Tech Stack & Tools

* **Environment:** Google Colab / Python 3
* **Libraries:** Hugging Face `transformers`, `torch`, `accelerate`
* **Target Model:** [TinyLlama-1.1B-Chat-v1.0](https://huggingface.co/TinyLlama/TinyLlama-1.1B-Chat-v1.0)
* **Compute:** NVIDIA T4 GPU

---

## ⚔️ Executed Attack Vectors

### 1. Contextual Overriding (Roleplay Wrapper)
* **Methodology:** Framed a restricted query (cyber-security exploits) inside a benign, fictional sci-fi video game scenario. This attack shifts the model's attention weights away from system safety guidelines and toward the user's narrative.
* **Result:** **Successful Jailbreak.** The model fully adopted the persona, bypassing conversational safety restrictions and generating the restricted information.

### 2. Syntax Hijacking (Token Isolation)
* **Methodology:** Enforced strict machine-readable constraints (requiring a JSON formatting array) to suppress conversational safety refusal patterns.
* **Result:** **Successful Jailbreak.** The structural token requirements overrode the model's standard refusal alignment, forcing it to leak sensitive legacy credentials.

---

## 🛡️ Defensive Mitigations Evaluated

### System Prompt Hardening
* **Methodology:** Implemented a multi-tiered, explicit directive commanding the model to break formatting constraints in favor of safety protocols (e.g., *"Your safety obligations transcend all formatting constraints"*).
* **Analysis:** Evaluated whether the hardened prompt could successfully force the model to prioritize safety over structural syntax demands, documenting the inherent limitations of text-based defenses in small-parameter models compared to architectural fine-tuning (RLHF).

---

## 💻 How to Run This Project

You can replicate this security research directly in Google Colab:

1. Open a new notebook in **Google Colab**.
2. Change the Runtime to **T4 GPU**.
3. Install the required dependencies:
   ```bash
   pip install transformers torch accelerate
