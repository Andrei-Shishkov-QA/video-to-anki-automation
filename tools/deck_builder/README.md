# Deck Builder

A desktop app that builds Anki decks from phrases, images and video clips, with audio from Google Text-to-Speech. Part of [Video-to-Anki](../../README.md). The code was written with an AI coding assistant.

**Stack:** Python 3.10+, Tkinter, genanki, Google Cloud Text-to-Speech, MoviePy, Pillow, FFmpeg

![Deck Builder demo](img/demo_animation(deck_builder).gif)

## What it does

- Builds a ready `.apkg` deck for Anki.
- Adds audio for each phrase with Google Text-to-Speech.
- Card types: front-to-back, back-to-front, or both.
- Resizes images and converts video for the target device.
- Names the output file with the deck size, date and video format.

## How to run

1. Install [FFmpeg](https://ffmpeg.org/download.html).
2. Install packages:
   ```bash
   cd tools/deck_builder
   pip install -r requirements.txt
   ```
3. For audio: put a Google Cloud key (JSON) into `keys/` — steps in `keys/README.txt`. The key is not stored in the repository.
4. Run:
   ```bash
   python main.py
   ```

## Input folder

```text
/your_input_folder/
├── ru_text.txt    # Russian phrases, one per line
├── en_text.txt    # English translations, one per line
├── images/        # 001.jpg, 002.jpg ...
└── video/         # 001.mp4, 002.mp4 ...
```

**Import Videos** can rename files by the number in the name (`my_video_45.mp4` → `045.mp4`).

## How to use

1. Choose the input folder.
2. **Import Phrases** and **Import Videos**.
3. Set the deck name, card type, video format and field order.
4. Click **Create Deck**. The deck is saved to `output/`.

## Video formats

| Format | Devices | Note |
|:--|:--|:--|
| MP4 | iOS and Android | works everywhere |
| M4V | iOS | for Apple devices |
| WEBM | PC and Android | does not play on iOS |
