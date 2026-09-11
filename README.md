# WebResearch-Firecrawl

Assistant de recherche web de type RAG (Retrieve-then-Generate). Reçoit une question, interroge le web via `firecrawl.search()` (qui renvoie à la fois les résultats et leur contenu scrapé en markdown, en un seul appel), puis un agent Groq rédige une synthèse sourcée : chaque affirmation cite sa source `[1]`, `[2]`..., et le modèle signale explicitement si les sources sont insuffisantes plutôt que d'inventer une réponse.

## Fonctionnement

1. `search_web()` — appelle Firecrawl, filtre les résultats invalides, renvoie une liste de sources
2. `research()` — enchaîne la recherche puis demande au LLM la synthèse finale

## Tech stack

- **Streamlit** — interface web
- **Agno** — framework d'agent IA
- **Firecrawl** — recherche web + scraping de contenu
- **Groq** (`openai/gpt-oss-120b`) — LLM de synthèse
- **Pydantic** — structure des données

## Lancer le projet

```bash
pip install -r requirements.txt
```

Créer un fichier `.env` avec :
```
GROQ_API_KEY=...
FIRECRAWL_API_KEY=...
```

```bash
streamlit run app.py
```
