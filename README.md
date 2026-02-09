# 🏥 MediBot: AI Clinical Triage Assistant

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-Transformers-yellow)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-red)
![Gradio](https://img.shields.io/badge/Gradio-UI-orange)
![License](https://img.shields.io/badge/License-MIT-green)

**MediBot** is a domain-specific Large Language Model (LLM) designed to assist in **clinical triage**. Fine-tuned on the **TinyLlama-1.1B** architecture using **QLoRA** (Quantized Low-Rank Adaptation), it runs efficiently on consumer hardware (including Google Colab's free tier) while providing structured medical analysis.

---

## 🚀 Features

* **Real-Time Triage:** Instantly analyzes patient symptoms to suggest potential conditions.
* **Urgency Classification:** Automatically categorizes cases as **Low**, **Moderate**, or **High/Critical** urgency.
* **Structured Output:** Forces a consistent response format: `1. Analysis`, `2. Advice`, `3. Urgency`.
* **Resource Efficient:** Optimized with 4-bit quantization to run on 16GB VRAM (T4 GPU).
* **User-Friendly UI:** Built with **Gradio** for an accessible, professional web interface.

---

## 📸 Screenshots

### 1. The Triage Interface
![MediBot UI](https://via.placeholder.com/800x400?text=Insert+Your+Gradio+UI+Screenshot+Here)
*The Gradio dashboard allowing input of Age, Gender, and Symptoms.*

### 2. Training Metrics
![Training Loss](https://via.placeholder.com/800x400?text=Insert+Training+Loss+Graph+Here)
*Training loss convergence over 1 epoch using QLoRA.*

---

## 🛠️ Tech Stack

* **Base Model:** `TinyLlama/TinyLlama-1.1B-Chat-v1.0`
* **Fine-Tuning:** PEFT (LoRA), BitsAndBytes (4-bit Quantization)
* **Dataset:** `ruslanmv/ai-medical-chatbot` (250k+ doctor-patient interactions)
* **Interface:** Gradio
* **Infrastructure:** Google Colab (Tesla T4 GPU)

---

## ⚙️ Installation & Setup

You can run this project directly in **Google Colab** or locally if you have a GPU with at least 8GB VRAM.

### Option 1: Google Colab (Recommended)
1.  Open the `MediBot_Training.ipynb` notebook in this repository.
2.  Click "Open in Colab".
3.  Change Runtime type to **T4 GPU**.
4.  Run all cells to install dependencies, load the model, and launch the Gradio app.

### Option 2: Local Installation
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/medibot-triage.git]
    cd medibot-triage
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the application:**
    ```bash
    python app.py
    ```

---

## 🧠 Model Training Details

The model was fine-tuned using **QLoRA** to adapt the pre-trained TinyLlama weights to the medical domain without overwriting them.

* **Rank (r):** 16
* **Alpha:** 32
* **Target Modules:** `q_proj`, `v_proj`, `k_proj`, `o_proj` (Attention layers)
* **Prompt Template:**
    ```text
    <|system|>
    You are an ER Nurse. Profile: [Age: {age}, Gender: {gender}].
    Format: 1. Analysis, 2. Advice, 3. Urgency.
    </s>
    <|user|>
    {symptoms}
    </s>
    <|assistant|>
    ```

---

## ⚠️ Medical Disclaimer

**This AI model is for educational and research purposes only.**

* It is **not** a licensed medical professional.
* It should **never** be used to diagnose real patients or replace professional medical advice.
* In a real emergency, always call emergency services (911/999).

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request