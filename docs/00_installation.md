# 00 — Installation de Flowise

## Prérequis

- Docker Desktop (Windows/Mac) ou Docker Engine (Linux)
- Docker Compose v2+
- 1 Go de RAM minimum (très léger !)
- Port disponible : `3001`

---

## 🚀 Installation rapide (Docker Compose)

```bash
# Cloner le repo
git clone https://github.com/opinaka-attik/atelier-flowise
cd atelier-flowise/docker

# Lancer Flowise
docker compose up -d

# Vérifier
docker ps
docker compose logs -f flowise
```

Ouvrir **http://localhost:3001** dans le navigateur.  
Identifiants par défaut : `admin` / `admin123`

---

## 🔑 Configurer Groq

1. Aller sur [console.groq.com](https://console.groq.com) et générer une clé API
2. Dans Flowise : **Credentials → Add Credential → Groq API**
3. Coller la clé API
4. La credential est réutilisable dans tous les nœuds ChatGroq

---

## 📦 Importer un flow

1. Ouvrir Flowise → **Chatflows**
2. Cliquer **Add New** (bouton bleu)
3. Dans l'éditeur : icône **Import** en haut à droite (nuage avec flèche)
4. Sélectionner un fichier `.json` du dossier `flows/`
5. Configurer les credentials Groq dans les nœuds ChatGroq
6. Cliquer **Save Chatflow**

---

## 🧪 Tester via l'interface

Chaque flow importé dispose d'un bouton **Chat** (icône bulle) en haut à droite — ouvre directement l'interface de chat.

---

## 🌐 Tester via API

```bash
# Récupérer l'ID du chatflow dans l'URL Flowise
# Format : http://localhost:3001/chatflows/{CHATFLOW_ID}

curl -X POST http://localhost:3001/api/v1/prediction/CHATFLOW_ID \
  -H "Content-Type: application/json" \
  -d '{"question": "Bonjour, qui es-tu ?"}'
```

---

## 🔄 Commandes utiles

```bash
# Arrêter Flowise
docker compose down

# Voir les logs
docker compose logs -f flowise

# Mettre à jour
docker compose pull && docker compose up -d

# Sauvegarder les données
docker cp flowise:/root/.flowise ./backup-flowise
```
