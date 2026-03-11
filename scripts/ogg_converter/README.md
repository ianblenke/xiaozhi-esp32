# ogg_converter - Xiaozhi AI OGG Audio Batch Converter

This script is a batch OGG conversion tool that supports converting input audio files to OGG format usable by Xiaozhi.

Based on the Python third-party library `ffmpeg-python`, **requires** `ffmpeg` environment.

You can go [here](https://ffmpeg.org/download.html) to download the ffmpeg distribution for your system and add it to your environment variables or place it in the script directory.

Supports mutual conversion between OGG and audio, loudness adjustment and other features.

# Create and Activate Virtual Environment

```bash
# Create virtual environment
python -m venv venv
# Activate virtual environment
source venv/bin/activate # Mac/Linux
venv\Scripts\activate # Windows
```
# Download FFmpeg
Go [here](https://ffmpeg.org/download.html) to download ffmpeg.

Download the version corresponding to your current system and place the `ffmpeg` executable in the script directory or add the executable's directory to your environment variables.

# Install Dependencies
Please execute in the virtual environment

```bash
pip install ffmpeg-python
```

# Run the Script
```bash
python ogg_covertor.py
```
