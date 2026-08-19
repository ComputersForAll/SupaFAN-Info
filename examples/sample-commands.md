# Sample CLI Commands

All commands are run from the root of the main `SupaFAN` repository.

## 1. Basic metadata extraction
```bash
python main.py -t @MarkRober
```
cans the last 25 uploads, extracts metadata and comments. No downloads.

### 2. Include video downloads
```bash
python main.py -t @MarkRober -d
```
Downloads the 25 most recent videos as MP4 (merges video + audio).

#### 3. Scan all videos
```bash
python main.py -t @MarkRober --scan-all
Scans every video in the uploads playlist (may take a long time).
```

### 4. Limit scan depth
```bash
python main.py -t @MarkRober -m 5
Only fetches the 5 most recent videos.
```
### 5. Use a specific channel ID
```bash
python main.py -t UCX6OQ3DkcsbYNE6H8uQQuVA
```
### 6. Interactive mode
```bash
python main.py
Prompts you for all settings (target, scan depth, download, output folder).
```
### 7. Quiet mode (minimal output)
```bash
python main.py -t @MarkRober -q
```
### 8. Set custom output directory
```bash
python main.py -t @MarkRober -o ./my_output
```
