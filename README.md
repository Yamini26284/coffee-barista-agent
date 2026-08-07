# ☕ Coffee Barista AI Agent

A conversational AI agent that recommends coffee shop orders using Retrieval-Augmented Generation (RAG), built with Google's Agent Development Kit (ADK) and Gemini, deployed on Google Cloud Run.

## What it does

Customers chat with a barista agent that recommends drinks and pastries based on their preferences (e.g. dairy-free, vegan, strong, cold). The agent grounds every recommendation in real menu data via a custom retrieval tool — it never suggests items that aren't actually on the menu.

## Architecture

- **Frontend:** Streamlit chat interface
- **Agent Runtime:** Google ADK `LlmAgent`, powered by Gemini
- **Retrieval:** Custom Python tool (`get_menu()`) that grounds responses in `menu.json`
- **Deployment:** Google Cloud Run (containerized via buildpacks)

**Flow:** User → Streamlit UI (Cloud Run) → ADK Agent → `get_menu()` tool → Gemini API → grounded response

## Tech Stack

- Google Agent Development Kit (ADK)
- Gemini (via Vertex AI)
- Streamlit
- Google Cloud Run

## Project Structure

\```
coffee-barista-agent/
├── agent.py          # ADK agent definition + get_menu() tool
├── app.py            # Streamlit chat UI
├── menu.json          # Mock menu data (grounding source)
├── requirements.txt   # Python dependencies
├── LICENSE             # Apache 2.0
└── README.md
\```

## Running Locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

## Deployment

Deployed to Google Cloud Run using source-based deployment:

```bash
gcloud run deploy coffee-barista \
  --source . \
  --region <your-region> \
  --allow-unauthenticated \
  --service-account "<your-service-account>"
```

## Credits & Attribution

This project is based on Google's official codelab: [*Build a RAG AI Agent in Streamlit using Google ADK and Cloud Run*](https://codelabs.developers.google.com/codelabs/cloud-run/build-streamlit-rag-agent-google-adk-cloud-run), licensed under Apache 2.0 (code) / CC-BY-4.0 (content). Built as part of Google's GenAI Academy APAC — Track 1.

## Demo

*(Video/GIF coming soon)*

## License

Apache 2.0 — see [LICENSE](LICENSE)
