```markdown
# Output Format Reference

SupaFAN generates four files per run.

## 1. `channel_stats_*.json`
A lightweight summary of the channel.

```json
{
  "script_version": "2.0.0",
  "generated_at": "2026-08-19T14:32:10+00:00",
  "channel_metadata": {
    "title": "Sample Channel",
    "subscriber_count": "123456",
    "view_count": "1234567",
    "video_count": "42"
  },
  "scanned_videos_count": 25,
  "total_comments_collected": 320
}
