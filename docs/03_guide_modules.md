# 03 — Guide des modules

## Module 01 — Chatbot Simple
**Fichier** : `flows/01_chatbot_simple.json`  
**Niveau** : Débutant | **Durée** : 10 min

### Objectif
Chatbot conversationnel avec mémoire complète de la session.

### Architecture
```
ChatGroq + BufferMemory → ConversationChain
```

### Étapes
1. Importer le flow
2. Cliquer le nœud **ChatGroq** → configurer la credential Groq
3. Cliquer **Save Chatflow**
4. Cliquer l'icône **Chat** en haut à droite
5. Tester : `"Bonjour ! Comment tu t'appelles ?"`

### Test API
```bash
curl -X POST http://localhost:3001/api/v1/prediction/CHATFLOW_ID \
  -H "Content-Type: application/json" \
  -d '{"question": "Bonjour ! Qui es-tu ?", "sessionId": "session-001"}'
```

---

## Module 02 — Prompt Template
**Fichier** : `flows/02_prompt_template.json`  
**Niveau** : Débutant | **Durée** : 15 min

### Objectif
Créer un expert configurable via variables de prompt.

### Architecture
```
ChatGroq + ChatPromptTemplate → LLMChain
```

### Test
```bash
curl -X POST http://localhost:3001/api/v1/prediction/CHATFLOW_ID \
  -H "Content-Type: application/json" \
  -d '{"question": "Quels sont les avantages de Docker ?", "overrideConfig": {"systemMessagePrompt": "Tu es un expert en {domaine}.", "domaine": "DevOps"}}'
```

---

## Module 03 — RAG Documents
**Fichier** : `flows/03_rag_documents.json`  
**Niveau** : Intermédiaire | **Durée** : 20 min

### Objectif
Q&A sur un fichier PDF uploadé directement dans Flowise.

### Architecture
```
PDFLoader + FakeEmbeddings → MemoryVectorStore → RetrievalQAChain + ChatGroq
```

### Étapes
1. Importer le flow
2. Cliquer le nœud **PDF File** → uploader un PDF
3. Cliquer **Save Chatflow**
4. Tester avec une question sur le contenu du PDF

> ⚠️ Pour la production : remplacer **Fake Embeddings** par **OpenAI Embeddings** ou **HuggingFace**

---

## Module 04 — Agent avec Outils
**Fichier** : `flows/04_agent_tools.json`  
**Niveau** : Intermédiaire | **Durée** : 25 min

### Objectif
Agent ReAct avec calculatrice et recherche web.

### Architecture
```
ChatGroq + Calculator + SearchAPI + BufferMemory → ReAct Agent
```

### Test
```bash
curl -X POST http://localhost:3001/api/v1/prediction/CHATFLOW_ID \
  -H "Content-Type: application/json" \
  -d '{"question": "Calcule 25% de 1284"}'
```

---

## Module 05 — RAG Conversationnel
**Fichier** : `flows/05_conversational_rag.json`  
**Niveau** : Avancé | **Durée** : 30 min

### Objectif
RAG avec mémoire de conversation (garde le contexte des échanges précédents).

### Architecture
```
TextLoader + FakeEmbeddings → MemoryVectorStore
ChatGroq + BufferWindowMemory(k=4) → ConversationalRetrievalQAChain
```

### Test
```bash
# Question 1
curl -X POST http://localhost:3001/api/v1/prediction/CHATFLOW_ID \
  -H "Content-Type: application/json" \
  -d '{"question": "Qu est-ce que n8n ?", "sessionId": "session-rag-001"}'

# Question 2 (utilise le contexte de la question 1)
curl -X POST http://localhost:3001/api/v1/prediction/CHATFLOW_ID \
  -H "Content-Type: application/json" \
  -d '{"question": "Et comment le comparer à Activepieces ?", "sessionId": "session-rag-001"}'
```
