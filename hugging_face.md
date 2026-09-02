# 🤗 Hugging Face Setup

To make the workshop accessible for everyone, we will use cloud-based models instead of running models locally.

Running models locally requires different hardware capabilities, and we want everyone to have the same experience regardless of their laptop specifications.

## Before the workshop

### 1. Create a Hugging Face account

If you do not already have one, create an account:

https://huggingface.co/join

### 2. Create a Hugging Face access token

Go to:

https://huggingface.co/settings/tokens

* Click **Create new token**.
* Give your token a recognizable name (for example: `ai-agent-workshop`).
* Copy your token and SAVE IT somewhere safe!!! You will need it later to connect the notebook to Hugging Face.

**Please create a new token specifically for this workshop** and avoid reusing tokens from previous projects.

### 3. Get access to the UnBias-Plus model

For the hands-on exercise, we will use our private copy of the **UnBias-Plus** model:

https://huggingface.co/stasiafromberms/Qwen3-8B-UnBias-Plus-SFT-Instruct-V2

**Important: The model is private.**

1. Open the model page above while logged into your Hugging Face account.
2. If Hugging Face shows an access, usage, or license warning, **read it and accept/agree to the terms**.
3. Make sure the model page is accessible to you without an access warning.

You need to complete this step **before creating your inference endpoint**.

If you later get an access or permission error while creating the endpoint, go back to the model page above and check whether Hugging Face is asking you to accept or confirm something.

### 4. Create a Hugging Face Inference Endpoint

Once you have access to the model, create a dedicated **Inference Endpoint** for it.

From the model page:

https://huggingface.co/stasiafromberms/Qwen3-8B-UnBias-Plus-SFT-Instruct-V2

select **Deploy → Hugging Face Inference Endpoints** and follow the setup steps.

Once your endpoint has been created and is **Running**:

1. Copy the **endpoint URL**.
2. Save it somewhere safe.
3. You will need both the endpoint URL and your Hugging Face access token during the workshop.

Your setup should contain:

```text
HF_TOKEN = your Hugging Face access token
HF_ENDPOINT = your Inference Endpoint URL
```

## 💳 About usage and costs

The Inference Endpoint is a **paid cloud service**.

For this workshop, please expect to spend **roughly €2**, depending on the hardware configuration, provider, how long the endpoint is running, and how much you use it.

The exact amount may be higher or lower.

To avoid unnecessary costs:

* Create the endpoint shortly before the workshop.
* Avoid repeatedly running large numbers of model requests.
* **Pause or delete the endpoint when you are finished with the workshop.**
* Do not leave the endpoint running after the workshop.

### A note about API usage

The workshop is designed around small examples and short experiments. Normal usage during the session should remain low.

Please avoid repeatedly running large numbers of requests, as each request uses the paid inference endpoint.

We will also show you how to stop the endpoint at the end of the workshop so that you do not continue to incur charges.
