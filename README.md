# SupaFAN-Info – Documentation & Examples

![Static Badge](https://img.shields.io/badge/SupaFAN-Info-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-No%20License%20For%20Info-green?style=for-the-badge)

**Companion repository for the SupaFAN YouTube OSINT pipeline**  
Here you'll find comprehensive documentation, usage guides, and sanitized sample outputs – all without exposing any real user data.

---

## 📖 Overview

This repo exists to help you understand and use the [SupaFAN pipeline](https://github.com/DAPOWER99/SupaFAN) more effectively.

- **Documentation** – Detailed explanations of each pipeline stage (resolver, extractor, AI engine, writer).
- **Setup guides** – Step‑by‑step instructions for API keys, environment, and dependencies.
- **Sample outputs** – Redacted examples of the JSON reports and the exhaustive `info.txt` file.
- **Troubleshooting** – Common pitfalls and how to fix them.

All sample data has been **anonymised** (channel IDs, video IDs, names, and comments are replaced with placeholders). Run the actual pipeline on your own targets to get real insights.

---

## 📂 Repository Contents
```markdown
SupaFAN-Info/
├── README.md                         # You are here
├── docs/
│   ├── pipeline-overview.md          # High‑level architecture
│   ├── api-keys-setup.md             # How to obtain and configure API keys
│   ├── output-format.md              # Explanation of JSON fields & info.txt structure
│   └── troubleshooting.md            # Common errors and solutions
├── examples/
│   ├── sample-output/                # Redacted report samples
│   │   ├── channel_stats_sample.json
│   │   ├── knowledge_web_sample.json
│   │   ├── ai_analysis_sample.json
│   │   └── info_sample.txt
│   └── sample-commands.md            # CLI usage examples with different options
└── .gitignore                        # Ensures no real data is ever committed
```

---

## 🚀 Getting Started with the Main Pipeline

1. **Clone the main repository**  
   ```bash
   git clone https://github.com/DAPOWER99/SupaFAN.git
   cd SupaFAN
   ```

2. **Install dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up API keys** – Copy `sample.env` to `.env` and fill in your YouTube Data API v3 key and OpenRouter API key.

4. **Run the pipeline** – See `examples/sample-commands.md` for typical invocations.

> ⚠️ **Important:** Never commit your `.env` or `cookies.txt` files to version control – they are already ignored in the main repo.

---

## 📄 Sample Outputs

In the `examples/sample-output/` folder you will find:

- **`channel_stats_sample.json`** – Basic channel metrics (subscribers, views, video count, etc.).
- **`knowledge_web_sample.json`** – Full video telemetry and comment corpus (anonymised).
- **`ai_analysis_sample.json`** – The AI‑generated OSINT report from OpenRouter.
- **`info_sample.txt`** – The exhaustive, human‑readable report that combines everything.

These are intended to give you a clear picture of what the pipeline produces, so you can interpret your own results.

---

## 🧰 Troubleshooting Quick Tips

| Issue | Likely Cause | Solution |
|-------|--------------|----------|
| `403 Forbidden` on video download | YouTube requires authentication | Place a valid `cookies.txt` (exported from your browser) in the main repo root. |
| OpenRouter returns a 429 | Rate limiting | The pipeline automatically backs off and retries; wait or reduce your scanning volume. |
| `YOUTUBE_API_KEY` missing | `.env` not set up | Copy `sample.env` → `.env` and add your key. |
| Comments not appearing | Comments disabled on that video | Normal – the pipeline logs that status. |

For a deeper dive, see the full [troubleshooting guide](docs/troubleshooting.md).

---

## 🧑‍💻 Contributing

Found a bug in the documentation? Have a better example?  
Open an issue or a pull request – contributions are welcome!  
Please ensure any example data remains anonymised.

---

## 📜 License

This documentation repository is released under no license (consider it under the public domain, but the main repo is not) – feel free to reuse, adapt, and share.

---

**Happy OSINT Researching! 🔍**  
– [DAPOWER99](https://github.com/DAPOWER99)
```

---

This README is fully self‑contained and ready to be the front page of your new info repo. If you need any of the linked markdown files (`pipeline-overview.md`, etc.) written out as well, just ask – I'll supply them in one go.
