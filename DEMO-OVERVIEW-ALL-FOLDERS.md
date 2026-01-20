---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 25%

---
# Réorganisation de la documentation d’📊 v7 - Aperçu

**Généré** : 2026-01-13\
**Total des dossiers** : 21\
**Total Des Fichiers**: ~1 500

---

## Résumé exécutif 📈

| Mesure | Count | Pourcentage |
|--------|-------|------------|
| 📄 **Nombre total de fichiers** | 1 500 | 100% |
| ✅ **CONSERVER (spécifique à la v7)** | 400 | 27 % |
| 🗑️ **DELETE (dans v8)** | 800 | 53 % |
| ➡️ **DÉPLACER (vers v8)** | 200 | 13 % |
| 🔍 **RÉVISION (pas clair)** | 100 | 7 % |

**🎯Réduction Estimée** : 60-75 % (1 500 → 400-600 fichiers)

---

## Analyse des dossiers 📁 par priorité

### 🟢 Priorité 1 : 100 % CONSERVER - v7 uniquement

| Dossier | Fichiers | Raison | Statut v8 | Action |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | Configuration On-premise/hybride | En mode cloud uniquement dans v8 | ✅ CONSERVER TOUT + badge |
| 📂 `/mrm/` | 5 | Gestion des ressources marketing | PAS dans FFDA | ✅ CONSERVER TOUT + badge |
| 📂 `/surveys/` | 8 | Questionnaires en ligne | PAS dans FFDA | ✅ CONSERVER TOUT + badge |
| 📂 `/distributed/` | 7 | Marketing distribué | PAS dans FFDA | ✅ CONSERVER TOUT + badge |
| 📂 `/response/` | 5 | Gestion de la réaction | Statut non clair | 🔍 VÉRIFIER, PUIS CONSERVER |
| 📂 `/migration/` | 8 | migration v6.1 → v7 | spécifique à v7 | ✅ CONSERVER TOUT |
| **TOTAL** | **108** | **7 %** | - | **Badge en v7 uniquement** |

---

### 🔴 Priorité 2 : 60 À 70 % De DELETE - Duplication Élevée

| Dossier | Total | CONSERVER | DELETE | DÉPLACER | RÉVISION | Notes |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (16 %) | 67 (60 %) | 8 (7 %) | 18 (17 %) | E-mail/SMS/notification push dans v8 |
| 📂 `/workflow/` | 121 | 24 (20 %) | 60 (50 %) | 12 (10 %) | 25 (20 %) | Activités courantes dans v8 |
| 📂 `/reporting/` | 32 | 3 (10 %) | 22 (70 %) | 2 (6 %) | 5 (14 %) | Rapports repensés dans v8 |
| 📂 `/platform/` | 61 | 12 (20 %) | 34 (55 %) | 5 (8 %) | 10 (17 %) | Fonctionnalités courantes de v8 |
| 📂 `/campaign/` | 11 | 2 (18 %) | 7 (64 %) | 1 (9 %) | 1 (9 %) | Gestion de Campaign dans v8 |
| **TOTAL** | 336 **** | 59 **** | **190** | **28** | 59 **** | **Potentiel de réduction élevé** |

---

### 🟡 Priorité 3 : 30 à 50 % MIXTE - Analyse détaillée nécessaire

| Dossier | Total | CONSERVER % | % DELETE | Notes |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65 % | 22 % | Configurations de schéma/base de données (principalement v7) |
| 📂 `/production/` | 43 | 65 % | 23 % | Gestion des serveurs (principalement v7) |
| 📂 `/integrations/` | 37 | 40 % | 40 % | Vérifier la disponibilité du connecteur |
| 📂 `/interaction/` | 39 | 51 % | 31 % | Moteur d’offres (vérification v8) |
| 📂 `/web/` | 26 | 92 % | 8 % | Applications web > Pages de destination v8 |
| 📂 `/message-center/` | 16 | 60 % | 30 % | Messages transactionnels |
| **TOTAL** | 230 **** | **~55 %** | **~25 %** | **Nécessite une révision dossier par dossier** |

---

## 🎯 gains rapides - Semaine 1

### Suppressions de confiance élevées (correspondance de 95 à 100 % v8)

