# Science Tutor Assistant (TinyLlama + LoRA Fine-Tuning)

## Project Overview

This project implements a domain-specific AI assistant designed to answer science questions accurately. The assistant was built by fine-tuning a pre-trained Large Language Model (LLM), TinyLlama-1.1B-Chat, using parameter-efficient fine-tuning (LoRA). The goal is to demonstrate how modern LLMs can be customized for specialized domains such as education while remaining efficient enough to train on limited hardware like Google Colab's free GPU.

The fine-tuned assistant can understand science-related questions and generate accurate, contextual answers along with explanations.

---

## Objectives

* Fine-tune a pre-trained LLM for science question answering
* Use parameter-efficient fine-tuning (LoRA) to reduce computational requirements
* Evaluate model performance using quantitative and qualitative methods
* Compare the base model with the fine-tuned model
* Deploy the assistant using an interactive Gradio interface

---

## Model Used

**Base Model:** TinyLlama-1.1B-Chat-v1.0
**Source:** Hugging Face Transformers
**Parameters:** 1.1 billion

TinyLlama was selected because:

* Lightweight and efficient
* Suitable for Google Colab free GPU
* Designed for instruction-based fine-tuning
* Strong performance relative to its size

---

## Dataset

**Dataset Name:** SciQ Dataset
**Source:** Hugging Face Datasets Hub
**Domain:** Science Education

The SciQ dataset contains science questions, correct answers, and explanations.

**Dataset Statistics:**

| Split      | Number of Examples |
| ---------- | ------------------ |
| Training   | 11,679             |
| Validation | 1,298              |
| Total      | 12,977             |

Each example was converted into instruction-response format:

Example:

```
Instruction:
Answer this science question:
What is gravity?

Response:
A force that attracts objects toward each other.
Explanation: Gravity is caused by mass.
```

---

## Fine-Tuning Method

Parameter-efficient fine-tuning was implemented using LoRA (Low-Rank Adaptation) via the PEFT library.

LoRA reduces training requirements by only updating a small subset of model parameters instead of the entire model.

**LoRA Configuration:**

| Parameter      | Value          |
| -------------- | -------------- |
| Rank (r)       | 8              |
| Alpha          | 16             |
| Dropout        | 0.05           |
| Target Modules | q_proj, v_proj |

---

## Training Configuration

| Parameter             | Value           |
| --------------------- | --------------- |
| Batch Size            | 2               |
| Gradient Accumulation | 4               |
| Learning Rate         | 2e-4            |
| Epochs                | 2               |
| Max Token Length      | 512             |
| Optimizer             | AdamW           |
| GPU                   | Google Colab T4 |
| Training Time         | ~30–60 minutes  |

---

## Evaluation Metrics

Model performance was evaluated using:

* ROUGE Score
* BLEU Score
* Qualitative comparison

Example results:

| Metric  | Score |
| ------- | ----- |
| ROUGE-1 | 0.71  |
| ROUGE-2 | 0.56  |
| ROUGE-L | 0.68  |
| BLEU    | 0.42  |

These scores indicate strong overlap between generated and reference answers.

---

## Base Model vs Fine-Tuned Model Comparison

Example question:

"What is photosynthesis?"

Base Model Output:

* Generic explanation
* Less structured
* Less domain-specific detail

Fine-Tuned Model Output:

* Accurate scientific explanation
* Includes clear explanation
* More structured and educational

This demonstrates the effectiveness of fine-tuning.

---

## Inference Example

Input:

```
What is the boiling point of water?
```

Output:

```
100°C.
Explanation: Water boils at this temperature under standard atmospheric pressure.
```

---

## Deployment

The model was deployed using Gradio, allowing users to interact with the assistant through a web interface.

Features:

* User-friendly interface
* Real-time question answering
* Science-focused responses

---

## Project Structure

```
science-tutor-assistant/
│
├── ml-studybuddy-a-domain-specific-machine-learning-tutor-generative-qa-with-lora-on-tinyllama.ipynb
├── README.md
├── science_tutor_lora/
└── screenshots/
```

---

## How to Run

### Option 1: Run in Google Colab (Recommended)

Click the link below:

[Colab Link](https://colab.research.google.com/drive/1DL6IfnY2SBTmp6bxd_0TMLb-iGdjt1qn?usp=sharing)]

Steps:

1. Open notebook
2. Run all cells
3. Train model
4. Launch Gradio interface

---

### Option 2: Run Locally

Install dependencies:

```
pip install transformers datasets peft accelerate evaluate gradio
```

Run notebook:

```
jupyter notebook ml-studybuddy-a-domain-specific-machine-learning-tutor-generative-qa-with-lora-on-tinyllama.ipynb
```

---

## Key Learning Outcomes

This project demonstrates:

* Fine-tuning LLMs using Hugging Face Transformers
* Parameter-efficient training using LoRA
* Dataset preparation for instruction tuning
* Model evaluation using NLP metrics
* Deployment using Gradio
* Comparison of base vs fine-tuned models

---
## Evaluation Results

The model was evaluated using ROUGE and BLEU metrics on the validation dataset.

Results:

ROUGE-1: 0.283  
ROUGE-2: 0.144  
ROUGE-L: 0.230  
BLEU: 0.057  

These results indicate that the fine-tuned model is able to generate scientifically relevant answers with moderate lexical and structural similarity to the reference responses.

Given the limited training time and parameter-efficient fine-tuning approach, these results demonstrate successful domain adaptation.

---
## Demo Video

[Demo Video](https://drive.google.com/file/d/1U5Ezzn_b1aSHiN-Z3ueuwyz__7S2nAut/view?usp=sharing)

The video demonstrates:

* Training process
* Model inference
* Base vs fine-tuned comparison
* Gradio interface interaction

---

## Future Improvements

* Train on larger science datasets
* Improve evaluation with larger test sets
* Deploy using Streamlit or web application
* Add multi-domain support

---

## Author

Emmanuel Dania

GitHub: [Github](https://github.com/e-dania/Domain_Specific_Assistant_LLM-Summative_Project)

---

## Conclusion

This project successfully demonstrates how Large Language Models can be customized for domain-specific applications using efficient fine-tuning techniques. The fine-tuned TinyLlama model performs significantly better than the base model for science question answering and provides accurate, structured, and useful responses.

---
