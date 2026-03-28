# 01 — Interface Flowise

## Vue d'ensemble

Flowise est une interface **drag & drop** basée sur LangChain. Chaque nœud du canvas représente un composant LangChain (LLM, Memory, VectorStore, Chain, Tool...).

---

## 🖼️ Zones de l'interface

### 1. Barre latérale gauche
| Section | Rôle |
|---------|------|
| **Chatflows** | Flows de type chatbot avec mémoire |
| **Agentflows** | Flows orientés agents multi-étapes |
| **Marketplaces** | Templates prêts à l'emploi |
| **Tools** | Outils custom (fonctions) |
| **Credentials** | Clés API centralisées |
| **Variables** | Variables globales |

### 2. Canvas (zone centrale)
- **Drag & drop** depuis le panneau de nœuds (bouton **+**)
- Connecter les sorties vers les entrées
- Clic sur un nœud pour le configurer
- Code couleur : 🟢 Chains | 🔵 Models | 🟡 Memory | 🟠 Tools | 🔴 Vector Stores

### 3. Panneau de nœuds (icône **+**)
Organisé par catégories :
- Chat Models, LLMs
- Prompts
- Memory
- Chains
- Agents
- Tools
- Document Loaders
- Text Splitters
- Vector Stores
- Embeddings

### 4. Barre du haut
- **Save** : sauvegarder le flow
- **Chat** : ouvrir l'interface de chat
- **API** : voir les endpoints REST
- **Import/Export** : importer/exporter JSON

---

## 🔵 Types de nœuds principaux

| Nœud | Catégorie | Rôle |
|------|-----------|------|
| ChatGroq | Chat Models | LLM via Groq |
| ConversationChain | Chains | Chatbot avec mémoire |
| RetrievalQAChain | Chains | Q&A sur documents (RAG) |
| ConversationalRetrievalQAChain | Chains | RAG + mémoire conversation |
| AgentExecutor | Agents | Agent ReAct avec outils |
| BufferMemory | Memory | Mémoire complète |
| BufferWindowMemory | Memory | Mémoire glissante (K tours) |
| MemoryVectorStore | Vector Stores | Stockage vectoriel en RAM |
| PDFLoader | Document Loaders | Charger un PDF |
| Calculator | Tools | Calcul mathématique |