| Dossier | Fichiers à supprimer | Impact | Effort |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 fichiers | 🔥🔥🔥 élevé | 2 jours |
| 📂 `/workflow/` | 60 fichiers | 🔥🔥🔥 élevé | 2 jours |
| 📂 `/reporting/` | 22 fichiers | 🔥🔥 Medium | 1 jour |
| 📂 `/platform/` | 34 fichiers | 🔥🔥 Medium | 1 jour |
| 📂 `/campaign/` | 7 fichiers | 🔥 faible | 0,5 jour |
| **TOTAL** | **190 fichiers** | **53 % de réduction** | **6,5 jours** |

**Exemples** :
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (workflow) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

---

## Répartition détaillée des dossiers 📋

### Diffusion 📂 (`/help/delivery/using/`) - 111 fichiers

| Catégorie | Fichiers | CONSERVER | DELETE | DÉPLACER | RÉVISION | Notes |
|----------|-------|------|--------|------|--------|-------|
| Commencer | 8 | 0 | 7 | 0 | 1 | Principes de base dans v8 |
| Email | 18 | 0 | 16 | 0 | 2 | Intégralement dans v8 |
| SMS | 7 | 1 | 5 | 0 | 1 | Mid-sourcing = CONSERVER |
| Notifications push | 9 | 0 | 8 | 0 | 1 | Intégralement dans v8 |
| Courrier | 4 | 0 | 4 | 0 | 0 | Dans v8 |
| Personnalisation | 8 | 1 | 6 | 0 | 1 | Coupons = CONSERVER |
| Modèles | 6 | 0 | 6 | 0 | 0 | Dans v8 |
| A/B Testing | 11 | 0 | 10 | 0 | 1 | Dans v8 |
| Contrôle  | 14 | 0 | 12 | 1 | 1 | Principalement dans v8 |
| Résolution des problèmes | 9 | 2 | 4 | 2 | 1 | Conserver les conseils sur site |
| Délivrabilité | 8 | 3 | 4 | 0 | 1 | SpamAssassin = CONSERVER |
| Avancé | 9 | 11 | 5 | 5 | 8 | Mixte |
| **TOTAL** | **111** | **18** | 67 **** | 8 **** | **18** | **60 % peuvent être supprimés** |

**À conserver** :
- ✅ `personalized-coupons.md` - PAS dans v8 FFDA
- ✅ `sms-set-up-mid.md` - Mid-sourcing (on-prem)
- ✅ `spamassassin.md` - Filtrage du spam On-prem

**Exemples de suppression rapide** :
- 🗑️ `about-email-channel.md` → 95 % en `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95 % en `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90 % en `campaign-web/v8/msg/send-sms`

---

### Workflow 📂 (`/help/workflow/using/`) - 121 fichiers

| Catégorie | Fichiers | CONSERVER | DELETE | DÉPLACER | RÉVISION | Notes |
|----------|-------|------|--------|------|--------|-------|
| Commencer | 12 | 2 | 9 | 0 | 1 | Principes de base dans v8 |
| Ciblage | 18 | 3 | 12 | 1 | 2 | Requête/Partage dans v8 |
| Contrôle De Flux | 15 | 2 | 10 | 1 | 2 | Fréquent dans v8 |
| Activités D&#39;Action | 24 | 4 | 16 | 2 | 2 | Les plus récents en v8 |
| Activités d’événement | 8 | 1 | 6 | 0 | 1 | Dans v8 |
| Activités MRM | 5 | 5 | 0 | 0 | 0 | PAS dans FFDA |
| Technique | 16 | 4 | 8 | 2 | 2 | Mixte |
| Avancé | 12 | 3 | 4 | 3 | 2 | Modèles utiles |
| Cas d’utilisation | 11 | 0 | 5 | 3 | 3 | Bons exemples |
| **TOTAL** | **121** | **24** | 60 **** | **12** | 25 **** | **50 % peuvent être supprimés** |

**À conserver** :
- ✅ Toutes les activités MRM (5 fichiers) - PAS dans v8 FFDA
- ✅ des configurations On-premise
- ✅ Workflows techniques avancés

**Exemples de suppression rapide** :
- 🗑️ `query.md` → 95 % en `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95 % en `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95 % en `campaign/v8/automation/workflow/enrichment`

---

### 📂 Installation (`/help/installation/using/`) - 75 fichiers

