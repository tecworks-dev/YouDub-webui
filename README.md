
# YouDub-webui: High-quality video localization tool
## Table of contents
- [YouDub-webui: High-quality video localization tool](#youdub-webui-High-quality video localization tool)
  - [Directory](#Directory)
  - [Introduction](#Introduction)
  - [Main Features](#Main Features)
  - [Installation and Usage Guide](#Installation and Usage Guide)
    - [1. Clone the repository](#1-Clone the repository)
    - [2. Install dependencies](#2-Install dependencies)
      - [Automatic installation](#Automatic installation)
      - [Manual Installation](#Manual Installation)
    - [3. Environment Settings](#3-Environment Settings)
    - [4. Run the program](#4-Run the program)
      - [Autorun](#Autorun)
      - [Manual Run](#Manual Run)
  - [Usage steps](#Usage steps)
    - [1. **Fully automatic (Do Everything)**](#1-Fully automatic-do-everything)
    - [2. **Download Video**](#2-Download-video)
    - [3. Demucs Interface]
    - [4. Whisper Inference]
    - [5. **Subtitle Translation (Translation Interface)**](#5-Subtitle Translation-translation-interface)
    - [6. **Speech Synthesis (TTS Interface)**](#6-speech synthesis-tts-interface)
    - [7. Synthesize Video Interface](#7-Synthesize-video-interface)
  - [Technical Details](#Technical Details)
    - [AI Speech Recognition](#ai-speech-recognition)
    - [Large Language Model Translation](#Large Language Model Translation)
    - [AI Voice Cloning](#ai-voice-cloning)
    - [Video Processing](#Video Processing)
  - [Contribution Guidelines](#Contribution Guidelines)
  - [License Agreement](#License Agreement)
  - [Support and Contact](#Support and Contact)

## Introduction
`YouDub-webui` is a web interactive version of the [`YouDub`](https://github.com/liuzhao1225/YouDub) project, built on `Gradio`, providing users with a simple interface to access and use the powerful features of [`YouDub`](https://github.com/liuzhao1225/YouDub). [`YouDub`](https://github.com/liuzhao1225/YouDub) is a groundbreaking open source tool designed to translate and dub high-quality videos on YouTube and other platforms into Chinese versions. The tool combines the latest AI technologies, including speech recognition, large language model translation, and AI sound cloning technology to provide Chinese dubbing similar to the original video, providing Chinese users with an excellent viewing experience.

`YouDub-webui` is suitable for a variety of scenarios, including education, entertainment and professional translation, and is particularly suitable for users who want to localize excellent foreign video content. The simple interface of this tool makes it easy for even non-technical users to get started and quickly localize videos.

For more information and examples about `YouDub-webui`, please visit our [bilibili video homepage](https://space.bilibili.com/1263732318). In order to better serve the community, we have also set up a WeChat group. Welcome to join us by scanning the [QR code](#Support and Contact) below to discuss and contribute to the development of `YouDub-webui`.


Of course, I will rewrite the main features section of `YouDub-webui`.

---

## Main Features
`YouDub-webui` integrates a number of advanced technologies and provides a complete set of video localization toolkits. Its main features include:

- **Video Download**: Supports downloading YouTube videos directly through links. Whether it is a single video, a playlist or multiple videos in a channel, it can be downloaded easily.
- **AI Speech Recognition**: Using advanced AI technology, the speech in the video is efficiently converted into text. It not only provides accurate speech-to-text conversion, but also automatically aligns time and identifies different speakers, greatly enhancing the richness and accuracy of information.
- **Large Language Model Translation**: Combined with large language models such as GPT, fast and accurate Chinese translation is achieved. Whether it is slang or professional terms, they can be properly translated to ensure the accuracy and authenticity of the content.
- **AI Voice Cloning**: Through AI voice cloning technology, Chinese voices similar to the original video dubbing are generated. This not only improves the viewing experience of the video, but also retains the emotional and intonation characteristics of the original video.
- **Video Processing**: It integrates multiple functions such as audio and video synchronization processing, subtitle addition, video playback speed adjustment and frame rate setting. Users can generate high-quality final videos as needed to achieve a seamless viewing experience.
- **Automatic upload**: Supports automatic uploading of the final video to the Bilibili platform. Users can upload videos to the Bilibili platform without leaving `YouDub-webui`, realizing one-click video localization.

These features of `YouDub-webui` make it a powerful and easy-to-use video localization tool that can benefit both individual users and professional teams.


## Installation and Usage Guide

To use YouDub-webui, follow these steps to install and configure your environment:

### 1. Clone the repository
First, clone the YouDub-webui repository to your local system:
```bash
git clone https://github.com/liuzhao1225/YouDub-webui.git
```

### 2. Install dependencies
You can choose to install dependencies automatically or manually:

#### Automatic Installation
- Enter the `YouDub-webui` directory and run the `setup_windows` script.
- The script will create a `venv` virtual environment in the current directory and automatically install the required dependencies, including the CUDA 12.1 version of PyTorch.

#### Manual Installation
- Enter the `YouDub-webui` directory and use the following command to install dependencies:
  ```bash
  cd YouDub-webui
  pip install -r requirements.txt
  ```
- Due to the special nature of TTS dependencies, TTS has been removed from `requirements.txt` and needs to be installed manually:
  ```bash
  pip install TTS
  ```
- The default installation is the CPU version of PyTorch. If you need to manually install a specific CUDA version of PyTorch, you can get the installation command from the [PyTorch official website](https://pytorch.org/) according to your CUDA version.

### 3. Environment Setup
Before running, please configure the environment variables:

- **Environment variable configuration**: Rename `.env.example` to `.env` and fill in the following environment variables:
  - `OPENAI_API_KEY`: OpenAI API key, usually in the format of `sk-xxx`.
  - `MODEL_NAME`: Model name, such as 'gpt-4' or 'gpt-3.5-turbo'.
  - `OPENAI_API_BASE`: OpenAI API base URL. If you use your own deployed model, please fill it in.
  - `HF_TOKEN`: Hugging Face token, used for speaker diarization.
  - `HF_ENDPOINT`: If you get errors downloading models from `huggingface`, you can add this environment variable.
  - `APPID` and `ACCESS_TOKEN`: Credentials required for Volcano Engine TTS.
  - `BILI_BASE64`: The credentials required by the Bilibili API. For more information, please refer to [bilibili-toolman Preparing Credentials](https://github.com/mos9527/bilibili-toolman?tab=readme-ov-file#%E5%87%86%E5%A4%87%E5%87%AD%E6%8D%AE) for how to obtain them.

### 4. Run the program
Choose one of the following ways to run the program:

#### Automatically run
- Run `run_windows.bat` in the `YouDub-webui` directory.

#### Manual Run
- Start the main program using the following command:
  ```bash
  python app.py
  ```

## Usage Steps

### 1. **Do Everything**

This interface is a one-stop solution that will perform all steps from video downloading to video synthesis.

- **Root Folder**: Set the root directory of video files.
- **Video URL**: Enter the URL of the video or playlist or channel.
- **Number of videos to download**: Set the number of videos to download.
- **Resolution**: Select the resolution of the downloaded video.
- **Demucs Model**: Select the Demucs model for audio separation.
- **Demucs Device**: Select the audio separation processing device.
- **Number of shifts**: Set the number of shifts when separating audio.
- **Whisper Model**: Select the Whisper model for speech recognition.
- **Whisper Download Root**: Set the download root directory of Whisper models.
- **Whisper Batch Size**: Set the batch size for Whisper processing.
- **Whisper Diarization**: Select whether to perform speaker separation.
- **Translation Target Language**: Select the target translation language for the subtitles.
- **Force Bytedance**: Select whether to force the use of Bytedance speech synthesis.
- **Subtitles**: Choose whether to include subtitles in the video.
- **Speed ​​Up**: Set the video playback speed.
- **FPS**: Set the frame rate of the video.
- **Max Workers**: Set the maximum number of worker threads to process tasks.
- **Max Retries**: Set the maximum number of retries after a task fails.
- **Auto Upload Video**: Select whether to automatically upload videos to Bilibili.

### 2. **Download Video**

This interface is used to download videos individually.

- **Video URL**: Enter the URL of the video or playlist or channel.
- **Output Folder**: Set the output folder for the video after downloading.
- **Resolution**: Select the resolution of the downloaded video.
- **Number of videos to download**: Set the number of videos to download.

### 3. **Vocal Separation (Demucs Interface)**

This interface is used to separate human voice from video.

- **Folder**: Set the folder containing videos.
- **Model**: Select the Demucs model for audio separation.
- **Device**: Select the processing device for audio separation.
- **Progress Bar in Console**: Choose whether to display the progress bar in the console.
- **Number of shifts**: Set the number of shifts when separating audio.

### 4. Whisper Inference

This interface is used for speech recognition from video audio.

- **Folder**: Set the folder containing videos.
- **Model**: Select the Whisper model to use for speech recognition.
- **Download Root**: Set the download root directory of Whisper models.
- **Device**: Select the processing device for speech recognition.
- **Batch Size**: Set the batch size for Whisper processing.
- **Diarization**: Select whether to perform speaker separation.

### 5. **Subtitle Translation (Translation Interface)**

This interface is used to convert the recognized speech into subtitles and translate them.

- **Folder**: Set the folder containing videos.
- **Target Language**: Select the target language for subtitle translation.

### 6. **Speech Synthesis (TTS Interface)**

This interface is used to convert the translated text into speech.

- **Folder**: Set the folder containing videos.
- **Force Bytedance**: Select whether to force the use of Bytedance speech synthesis.

### 7. **Synthesize Video Interface**

This interface is used to synthesize video, subtitles and speech into the final video.

- **Folder**: Set the folder containing videos.
- **Subtitles**: Choose whether to include subtitles in the video.
- **Speed ​​Up**: Set the video playback speed.
- **FPS**: Set the frame rate of the video.
- **Resolution**: Select the resolution of the video.

Technical Details

AI Voice Recognition
Our AI speech recognition capabilities are now based on [WhisperX](https://github.com/m-bain/whisperX). WhisperX is an efficient speech recognition system built on the Whisper system developed by OpenAI. It not only accurately converts speech to text, but also automatically aligns time and identifies the speaker of each sentence. This advanced processing method not only improves processing speed and accuracy, but also provides users with richer information, such as speaker identification.

### Large Language Model Translation
Our translation function continues to use various models provided by the OpenAI API, including the official GPT model. At the same time, we are also leveraging projects such as [api-for-open-llm](https://github.com/xusenlinzy/api-for-open-llm), which enables us to more flexibly integrate and utilize different large language models for translation work, ensuring translation quality and efficiency.

### AI Voice Cloning
For voice cloning, we have turned to [Coqui AI TTS](https://github.com/coqui-ai/TTS). At the same time, for single-speaker situations, we use Volcano Engine for TTS to obtain better sound quality. Volcano Engine's advanced technology can generate extremely natural and fluent voices, which are suitable for a variety of application scenarios and improve the overall quality of the final product.

### Video Processing
In terms of video processing, we still emphasize the synchronization of audio and video. Our goal is to ensure perfect alignment of audio and video and generate accurate subtitles to provide users with a seamless and immersive viewing experience. Our processing flow and technology ensure the high quality of video content and the continuity of viewing.


## Contribution Guidelines
Welcome to contribute to `YouDub-webui`. You can submit improvement suggestions or report problems through [GitHub Issues](https://github.com/liuzhao1225/YouDub-webui/issues) or [Pull Request](https://github.com/liuzhao1225/YouDub-webui/pulls).

## License Agreement
`YouDub-webui` is licensed under the Apache License 2.0. When using this tool, please ensure that you comply with relevant laws and regulations, including copyright, data protection, and privacy laws. Do not use this tool without the permission of the original content creator and/or copyright owner.

## Support and Contact
If you need help or have any questions, please contact us through [GitHub Issues](https://github.com/liuzhao1225/YouDub-webui/issues).
Join our Discord server for discussion and support: [Discord server](https://discord.gg/vbkYnN2Rrm)
You can also join our WeChat group by scanning the QR code below:

![WeChat Group](https://github.com/liuzhao1225/YouDub/blob/main/docs/d50300d5db9d8cc71861174fc5d33b1.jpg)
