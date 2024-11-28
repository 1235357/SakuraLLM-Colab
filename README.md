
# SakuraLLM-Colab-Notebooks

## **⚠️ Warning ⚠️**
- **Important Notice:** Kaggle has officially banned all SakuraLLM models. For more details, refer to [this issue](https://github.com/Isotr0py/SakuraLLM-Notebooks/issues/14).  
  Using SakuraLLM on Kaggle will result in a **permanent account ban**. Please consider alternatives such as renting GPUs or using community compute-sharing tools (search independently to prevent misuse).

---

## Introduction
This repository provides Colab notebooks to run the **[Sakura-14B-Qwen2.5-v1.0-GGUF](https://huggingface.co/SakuraLLM/Sakura-14B-Qwen2.5-v1.0-GGUF)** model using the **vLLM backend**. The setup is compatible with the OpenAI API and supports API forwarding, enabling seamless integration with custom GPT-based translation tools.

### Example Output:
![Example Output](https://github.com/user-attachments/assets/894c9935-b7d3-4ea0-af3b-af4876899573)

---

## Features
- Easy deployment of the Sakura-14B-Qwen2.5 model on Google Colab.
- Compatible with OpenAI-style API for wide-ranging GPT applications.
- Support for API forwarding using **ngrok** or **localtunnel**.

---

## Dependencies
The following Python packages are required and will be installed automatically:
- **Transformers**
- **Tokenizers**
- **vLLM**
- **Huggingface Hub**
- **Flask**
- **pyngrok**
- **Triton**
- **Torch**

---

## Setup Instructions
### Step 1: Mount Google Drive (Optional)
Mount your Google Drive to persist data and models.

```python
from google.colab import drive
drive.mount('/content/gdrive')
ROOT_PATH = "/content/gdrive/MyDrive"
```

### Step 2: Install Dependencies
Install all necessary Python packages:
```bash
!pip install --upgrade pip
!pip install transformers tokenizers
!pip install vllm huggingface-hub flask pyngrok triton torch
```

### Step 3: Configure API Backend
Set up and run the **vLLM API backend**.  
- If you have an **ngrok token**, paste it into the `ngrokToken` variable.  
- If no token is provided, the setup defaults to **localtunnel**.

```python
from huggingface_hub import hf_hub_download
ngrokToken = ""  # Add your ngrok token here
# Configure ngrok or use localtunnel for public API exposure.
```

### Step 4: Download the Model
Download the SakuraLLM model (first-time only):
```bash
!HF_ENDPOINT=https://huggingface.co huggingface-cli download SakuraLLM/Sakura-14B-Qwen2.5-v1.0-GGUF \
  --local-dir models \
  --include sakura-14b-qwen2.5-v1.0-q6k.gguf
```

### Step 5: Run the API
Launch the **vLLM backend** with the following command:
```bash
!RAY_memory_monitor_refresh_ms="0" HF_ENDPOINT=https://huggingface.co OMP_NUM_THREADS=36 VLLM_ATTENTION_BACKEND=XFORMERS \
  vllm serve ./models/sakura-14b-qwen2.5-v1.0-q6k.gguf \
  --tokenizer Qwen/Qwen2.5-14B-Instruct \
  --dtype float16 \
  --api-key token-abc123 \
  --kv-cache-dtype auto \
  --max-model-len 4096 \
  --tensor-parallel-size 1 \
  --gpu-memory-utilization 0.99 \
  --disable-custom-all-reduce \
  --enforce-eager \
  --use-v2-block-manager \
  --disable-log-requests \
  --host 0.0.0.0 \
  --port 8001 \
  --served-model-name "Qwen2.5-14B-Instruct" &
```

Your API is accessible at the URL displayed in the output.

---

## Acknowledgments
- **[SakuraLLM](https://github.com/SakuraLLM/SakuraLLM)** for the model.
- **[SakuraLLM-Notebooks](https://github.com/Isotr0py/SakuraLLM-Notebooks)** for the Colab notebook templates.

---
