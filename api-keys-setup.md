# API Keys Setup

SupaFAN requires two API keys: one for YouTube Data API v3 and one for OpenRouter.

## 1. YouTube Data API v3

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (or select an existing one).
3. Navigate to **APIs & Services > Library**.
4. Search for **YouTube Data API v3** and enable it.
5. Go to **APIs & Services > Credentials**.
6. Click **+ Create Credentials > API Key**.
7. Copy your new API key.
8. (Optional) Restrict the key to only the YouTube Data API v3 for security.

## 2. OpenRouter API Key

1. Go to [OpenRouter](https://openrouter.ai/) and sign up/log in.
2. Navigate to your **API Keys** section (dashboard).
3. Click **Create Key**.
4. Give it a name (e.g., `SupaFAN`) and copy the key.
5. No payment is required for free models (though you may need credits for premium models).

## 3. Configure `.env`

In the root of the SupaFAN main repository, copy `sample.env` to `.env`:

```bash
cp sample.env .env
```
Open .env and fill in your keys:
```
YOUTUBE_API_KEY=AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXX
OPENROUTER_API_KEY=sk-or-v1-YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY
```
Optionally set a preferred model (default is openrouter/free):
```OPENROUTER_MODEL=google/gemma-3-27b-it:free ```
as an example
4. Verify
Run the pipeline with any target. If the pre‑flight check passes, your keys are working.

text

---
