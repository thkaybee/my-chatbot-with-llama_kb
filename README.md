# Chemistry Validator LLM

A fine-tuned Llama 3.1 8B model that determines whether a user query is related to chemical science and returns a machine-readable JSON response.

This project was developed as part of a complete LLM workflow covering dataset creation, supervised fine-tuning, model quantization, deployment, and API serving.

---

## Architecture

```text
User Query
    │
    ▼
Chemistry Validator LLM
    │
    ├── valid = true
    │       ▼
    │   Chemistry Assistant
    │
    └── valid = false
            ▼
       Reject Query
```

---

## Project Overview

The goal of this project is to create a lightweight validator model that classifies user queries into:

- Valid Chemistry Questions
- Invalid / Non-Chemistry Questions

The model responds with structured JSON output that can be consumed by applications and APIs.

---

## Dataset Creation

A supervised fine-tuning dataset was created using the Alpaca instruction format.

Dataset contains:

- Chemistry questions
- Politics questions
- General knowledge questions
- Non-chemistry statements

### Dataset Repository

https://huggingface.co/datasets/thkaybee/chemistry-validator-dataset

### Example Dataset Record

```json
{
  "instruction": "Determine if the input is a question related to chemical science...",
  "input": "Can elements be broken down into simpler substances?",
  "output": "{'valid': true}"
}
```

---

## Fine-Tuning

### Base Model

Meta Llama 3.1 8B Instruct

### Framework

- Unsloth
- LoRA (Low Rank Adaptation)
- Google Colab Tesla T4 GPU

### Training Configuration

- 933 training examples
- 60 training steps
- GGUF export support

---

## Results

### Example 1

Input:

```text
Can elements be broken down into simpler substances?
```

Output:

```json
{
  "valid": true
}
```

### Example 2

Input:

```text
Was Donald Trump a good president?
```

Output:

```json
{
  "valid": false,
  "reason": "politics"
}
```

---

## Model Export

Exported GGUF Formats:

- Q4_K_M
- Q5_K_M
- Q8_0

### Hugging Face Model Repository

https://huggingface.co/thkaybee/chemistry-validator-llama

---

## Deployment

The model was deployed using:

- GaiaNet
- WasmEdge
- LlamaEdge

### Public Deployment

https://0x225c8b3c4525e6e06fc0e50d2f90d7e8731ecc7e.gaia.domains

### Local API

```text
http://localhost:9068/v1/chat/completions
```

### Local Chatbot UI

```text
http://localhost:8080/chatbot-ui/index.html
```

---

## API Example

### Request

```bash
curl -X POST http://localhost:9068/v1/chat/completions \
-H "Content-Type: application/json" \
-d '{
  "messages":[
    {
      "role":"system",
      "content":"Determine if the input is a question related to chemical science."
    },
    {
      "role":"user",
      "content":"Was Donald Trump a good president?"
    }
  ]
}'
```

### Response

```json
{
  "valid": false,
  "reason": "politics"
}
```

---

## Skills Demonstrated

- Dataset Creation
- Prompt Engineering
- Instruction Tuning
- LoRA Fine-Tuning
- Llama 3.1
- Hugging Face Datasets
- Hugging Face Models
- GGUF Export
- Model Quantization
- GaiaNet Deployment
- OpenAI-Compatible APIs
- WasmEdge
- LlamaEdge

---

## Repository Structure

```text
.
├── chemistry-by-chapter.txt
├── politics.txt
├── finetune.json
├── generate_valid_questions.py
├── README.md
│
├── docs
│   ├── deployment_guide.md
│   └── training_notes.md
│
├── gaianet
│   └── sample_config.json
│
└── notebooks
    └── chemistry_validator_finetuning.ipynb
```

---

## Project Status

Completed ✅

- Dataset Created
- Model Fine-Tuned
- GGUF Models Exported
- Model Uploaded to Hugging Face
- Public Deployment Live
- API Verified

---

## Related Links

### GitHub Repository

https://github.com/thkaybee/my-chatbot-with-llama_kb

### Dataset

https://huggingface.co/datasets/thkaybee/chemistry-validator-dataset

### Fine-Tuned Model

https://huggingface.co/thkaybee/chemistry-validator-llama

### Public Deployment

https://0x225c8b3c4525e6e06fc0e50d2f90d7e8731ecc7e.gaia.domains

---

## Author

Krishna Bharadwaj

Computer Science Undergraduate  
Mahatma Gandhi Institute of Technology
