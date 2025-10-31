# pxt-tucci

A PixelTable project using uv for dependency management.

## Setup

This project uses [uv](https://github.com/astral-sh/uv) for dependency management. Dependencies are managed natively through `uv` - no pip or manual venv management needed.

## Usage

- Run code: `uv run python <script.py>` or `uv run jupyter notebook`
- Add dependencies: `uv add <package>`
- Sync environment: `uv sync`

## Dependencies

- **pixeltable**: Primary library for this project. All code should use native PixelTable APIs.