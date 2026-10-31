# Subtitle Processor

A desktop app that finds phrases from your study list in film subtitles and prepares them for Anki cards. Part of [Video-to-Anki](../../README.md). The code was written with an AI coding assistant.

**Stack:** Python 3, PyQt5, SQLite, pymorphy3, pysrt

![Subtitle Processor demo](img/demo_animation(subtitle_extractor).gif)

## What it does

- Finds phrases in the subtitles even when the word form is different ("go" — "going"): words are reduced to their base form, and similar phrases are matched with a similarity score.
- Search runs in the background, so the window does not freeze.
- Saves the session in SQLite, so you can stop and continue later.
- Calculates the start and end time of a phrase inside a long subtitle line.

## How to run

You need Python 3.10+ and FFmpeg.

```bash
cd tools/subtitle_extractor
pip install -r requirements.txt
python app.py
```

## How to use

### 1. Input
- **Subtitles (SRT)** from the film or series.
- **English phrases (TXT)** — one per line.
- **Russian translations (TXT)** — one per line.
- **Output folder.**

### 2. Find and review
1. Click **Find Matches**. The table fills with full matches (green) and partial or not found ones.
2. Double-click a row to include or exclude it.
3. Use the slider to make matching stricter or softer.
4. If a phrase is not found, select it and click **Find Manually** to link it by hand.
5. To fix timing, select rows and click **Modify Timestamps** (for example, `-0.2` to the start, `+0.5` to the end), so the clip is not cut off.

### 3. Export
- **Get Excerpts** — text files with the found lines.
- **Get Timestamps** — a new `.srt` file with only the lines from your list.

## Files

- `app.py` — the window and background search.
- `database.py` — work with SQLite.
- `subtitle_processor.py` — phrase matching.
- `utils.py` — reading SRT and calculating timestamps.
