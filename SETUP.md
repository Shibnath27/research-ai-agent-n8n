# 🔧 Setup Guide – OpenRouter & Perplexity in n8n

This guide explains how to configure **OpenRouter** and **Perplexity** inside your **n8n** instance (running on Proxmox or any server).

---

## 📌 1. OpenRouter Setup

### Step 1 – Get API Key
1. Go to [OpenRouter](https://openrouter.ai/).
2. Create an account and log in.
3. Navigate to **Dashboard → API Keys**.
4. Generate a new key and copy it.

---

### Step 2 – Create Credential in n8n
1. In n8n, go to **Credentials → New**.
2. Choose **Generic API Key**.
3. Enter:
   - **Name:** `OpenRouter API`
   - **Key Name:** `Authorization`
   - **Value:** `Bearer YOUR_API_KEY`

---

### Step 3 – Test with HTTP Request Node
1. Add a new **HTTP Request** node in your workflow.
2. Configure:
   - **Method:** `POST`
   - **URL:** `https://openrouter.ai/api/v1/chat/completions`
   - **Headers:**
     - `Content-Type: application/json`
     - `Authorization: Bearer {{your_api_key}}`
   - **Body (JSON):**
     ```json
     {
       "model": "openai/gpt-4",
       "messages": [
         {"role": "user", "content": "Hello OpenRouter, can you explain what you do?"}
       ]
     }
     ```
3. Run the node → you should see a text response.

---

## 📌 2. Perplexity Setup

### Step 1 – Get API Key
1. Go to [Perplexity AI](https://www.perplexity.ai/).
2. Sign in and upgrade to **Pro** (API access required).
3. Navigate to **Settings → API Key**.
4. Copy your API key.

---

### Step 2 – Create Credential in n8n
1. In n8n, go to **Credentials → New**.
2. Choose **Generic API Key**.
3. Enter:
   - **Name:** `Perplexity API`
   - **Key Name:** `Authorization`
   - **Value:** `Bearer YOUR_API_KEY`

---

### Step 3 – Test with HTTP Request Node
1. Add a new **HTTP Request** node.
2. Configure:
   - **Method:** `POST`
   - **URL:** `https://api.perplexity.ai/chat/completions`
   - **Headers:**
     - `Content-Type: application/json`
     - `Authorization: Bearer {{your_api_key}}`
   - **Body (JSON):**
     ```json
     {
       "model": "sonar-medium-online",
       "messages": [
         {"role": "system", "content": "Be precise and concise."},
         {"role": "user", "content": "What are the latest AI trends in 2025?"}
       ],
       "max_tokens": 300,
       "temperature": 0.7
     }
     ```
3. Run the node → you should see a response with references/citations.

---

## ✅ Verification
- If the node returns a valid response → setup is complete.
- If you get `401 Unauthorized` → check API key formatting (`Bearer YOUR_KEY`).

---

## 📌 Next Steps
- Combine OpenRouter + Perplexity in a single workflow.
- Use **Google Sheets node** to log results.
- Automate research tasks with a **Schedule Trigger**.
