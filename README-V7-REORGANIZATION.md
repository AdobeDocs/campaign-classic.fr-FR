---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# Kit de réorganisation de la documentation 📚 v7

invites **2 pour analyzer et réorganiser la doc v7 → v8**

&#x200B;---

## 📁 DES FICHIERS

### 🔍 des invites (instructions)

| Fichier | Description | Sortie |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les dossiers v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analyse détaillée d&#39;un dossier avec % correspondance | `[folder]-detailed-analysis.md` |

&#x200B;---

## Utilisation de 🚀

### 1️⃣ Vue d&#39;Ensemble (tous les dossiers)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère** :
- 📊 Synthèse (statistiques globales)
- 📁 Analyser des 21 dossiers
- 🎯 Matrice de priorisation
- ✅ des éléments d&#39;action
- ⚠️ Risques
- 📈 Métriques

**Taille** : Markdown de 50 à 60 pages

&#x200B;---

### 2️⃣ Analyse de la détection d&#39;un dossier

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère** :
- 📊 du dossier
- 📋 Tableau détaillé organisé comme Experience League
- 🔗 Liens cliquables (v7 + Experience League)
- 📈 Jusqu&#39;à 3 correspondances v8 par fichier avec %
- 📄 Récapitulatif du fichier par fichier
- Plan 🎯 réorganisation
- ✅ des cases à cocher pour le suivi

**Taille** : Markdown de 30 à 40 pages

&#x200B;---

## 📊 Exemple d&#39;Output

### Invite 1 (Présentation)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Invite 2 (Dossier Détaillé)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

&#x200B;---

## Workflow 🎯 recommandé

### Semaine 1 : Vue d&#39;ensemble1. Exécuter **Invite 1** → Obtenir `v7-reorganization-overview.md`2. Identifier les dossiers prioritaires3. Partager avec les parties prenantes

### Semaine 2-4 : Analyse détaillée1. Pour chaque dossier prioritaire :   - Exécuter **Invite 2**   - Obtenir `[folder]-detailed-analysis.md`   - Valider les décisions   - Commencer les actions

### Semaine 5+ : Exécution1. Supprimer les fichiers identifiés (DELETE)2. Badger les fichiers v7 uniquement (KEEP)3. Migration du contenu manquant (MOVE)4. Reviewer les cas ambigus (REVIEW)

&#x200B;---

## Conseils 💡

### Pour les invites- ✅ Copier/coller l&#39;intégralité du message- ✅ Ne pas modifier le format- ✅ Adapter seulement le chemin du dossier (Invite 2)

### Pour les sorties- 📝 Output en Markdown (pas HTML)- 🔗 les liens cliquables automatiques- ✅ des cases à cocher pour le suivi- 📊 statistiques et pourcentages- 🎨 Emojis et icônes

### Pour l&#39;analyse- 🎯 Commencer par les gros dossiers (diffusion, workflow)- ⚡ Prioriser les quick wins (95-100% match)- 🔍 Reviewer manuellement les cas ambigus (&lt;70% de correspondance)- ✅ Valider avec SME avant suppression massive

&#x200B;---

## ⚠️ important

### Avant de supprimer1. ✅ Vérifier l&#39;équivalent v82. ✅ Vérifier qu&#39;il n&#39;y a pas de contenu spécifique à v73. ✅ Mettre à jour `redirects.csv`4. ✅ Valider avec un expert (pour les premiers ministres)

### Pour les fichiers v7 uniquement1. ✅ Ajouter un badge au début du fichier2. ✅ Expliquer pourquoi c&#39;est v7-only3. ✅ Lien vers les limitations v8

&#x200B;---

## Assistance 🆘

**Questions** ?
- L’invite ne fonctionne pas → Vérifier les chemins des référentiels
- Sortie trop longue → Demander un résumé
- Besoin d&#39;aide → Ping l&#39;équipe doc

&#x200B;---

**Dernière mise à jour** : 2026-01-13

