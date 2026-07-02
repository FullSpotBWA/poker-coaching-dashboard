# 📘 Mode d'emploi

Ce dépôt contient le dashboard de coaching poker. Ce guide explique comment l'utiliser, que tu sois familier avec Git/GitHub ou non.

## 1. Ouvrir le dashboard (sans rien installer)

C'est un simple fichier HTML : pas besoin de compte, ni d'installation, ni d'internet une fois téléchargé.

1. Va sur la page du dépôt : `https://github.com/FullSpotBWA/poker-coaching-dashboard`
2. Clique sur le bouton vert **"Code"** → **"Download ZIP"**
3. Dézippe le dossier sur ton PC
4. Double-clique sur **`poker-dashboard-LATEST.html`** → il s'ouvre dans ton navigateur

C'est tout. Mets-le en favori dans ton navigateur pour l'ouvrir rapidement la prochaine fois.

## 2. Récupérer les mises à jour

Le dashboard évolue (nouvelles sessions, nouvelles fonctionnalités). Pour récupérer la dernière version :

- **Simple, sans Git** : retélécharge le ZIP (étape 1 ci-dessus) et remplace ton ancien dossier.
- **Avec Git**, si tu as cloné le dépôt :
  ```
  git pull
  ```

⚠️ **`poker-dashboard-LATEST.html` est toujours la version à jour à utiliser.** Les fichiers datés (`poker-dashboard-2026-XX-XX.html`) sont des versions figées gardées comme historique — ne t'en sers pas pour réviser au quotidien. Le détail de ce qui a changé à chaque version est dans [CHANGELOG.md](CHANGELOG.md).

## 3. Créer et partager tes propres QCM

Le dashboard permet de créer tes propres questions à choix multiples : une question, une image collée depuis ton presse-papier (Ctrl+V), et 4 réponses que tu définis toi-même.

Ces QCM sont enregistrés **uniquement dans ton navigateur** (pas dans le fichier, pas sur GitHub) — chacun a les siens. Pour les partager avec quelqu'un d'autre :

1. Dans le dashboard → **Quiz Mode → QCM → 🧩 Créer / gérer mes QCM**
2. Clique sur **⬇️ Exporter** → un fichier `mes-qcm-poker-AAAA-MM-JJ.json` est téléchargé
3. Envoie ce fichier à la personne (mail, Drive, WhatsApp...)
4. Elle ouvre son propre dashboard → même menu → **⬆️ Importer** → sélectionne le fichier reçu

Ses propres QCM restent intacts ; les tiens s'ajoutent aux siens (ou se mettent à jour si elle réimporte une version plus récente du même fichier).

## 4. C'est quoi Git / GitHub, en deux mots ?

- **GitHub** : un espace en ligne où le projet est stocké et versionné.
- **Git** : l'outil qui permet de récupérer (`pull`) ou d'envoyer (`push`) les changements entre un PC et GitHub.

Si tu ne comptes pas modifier le dashboard toi-même, tu n'as besoin de rien de tout ça : la méthode "Download ZIP" (point 1) suffit amplement.

## 5. Pour qui veut faire évoluer le dashboard

Le dashboard est mis à jour avec l'aide de Claude Code, en suivant un workflow défini dans [CLAUDE.md](CLAUDE.md) : ajout d'un nouveau coaching, génération des flashcards, mise à jour de l'historique dans [CHANGELOG.md](CHANGELOG.md), puis `git commit` + `git push`.
