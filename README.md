# Nexora Vibe Matcher

A self-contained Jupyter notebook project built for the Nexora AI Internship. The notebook walks through a proof-of-concept recommender that matches user vibe descriptions to a small fashion catalog using vector similarity.

## Project Highlights
- **Dual Embedding Backends:** Uses OpenAI `text-embedding-3-small` when an API key is provided; otherwise, falls back to TF-IDF.
- **Vibe Matcher Function:** `vibe_matcher(query, top_k=3)` returns the top matches with similarity scores and latency measurements.
- **Good Match Metric:** Reports how many matches exceed the 0.7 cosine similarity threshold.
- **Latency Analytics:** Logs and visualizes per-query latency, including average and run counts.
- **Reflection & Wrap-Up:** Documents learnings and future improvements.

## Repository Structure
```
Nexora_Vibe_Matcher/
├── README.md
├── vibe_matcher.ipynb
├── .gitignore
└── (generated temporary folders such as `tmp/` or `tmp_runtime/` are ignored)
```

## Prerequisites
- Python 3.9+
- Recommended to use a virtual environment (`python -m venv .venv`)

Required packages are imported directly in the notebook (install via `pip install` as needed):
- `pandas`, `numpy`
- `scikit-learn`
- `matplotlib`
- `openai`
- `python-dotenv`

## Getting Started
1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/Nexora_Vibe_Matcher.git
   cd Nexora_Vibe_Matcher
   ```

2. **Create and activate a virtual environment (optional but recommended)**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # macOS/Linux
   .venv\Scripts\activate   # Windows
   ```

3. **Install dependencies**
   ```bash
   pip install pandas numpy scikit-learn matplotlib openai python-dotenv
   ```

4. **Set up OpenAI (optional)**
   - Create a `.env` file in the project root:
     ```bash
     echo "OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxx" > .env
     ```
   - If no key is provided, the notebook will automatically switch to TF-IDF embeddings.

5. **Launch Jupyter and run the notebook**
   ```bash
   jupyter notebook vibe_matcher.ipynb
   ```
   Run all cells top-to-bottom for a fresh execution.

## Notebook Walkthrough
- **Environment Setup:** Imports, environment variables, and backend initialization.
- **Mock Catalog Construction:** Creates a small dataset of fashion items with descriptions and vibe tags.
- **Embedding Generation:** Embeds the catalog using OpenAI or TF-IDF.
- **`vibe_matcher` Utility:** Handles query embedding, cosine similarity, latency logging, and friendly no-match messages.
- **Sample Queries:** Tests the matcher with “energetic urban chic”, “elegant festive wear”, and “rugged outdoor adventure”.
- **Good Match Metric:** Reruns queries and counts results with similarity > 0.7.
- **Latency Analysis:** Summaries and bar charts for per-query latency.
- **Reflection & Submission:** Key takeaways and a timestamp confirming readiness.

## Results Snapshot
- **Backend:** Defaults to TF-IDF when no OpenAI key is present; prints the active backend each run.
- **Similarity Scores:** With the mock dataset, most matches score < 0.7; the good-match metric still confirms the calculations.
- **Latency:** Queries return in < 1 ms locally (TF-IDF) in this mock setup.

## Future Enhancements
- Plug in larger catalogs or a vector database for scale.
- Expand vibe taxonomies and add richer metadata.
- Explore re-ranking strategies (e.g., diversity-aware ranking, personalization).
- Connect the notebook to a lightweight API or UI for real-time demos.

## License
This project is provided for educational purposes as part of the Nexora AI Internship assignment.

