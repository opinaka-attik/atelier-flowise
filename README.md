# 🧠 Atelier Flowise — Chatbots, RAG & Agents

Atelier pratique pour découvrir **Flowise** à travers des flows JSON progressifs.
Flowise est une alternative légère à Dify, idéale pour créer des chatbots, pipelines RAG et agents simples.

## 🗂️ Structure

```
atelier-flowise/
├── flows/              # Fichiers JSON importables dans Flowise
│   ├── 01_chatbot_simple.json
│   ├── 02_prompt_template.json
│   ├── 03_rag_documents.json
│   ├── 04_agent_tools.json
│   └── 05_conversational_rag.json
├── docs/
│   ├── 00_installation.md
│   ├── 01_interface_flowise.md
│   ├── 02_concepts_cles.md
│   ├── 03_guide_modules.md
│   └── 04_depannage.md
├── docker/
│   └── docker-compose.yml
└── README.md
```

## 🚀 Démarrage rapide

```bash
git clone https://github.com/opinaka-attik/atelier-flowise
cd atelier-flowise/docker
docker compose up -d
# Ouvrir http://localhost:3001
```

## 📦 Importer un flow

1. Ouvrir Flowise → **Chatflows** → **Add New**
2. Cliquer l'icône **Import** (en haut à droite)
3. Sélectionner un fichier `.json` du dossier `flows/`
4. Cliquer **Save** pour sauvegarder

## 📚 Modules

| # | Fichier | Niveau | Concept |
|---|---------|--------|---------|
| 01 | `01_chatbot_simple.json` | Débutant | Chatbot simple avec mémoire |
| 02 | `02_prompt_template.json` | Débutant | Prompt système + variables |
| 03 | `03_rag_documents.json` | Intermédiaire | RAG : upload PDF → Q&A |
| 04 | `04_agent_tools.json` | Intermédiaire | Agent avec outils (calculatrice, web) |
| 05 | `05_conversational_rag.json` | Avancé | RAG conversationnel avec mémoire |

## ⚙️ Prérequis

- Docker + Docker Compose
- Compte [Groq](https://console.groq.com) (gratuit) pour les LLM

## 🔄 Flowise vs Dify

| | Flowise | Dify |
|--|---------|------|
| Installation | Ultra-rapide (1 container) | Multi-containers |
| Interface | Canvas drag & drop | Studio structuré |
| RAG | Natif, simple | Natif, avancé |
| Agents | LangChain natif | ReAct + tools |
| API | REST intégrée | REST intégrée |
| Usage | Chatbots rapides | Apps AI complètes |
