---
layout: default
title: Overview
parent: Hosted Large Language Models
nav_order: 1
description: ""
permalink: /hosted-llms/
---

{: .note }
This service is in beta for the fall 2025 semester and we are looking for early adopters.

# Overview

SDSU instructors and researchers can take advantage of hosted, open-weight large language models (LLMs) for courses and research projects.
LLMs are provided via [Open WebUI](https://docs.openwebui.com/) which "is an extensible, feature-rich, and user-friendly self-hosted AI platform".
Open WebUI offers both a web-based chat interface similar to ChatGPT as well as a REpresentational State Transfer (REST) Application Programming Interface (API) compatible with the OpenAI API's models and chat completions endpoints.

This service is not intended to replace [university recommended AI tools](https://it.sdsu.edu/services/ai), but rather serves to provide access to open-weight models in instructional and research settings.

## Current Models

| Model | Parameters | Context Length | Input | Output | 
|:------|:----------:|:--------------:|:------|:-------|
| DeepSeek-R1-Distill-Llama-70B | 70b | 128K | Text | Text |
| gpt-oss | 120b | 128K | Text | Text |
| Llama 3.1 | 70b | 128K | Text | Text |
| Llama 4 | 109b | 10M | Text, Image | Text |

## Requesting Access

Instructors and researchers may request access for their courses and research labs.
This service does not require VPN to access. 
Please request access by completing the following steps:

1. Sign into [ServiceNow](https://sdsu.service-now.com/) with your SDSUid
1. Complete the [Research Cyberinfrastructure Consultation Form](https://sdsu.service-now.com/sp?id=sc_cat_item&sys_id=029639611bb825505764fd1b1e4bcb3a&sysparm_category=29ac153fdbbf4c9024094672399619e9)
    - The "Request Type" field should be set to "Access to Existing Cyberinfrastructure"
    - The "Please provide a description of your request" field should include "Hosted LLM access" and the following information:
        - Instructional use: The my.SDSU catalog course number and class number
        - Research use: List of SDSUids of lab members
1. Wait for confirmation of access via the ServiceNow ticket, this usually takes 1-2 business days
1. Once granted access, direct students or lab members to sign into Open WebUI with their SDSUid credentials

### Accessing Open WebUI

1. Sign into [our Open WebUI instance](https://sdsu-rci-owui.nrp-nautilus.io/) with your SDSUid by clicking the "Continue with SSO" button
    - ![Open WebUI sign in page](/images/hostedllms/requesting-access-1.png)
1. Search for "San Diego State University" and click "Log On"
    - ![CILogon sign in page](/images/hostedllms/requesting-access-2.png)
    - *Note*: If you did use another authentication option, please use CILogon's [log out page](https://cilogon.org/logout/) and repeat the previous step
1. Authenticate with your SDSUid credentials and approve DUO as you normally would
    - ![Shiboleth sign in page](/images/hostedllms/requesting-access-3.png)
1. If this is your first time signing in, then you may be greeted by a welcome message
    - ![Open WebUI welcome pop up](/images/hostedllms/requesting-access-4.png)
1. You should now have access to the chat interface

## Web-based Chat

Open WebUI offers a web-based chat interface similar to ChatGPT and other LLMs.
This allows users an easy way to chat with models, start multiple conversations and choose which model they want to use.

![conversation with llama 3.1 about San Diego State University](/images/hostedllms/web-based-chat-1.png)

## API Access

Open WebUI offers a [REST API](https://docs.openwebui.com/getting-started/api-endpoints) that is compatible with the OpenAI API's models and chat completions endpoints.
Once you have been granted access, you can follow these steps to obtain an API key:

1. Navigate to [our Open WebUI instance](https://sdsu-rci-owui.nrp-nautilus.io/)
1. Click your name in the lower left or upper right
    - ![user profile menu](/images/hostedllms/api-access-1.png)
1. Click "Settings"
1. Click "Account"
    - ![user account settings](/images/hostedllms/api-access-2.png)
1. Click "Show" next to "API keys"
1. Click "+ Create new secret key"
    - ![API key creation](/images/hostedllms/api-access-3.png)
       - *Note*: Do not use the JWT token as this expires periodically
1. Click the clipboard/copy icon to copy your new API key
    - ![API key created and ready to copy](/images/hostedllms/api-access-4.png)
    - If you should need to rotate your API key, please follow the above directions and then click the circle/refresh icon and then click the clipboard/copy icon to copy the new key

### Sample Code

Once you have your API key, you can use the OpenAI API-compatible models and chat completions endpoints.

In the following sections we provide sample code using the [OpenAI Python API library](https://pypi.org/project/openai/).
The following examples should work on the instructional and research JupyterHub instances using the LLM Notebook.
Other methods of interacting with REST APIs, such as Postman and curl, should still apply.

#### OpenAI Python API Configuration

Please follow these steps to configure the OpenAI Python API library to work with our instance of  Open WebUI:

1. Create an environment variable `OPENAI_API_KEY_OWUI` for your Open WebUI API key
    - MacOS/Linux
    ```bash
    export OPENAI_API_KEY_OWUI=sk-xxxxxxxxxxxxxxxxxxx
    ```
    - Windows PowerShell
    ```powershell
    $env:OPENAI_API_KEY_OWUI = "sk-xxxxxxxxxxxxxxxxxxx"
    ```
    - *Note*: Replace the value `sk-xxxxxxxxxxxxxxxxxxx` with your API key
1. Configure a client to work with Open WebUI
    ```python
    import os
    import openai

    API_KEY = os.environ.get("OPENAI_API_KEY_OWUI")

    client = openai.OpenAI(
        base_url = "https://sdsu-rci-owui.nrp-nautilus.io/api/",
        api_key = API_KEY
    )
    ```

#### Models Endpoint

This sample code calls the models endpoint to list available models.

```python
models = client.models.list()

for model in models.data:
    print(model.id)
```

#### Chat Completions Endpoint

This sample code calls the chat completions endpoint to generate a message. 

```python
response = client.chat.completions.create(
    model="llama3.1:70b",
    messages=[
        {"role": "user", "content": "Hello there!"}
    ],
    temperature=0.7,
)

print(response.choices[0].message.content)
```

## Rate Limiting

To ensure availability of these resources, we have enabled rate limiting for all users.
These rate limits apply to both web-based chat and API usage.

| Requests per Minute | Requests per Hour | Sliding Window Limit | Sliding Window |
|:-------------------:|:-----------------:|:--------------------:|:--------------:|
| 100 | 1000 | 250 | 15 |

{: .note }
These rate limits are subject to change to address real-time load.
