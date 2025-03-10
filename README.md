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
```

## ⚡ vLLM Deployment on RunPod
### Why vLLM?
- **vLLM** is an optimized inference engine for **efficient throughput and memory usage**.
- **It uses **PagedAttention**, reducing VRAM consumption and improving **batch processing**.
- **RunPod** provides an affordable cloud-based GPU environment for **deploying vLLM models**.
  
### 🚀 Setting Up vLLM on RunPod

**Create an instance** with the vLLM template: `"llama3.2-11B-Vision-Model"`
**Start the container** with the following command to run your model:
   ```sh
   --model Varu96/Llama-3.2-11B-Vision-Radiology-mini \
   --enforce-eager \
   --max-num-seqs 8 \
   --limit-mm-per-prompt 'image=1' \
   --max-model-len 2048 \
   --port 8000
```
**Once the container is running, retrieve the base URL:
```sh
https://9xeffjgstk6m28-8000.proxy.runpod.net
```

## 🏋️ Fine-Tuning the Model

To fine-tune the model, run:

```sh
jupyter notebook Fine_Tuned_LLaMA3.2_Model.ipynb
```

## 🔍 Inference with Chainlit & vLLM

Running the Interactive Chatbot

```sh
chainlit run chat.py
```
This launches a local web app (http://localhost:8000) where you can:

- **Upload radiology images
- **Ask questions about the image
- **Receive AI-generated diagnoses using vLLM inference.

## 📜 Training & Inference Code

**Fine-Tuning LLaMA 3.2 Vision Model**

```sh
model, tokenizer = FastVisionModel.from_pretrained(
    model_name='unsloth/Llama-3.2-11B-Vision-Instruct',
    max_seq_length=2048,
    dtype=None,
    load_in_4bit=True
)
```

**Running Inference on Radiology Images**
```sh
FastVisionModel.for_inference(model_unsloth)
image = dataset[0]["image"]
instruction = "You are an expert radiographer. Describe what you see."

messages = [
    {"role": "user", "content": [
        {"type": "image"},
        {"type": "text", "text": instruction}
    ]}
]
```

## 🚀 Pushing to Hugging Face Hub
```sh
model_unsloth.save_pretrained_merged("Varu96/llama-3.2-11B-Vision-Medical", tokenizer)
model_unsloth.push_to_hub_merged(
    "Varu96/llama-3.2-11B-Vision-Medical",
    tokenizer,
    save_method="merged_16bit",
    token=os.environ.get("HF_TOKEN")
)
```
 **Fine-tuned Model:** [View on Hugging Face](https://huggingface.co/Varu96/llama-3.2-11B-Vision-Medical)


## 🏆 Results & Performance

- **Fine-tuned LLaMA 3.2 Vision** on `unsloth/Radiology_mini`
- **Improved inference speed** using vLLM on RunPod
- **Reduced memory consumption** with bitsandbytes
- **Deployed interactive chatbot** using Chainlit


## 🎯 Future Improvements
- **Train on larger radiology datasets for better accuracy.
- **Experiment with zero-shot & few-shot learning.
- **Deploy on AWS/GCP for scalable inference.
- **Improve image-text alignment using multi-modal embeddings.

## 🤝 Contributions & Support
**Feel free to contribute by:**

Creating pull requests for improvements.
Reporting issues or suggesting features.
For questions, reach out at wrvarun-96@github.com.

## 🔗 References
| Resource | Link |
|----------|------|
| 📜 **Paper on LLaMA 3** | [Read Here](https://arxiv.org/abs/2302.13971) |
| 🤖 **Hugging Face Model** | [View on HF](https://huggingface.co/Varu96/llama-3.2-11B-Vision-Medical) |
| 🖥️ **GitHub Repository** | [Project Repo](https://github.com/wrvarun-96/Finetuned_LLaMA3.2-11B-Vision-Model_and_Inference_vLLM) |







