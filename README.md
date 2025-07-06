
# 🎬 YouTube KPT Synthesizer AI Agent with Multi-LLM

This repository contains a **production-ready n8n workflow** that ingests YouTube video content, extracts metadata and transcripts, cleans and structures the data, and synthesizes insights using multiple Large Language Models (LLMs) such as **OpenAI GPT-4 and DeepSeek**. This module implements a robust **Knowledge, Process, Technology (KPT)** summarizer pipeline for actionable insights.

---

## 🧠 **Project Overview**

The **YouTube KPT Synthesizer AI Agent** automates end-to-end video insight generation with the following architecture:

1. **Ingest YouTube Data**
   - Fetches video metadata (`videoId`, `channelName`, `publishDate`, `fullUrl`) via YouTube Data API.
   - Retrieves full transcripts using the Apify YouTube Scraper API.

2. **Clean and Process**
   - Cleans transcript data, removing noise, and consolidates it into a structured `fullTranscript`.
   - Merges metadata and transcript into a unified, consistent data structure.

3. **Multi-LLM Synthesis**
   - Uses **OpenAI GPT-4** to generate structured markdown summaries including:
     - **SEO Title**
     - **One-Sentence Summary**
     - **Key Takeaways** (Knowledge, Process, Technology insights)
     - **Concluding Thought**
   - Integrates **DeepSeek** as the final voting and synthesis agent, combining outputs from multiple models into a single actionable KPT summary.

4. **Output**
   - Posts the final synthesized markdown summary to Slack for immediate team review and archival.
   - Saves the output into connected knowledge bases (e.g. Notion) for long-term strategic tracking.

---

## 🖼️ **Workflow Architecture**

YouTube_KPT_Synthesizer_Workflow/
├── Trigger: Manual or Scheduler
├── Set Node: Input YouTube URL
├── Code Node: Extract Video ID
├── HTTP Request: Fetch YouTube Metadata
│   └── Code Node: Extract Metadata (channelName, publishDate, videoId, fullUrl)
├── HTTP Request: Request YouTube Transcript (Apify)
│   └── Code Node: Clean Transcript
├── Merge Node: Combine Metadata + Transcript
├── Multi-LLM Synthesis:
│   ├── OpenAI GPT-4 Node: Generate KPT Structured Summary
│   └── DeepSeek Agent Node: Final Synthesis & Voting (multi-LLM ensemble)
└── Slack Node: Post Final Markdown Summary

---

## 🔥 **Key Features**

- **Multi-LLM Ensemble Reasoning**: Combines outputs from GPT-4, Claude Mini, DeepSeek, and others for robust summarization.  
- **Automated Knowledge Extraction**: Converts unstructured transcripts into structured KPT summaries.  
- **Slack Integration**: Delivers insights directly to your Slack channels for rapid decision-making.  
- **Production-Ready Modular Design**: Integrates seamlessly within the broader **Synth AI Synthesis Agent** framework.

---

## 🚀 **Getting Started**

### 📝 **Prerequisites**

- [n8n](https://n8n.io/) (Cloud or self-hosted)
- API keys for:
  - YouTube Data API
  - Apify
  - OpenAI or your preferred OpenRouter models
  - Slack webhook

---

### 💻 **Installation**

1. Clone this repository:

```bash
git clone https://github.com/your-username/youtube-kpt-synthesizer-ai.git
cd youtube-kpt-synthesizer-ai
```

2. Import the `YouTube_Agent_Clean.json` workflow into your n8n instance.

3. Configure your credentials for all API calls within n8n.

4. Execute manually or set a scheduler for automated runs.

---

## 🤝 **Contributing**

Contributions are welcome to improve modularity, model integration, or output formatting. Please open an issue or submit a pull request.

---

## 📄 **License**

MIT

---

> © 2025 | Developed as part of the Synth AI Synthesis Agent system – demonstrating robust, multi-LLM agent orchestration and KPT summarization pipelines.
