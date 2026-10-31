# Video-to-Anki

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![GUI](https://img.shields.io/badge/GUI-PyQt5%20·%20Tkinter-green)
![Status](https://img.shields.io/badge/Status-Personal%20tool-lightgrey)

Two small desktop tools I made for myself to learn English from films and series. They turn subtitles and video into Anki flashcards with video clips and audio.

## How it was built

The code was written with an AI coding assistant (May 2025 – January 2026).

My part:
- idea and requirements: what the tools should do in my own learning routine;
- testing the tools on my own films and phrase lists and checking the resulting cards in Anki;
- Git: feature branches (`feature/gemini-api-test`, `go_to_sqlite`) and a release branch (`release/v1.0`).

There are almost no automated tests — the tools were tested by hand.

## Demos

### Subtitle Processor
![Subtitle Processor demo](img/demo_animation(subtitle_extractor).gif)

### Deck Builder
![Deck Builder demo](img/demo_animation(deck_builder).gif)

## Tools

| Tool | What it does | Stack |
|:--|:--|:--|
| **Subtitle Processor** (`tools/subtitle_extractor`) | Finds phrases from your list in the subtitles, even in another word form. You can fix matches and timestamps by hand and export only the lines you need. | PyQt5, SQLite, pymorphy3, pysrt |
| **Deck Builder** (`tools/deck_builder`) | Builds an Anki deck (`.apkg`) from phrases, images and video clips. Adds audio with Google Text-to-Speech. Video formats for iOS, Android and PC. | Tkinter, genanki, Google Cloud TTS, MoviePy, Pillow |

## Repository structure

```text
video-to-anki-automation/
├── tools/
│   ├── subtitle_extractor/   # Subtitle Processor (PyQt5)
│   └── deck_builder/         # Deck Builder (Tkinter)
├── img/                      # demo animations
├── requirements.txt
└── README.md
```

## How to run

You need Python 3.10+ and [FFmpeg](https://ffmpeg.org/download.html).

```bash
git clone https://github.com/Andrei-Shishkov-QA/video-to-anki-automation.git
cd video-to-anki-automation
pip install -r requirements.txt

python tools/subtitle_extractor/app.py   # Subtitle Processor
python tools/deck_builder/main.py        # Deck Builder
```

Deck Builder needs a Google Cloud key for audio — see `tools/deck_builder/keys/README.txt`.
