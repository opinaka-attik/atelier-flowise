# 02 — Concepts clés Flowise

## Architecture LangChain

Flowise est une interface visuelle pour **LangChain**. Chaque nœud = un composant LangChain. Les connexions représentent le passage de données entre composants.

```
Document Loader → Text Splitter → Embeddings → Vector Store
                                                     ↓
User Question → [Retriever] → LLM → Réponse
```

---

## 🧠 Les Chains

| Chain | Usage |
|-------|-------|
| `ConversationChain` | Chatbot simple avec mémoire |
| `LLMChain` | Prompt template → LLM |
| `RetrievalQAChain` | Q&A sur documents (sans mémoire) |
| `ConversationalRetrievalQAChain` | RAG + mémoire conversation |

---

## 📚 Le RAG (Retrieval-Augmented Generation)

Pipeline en 2 phases :

**Phase 1 — Indexation** (au chargement du flow) :
```
Document → Splitter → Embeddings → Vector Store
```

**Phase 2 — Recherche** (lors de chaque question) :
```
Question → Embeddings → Recherche similarité → Contexte → LLM → Réponse
```

---

## 💾 La Mémoire

| Type | Description | Usage |
|------|-------------|-------|
| `BufferMemory` | Garde tout l'historique | Conversations courtes |
| `BufferWindowMemory` | Garde les K derniers tours | Conversations longues |
| `SummaryMemory` | Résume l'historique | Très longues sessions |

---

## 🔐 Les Embeddings

Transforment le texte en vecteurs numériques pour la recherche sémantique :

| Embeddings | Avantages | Inconvénients |
|------------|-----------|---------------|
| `FakeEmbeddings` | Aucune API, test rapide | Qualité nulle (démo seulement) |
| `OpenAI Embeddings` | Très bonne qualité | Payant |
| `HuggingFace` | Gratuit, local | Plus lent |
| `OllamaEmbeddings` | 100% local | Besoin Ollama installé |

---

## 🔄 Flowise vs Dify — Comparatif

| | Flowise | Dify |
|--|---------|------|
| Stack | 1 container Node.js | Multi-containers |
| RAM | ~500 Mo | ~2 Go |
| Framework | LangChain | Propriétaire + LangChain |
| Canvas | Libre (drag & drop) | Structuré (workflow) |
| RAG | Simple à configurer | Plus complet (Knowledge) |
| Agents | ReAct via LangChain | ReAct natif + function_call |
| API REST | Prédiction par chatflow | Complète (multi-apps) |
| Multimodal | Limité | Oui (images, fichiers) |
| Idéal pour | Prototypage rapide RAG/chatbot | Apps AI complètes |
