

# SakuraLLM-Colab-Notebooks  
 
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/1235357/SakuraLLM-Colab/blob/main/sakura_14b_qwen2_5_v1_0_q6k_gguf_Colab.ipynb)  

---

## **⚠️ Important Warning ⚠️**  
🚨 **Kaggle Ban Notice**: Kaggle has officially banned all SakuraLLM models. Using them on Kaggle will result in a **permanent account ban**.  
👉 **Alternative Options**: Use GPU rental services or community compute-sharing platforms.  
🔗 For more details, see the [Issue Report](https://github.com/Isotr0py/SakuraLLM-Notebooks/issues/14).

---

## 📖 Introduction  
This repository offers an easy-to-use Google Colab notebook to deploy the **[Sakura-14B-Qwen2.5-v1.0-GGUF](https://huggingface.co/SakuraLLM/Sakura-14B-Qwen2.5-v1.0-GGUF)** model:  
- **Backend**: Uses **vLLM** for OpenAI-style API compatibility.  
- **Applications**: Translation tools, GPT-based custom bots, and other AI utilities.  
- **Visualization**: See example output below!  

---

### 💡 Key Features  
✔️ Easy one-click setup in Colab.  
✔️ Supports **OpenAI API** for effortless integration.  
✔️ Multiple API forwarding options (**ngrok** or **localtunnel**).  
✔️ Beginner-friendly guidance, with rich examples and troubleshooting steps.  

---

## 🚀 One-Click Launch in Colab  

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/1235357/SakuraLLM-Colab/blob/main/sakura_14b_qwen2_5_v1_0_q6k_gguf_Colab.ipynb)  

---

### 📊 Example Usage  
Below is a visualization of how the API to be used. Input any text in the prompt for dynamic results!  
<div align="center">  
<img src="https://github.com/user-attachments/assets/894c9935-b7d3-4ea0-af3b-af4876899573" width="600">  
</div>  

---

## 🛠️ Prerequisites  
To get started, you’ll need:  
1. **Google Account**: Access Colab.  
2. **Python Libraries** (installed automatically in the notebook).  
   - `transformers`, `tokenizers`, `vLLM`, `huggingface-hub`, `flask`, `pyngrok`, `triton`, `torch`.  
3. **ngrok Token** (Highly Suggest): Sign up at [ngrok](https://ngrok.com/), log in, and copy your token for API forwarding.  

---

## 📋 Step-by-Step Explaination  

### **Step 1: Mount Google Drive (Highly Suggest)**  
Mounting Google Drive ensures you can save models persistently across sessions.  
Paste this code into a Colab cell:  
```python
from google.colab import drive
drive.mount('/content/gdrive')
ROOT_PATH = "/content/gdrive/MyDrive"
```  
⚠️ **Skipping This Step**: Set the working directory to `/content` if you choose not to mount:  
```python
ROOT_PATH = "/content"
```  

---

### **Step 2: Install Required Libraries**  
Run this command in Colab to install all dependencies:  
```bash
!pip install --upgrade pip
!pip install transformers tokenizers vllm huggingface-hub flask pyngrok triton torch
```  

---

### **Step 3: API Forwarding Configuration**  
- If you have an **ngrok token**, paste it into the `ngrokToken` variable:  
  ```python
  ngrokToken = "YOUR_NGROK_TOKEN"  # Replace with your token
  ```
- If no token is provided, the notebook will use **localtunnel** by default.  

⏳ **Output**: The notebook will display your public API URL. Save this for use in API requests.  

---

### **Step 4: Download the Model**  
First-time users must download the model to the working directory:  
```bash
!HF_ENDPOINT=https://huggingface.co huggingface-cli download SakuraLLM/Sakura-14B-Qwen2.5-v1.0-GGUF \
  --local-dir models \
  --include sakura-14b-qwen2.5-v1.0-q6k.gguf
```

---

### **Step 5: Launch vLLM Backend**  
Start the API backend with this command:  
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

💻 **Result**: A public API URL (e.g., `http://localhost:8001` or an ngrok URL).  

---

## 🔧 Testing the API  

### Python Example Code  
Use the following script to send requests to the API. Replace `<YOUR_API_URL>` with the public API endpoint.  
```python
import requests

API_ENDPOINT = "<YOUR_API_URL>"  # Replace with your API URL
API_KEY = "token-abc123"  # Replace with your API key

headers = {"Authorization": f"Bearer {API_KEY}"}
data = {
    "prompt": "Translate this sentence to Japanese: 'Good morning!'",
    "max_tokens": 50
}

response = requests.post(f"{API_ENDPOINT}/v1/completions", json=data, headers=headers)
print(response.json())
```

---

## ❓ FAQ  

### **Q1: What is the purpose of mounting Google Drive?**  
Mounting Drive ensures all downloaded models and intermediate data are saved for future sessions. Without this, data is erased when Colab disconnects.  

### **Q2: Do I need a powerful GPU?**  
No, the notebook is designed for free-tier Colab GPUs. However, performance may improve with Colab Pro or rented GPUs.  

### **Q3: How do I troubleshoot API connection issues?**  
- Ensure `ngrokToken` is correctly set (if using ngrok).  
- Check the public URL displayed after Step 5.  
- Restart the notebook if problems persist.  

### **Q4: Can I modify the model?**  
Yes! Fine-tune the model using tools like Hugging Face’s **transformers** library. For large models, ensure adequate GPU resources.  

---

## 🙌 Acknowledgments  
- **[SakuraLLM](https://github.com/SakuraLLM/SakuraLLM)**: For providing the model.  
- **[SakuraLLM-Notebooks](https://github.com/Isotr0py/SakuraLLM-Notebooks)**: For inspiring this repository.  

---
