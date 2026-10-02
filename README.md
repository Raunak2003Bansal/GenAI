# GenAI

This repository contains hands-on notebooks for experimenting with generative AI. The current example demonstrates zero-shot, one-shot, and few-shot prompting with DeepSeek.

## Repository contents

| Path | Description |
| --- | --- |
| [`PromptEngineering/Zero_One_Few_Shot_Prompting.ipynb`](PromptEngineering/Zero_One_Few_Shot_Prompting.ipynb) | Prompting examples for transaction classification and banking complaint routing |
| [`PromptEngineering/README.md`](PromptEngineering/README.md) | Notebook-specific overview |
| [`requirements.txt`](requirements.txt) | Pinned Python environment dependencies |

## Requirements

- Python **3.12.14** (the version recorded by the notebook kernel)
- [uv](https://docs.astral.sh/uv/) for installing Python and managing the environment
- A DeepSeek API key to run the model-backed notebook cells

### Create the environment with uv

From the repository root, install the matching Python version, create and activate a virtual environment, and install the listed dependencies:

```powershell
uv python install 3.12.14
uv venv --python 3.12.14
.\.venv\Scripts\Activate.ps1
uv pip install -r requirements.txt
```

If PowerShell blocks activation, either allow the script for the current terminal with `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`, or skip activation and target the environment explicitly:

```powershell
uv pip install --python .venv\Scripts\python.exe -r requirements.txt
```

On macOS or Linux, activate the environment with `source .venv/bin/activate` instead.

In VS Code, open the notebook and select the `.venv` Python 3.12.14 environment as its kernel.

### Install and record dependencies

Install any additional package into the active environment with:

```powershell
uv pip install package-name
```

Then refresh the pinned environment file:

```powershell
uv pip freeze | Set-Content -Encoding utf8 requirements.txt
```

`uv pip freeze` records every installed package and version, including transitive dependencies. Keep using this approach if you want `requirements.txt` to remain a full environment snapshot.

The PowerShell command writes UTF-8 text, which keeps the requirements file readable by package tools. On macOS or Linux, use `uv pip freeze > requirements.txt`.

## Configure the API key

Create a `.env` file in the repository root with your own DeepSeek key:

```dotenv
DEEPSEEK_API_KEY=your_deepseek_api_key
```

The notebook loads this variable with `python-dotenv` and sends requests to DeepSeek using its OpenAI-compatible API. Do not commit `.env` or share its contents. The repository `.gitignore` excludes it.

## Run the notebook

Open `PromptEngineering/Zero_One_Few_Shot_Prompting.ipynb` in VS Code, choose the `.venv` kernel, and run the cells. The notebook compares prompting styles on transaction classification and customer complaint routing; the API key must be configured before running cells that call the model.
