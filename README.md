# Hinglish-LLM
Hinglish LLM 🚀  A bilingual Large Language Model (LLM) fine-tuned to understand and generate text in **Hinglish** – a mix of Hindi and English, commonly used in informal conversations in India. This model is suitable for chatbot applications, text generation, and language understanding in Hinglish.

🔍 Model Overview

- **Model Name:** Hinglish LLM
- **Languages:** Hinglish (Hindi-English code-mixed)
- **Model Type:** Causal Language Model (Chat-style)
- **Base Model:** [e.g., GPT2 / LLaMA / Falcon] *(Update if known)*
- **Trained On:** Code-mixed Hindi-English conversational data

📦 Model Details

- **Tokenizer:** Custom SentencePiece tokenizer trained on Hinglish corpus
- **Model Architecture:** Transformer-based autoregressive language model
- **Model Size:** [e.g., 124M / 1.3B] *(Update if known)*
- **Intended Use:** Chatbots, question answering, informal dialogue systems

🔧 Installation

To use the model in your project, install the required libraries:

```bash
"pip install transformers huggingface_hub gradio"
```

How to use
```
from transformers import AutoTokenizer, AutoModelForCausalLM

model_name = "Ramavadhoota/hinglish-llm"

# Load tokenizer and model
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name)

# Generate a response
input_text = "Kya haal hai?"
input_ids = tokenizer.encode(input_text, return_tensors="pt")
output = model.generate(input_ids, max_new_tokens=50)
response = tokenizer.decode(output[0], skip_special_tokens=True)

print(response)
```

Demo (Gradio UI)
```
import gradio as gr

def chat_fn(prompt):
    input_ids = tokenizer(prompt, return_tensors="pt").input_ids
    output = model.generate(input_ids, max_new_tokens=50)
    return tokenizer.decode(output[0], skip_special_tokens=True)

gr.Interface(fn=chat_fn, inputs="text", outputs="text").launch()
```