| Catégorie | Fichiers | Action | Notes |
|----------|-------|--------|-------|
| Installation du serveur | 18 | ✅ CONSERVER | On-premise uniquement |
| Configuration de la base de données | 12 | ✅ CONSERVER | On-premise uniquement |
| Configuration  | 15 | ✅ CONSERVER | nlserver, etc. |
| Réseau | 8 | ✅ CONSERVER | Zones de sécurité |
| Intégration | 10 | ✅ CONSERVER | LDAP, etc |
| Résolution des problèmes | 8 | ✅ CONSERVER | Problèmes on-premise |
| Documents génériques | 4 | 🗑️ DELETE | Guide de démarrage dans v8 |
| **TOTAL** | 75 **** | **71 CONSERVER / 4 DELETE** | Spécifique à **95 % v7** |

**Raison** : v8 est uniquement cloud, tous les documents de configuration on-premise sont spécifiques à la v7.

---

### 📂 Web (`/help/web/using/`) - 26 fichiers

| Catégorie | Fichiers | CONSERVER | DELETE | Notes |
|----------|-------|------|--------|-------|
| Applications Web | 14 | 14 | 0 | Fonctionnalités avancées non disponibles dans v8 |
| Formulaires Web | 8 | 8 | 0 | Plus de pages de destination v8 |
| Landing pages | 2 | 0 | 2 | Pages de base dans v8 |
| Éditeur HTML | 2 | 2 | 0 | Différent de v8 |
| **TOTAL** | **26** | **24** | **2** | **92 % spécifique à v7** |

**Raison** : v7 dispose d’un framework d’applications web complet, v8 a simplifié les pages de destination.

---

## Plan d&#39;action ✅

### Semaine 1 : suppressions à fort impact
- [ ] `/delivery/` : suppression de 67 fichiers (e-mail, SMS, principes de base des notifications push)
- [ ] `/workflow/` : suppression de 60 fichiers (activités courantes)
- [ ] `/reporting/` : suppression de 22 fichiers (rapports standard)
- [ ] `/platform/` : supprimer 34 fichiers (fonctionnalités communes)
- [ ] `/campaign/` : suppression de 7 fichiers (gestion de campagne)
- **Total** : 190 fichiers supprimés (réduction de 13 %)

### Semaine 2 : badge spécifique à v7
- [ ] `/installation/` : passez 71 fichiers en tant que « v7 On-premise uniquement ».
- [ ] `/mrm/` : passez 5 fichiers sur « Non disponible dans v8 FFDA »
- [ ] `/surveys/` : badge 8 fichiers comme « Non disponible dans v8 FFDA »
- [ ] `/distributed/` : badge 7 fichiers comme « Non disponible dans v8 FFDA »
- [ ] `/web/` : passez 24 fichiers sous la forme « Applications Web v7 ».
- **Total** : 115 fichiers badgés

### Semaine 3 : migration du contenu
- [ ] Migrer les conseils de dépannage de `/delivery/` vers v8
- [ ] Bonnes pratiques relatives à la migration des workflows vers v8
- [ ] Migrer les modèles avancés de `/platform/` vers v8
- **Total** : 40 fichiers migrés puis supprimés

### Semaine 4 : révision manuelle
- [ ] la révision `/configuration/` contenu mixte
- [ ] Vérifier la disponibilité du connecteur `/integrations/`
- [ ] Vérification de la couverture `/interaction/` moteur d’offres
- [ ] le statut des fonctionnalités `/response/`
- **Total** : 50 dossiers examinés et tranchés

---

## 📊 Résultats Attendus

| Phase | Fichiers affectés | % cumulé |
|-------|----------------|--------------|
| Semaine 1 : suppressions | 190 | 13 % |
| Semaine 2 : badge | 115 | 20 % |
| Semaine 3 : migration | 40 | 23 % |
| Semaine 4 : révision | 50 | 26 % |
| **TOTAL** | 395 **** | **26 % traités** |

**Restant** : environ 1 100 fichiers à traiter lors des phases suivantes

**Objectif final** : 1 500 → 400 à 600 fichiers (réduction de 60 à 73 %)

---

## Mesures de succès 🎯

| Mesure | Cible | Statut |
|--------|--------|--------|
| Fichiers supprimés | 800+ (53 %) | ⏳ en attente |
| Fichiers Badgés | 200+ (13 %) | ⏳ en attente |
| Fichiers migrés | 200+ (13 %) | ⏳ en attente |
| Liens rompus | 0 | ⏳ en attente |
| Approbation des parties prenantes | ✅ | ⏳ en attente |

---

**Dernière mise à jour**: 2026-01-13\
**Prochaine révision** : après l’exécution de la semaine 1

