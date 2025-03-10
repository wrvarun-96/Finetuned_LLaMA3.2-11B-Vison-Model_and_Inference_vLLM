# 🚀 Finetuned LLaMA 3.2-11B Vision Model and Inference with vLLM on RunPod

This repository contains the **fine-tuned LLaMA 3.2-11B Vision Model** for **radiology image analysis**, along with **efficient inference using vLLM on RunPod**. The model was fine-tuned using **LoRA (Low-Rank Adaptation)** with **Unsloth**, optimized with **4-bit quantization (bitsandbytes)**, and deployed using **Chainlit**.

---

## 📖 **Project Overview**
- **Model**: `LLaMA 3.2-11B Vision`
- **Fine-Tuning Framework**: `Unsloth`
- **Inference Engine**: `vLLM on RunPod`
- **Dataset**: `unsloth/Radiology_mini`
- **Training Method**: `LoRA` (Parameter Efficient Fine-Tuning)
- **Quantization**: `4-bit`
- **Deployment**: `Chainlit` chatbot

---

## 📂 **Repository Structure**
```plaintext
📦 Finetuned_LLaMA3.2-11B-Vision-Model_and_Inference_vLLM
├── chat.py                    # Chainlit-powered chatbot for image inference
├── Fine_Tuned_LLaMA3.2_Model.ipynb  # Jupyter Notebook for model fine-tuning
├── requirements.txt            # Required dependencies
├── chainlit.md                 # Documentation for running Chainlit
├── vllm/                       # vLLM inference scripts
├── __pycache__/                # Python cache files
└── README.md                   # Project documentation (this file)
