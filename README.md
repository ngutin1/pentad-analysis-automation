# Campaign Rhetoric Analysis: Pentad Analysis of Harris 2024 Campaign Speeches

A comprehensive pipeline for transcribing, processing, and analyzing political campaign rhetoric using Kenneth Burke's pentad framework. This project focuses on Kamala Harris's 2024 presidential campaign speeches to understand rhetorical strategies and their correlation with polling trends.

## Project Overview

This project systematically analyzes campaign rhetoric through:

- **Automated transcription** of YouTube campaign videos using Whisper AI
- **Semantic chunking** for optimal text processing
- **Pentad analysis** to quantify rhetorical choices and strategies

## Dataset

The analysis covers **71 campaign events** from Kamala Harris's 2024 presidential campaign, including:
- Rally speeches
- Interview appearances  
- Town halls
- Campaign events
- Podcast appearances


## Technical Pipeline

### 1. Data Collection & Transcription
- **Input**: YouTube URLs with timestamp ranges from campaign events
- **Audio Extraction**: `yt-dlp` for downloading campaign video segments
- **Transcription**: OpenAI Whisper (small model) for speech-to-text conversion
- **Cleaning**: Script to remove audience responses, chants, and repetitive elements

### 2. Text Processing
- **Semantic Chunking**: Using sentence transformers (`all-MiniLM-L6-v2`) for coherent text segmentation
- **Optimal Chunk Size**: 2000-4000 characters for LLM processing efficiency
- **Similarity Threshold**: 0.6 cosine similarity for maintaining rhetorical coherence

### 3. Pentad Analysis Framework
[Kenneth Burke's Pentad] analyzes rhetoric through five elements:
- **Act**: What was done/proposed
- **Scene**: Context and setting
- **Agent**: Who is responsible/involved
- **Agency**: How something is accomplished
- **Purpose**: Why something is done

# 4. Analysis
https://ngutin.substack.com/p/the-art-of-failed-storytelling-the

## Contributing

Contributions are welcome! Areas of particular interest:
- Improving transcription accuracy for irregular speech patterns
- Enhancing semantic chunking algorithms
- Developing pentad analysis automation
- Creating visualization tools for rhetorical trends

## License

This project is licensed under the MIT License - see the [LICENSE] file for details.

## Acknowledgments

- **Ballotpedia** for comprehensive campaign event tracking and metadata
- **OpenAI Whisper** for speech transcription capabilities
- **Sentence Transformers** for semantic text processing
- **Kenneth Burke** for the pentad rhetorical analysis framework
- **Campaign staff and media outlets** for providing publicly available speech recordings

