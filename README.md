# Campaign Rhetoric Analysis: Pentad Analysis of Harris 2024 Campaign Speeches

A comprehensive pipeline for transcribing, processing, and analyzing political campaign rhetoric using Kenneth Burke's pentad framework. This project focuses on Kamala Harris's 2024 presidential campaign speeches to understand rhetorical strategies and their correlation with polling trends.

## Project Overview

This project systematically analyzes campaign rhetoric through:

- **Automated transcription** of YouTube campaign videos using Whisper AI
- **Semantic chunking** for optimal text processing
- **Pentad analysis** to quantify rhetorical choices and strategies
- **Correlation analysis** between rhetorical patterns and polling momentum

## Dataset

The analysis covers **71 campaign events** from Kamala Harris's 2024 presidential campaign, including:
- Rally speeches
- Interview appearances  
- Town halls
- Campaign events
- Podcast appearances

**Output**: 624 text chunks (553 semantic chunks + 71 full transcripts) totaling over 500,000 words of campaign rhetoric.

## Technical Pipeline

### 1. Data Collection & Transcription
- **Input**: YouTube URLs with timestamp ranges from campaign events
- **Audio Extraction**: `yt-dlp` for downloading campaign video segments
- **Transcription**: OpenAI Whisper (small model) for speech-to-text conversion
- **Cleaning**: Custom algorithms to remove audience responses, chants, and repetitive elements

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

## Getting Started

### Prerequisites
```bash
# Core dependencies
pip install yt-dlp whisper-timestamped pandas tqdm
pip install sentence-transformers torch
pip install tensorflow==2.13.0 tf-keras  # Optional for advanced analysis

# System requirement: ffmpeg for audio processing
# Windows: Download from https://ffmpeg.org/download.html
# macOS: brew install ffmpeg
# Linux: sudo apt install ffmpeg
```

### Installation
```bash
git clone https://github.com/ngutin1/pentad-analysis-automation
cd pentad-analysis-automation
pip install -r requirements.txt
```

### Basic Usage
```python
# Load and process campaign events
import pandas as pd
from script import process_event, clean_transcript, test_chunker

# Load campaign event data
events_df = pd.read_csv('Kamala_Activity.csv')

# Process individual event
result_df = process_event(events_df.iloc[0])

# Or process multiple events
results = []
for idx, row in events_df.iterrows():
    try:
        result = process_event(row)
        if not result.empty:
            results.append(result)
            print(f"Processed: {row['Date']} - {row['Type']}")
    except Exception as e:
        print(f"Error processing {row['Date']}: {e}")

# Combine results
analysis_df = pd.concat(results, ignore_index=True)
analysis_df.to_csv('pentad_analysis_data.csv', index=False)
```

## Project Structure
```
campaign-rhetoric-analysis/
├── script.ipynb              # Main processing pipeline
├── Kamala_Activity.csv       # Campaign event metadata
├── pentad_analysis_data.csv  # Processed speech chunks
├── requirements.txt          # Python dependencies
├── README.md                # This file
```

## Key Functions

### `download_audio(youtube_url, start_time, duration=None)`
Downloads audio segments from YouTube videos using yt-dlp.

### `new_transcribe_audio(start_time_seconds, video_id=None, event_date=None, location=None)`
Transcribes audio using Whisper with metadata tracking.

### `clean_transcript(text, min_repeat_threshold=3, min_word_length=2)`
Removes audience responses, repetitive chants, and transcription artifacts.

### `test_chunker(speech_text, threshold=0.6, min_sentences=5, target_chunk_size=2000, max_chunk_size=4000)`
Creates semantically coherent text chunks optimized for LLM analysis.


## Technical Details

### Transcription Accuracy
- **Model**: OpenAI Whisper (small) for speed/accuracy balance
- **Language Detection**: Automatic with English optimization
- **Error Handling**: Graceful handling of audio boundary issues
- **Quality Control**: Manual review flagged for 4-6 irregular speaking events

### Chunking Algorithm
- **Embedding Model**: `all-MiniLM-L6-v2` for semantic similarity
- **Similarity Threshold**: 0.6 cosine similarity for coherence
- **Size Optimization**: 2K-4K character chunks for LLM processing
- **Boundary Preservation**: Maintains sentence and rhetorical integrity

## Future Development

### Phase 1: Pentad Automation
- [ ] Design LLM prompts for pentad element extraction
- [ ] Create JSON schema for structured rhetorical analysis
- [ ] Implement automated pentad classification pipeline

### Phase 2: Correlation Analysis
- [ ] Integrate polling data with rhetorical analysis
- [ ] Develop metrics for rhetorical strategy effectiveness
- [ ] Create visualizations for trend analysis

### Phase 3: Comparative Framework
- [ ] Expand to multi-candidate analysis
- [ ] Develop rhetorical strategy taxonomies
- [ ] Build predictive models for campaign messaging effectiveness


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

## Contact

For questions about methodology, collaboration opportunities, or data access:
- Create an issue in this repository
- Contact: [nicholasgutin@gmail.com]

---

*This project is for academic and research purposes, analyzing publicly available campaign content to understand political rhetoric and communication strategies.*
 
