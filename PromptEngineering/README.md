# Zero-, One-, and Few-Shot Prompting

This notebook demonstrates zero-shot, one-shot, and few-shot prompts for banking transaction classification and customer complaint routing. It calls DeepSeek through the OpenAI-compatible Python client.

## Run it

Follow the environment setup and API-key instructions in the repository [README](../README.md). The notebook is [`Zero_One_Few_Shot_Prompting.ipynb`](Zero_One_Few_Shot_Prompting.ipynb).

Set `DEEPSEEK_API_KEY` in the repository-root `.env` file before running model-backed cells. Do not commit that file.

The complaint-routing examples ask the model to return structured results such as a department, priority, suggested action, and estimated resolution time. The transaction example compares classifications produced with different prompting styles.
