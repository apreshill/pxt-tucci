# pxt-tucci

A PixelTable project using uv for dependency management.

## Setup

This project uses [uv](https://github.com/astral-sh/uv) for dependency management. Dependencies are managed natively through `uv` - no pip or manual venv management needed.

1. Install dependencies: `uv sync` (this includes the spaCy English model and torch/transformers required for sentence splitting, object detection, and CLIP embeddings)
2. Configure OpenAI API key: The notebook will prompt you to enter your API key when you run it, or you can set it as an environment variable `OPENAI_API_KEY`

## Usage

- Run code: `uv run python <script.py>` or `uv run jupyter notebook`
- Add dependencies: `uv add <package>`
- Sync environment: `uv sync`

## Dependencies

### Core Dependencies

- **pixeltable** (>=0.3.13): Primary library for this project. Provides table, view, and computed column functionality.

### Audio Processing & Transcription

- **openai** (>=1.0.0): Required for OpenAI Whisper transcription (`pxt.functions.openai.transcriptions()`)
  - Used in: View 2 - transcribing audio chunks

### Text Processing & Embeddings

- **sentence-transformers** (>=2.0.0): Required for Hugging Face sentence embeddings
  - Used in: View 2 - creating embedding indexes on transcript text
  
- **spacy** (>=3.0.0): Required for sentence splitting in text processing
  - Used in: View 2 - splitting transcript text into sentences using `StringSplitter`
  - **en-core-web-sm**: The spaCy English language model is automatically installed via `uv sync` as a URL dependency

### Computer Vision & Object Detection

- **torch**: Required for PyTorch-based models (DETR object detection and CLIP embeddings)
  - Used in: View 3 - detecting objects in frames extracted from video and creating multimodal embeddings
  
- **transformers**: Required for Hugging Face transformer models (DETR and CLIP)
  - Used in: View 3 - detecting objects in frames using `pxt.functions.huggingface.detr_for_object_detection()` with model `facebook/detr-resnet-50`
  - Used in: View 3 - creating CLIP embeddings for multimodal search using `pxt.functions.huggingface.clip` with model `openai/clip-vit-base-patch32` via `add_embedding_index()`

### Development

- **jupyter** (>=1.1.1): For running the notebook