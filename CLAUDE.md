# CLAUDE.md

This file provides guidance for Claude Code when working with this repository.

## Project Overview

A simple Streamlit chatbot app powered by OpenAI's GPT-3.5-turbo model. Users enter their OpenAI API key in the UI and chat with the model directly in the browser.

## Tech Stack

- **Python** — primary language
- **Streamlit** — UI framework for the web app
- **OpenAI Python SDK** — LLM backend (GPT-3.5-turbo)

## Repository Structure

```
streamlit_app.py   # Main application (single-file app)
requirements.txt   # Python dependencies
README.md          # User-facing setup instructions
```

## Development Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run the app:
   ```bash
   streamlit run streamlit_app.py
   ```

3. Open http://localhost:8501 in your browser, enter an OpenAI API key, and start chatting.

## Environment / Secrets

The app accepts the OpenAI API key via a UI input field. Alternatively, you can store it in `.streamlit/secrets.toml`:

```toml
OPENAI_API_KEY = "sk-..."
```

Then access it in code via `st.secrets["OPENAI_API_KEY"]`. Never commit API keys to the repository.

## Key Conventions

- Keep the app in a single file (`streamlit_app.py`) unless complexity clearly warrants splitting.
- Use `st.session_state` for any state that must persist across Streamlit reruns.
- Stream LLM responses with `stream=True` and `st.write_stream()` for a better UX.
- No test suite currently exists — manual testing via `streamlit run` is the primary verification method.
