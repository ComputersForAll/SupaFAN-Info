```markdown
# Troubleshooting Guide

## 1. `403 Forbidden` on video download

**Cause**: YouTube restricts the requested format, or your IP is rate‑limited.

**Solution**: Export your browser cookies:
1. Install a browser extension that exports cookies (e.g., “Get cookies.txt”).
2. Export to the SupaFAN root directory as `cookies.txt`.
3. Rerun the download.

## 2. OpenRouter returns `429 Too Many Requests`

**Cause**: Rate limiting (free tiers often have low RPM).

**Solution**:
- The pipeline automatically retries with exponential backoff. Wait.
- Reduce `--max-videos` to lower the prompt size.
- Add a paid key to your OpenRouter account for higher limits.

## 3. `YOUTUBE_API_KEY` not found or invalid

**Cause**: Missing or misformatted `.env`.

**Solution**:
- Ensure `.env` exists in the root directory.
- Check for typos in the key.
- Verify the YouTube Data API is enabled in Google Cloud Console.
- Use `python main.py -t @MrBeast` to test without downloads.

## 4. Comments are missing or show “disabled”

**Cause**: The video creator turned off comments, or YouTube’s API returned a 403.

**This is normal**. The pipeline logs `"comments_disabled": true` and skips them.

## 5. JSON parse error from OpenRouter

**Cause**: The AI model returned malformed JSON (extra text, markdown, or ‘thinking’ tags).

**Solution**:
- The pipeline automatically cleans Markdown code fences and `<think>` wrappers.
- If it persists, try a more reliable model like `openrouter/free`.
- You can manually edit the prompt in `ai_engine.py` to enforce raw JSON output.

## 6. `static-ffmpeg` not linking on Windows

**Cause**: Python path issues or missing binaries.

**Solution**:
- Run `pip install static-ffmpeg --upgrade`.
- If that fails, install system‑wide ffmpeg and add it to PATH.
- The pipeline will fall back to lower‑quality single‑file downloads.

## 7. Pipeline stops with “partial failure”

**Cause**: One of the stages (e.g., video scanning) hit an API quota limit.

**Solution**:
- Check your YouTube API quota usage.
- Reduce `--max-videos` or wait for quota to reset.
- The saved JSON files will contain whatever was fetched before the failure.
