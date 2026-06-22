# Chemistry Validator LLM

A fine-tuned Llama 3.1 8B model that determines whether a user query is related to chemical science and returns a machine-readable JSON response.

This project was developed as part of the Manning LiveProject: Fine-Tune and Deploy a Validator LLM.

---

## Project Overview

The goal of this project is to create a lightweight validator model that classifies user queries into:

- Valid Chemistry Questions
- Invalid / Non-Chemistry Questions

The model responds with structured JSON output.

### Example

#### Input

```text
Can elements be broken down into simpler substances?
```

#### Output

```json
{
  "valid": true
}
```

#### Input

```text
Was Donald Trump a good president?
```

#### Output

```json
{
  "valid": false,
  "reason": "politics"
}
```

---

## Project Workflow

### 1. Dataset Creation

Created a supervised fine-tuning dataset using the Alpaca instruction format.

Dataset contains:

- Chemistry-related questions
- Politics questions
- General knowledge questions
- Non-chemistry statements

Example dataset record:

```json
{
  "instruction": "Determine if the input is a question related to chemical science...",
  "input": "Can elements be broken down into simpler substances?",
  "output": "{'valid': true}"
}
```

### Dataset Repository

https://huggingface.co/datasets/thkaybee/chemistry-validator-dataset

---

### 2. Fine-Tuning

Base Model:

- Llama 3.1 8B Instruct

Fine-Tuning Framework:

- Unsloth
- LoRA (Low Rank Adaptation)
- Google Colab Tesla T4 GPU

Training Configuration:

- 933 training examples
- 60 training steps
- GGUF export support

---

### 3. Model Export

Exported GGUF formats:

- Q4_K_M
- Q5_K_M
- Q8_0

Model Repository:

https://huggingface.co/thkaybee/chemistry-validator-llama

---

### 4. Deployment

The fine-tuned model was deployed using:

- GaiaNet
- WasmEdge
- LlamaEdge

Public Deployment:

https://0x225c8b3c4525e6e06fc0e50d2f90d7e8731ecc7e.gaia.domains

---

## API Usage

### Example Request

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

### Example Response

```json
{
  "valid": false,
  "reason": "politics"
}
```

---

## Technologies Used

- Python
- Hugging Face Datasets
- Hugging Face Models
- Llama 3.1 8B
- Unsloth
- LoRA Fine-Tuning
- GGUF
- WasmEdge
- LlamaEdge
- GaiaNet
- GitHub
- Google Colab

---

## Repository Structure

```text
.
├── chemistry-by-chapter.txt
├── generate_valid_questions.py
├── politics.txt
├── finetune.json
└── README.md
```

---

## Related Links

### GitHub Repository

https://github.com/thkaybee/my-chatbot-with-llama_kb

### Dataset

https://huggingface.co/datasets/thkaybee/chemistry-validator-dataset

### Fine-Tuned Model

https://huggingface.co/thkaybee/chemistry-validator-llama

### Deployment

https://0x225c8b3c4525e6e06fc0e50d2f90d7e8731ecc7e.gaia.domains

---

## Author

Krishna Bharadwaj

Computer Science Undergraduate  
Mahatma Gandhi Institute of Technology
