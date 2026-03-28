# 04 — Dépannage Flowise

## Problèmes fréquents

---

### ⚠️ Flowise ne démarre pas

```bash
# Vérifier les logs
docker compose logs flowise

# Problème de permissions volume
docker compose down -v
docker compose up -d
```

---

### ⚠️ Erreur « Credential not found »

**Cause** : Le nœud ChatGroq n'a pas de credential configurée  
→ Cliquer le nœud ChatGroq → champ **Connect Credential** → sélectionner ou créer la credential Groq

---

### ⚠️ L'API retourne `{ "error": "Chatflow not found" }`

**Cause** : Mauvais CHATFLOW_ID  
→ L'ID est visible dans l'URL quand le flow est ouvert :  
`http://localhost:3001/chatflows/CHATFLOW_ID`

---

### ⚠️ Le RAG ne retrouve pas les bons documents

**Cause** : FakeEmbeddings utilisé (pas de vraie similarité sémantique)  
→ Remplacer par des vrais embeddings :
- **OpenAI Embeddings** : meilleure qualité, payant
- **HuggingFace Inference** : gratuit, qualité correcte
- **Ollama Embeddings** : 100% local, nécessite Ollama

---

### ⚠️ Groq retourne une erreur 429 (rate limit)

**Cause** : Trop de requêtes sur le plan gratuit  
→ Attendre 1 minute  
→ Utiliser `llama3-8b-8192` (moins de tokens) au lieu de `llama3-70b-8192`  
→ Ou changer de modèle : `gemma2-9b-it` est très rapide

---

### ⚠️ La mémoire ne fonctionne pas entre sessions

**Cause** : `sessionId` non passé dans la requête API  
→ Toujours inclure un `sessionId` stable dans les appels API :
```bash
curl -X POST http://localhost:3001/api/v1/prediction/CHATFLOW_ID \
  -H "Content-Type: application/json" \
  -d '{"question": "...", "sessionId": "user-123"}'
```

---

### 🔍 Déboguer un flow

1. Cliquer le nœud suspect
2. Cliquer **Test Node** (icône ▶️ dans le nœud)
3. Voir le résultat exact produit par ce nœud isolément

C'est la méthode la plus efficace pour isoler un problème dans la chaîne.
