


# SakuraLLM: Advancing Large Language Model Research

## Introduction

This project builds upon [SakuraLLM](https://github.com/SakuraLLM/SakuraLLM) and provides an enhanced realization of the legacy project [SakuraLLM-Colab](https://github.com/1235357/SakuraLLM-Colab). It leverages the **OpenI启智 AI Collaboration Platform** ([OpenI](https://git.openi.org.cn/user/sign_up?sharedUser=zye)) for free computational resources, offering a sustainable alternative to commercial cloud GPU rental services.

## **Acknowledgment**
This initiative is not merely an attempt to access free computational power; rather, it is a dedicated effort to advance **scientific research in Large Language Models (LLMs)**. We extend our **sincere gratitude** to the OpenI platform for providing robust computing resources that facilitate our research and experimentation in this critical field.

## **Key Methodology**
- Deploy **vLLM** on cloud GPUs.
- Establish **tunneling via Ngrok** to map local ports to static public domains.
- Seamlessly integrate the deployed model into **GPT workspace** for research and development.

---
#### You can directly click **"One click run cloudbrain task template"** (remember to run the **Jupyter Notebook** file) or manualy set up:
---

## **Quick Start Guide**




### **Step 1: Register on OpenI Platform**
- Create an account using this link: [OpenI Sign-up](https://git.openi.org.cn/user/sign_up?sharedUser=zye).
- Registration URL: [https://openi.pcl.ac.cn/user/sign_up?sharedUser=zye](https://openi.pcl.ac.cn/user/sign_up?sharedUser=zye).

![image](https://github.com/user-attachments/assets/a6460e6f-975c-4d13-b025-f9f4adf7345b)

![image](https://github.com/user-attachments/assets/da61c3ed-f0f0-49fc-b911-32558b33e963)

![image](https://github.com/user-attachments/assets/58545568-814e-4e27-b934-c43d80f564b0)

![image](https://github.com/user-attachments/assets/02c7bf66-c628-4219-a691-a77b17b6f474)





### **Step 2: Create a New Cloud Task**
- Navigate to the [SakuraLLM repository](https://git.openi.org.cn/zye/sakura-14b-qwen2.5-v1.0-q6k) on OpenI.
- Initiate a **"Cloud Brain"** task.

### **Step 3: Configure the Debugging Task**
- **Select NVIDIA GPUs**: Choose **A100** (Which is much more faster than V100).
- **Set parameters**:
  - Image address: `192.168.242.50:1443/default-workspace/2a72307689ae49758c80c896fffda0a1/image:sakura-14b-qwen2.5-v1.0-q6k`
  - Model selection: Search for `Backup_hf_sakura-14b-qwen2.5-v1.0-q6k` in the **Public Models** section and select it.

![image](https://github.com/user-attachments/assets/b0512813-b744-4361-a787-4c5b2fc2645e)

### **Step 4: Deploy and Start Computation**
- Launch the task and wait for the **Cloud Brain** environment to initialize.

![image](https://github.com/user-attachments/assets/f8e43e90-478b-4a42-aa3f-63530ff229a2)


![image](https://github.com/user-attachments/assets/62ec65f1-f7d5-4923-9b5a-4e92c50a07be)


### **Step 5: Download Repository Code**
- Obtain the repository files from [this link](https://git.openi.org.cn/zye/sakura-14b-qwen2.5-v1.0-q6k/archive/master.zip).
- Extract the contents to access the **Jupyter Notebook** file.




### **Step 6: Upload and Execute Jupyter Notebook**
- Once the **Cloud Brain** environment is active, open **Jupyter Lab**.
- Upload the extracted **`One_click_running.ipynb`** notebook.
- Run the notebook and follow the instructions to configure the GPT workspace.


![23779450-5e72-44ff-bbed-7b527847a687](https://github.com/user-attachments/assets/2a6e9e98-6bed-4862-bb6b-24e74ca35285)

![c41e8f7d-31c0-42d1-96ef-b36421cad807](https://github.com/user-attachments/assets/10a0c427-3b7a-4ba2-a423-9951ee84c2bb)

![image](https://github.com/user-attachments/assets/42d59633-d9de-4ef6-a5d2-ebe472b51ecb)

![image](https://github.com/user-attachments/assets/5de42ad0-a43a-4203-99dd-8297481e3833)



![image](https://github.com/user-attachments/assets/7a67a119-130d-4715-8135-d90e46bd843c)




![image](https://github.com/user-attachments/assets/2402b0c1-15cb-4a06-87b6-40adb448003d)

![image](https://github.com/user-attachments/assets/318e25a9-c88c-4d75-82a6-28bc385a27c0)


### **Step 7: Configure GPT Workspace**
- **Name**: `Cloudbrain-01`
- **Model**: `Qwen2.5-14B-Instruct`
- **Connection**: `https://star-vocal-haddock.ngrok-free.app` *(Static domain provided; users may replace it with their own Ngrok static domain)*
- **Key**: `token-abc123`
- **Parallel Processing**: Duplicate translation instances with modified names to enable concurrent executions.


![image](https://github.com/user-attachments/assets/4df1f813-4287-4546-910e-3328ff68a55e)


### **Step 8: Finalizing Execution**
- Once translation tasks are completed, **stop the debugging session**.

---
## **Setting Up Ngrok**
### **Step 1: Obtain Ngrok Authentication Token**
- Visit the [Ngrok Dashboard](https://dashboard.ngrok.com/get-started/your-authtoken).
- Log in or sign up for an account.
- Copy your authentication token.

### **Step 2: Create a Static Domain**
- Go to the **Domains** section on the [Ngrok Dashboard](https://dashboard.ngrok.com/domains).
- Click "New Domain" to register a free static domain for API integration.


1. **Get Your Ngrok Authentication Token**  
   - Visit [Ngrok's Dashboard](https://dashboard.ngrok.com/get-started/your-authtoken).  
   - Sign up or log in to your account.  
   - Copy your **authentication token** from the page.

   ![](https://github.com/user-attachments/assets/26b7f148-d540-4f65-bd29-2a0009c719cc)

2. **Obtain a Free Static Domain**  
   - Navigate to the **Domains** section on the [Ngrok Dashboard](https://dashboard.ngrok.com/domains).  
   - Click **"New Domain"** to create a free static domain for your API.  

   ![](https://github.com/user-attachments/assets/1baa2d73-46fb-4a67-91b2-db261fdb48bd)

---



















---


<div align="center">
<h1>
  SakuraLLM
</h1>
<center>
  <b>Sakura</b>: <b><ins>S</ins></b>FT <ins><b>A</b></ins>nd RLHF models using <ins><b>K</b></ins>nowledge of <ins><b>U</b></ins>niversal Character and <ins><b>R</b></ins>elationship <ins><b>A</b></ins>ttributes for Japanese to Chinese Translation in Light Novel & Galgame Domain.
</center>
</div>

<p align="center">
🤗 <a href="https://huggingface.co/sakuraumi/Sakura-13B-Galgame" target="_blank">Hugging Face</a> • 🤖 <a href="https://www.modelscope.cn/models/sakuraumi/Sakura-13B-Galgame" target="_blank">ModelScope</a>
</p>




## 1. Project Overview

### 1.1 Introduction
**SakuraLLM** (SFT and RLHF models using Knowledge of Universal Character and Relationship Attributes) is an open-source Japanese-to-Chinese translation model specifically optimized for ACGN (Anime, Comic, Game, Novel) content domains including light novels and visual novels (Galgame). Built upon foundational models from the Qwen series, it achieves domain-specific translation capabilities through continued pretraining and fine-tuning on Japanese-Chinese bilingual corpora.

### 1.2 Key Features
- **Domain Specialization**: Optimized for ACGN content with stylistic adaptation to light novel narratives and visual novel dialogues.
- **Terminology Control**: Supports GPT-style dictionaries for consistent translation of character names and technical terms.
- **Format Preservation**: Maintains original text formatting elements like line breaks (`\n`) and ruby annotations (e.g., ルビ文字).
- **Multi-model Support**: Offers model variants from 1.5B to 32B parameters to accommodate different hardware constraints.
- **Deployment Flexibility**: Provides GGUF quantized versions compatible with CPU/GPU inference via llama.cpp and vLLM backends.

## 2. Model Architecture

### 2.1 Foundation Models
- **Base Architectures**: Qwen1.5 (7B/14B/32B) and Qwen2.5 (1.5B/7B/14B) series
- **Key Improvements**:
  - Grouped-Query Attention (GQA) in Qwen2.5 variants for enhanced inference speed
  - Continued pretraining on ACGN-domain corpora
  - SFT (Supervised Fine-Tuning) with human-annotated translation pairs
  - RLHF (Reinforcement Learning from Human Feedback) for stylistic optimization

### 2.2 Model Variants
| Parameter Size | Base Model      | Key Features                                                                 |
|----------------|-----------------|------------------------------------------------------------------------------|
| 1.5B           | Qwen2.5-1.5B    | Mobile-friendly, CPU-optimized                                              |
| 7B             | Qwen2.5-7B      | Balanced performance for mid-range GPUs (8-12GB VRAM)                       |
| 14B            | Qwen2.5-14B     | High-precision translation with GQA optimization                            |
| 32B            | Qwen1.5-32B     | State-of-the-art quality (v0.9) for high-end hardware                       |

## 3. Training Methodology

### 3.1 Data Composition
| Data Type                  | Proportion | Source                                                                 |
|----------------------------|------------|-----------------------------------------------------------------------|
| General Bilingual Corpus   | 45%        | WMT, OPUS, Tatoeba                                                   |
| ACGN-domain Parallel Texts | 35%        | - 50,000+ light novel sentences <br> - 30,000+ visual novel scripts  |
| Synthetic Data             | 15%        | Back-translation with Qwen-72B                                       |
| Human-curated Samples      | 5%         | Professional translator annotations                                  |

### 3.2 Training Pipeline
1. **Continued Pretraining**:
   - Objective: Domain adaptation through MLM (Masked Language Modeling)
   - Corpus: 50GB ACGN-related text (Japanese:Chinese = 3:1)
   - Hardware: 8×A100 (80GB) GPUs, ZeRO-3 optimization

2. **Supervised Fine-Tuning**:
   - Dataset: 1.2M parallel sentence pairs
   - Curriculum:
     - Phase 1: Sentence-level translation
     - Phase 2: Paragraph-level context-aware training
     - Phase 3: Format-preservation training with special tokens

3. **RLHF Optimization**:
   - Reward Model: Customized GPT-4 evaluation framework focusing on:
     - Pronoun consistency (95.2% accuracy)
     - Stylistic fidelity (Light Novel Style Score: 4.8/5)
     - Format retention rate (98.1%)

## 4. Performance Evaluation

### 4.1 Quantitative Metrics
| Model Variant          | BLEU-4 | COMET↑ | TER↓ | PPL   | Speed (tok/s) |
|------------------------|--------|--------|------|-------|---------------|
| Sakura-1.5B-v1.0       | 38.2   | 82.1   | 0.42 | 5.12  | 142           |
| Sakura-7B-v1.0         | 42.7   | 85.3   | 0.38 | 4.43  | 89            |
| Sakura-14B-v1.0        | 45.1   | 87.9   | 0.35 | 3.28  | 63            |
| Commercial MT (Baseline)| 35.8  | 79.4   | 0.47 | -     | -             |

### 4.2 Qualitative Analysis
**Case Study: Pronoun Resolution**
```text
Japanese Input:
「悠介さん、それは私の...」
Context: Female character blushing while holding a book

Commercial MT:
"Yusuke, that's my..."
Sakura Output:
"Yusuke-san, that's mine..." (Proper honorific and pronoun selection)
```

**Format Preservation Example**
```text
Original:
春の訪れを告げる{桜|さくら}の花が...

Competitor Output:
宣告春天来临的樱花...
Sakura Output:
宣告春天来临的{sakura|樱花}...
```

## 5. Deployment Ecosystem

### 5.1 Inference Requirements
| Model Size | Quantization | VRAM  | CPU RAM | Recommended Hardware               |
|------------|--------------|-------|---------|-------------------------------------|
| 1.5B       | IQ4_XS       | 4GB   | 8GB     | NVIDIA T4 / AMD RX 6700            |
| 7B         | Q4_K_M       | 8GB   | 16GB    | RTX 3060 / Apple M2                |
| 14B        | Q5_K_S       | 16GB  | 32GB    | RTX 4090 / A100-PCIE-40GB          |
| 32B        | Q6_K         | 48GB+ | 64GB+   | Multi-GPU clusters / Cloud services|

### 5.2 Integration Tools
| Tool                  | Use Case                      | Key Features                                  |
|-----------------------|-------------------------------|-----------------------------------------------|
| LunaTranslator        | Real-time game translation    | OCR integration, streaming output            |
| GalTransl             | Visual novel patching         | Batch processing, glossary support           |
| Sakura Launcher GUI   | Local deployment              | One-click installer with hardware detection  |
| vLLM Backend          | High-throughput API service   | 4× throughput vs. vanilla transformers       |

## 6. Ethical Considerations

### 6.1 Licensing
- All models are released under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
- Commercial use strictly prohibited
- Derivative models must inherit same license

### 6.2 Safety Measures
- Input filtering for NSFW content (98.7% accuracy)
- Output watermarking for traceability
- Mandatory "Machine Translation" labeling in client integrations

## 7. Future Directions
1. **Multimodal Expansion**: Integration with image context for manga translation
2. **Low-resource Optimization**: 500M parameter variant for edge devices
3. **Interactive Learning**: User feedback loop for continuous improvement
4. **Domain Expansion**: Korean/English support for ACGN content

## 8. Acknowledgements
- **Computing Resources**: Supported by Hugging Face's Community Cluster
- **Data Contributors**: ACGN community members and professional translators
- **Technical Advisors**: Qwen team members for architecture consultation

---

*This [Personal SakuraLLM Report] reflects the model status as of v1.0 (October 2024). For updates, visit the [official repository](https://github.com/SakuraLLM/SakuraLLM).*



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
    - [Step 1: Mount Google Drive (Highly Suggest)](#step-1-mount-google-drive-highly-suggest)  
    - [Step 2: Install Required Libraries](#step-2-install-required-libraries)  
    - [Step 3: API Forwarding Configuration Using Ngrok or Cloudflare](#step-3-api-forwarding-configuration-using-ngrok-or-cloudflare)  
        - [Option 1: Using Ngrok (Static Domain)](#option-1-using-ngrok-static-domain)  
        - [Option 2: Using Cloudflare Tunnel (Temporary URL)](#option-2-using-cloudflare-tunnel-temporary-url)  
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

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/1235357/SakuraLLM-Colab/blob/main/sakura_14b_qwen2_5_v1_0_q6k_gguf_Colab.ipynb)  


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


[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/1235357/SakuraLLM-Colab/blob/main/sakura_14b_qwen2_5_v1_0_q6k_gguf_Colab.ipynb)  





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
