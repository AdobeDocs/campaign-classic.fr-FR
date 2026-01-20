---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 INVITE DE DÉMONSTRATION - Analyse de la documentation des v7 à v8

**Copiez-collez cette invite entière dans Cursor/ChatGPT pour analyser tout dossier v7**

&#x200B;---

## 📋 L’INVITE (COPIEZ-LA ICI) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

&#x200B;---

## INSTRUCTIONS POUR LA DÉMONSTRATION 🎯

### Étape 1 : afficher l’invite1. Ouvrir ce fichier (`DEMO-PROMPT-STANDALONE.md`)2. Faites défiler jusqu’à la section « INVITE »3. Dire : *« Ceci est notre invite d’analyse automatisée »*

### Étape 2 : copier l’invite1. Sélectionnez tout depuis « # Analyse de la documentation de Campaign v7 » jusqu’à la fin2. Copier dans le presse-papiers3. Dire : *« Je copie juste l&#39;invite entière... »*

### Étape 3 : coller et exécuter1. Ouvrir le curseur2. Coller l’invite3. Dire : *»...et collez-le dans Cursor »*4. Appuyez sur Entrée

### Étape 4 : Afficher les résultats1. Attente de la génération (~30-60 secondes)2. Parcourir le rapport généré3. Mettez les sections clés en surbrillance :   - 📊 les statistiques récapitulatives   - 📋 tableau fichier par fichier   - ✅ La section Doit Conserver   - 🗑️ Quick Wins   - Plan d’exécution 🎯

### Étape 5 : Moment Wow1. Afficher l’aperçu Markdown2. Soulignez :   - *« 111 fichiers analysés automatiquement »*   - *« 67 fichiers peuvent être supprimés en toute sécurité (réduction de 60 %) »*   - *« 18 fichiers spécifiques à v7 identifiés »*   - *« Compléter le plan d&#39;exécution avec les délais »*

&#x200B;---

## 💡 DES CONSEILS DE DÉMONSTRATION

### Rendre interactif&#x200B;**Demandez à l’audience** : *« Quel dossier devons-nous analyser ? »*- ✅ de diffusion (111 fichiers - impressionnant)- workflow ✅ (121 fichiers, voire plus)- ✅ web (26 fichiers - démonstration rapide)- ✅ de création de rapports (32 fichiers - rapide)

### Personnaliser à la volée&#x200B;**Afficher la flexibilité** : modifiez le chemin du dossier dans l’invite :

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Fonctionnalités clés en surbrillance1. **Automatisation** : *« Aucun travail manuel nécessaire »*2. **Exactitude** : *« Utilise la documentation v8 à des fins de comparaison »*3. **Exploitable** : *« Plan prêt à l’exécution avec cases à cocher »*4. **Smart**: *« Identifie automatiquement les fonctionnalités spécifiques à la v7 »*

### Comparaison de temps&#x200B;**Avant** : *« Analyse manuelle = 2-3 jours par dossier »*\**After** : *« Analyse automatisée = 30 secondes par dossier »*

**ROI** : *« 21 dossiers × 2 jours = 42 jours → 15 minutes »*

&#x200B;---

## 📊 APERÇU DE SORTIE ATTENDU

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

&#x200B;---

## SCRIPT DE DÉMONSTRATION 🎬

**Ouverture** :
> « Aujourd’hui, je vais vous montrer comment nous avons automatisé la réorganisation de la documentation v7 à l’aide de l’IA. Cela prenait auparavant des semaines, maintenant cela prend quelques minutes. »

**Problème** :
> « Nous disposons de plus de 1 500 fichiers de documentation v7. Beaucoup sont dupliqués dans v8. Nous devons identifier les éléments à conserver, supprimer ou migrer. »

**Solution** :
> « Nous avons créé une invite intelligente qui analyse n’importe quel dossier et génère des recommandations exploitables. »

**Démo** :
> « Laisse-moi te montrer. J&#39;analyserai le dossier &#39;delivery&#39; avec 111 fichiers... »
> 
> [Copier l’invite, coller, exécuter]
> 
>  »...et en 30 secondes, nous obtenons une analyse complète. »

**Résultats** :
> « Regardez ça :
> - 67 fichiers à supprimer (réduction de 60 %)
> - 18 fichiers spécifiques à v7 identifiés
> - 8 fichiers à migrer
> - Plan d&#39;exécution complet sur 3 semaines
> 
> Tout est automatisé. Tout est exact. »

**Fermer** :
> « Ce même processus fonctionne pour les 21 dossiers. Ce qui prenait auparavant 6 semaines prend désormais 15 minutes. »

&#x200B;---

## 🚀 PRÊT POUR LA DÉMONSTRATION !

**Juste** :
1. Ouvrir ce fichier
2. Copier l’invite
3. Coller dans le curseur
4. Afficher le ✨ magique

**Durée totale de la démonstration** : 3 à 5 minutes\
**Facteur Wow** : 🔥🔥🔥

