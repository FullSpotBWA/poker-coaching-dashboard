# 🃏 Poker Coaching Dashboard

Dashboard interactif de synthèse de coachings poker : sessions, flashcards en répétition espacée (SRS), QCM automatiques et QCM personnalisés.

## 🚀 Ouvrir le dashboard

👉 **[Ouvrir la dernière version](poker-dashboard-LATEST.html)** — c'est le fichier toujours à jour, celui à utiliser au quotidien.

> Sur GitHub, ce lien ouvre la vue "code source" du fichier plutôt que de l'exécuter. Pour l'ouvrir normalement dans ton navigateur : clique sur **"Raw"** (ou **"Download raw file"**) en haut à droite du fichier, enregistre-le, puis double-clique dessus. Détail complet dans [USAGE.md](USAGE.md).

## 🗂️ Versions disponibles

| Version | Date | Sessions | Flashcards | Fichier |
|---|---|---|---|---|
| **LATEST** (en cours) | à jour en continu | 4 | 79 + QCM perso | [poker-dashboard-LATEST.html](poker-dashboard-LATEST.html) |
| v3 | 2026-07-01 | 4 | 79 | [poker-dashboard-2026-07-01.html](poker-dashboard-2026-07-01.html) |
| v2 | 2026-05-08 | 3 | 66 | [poker-dashboard-2026-05-08.html](poker-dashboard-2026-05-08.html) |
| v1 | 2026-05-06 | 1 | — | [poker-dashboard-2026-05-06.html](poker-dashboard-2026-05-06.html) |

Les fichiers datés sont des versions figées conservées comme historique — utilise toujours **LATEST** pour réviser. Détail des changements de chaque version : [CHANGELOG.md](CHANGELOG.md).

## 📖 Documentation

| Fichier | Contenu |
|---|---|
| [USAGE.md](USAGE.md) | Comment ouvrir le dashboard, récupérer les mises à jour, créer/partager tes QCM perso — pour n'importe qui, même sans connaître Git |
| [CHANGELOG.md](CHANGELOG.md) | Historique détaillé de toutes les versions |
| [CLAUDE.md](CLAUDE.md) | Workflow suivi avec Claude Code pour ajouter un nouveau coaching au dashboard |

## 📁 Structure du dépôt

```
poker-coaching-dashboard/
├── README.md                          ← ce fichier (index de navigation)
├── USAGE.md                           ← mode d'emploi (ouverture, mises à jour, partage QCM)
├── CHANGELOG.md                       ← historique des versions
├── CLAUDE.md                          ← instructions du workflow agent
├── poker-dashboard-LATEST.html        ← dashboard à jour (à utiliser)
├── poker-dashboard-YYYY-MM-DD.html    ← versions figées (historique)
├── anki/                              ← exports Anki associés
└── transcriptions/                    ← transcriptions brutes des coachings
```
