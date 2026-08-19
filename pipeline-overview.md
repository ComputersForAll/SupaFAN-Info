# Pipeline Overview

SupaFAN operates as a modular, linear data‑processing pipeline. Each stage is independent and can be understood separately.

## 1. Channel Resolver
Takes any YouTube identifier (handle, channel URL, or direct UC‑ID) and resolves it to a standard **Channel ID** using the YouTube Data API.

- Handles: `@MarkRober`, `youtube.com/@MarkRober`, `youtube.com/channel/UC...`, and legacy `/user/` URLs.
- Falls back to YouTube Search when no pattern matches.

## 2. Data Extractor Engine
Fetches all visible metadata from the channel and its recent uploads.

### Channel Metadata
- Title, description, subscriber count, view count, video count, creation date, country, and branding.

### Video Scanning
- Iterates the uploads playlist.
- For each video: views, likes, description, tags, duration, and privacy status.
- Optional: downloads the actual video + audio using `yt-dlp`.

### Comment Mining
- Fetches up to 500 top comments per video with pagination.
- Captures author, timestamp, like count, reply count, and full plain‑text content.
- Detects if comments are disabled.

## 3. Payload Optimizer
Prepares the raw data for the AI model.

- Ranks videos by engagement and keeps only the top N.
- Trims descriptions and comments to fit a token budget.
- Exports a compact JSON corpus for the LLM.

## 4. AI Intelligence Engine
Uses OpenRouter (with fallback to `openrouter/free`) to analyse the corpus.

### What the AI does
- Identifies the channel’s **primary topic** and **sub‑niches**.
- Extracts a **knowledge web**: entities, technical concepts, recurring motifs.
- Mines **hidden data**: emails, social links, external domains, real names.
- Evaluates **audience sentiment**, **community engagement**, and **tone**.
- Generates an **executive OSINT summary** with OPSEC (operational security) notes.

### Fallback chain
- Tries the user‑defined model (e.g., `google/gemma-3-27b-it:free`).
- Falls back to `openrouter/free` (auto‑router), then specific free models.
- If all fail, returns a structured placeholder report.

## 5. Text Writer Engine (info.txt)
Generates a **single, exhaustive, human‑readable report** that contains:

- Complete channel telemetry.
- Full AI analysis (JSON + readable key‑findings).
- Every video’s metadata, tags, and full description.
- Every captured comment (untruncated).
- Pipeline execution statistics and error logs.

## 6. Orchestrator
Glues everything together. Runs pre‑flight checks, handles partial failures, saves JSON exports (stats, knowledge web, AI analysis), and produces the final `info.txt`.

---

**Next:** [API Keys Setup](api-keys-setup.md)
