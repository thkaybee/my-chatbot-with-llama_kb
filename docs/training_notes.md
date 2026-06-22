# Fine-Tuning Notes

## Base Model

Meta Llama 3.1 8B Instruct

## Framework

Unsloth

## Training Hardware

Google Colab Tesla T4

## Dataset

933 training examples

## Method

LoRA Fine-Tuning

## Output Formats

- Q4_K_M
- Q5_K_M
- Q8_0

## Validation Example

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
