# ⬇️ InnerUploader

**Download any file to your Google Drive using Google's own servers — no VPN needed.**

InnerUpload runs entirely inside [Google Colab](https://colab.research.google.com), so the download happens on Google's infrastructure and lands directly in your Google Drive. No local bandwidth used, no speed limits from your ISP.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/innerupload/blob/main/InnerUpload.ipynb)

---

## How it works

```
Your link  →  Google Colab (downloads)  →  Your Google Drive
```

1. You paste a download link into the notebook
2. Colab fetches the file on Google's servers
3. The file is saved to your Google Drive and you get a shareable link

---

## Supported link types

| Source | Example |
|---|---|
| Direct HTTP/HTTPS | `https://example.com/file.zip` |
| Google Drive (share link) | `https://drive.google.com/file/d/...` |
| Dropbox | `https://www.dropbox.com/s/...` |
| GitHub Releases | `https://github.com/user/repo/releases/download/...` |
| Most public servers | Any server that doesn't require login |

---

## Quick start

### Option A — Open directly in Colab
Click the badge at the top of this page. No installation needed.

### Option B — Manual
1. Download `InnerUpload.ipynb`
2. Go to [colab.research.google.com](https://colab.research.google.com)
3. Click **File → Upload notebook** and select the file
4. Click **Runtime → Run all**

---

## Usage

The notebook guides you through 4 steps:

**Step 1 — Install dependencies**
Run once. Installs `gdown`, `tqdm`, and `requests`.

**Step 2 — Mount Google Drive**
Grants Colab access to your Drive. Your files will be saved here.

**Step 3 — Settings**

| Field | Description | Default |
|---|---|---|
| `DRIVE_FOLDER_NAME` | Folder in your Drive to save files into | `InnerUpload` |
| `DOWNLOAD_LINKS` | One URL per line | _(empty)_ |
| `OVERWRITE_IF_EXISTS` | Re-download if file already exists | `false` |

**Step 4 — Start Download**
Runs the download and prints a shareable Drive link for each file when done.

**Bonus — Download from a .txt file**
Upload a plain text file with one URL per line and point the notebook to it. Useful for batch downloads.

---

## Output

After each download you'll see:
```
[1/2] 🔗 https://example.com/movie.mp4
   ✅ Saved: movie.mp4 (1204.3 MB)
   🔗 Drive link: https://drive.google.com/file/d/1abc.../view?usp=sharing
```

And a full summary at the end:
```
📊 Summary: 2 succeeded, 0 failed
📁 Saved to: /content/drive/MyDrive/InnerUpload

✅ Drive links:
   • https://example.com/movie.mp4
     → https://drive.google.com/file/d/1abc.../view?usp=sharing
```

---

## Notes

- **Session limit** — Free Colab sessions disconnect after ~12 hours of inactivity. For large batches, stay on the tab or use Colab Pro.
- **Storage** — Files are saved to your personal Google Drive. Make sure you have enough free space.
- **Private links** — Links that require login or a password won't work. The file must be publicly accessible.
- **Google Drive share links** — Large files on Drive show a virus-scan warning page. This notebook handles that automatically via `gdown`.

---

## Requirements

- A Google account (for Colab + Drive access)
- No installation, no VPN, no API keys

---

## License

MIT — free to use, modify, and share.
