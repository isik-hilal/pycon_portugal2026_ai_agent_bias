# This AI will judge your bias

## Workshop - PyCon Portugal 2026

This repository contains the materials for the **AI Agent Workshop on bias detection** using **LangGraph**, **LangChain**, and **UnBias-Plus**.

During this workshop, we will build an AI agent that can analyze text and use a dedicated bias-detection model to identify and discuss potential bias.

---

# Prerequisites

Before starting, make sure you have:

* Python **3.11 or newer**
* Git
* A Hugging Face account
* A Hugging Face payment method or sufficient credits for the workshop

> **Note:** We recommend using an isolated environment to avoid dependency conflicts between projects.

---

# Environment Setup

You can choose one of the following options depending on your preferred Python workflow.

---

# Option 1 (Recommended): Python Virtual Environment (`venv`)

## 1. Fork and clone the repository

```bash
git clone <repository-url>
cd <repository-folder>
```

## 2. Create a virtual environment

### Windows

```bash
python -m venv .venv
```

### macOS / Linux

```bash
python3 -m venv .venv
```

## 3. Activate the environment

### Windows

```bash
.venv\Scripts\activate
```

### macOS / Linux

```bash
source .venv/bin/activate
```

Once activated, your terminal should display something similar to:

```text
(.venv)
```

## 4. Install the required packages

```bash
pip install -r requirements.txt
```

## 5. Launch Jupyter

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

---

# Option 2: Conda Environment

If you already use Conda, you can create an isolated environment as follows.

## 1. Create the environment

```bash
conda create -n bias-agent python=3.11
```

## 2. Activate it

```bash
conda activate bias-agent
```

## 3. Install the required packages

```bash
pip install -r requirements.txt
```

## 4. Launch Jupyter

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

---

# Option 3: uv Environment

`uv` is a fast Python package and environment manager. If you already use `uv`, you can set up the workshop environment with:

## 1. Install uv

Follow the installation instructions:

https://docs.astral.sh/uv/getting-started/installation/

If you already have `uv` installed, you can skip this step.

## 2. Create a virtual environment

```bash
uv venv --python 3.11
```

## 3. Activate the environment

### Windows

```bash
.venv\Scripts\activate
```

### macOS / Linux

```bash
source .venv/bin/activate
```

## 4. Install dependencies

```bash
uv pip install -r requirements.txt
```

## 5. Register the environment as a Jupyter Kernel

```bash
python -m ipykernel install --user --name workshop-env --display-name "Python (Workshop)"
```

## 6. Launch Jupyter

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

---

# Hugging Face Setup

This workshop uses **UnBias-Plus**, a hosted bias-detection model, through a Hugging Face **Inference Endpoint**.

We use a hosted model instead of running the model locally because the model is relatively large and local hardware requirements vary significantly. Using an endpoint allows everyone to work with the same model.

## 1. Create a Hugging Face account

If you do not already have one, create an account:

https://huggingface.co/join

## 2. Create a Hugging Face access token

Go to:

https://huggingface.co/settings/tokens

1. Click **Create new token**.
2. Give it a recognizable name, for example `ai-agent-workshop`.
3. Copy your token and save it somewhere safe.

**Please create a new token specifically for this workshop** instead of reusing a token from another project.

⚠️ Treat your token like a password. Never share it publicly or commit it to GitHub.

> **The token itself is not what you are paying for.** It is used to authenticate requests to your Hugging Face resources.

## 3. Get access to the UnBias-Plus model

For the workshop, we use our private copy of the UnBias-Plus model:

https://huggingface.co/stasiafromberms/Qwen3-8B-UnBias-Plus-SFT-Instruct-V2

**Important: the model is private.**

1. Open the model page while logged into your Hugging Face account.
2. If Hugging Face shows an access, usage, or license warning, **read it and accept/agree to the terms**.
3. Make sure you can access the model without an access warning.

You need to complete this step before creating your inference endpoint.

If you receive an access or permission error while creating the endpoint, go back to the model page and check whether Hugging Face is asking you to accept or confirm something.

---

# 💳 Payment and API Usage

During the workshop, you will create and use an **Inference Endpoint** for the UnBias-Plus model.

The endpoint is a **paid Hugging Face service**. We will be making multiple model requests throughout the workshop while we build the agent, create tools, and test different examples.

Please make sure you have a **payment method or sufficient credits on your Hugging Face account** before the hands-on portion of the workshop.

We expect the workshop to cost approximately **€2 per participant**.

The exact cost may vary depending on:

* the hardware configuration,
* the provider,
* how long the endpoint is running,
* and how many requests are made.

> **The access token is not the charge. The cost comes from running the model through the Inference Endpoint and making inference requests.**

We recommend creating the endpoint during the workshop rather than leaving it running beforehand.

⚠️ **Important:** A running endpoint can continue to incur charges even when you are not actively using the notebook.

At the end of the workshop, **pause or delete your endpoint** to make sure you do not continue to incur charges.

---

# Creating the Inference Endpoint

We will create the endpoint during the workshop.

Start from the UnBias-Plus model page:

https://huggingface.co/stasiafromberms/Qwen3-8B-UnBias-Plus-SFT-Instruct-V2

Follow the Hugging Face deployment instructions and wait until the endpoint is **Running**.

Once it is running, copy the **endpoint URL**.

You will need both:

* your Hugging Face access token
* your Inference Endpoint URL

---

# Environment Variables

Create a `.env` file in the same folder as the notebook.

Add:

```text
HF_TOKEN=your_huggingface_token
HF_ENDPOINT=your_inference_endpoint_url
```

For example:

```text
HF_TOKEN=hf_xxxxxxxxxxxxxxxxx
HF_ENDPOINT=https://xxxxxxxxxxxxxxxx.eu-west-1.aws.endpoints.huggingface.cloud
```

Do **not** commit your `.env` file to GitHub.

---

# Verify the Installation

Open the notebook and run the first **Setup Check** cells.

These cells verify that:

* required packages are installed,
* your Hugging Face token is loaded,
* your endpoint URL is loaded,
* your environment is ready for the workshop.

If you encounter an error, first check:

* Is your virtual environment activated?
* Is your `.env` file in the correct folder?
* Is `HF_TOKEN` correctly added?
* Is `HF_ENDPOINT` correctly added?
* Is your Hugging Face endpoint running?
* Have you accepted the access/usage terms for the private UnBias-Plus model?

---

# During the Workshop

We will build the system step by step, including:

1. Connecting to Hugging Face.
2. Creating the UnBias-Plus Inference Endpoint.
3. Connecting the endpoint to LangChain.
4. Creating tools.
5. Building the agent with LangGraph.
6. Testing the agent with different examples.
7. Experimenting with bias detection.

Because these steps involve repeated model requests, **you will use your Hugging Face inference resources throughout the hands-on portion of the workshop**.

Please avoid unnecessary repeated requests. The exercises are designed around small examples and normal usage should remain low.

At the end of the workshop, **pause or delete your endpoint** so that it does not continue running and generating charges.
