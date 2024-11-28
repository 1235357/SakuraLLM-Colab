

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
<img src="https://github.com/user-attachments/assets/e17d1536-c372-4519-ac30-07b6cc6bbcf6" width="600">  
</div>  


<div align="center">  
<img src="https://github.com/user-attachments/assets/ade15643-d324-4ca9-ac1e-4bc20f9e0fd6" width="600">  
</div>  


<div align="center">  
<img src="https://github.com/user-attachments/assets/a2b623a5-6c94-44d3-9d7f-d93db8b8eae8" width="600">  
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

To install all necessary libraries, run the following command in your Colab notebook:  

```bash
!pip install --upgrade pip
!pip install transformers tokenizers vllm huggingface-hub flask pyngrok triton torch
```

---

### **Important Note:**  

Sometimes, during the installation process, you may encounter errors or warnings similar to the one shown below:  

<div align="center">  
<img src="https://github.com/user-attachments/assets/aa34e879-48d2-4896-9881-3b932741e665" width="600" alt="Installation Warning Example">  
</div>  

**What to do:**  
This is a normal occurrence, especially in Colab environments. Simply follow the instructions provided by the error message. In most cases, you can resolve the issue by clicking:  

1. **Runtime** (in the top Colab menu).  
2. Select **"Run all"** to restart the setup process.  

If it prompts you to re-enable certain permissions or runtime settings, accept those changes.

---

For further reassurance, here's another example of such an error you might see:  

<div align="center">  
<img src="https://github.com/user-attachments/assets/3b6955e0-d7d2-42ce-a167-318d2c69b6f5" width="600" alt="Runtime Restart Example">  
</div>  

By following these simple steps, you'll ensure that all dependencies are properly installed and your environment is correctly configured. If you continue to face issues, consider resetting the Colab runtime and re-running the commands.


---






### **Step 3: Ngrok API Forwarding Configuration**  

Set up ngrok with a static domain for consistent API access:  
```python
# Run API backend (vLLM)
# Use ngrok for API mapping
from huggingface_hub import hf_hub_download

# Set the ngrok authentication token
ngrokToken = "2pR573GJUUUuRlAPKFQcKemTJk7_2uisJCJJ8ng8ERcwBexTp"

if ngrokToken:
    from pyngrok import conf, ngrok
    
    # Configure the ngrok authentication token
    conf.get_default().auth_token = ngrokToken
    conf.get_default().monitor_thread = False

    # Start ngrok tunnel with the custom domain
    try:
        ssh_tunnel = ngrok.connect(8001, bind_tls=True, hostname="devoted-hen-awaited.ngrok-free.app")
        public_url = ssh_tunnel.public_url
        print('Custom Domain Address: ' + public_url)
    except Exception as e:
        print(f"Error starting ngrok tunnel: {e}")



%cd $ROOT_PATH

# Download the model for the first time
!HF_ENDPOINT=https://huggingface.co huggingface-cli download SakuraLLM/Sakura-14B-Qwen2.5-v1.0-GGUF --local-dir models --include sakura-14b-qwen2.5-v1.0-q6k.gguf

!RAY_memory_monitor_refresh_ms="0" HF_ENDPOINT=https://huggingface.co OMP_NUM_THREADS=36 VLLM_ATTENTION_BACKEND=XFORMERS vllm serve ./models/sakura-14b-qwen2.5-v1.0-q6k.gguf --tokenizer Qwen/Qwen2.5-14B-Instruct --dtype float16 --api-key token-abc123 --kv-cache-dtype auto --max-model-len 4096 --tensor-parallel-size 1 --gpu-memory-utilization 0.99 --disable-custom-all-reduce --enforce-eager --use-v2-block-manager --disable-log-requests --host 0.0.0.0 --port 8001 --served-model-name "Qwen2.5-14B-Instruct" &


```

⏳ **Output**: The notebook will display your public API URL ***in the first line***. Save this for use in API requests.  

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
