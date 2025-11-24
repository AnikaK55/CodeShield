## CodeShield: LLM-Powered Python Vulnerability Detection

CodeShield is a personal project where I explore how Large Language Models (LLMs) reason about software security. The goal is to evaluate whether an LLM can detect vulnerabilities in Python code, identify the type of vulnerability, and explain its reasoning - all using a controlled dataset, prompt templates and a reproducible evaluation pipeline.

## Project Overview 
CodeShield is designed as a lightweight research-style framework rather than a full application. It focuses on:
-  Building a curated dataset of Python vulnerability examples
-  Designing reusable prompt templates for classification and explanation
-  Interfacing with the GPT API to generate predictions
-  Implementing evaluation metrics to measure model reliability

## Dataset
I curated a hybrid dataset consisting of:
- Realistic vulnerability examples inspired by OWASP, GitHub Advisories, and CWE case studies
- Synthetic vulnerable snippets demonstrating patterns like:
  - SQL injection
  - Command injection
  - Hardcoded secrets
  - Unsafe deserialization
  - Weak cryptographic usage
  - Path traversal
  - Missing input validation
- Safe examples (~20 snippets) used as controls
Each entry follows a consistent JSONL format:
```json
{
  "code": "...",
  "is_vulnerable": true,
  "vuln_type": "Command Injection",
  "explanation": "User input is directly passed into os.system without sanitization."
}
```
The final dataset contains 90 - 120 vulnerable samples across ~30 vulnerability types.

## LLM Evaluation Pipeline
The evaluation pipeline performs the following steps:
- Load dataset
- Insert each sample into the appropriate prompt template
- Send the request to the GPT API
- Parse the model's output into structured fields
- Aggregate performance metrics across the dataset
- All model calls are executed through simple REST requests.

## Evaluation Metrics
I implemented multiple metrics to measure the model's reliability:
- Binary Classification Accuracy
- Vulnerability Type Accuracy
- Explanation Quality Score, based on:
  - Keyword overlap
  - Reasoning correctness
  - Alignment with ground truth
- Strict vs. Relaxed Matching
  - e.g., “OS Command Injection” vs. “Command Injection”
These metrics allow both precise and flexible evaluations depending on the experiment setup.

## Tech Stack
- Python
- OpenAI GPT API
- JSONL dataset
- Custom evaluation scripts




