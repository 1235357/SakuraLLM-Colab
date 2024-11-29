



# SakuraLLM-Colab-Notebooks  
 
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/1235357/SakuraLLM-Colab/blob/main/sakura_14b_qwen2_5_v1_0_q6k_gguf_Colab.ipynb)  

---



# 📑 Table of Contents

1. [⚠️ Important Warning ⚠️](#️-important-warning-️)
2. [📖 Introduction](#-introduction)
   - [💡 Key Features](#-key-features)
3. [🚀 One-Click Launch in Colab](#-one-click-launch-in-colab)
4. [📊 Example Usage](#-example-usage)
5. [🛠️ Prerequisites](#️-prerequisites)
6. [📋 Step-by-Step Explanation](#-step-by-step-explanation)
   - [Step 1: Mount Google Drive](#step-1-mount-google-drive)
   - [Step 2: Install Required Libraries](#step-2-install-required-libraries)
   - [Step 3: Ngrok API Forwarding Configuration](#step-3-ngrok-api-forwarding-configuration)
     - [Option 1: Using Ngrok](#option-1-using-ngrok-static-domain)
     - [Option 2: Using Cloudflare Tunnel](#option-2-using-cloudflare-tunnel-temporary-url)
   - [Step 4: Downloading the Model and Starting the API Server](#step-4-downloading-the-model-and-starting-the-api-server)
7. [🔧 Testing the API](#-testing-the-api)
   - [Python Example Code](#python-example-code)
8. [❓ FAQ](#-faq)
   - [Q1: What is the purpose of mounting Google Drive?](#q1-what-is-the-purpose-of-mounting-google-drive)
   - [Q2: Do I need a powerful GPU?](#q2-do-i-need-a-powerful-gpu)
   - [Q3: I encountered the error "Failed to infer device type." What does it mean?](#q3-i-encountered-the-error-failed-to-infer-device-type-what-does-it-mean)
   - [Q4: How do I troubleshoot API connection issues?](#q4-how-do-i-troubleshoot-api-connection-issues)
   - [Q5: Can I modify the model?](#q5-can-i-modify-the-model)
   - [Q6: What is the API Key and model name?](#q6-what-is-the-api-key-and-model-name)
   - [Q7: Why doesn’t the public API URL work with the Sakura workspace?](#q7-why-doesnt-the-public-api-url-work-with-the-sakura-workspace)
   - [Q8: Is it safe to use Colab for this project?](#q8-is-it-safe-to-use-colab-for-this-project)
   - [Q9: Is there a one-click setup?](#q9-is-there-a-one-click-setup)
9. [🙌 Acknowledgments](#-acknowledgments)



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


>
>> The vLLM backend supports adding multiple translators at the same time (request concurrency)
>


<div align="center">  
<img src="https://github.com/user-attachments/assets/dfe4597c-ab74-4a14-a3d0-5de3d00b21d2" width="600">  
</div>  


<div align="center">  
<img src="https://github.com/user-attachments/assets/01b07aa1-6667-487e-be1a-11c9ae92d55f" width="600">  
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

### **Step 3: API Forwarding Configuration Using Ngrok or Cloudflare**

This step helps you configure API forwarding so that your application can be accessed over the internet, even if you don't have a static domain. We'll guide you through two options:

1. **Using Ngrok** - For static domain forwarding with a custom domain.  
2. **Using Cloudflare Tunnel** - For temporary API access.  

---

#### **Option 1: Using Ngrok (Static Domain)**

Ngrok simplifies API forwarding by providing a secure and reliable tunnel. If you need a static domain for consistent access, follow these steps:

---

##### **Steps to Set Up Ngrok**

1. **Get Your Ngrok Authentication Token**  
   - Visit [Ngrok's Dashboard](https://dashboard.ngrok.com/get-started/your-authtoken).  
   - Sign up or log in to your account.  
   - Copy your **authentication token** from the page.

   <div align="center">  
   <img src="https://github.com/user-attachments/assets/26b7f148-d540-4f65-bd29-2a0009c719cc" width="600">  
   </div>  

2. **Obtain a Free Static Domain**  
   - Navigate to the **Domains** section on the [Ngrok Dashboard](https://dashboard.ngrok.com/domains).  
   - Click **"New Domain"** to create a free static domain for your API.  

   <div align="center">  
   <img src="https://github.com/user-attachments/assets/1baa2d73-46fb-4a67-91b2-db261fdb48bd" width="600">  
   </div>  

---

##### **Python Code for Ngrok Configuration**

Add the following Python code to your project to set up Ngrok with your static domain:

```python
# Set the ngrok authentication token (get it from https://dashboard.ngrok.com/get-started/your-authtoken)
ngrokToken = ""  # Add your token here

if ngrokToken:
    from pyngrok import conf, ngrok
    
    # Configure the ngrok authentication token
    conf.get_default().auth_token = ngrokToken
    conf.get_default().monitor_thread = False

    # Start ngrok tunnel with the custom domain
    try:
        # Set the ngrok free static domain (from https://dashboard.ngrok.com/domains)
        ssh_tunnel = ngrok.connect(8001, bind_tls=True, hostname="")
        public_url = ssh_tunnel.public_url
        print('Custom Domain Address: ' + public_url)
    except Exception as e:
        print(f"Error starting ngrok tunnel: {e}")
```

---

##### **Expected Output**
- The script will display your public API URL on the **first line** of the output.  
- Save this URL; you’ll use it for making API requests.  

---

#### **Option 2: Using Cloudflare Tunnel (Temporary URL)**

If you don’t have a static domain or an Ngrok authentication token, Cloudflare’s `cloudflared` provides a quick, temporary URL for API access.  

---

##### **Steps to Set Up Cloudflare Tunnel**

1. **Download the `cloudflared` Binary**  
   Run the following commands to download and prepare `cloudflared` for use:

   ```bash
   # Navigate to the root path of your project
   %cd $ROOT_PATH

   # Download the latest Cloudflare binary
   !wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 -O cloudflared
   !chmod a+x cloudflared
   ```

2. **Start the Tunnel**  
   Execute this command to open a Cloudflare tunnel:

   ```bash
   !./cloudflared tunnel --url localhost:8001
   ```

---

##### **Expected Output**
- A temporary Cloudflare URL will appear in the output.  
- Use this URL for testing API requests during your development session.  

---

#### **Tips for Beginners**

- **Ngrok vs. Cloudflare**:  
   - Use **Ngrok** if you need a persistent, custom domain for reliable API access.  
   - Use **Cloudflare** for a quick, temporary solution without account setup.  

- **Best Practices**:  
   - Save the displayed URLs immediately after running the commands.  
   - Test the connection by accessing the URL in your browser or API client.

By following these steps, you’ll successfully set up API forwarding for your project using either Ngrok or Cloudflare.






---

### **Step 4: Downloading the Model and Starting the API Server**  

Once the tunnel is set up, proceed to download the model and run the API server:  

```bash
# Navigate to the root path
%cd $ROOT_PATH

# Download the model from Hugging Face
!HF_ENDPOINT=https://huggingface.co huggingface-cli download SakuraLLM/Sakura-14B-Qwen2.5-v1.0-GGUF --local-dir models --include sakura-14b-qwen2.5-v1.0-q6k.gguf

# Start the API server with vLLM
!RAY_memory_monitor_refresh_ms="0" HF_ENDPOINT=https://huggingface.co OMP_NUM_THREADS=36 \
VLLM_ATTENTION_BACKEND=XFORMERS vllm serve ./models/sakura-14b-qwen2.5-v1.0-q6k.gguf \
--tokenizer Qwen/Qwen2.5-14B-Instruct --dtype float16 --api-key token-abc123 \
--kv-cache-dtype auto --max-model-len 4096 --tensor-parallel-size 1 \
--gpu-memory-utilization 0.99 --disable-custom-all-reduce --enforce-eager \
--use-v2-block-manager --disable-log-requests --host 0.0.0.0 --port 8001 \
--served-model-name "Qwen2.5-14B-Instruct" &
```

⏳ **Output**: Your API backend will start, and you can use the displayed public URL from the previous step for making requests.



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
Mounting Drive ensures that all downloaded models and intermediate data are preserved between sessions. Without this, data is erased when Colab disconnects.  

### **Q2: Do I need a powerful GPU?**  
No, the notebook is designed for use with free-tier Colab GPUs. However, performance and speed may improve if you use Colab Pro, Colab Pro+, or rented GPUs with higher memory capacity.  

### **Q3: I encountered the error "Failed to infer device type." What does it mean?**  
This typically happens when:  
1. Insufficient GPU memory is available for the model.  
2. The notebook is configured to use GPU, but Colab assigns a CPU-only runtime.  
3. A dependency conflict in the environment.

#### Solutions:  
- Check if the assigned runtime is GPU-enabled (`Runtime > Change runtime type > Hardware accelerator > GPU`).  
- Verify that the model's size fits within your GPU’s memory capacity (15GB is usually sufficient for most tasks).  
- Restart the runtime, clear storage if needed, and re-run the notebook.

---

### **Q4: How do I troubleshoot API connection issues?**  

#### If you're using ngrok:  
- Ensure your `ngrokToken` is correctly set and matches your ngrok account.  
- Confirm that the generated public URL appears in the output after Step 3.  
- Verify the connection by opening the public URL in a browser to check the API's availability.  

#### If the public URL works but not in the Sakura workspace:  
- Ensure the API Key specified during setup (e.g., `--api-key token-abc123`) matches the key used in Sakura.  
- Double-check the model name (e.g., `--served-model-name "Qwen2.5-14B-Instruct"`) for consistency.  

For Cloudflare users, remember that the URL is temporary and may require reconfiguration between sessions.  

---

### **Q5: Can I modify the model?**  
Yes! The notebook supports fine-tuning or modifications to the model using tools like Hugging Face's **transformers** library. For large models, ensure you have sufficient GPU resources. Cloud environments may not always support extensive fine-tuning, but you can use your local machine or rented servers for advanced customization.

---

### **Q6: What is the API Key and model name?**  
- The **API Key** is manually set during the vLLM backend setup. For example, in the code:  
  ```bash
  --api-key token-abc123
  ```
  Use the same API Key (`token-abc123`) in the Sakura workspace or other applications.  

- The **model name** is defined in the setup as:  
  ```bash
  --served-model-name "Qwen2.5-14B-Instruct"
  ```
  Ensure you input this exact model name in the application using the API.  

---

### **Q7: Why doesn’t the public API URL work with the Sakura workspace?**  
This is commonly due to:  
1. **Incorrect API Key**: Ensure the key matches what was set during the vLLM server startup.  
2. **Model name mismatch**: The model name used in the backend must match the one configured in the Sakura workspace.  
3. **Dynamic URLs**: If you use a non-static URL (e.g., without a custom ngrok domain), the URL changes with each session.  

#### Suggested Solution:  
- Double-check the API Key and model name used in the workspace.  
- For persistent URLs, use a static ngrok domain or migrate to a local hosting setup for stability.  

---

### **Q8: Is it safe to use Colab for this project?**  
Using Colab for personal or research projects is generally acceptable. However, avoid engaging in activities that violate Google's [usage policies](https://research.google.com/colaboratory/faq.html?hl=en#disallowed-activities), such as excessive resource usage or sharing Colab-generated APIs publicly without restrictions. Always respect the terms of service to prevent potential limitations or bans.  

---

### **Q9: Is there a one-click setup?**  
Yes! The Colab notebook includes a one-click launcher link for streamlined operation. Simply open the link and run all cells without modifying the code. This setup is tested to work seamlessly as long as runtime conditions are met.















---

## 🙌 Acknowledgments  
- **[SakuraLLM](https://github.com/SakuraLLM/SakuraLLM)**: For providing the model.  
- **[SakuraLLM-Notebooks](https://github.com/Isotr0py/SakuraLLM-Notebooks)**: For inspiring this repository.  

---
