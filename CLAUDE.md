# 🃏 Poker Coaching Dashboard — Instructions Agent Claude Code

## Contexte du projet
Ce dossier contient un dashboard HTML interactif de synthèse de coachings poker.
Chaque fois qu'une nouvelle transcription de coaching est fournie, l'agent doit
mettre à jour le dashboard et générer les cartes Anki associées.

---

## Structure du dossier

```
Coaching Poker/
├── CLAUDE.md                          ← ce fichier (instructions agent)
├── README.md                          ← index de navigation (versions, liens)
├── USAGE.md                           ← mode d'emploi pour l'utilisateur final
├── CHANGELOG.md                       ← historique des versions (à tenir à jour, voir étape 6)
├── poker-dashboard-LATEST.html        ← version toujours à jour
├── poker-dashboard-YYYY-MM-DD.html    ← versions horodatées (historique)
├── anki/
│   └── anki-vN-YYYY-MM-DD.txt        ← fichiers Anki horodatés
└── transcriptions/
    └── nom-du-coaching.txt            ← transcriptions brutes
```

---

## Workflow à suivre pour chaque nouveau coaching

### 1. Lire le fichier existant
Toujours commencer par lire `poker-dashboard-LATEST.html` pour connaître :
- Les sessions déjà présentes (IDs dans la sidebar)
- Le nombre de flashcards existantes dans `quizData`
- Le numéro de la prochaine session (01, 02, 03...)
- Le style et la structure déjà en place

### 2. Analyser la transcription
Extraire depuis la transcription fournie :
- **Titre** et **coach**
- **3 à 6 Key Concepts** (idées fondamentales)
- **Situations & Lines analysées** (spots, positions, stacks, erreurs communes)
- **Takeaways actionnables** (liste concrète, format checklist)
- **Citations clés** (verbatims marquants du coach, 1-3 max)
- **Données chiffrées** (fréquences, sizings, EV) pour les stats du header

### 3. Mettre à jour le dashboard HTML
Modifier `poker-dashboard-LATEST.html` pour :

**a) Ajouter l'entrée dans `sessionsIndex` (sidebar dynamique, ne pas écrire le HTML de la sidebar à la main) :**
Depuis la refonte du bandeau (recherche + groupes pliables par Thématique/Coach/Provenance), la sidebar se génère automatiquement à partir du tableau `sessionsIndex` défini dans le `<script>` (juste avant `quizData`). Ajouter une entrée à la fin du tableau :
```javascript
{ id: "session-NOM-ID", icon: "0N", navClass: "categorie", title: "Titre Court", meta: "Catégorie • Niveau", theme: "categorie", themeLabel: "Libellé Thématique", coach: "Nom du Coach" /* ou null si non précisé */, source: "Coaching Vidéo" /* ou "Coaching 1-to-1", "Review + Solver", etc. */, minutes: 35 },
```
- `navClass` doit correspondre à une classe CSS existante (`.nav-item.<navClass> .nav-item-icon`) pour la couleur de l'icône ; créer une nouvelle classe + variable `--accent-*` si c'est une thématique inédite (voir section couleurs).
- `theme`/`themeLabel` = regroupement par thématique (aligné sur les catégories du quiz : pko, sqz, icm, math, hu, xr, mw...).
- `coach` = nom du coach (ou `null` → regroupé sous « Non précisé »).
- `source` = provenance du coaching (Coaching Vidéo / Coaching 1-to-1 / Review + Solver / autre — libre, les groupes se créent automatiquement à partir des valeurs utilisées).
- `minutes` alimente directement le total « ⏱️ ~N min de contenu » de la sidebar (estimer ~35-45 min par coaching, moins si la session est partielle/en cours).

Les compteurs de la sidebar (nombre de sessions, minutes, takeaways, flashcards) et le nombre de cartes du Quiz Mode se recalculent automatiquement depuis `sessionsIndex` et `quizData` (`refreshNavStats()`) — **ne pas les coder en dur**, ne pas modifier `renderSidebarSessions`, `groupSessions`, `toggleNavGroup`, `setNavGrouping`, `handleNavSearch`/`clearNavSearch`, `syncActiveNavItem` ou `refreshNavStats` (logique de nav déjà en place, ne toucher que le tableau `sessionsIndex`).

**c) Ajouter la nouvelle session dans le `<main>` :**
Structure complète :
- `session-header` avec badge, titre, sous-titre, meta
- `stats-grid` (3 stats chiffrées clés du coaching)
- `content-section` Key Concepts (cards)
- `content-section` Situations & Lines (situation-cards)
- `content-section` Ranges & Constructions (si pertinent)
- `content-section` Takeaways (checklist avec checkboxes)
- `content-section` Citations Clés (quote-cards)

**d) Mettre à jour le `quizData` array :**
Ajouter les nouvelles cartes avec ce format :
```javascript
{ q: "Question ?", a: "Réponse.", tag: "TAG", session: "Session 0N", category: "CATEGORIE" },
// Pour les takeaways :
{ q: "[TAKEAWAY] Action à faire ?", a: "Explication.", tag: "TAKEAWAY", session: "Session 0N", category: "CATEGORIE", isTakeaway: true },
```

**e) Mettre à jour les filtres du Quiz Mode :**
Ajouter le nouveau filtre avec le bon nombre de cartes.

### 4. Générer le fichier Anki
Créer `anki/anki-vN-YYYY-MM-DD.txt` avec TOUTES les cartes (sessions précédentes + nouvelles).
Format :
```
Question\tRéponse\tTags
```
Inclure les cartes de toutes les sessions précédentes + nouvelles.
Les takeaways doivent être inclus avec tag `takeaway`.

### 5. Sauvegarder les fichiers

```bash
# Copier avec horodatage AVANT de modifier LATEST
cp poker-dashboard-LATEST.html poker-dashboard-$(date +%Y-%m-%d).html

# Le fichier LATEST est ensuite mis à jour
# Le fichier horodaté garde l'historique
```

### 6. Mettre à jour l'historique et pousser sur GitHub

**Règle obligatoire** : à chaque mise à jour de `poker-dashboard-LATEST.html`, ajouter une entrée dans [CHANGELOG.md](CHANGELOG.md) (nouvelle section datée, avec ce qui a été ajouté/modifié — sessions, flashcards, fonctionnalités). Mettre aussi à jour le tableau des versions dans [README.md](README.md) si une nouvelle version horodatée a été créée.

Puis committer et pousser :
```bash
git add -A
git commit -m "Description courte de la mise à jour"
git push
```

---

## Classes CSS importantes (ne pas modifier)

| Classe | Usage |
|--------|-------|
| `session-content` | Container de chaque session |
| `session-content active` | Session visible |
| `nav-item pko` | Onglet PKO (vert) |
| `nav-item postflop` | Onglet Postflop (cyan) |
| `nav-item icm` / `math` / `hu` / `xr` / `mw` | Onglets par thématique (teal / violet / bleu / rouge / or) |
| `nav-group` / `nav-group-header` / `nav-group-items` | Groupe pliable de la sidebar (généré par JS, voir `sessionsIndex`) |
| `nav-search-input` | Champ de recherche de la sidebar |
| `concept-tag` | Badge catégorie sur les cards |
| `situation-block errors` | Bloc erreurs communes (rouge) |
| `checklist-box` | Checkbox takeaway |
| `srs-btn` | Boutons du système SRS |

---

## Design system — Thèmes (Clair / Sombre / Soft)

Depuis la refonte « Editorial Clean », le dashboard a 3 thèmes commutables (bouton en haut de la sidebar, sous le logo) : **Clair** (défaut), **Sombre**, **Soft**. Un attribut `data-theme="dark"` ou `data-theme="soft"` sur `<html>` fait basculer tous les tokens CSS ci-dessous (posé par `setDashboardTheme()`, persisté en localStorage, appliqué avant le premier rendu par un petit script inline en tête de `<head>` pour éviter un flash).

**Règle d'or : tout le CSS consomme des variables, jamais de couleur en dur.** Si tu ajoutes une nouvelle règle CSS avec une couleur, utilise une variable existante (ou crée-en une nouvelle déclinée dans les 3 blocs de thème) — ne jamais écrire un hex ou un rgb littéral directement dans un sélecteur de contenu (badges, tags, icônes, cartes...).

Tokens neutres (fond/texte/bordure) — définis dans `:root` (Clair), `[data-theme="dark"]`, `[data-theme="soft"]` :
`--bg-primary`, `--bg-secondary`, `--bg-card`, `--bg-card-hover`, `--text-primary`, `--text-secondary`, `--text-muted`, `--border-color`, `--border-glow`.

Polices : `--font-heading` (Source Serif 4, titres), `--font-body` (Public Sans, texte courant), `--font-label` (Public Sans, tags/meta/labels — remplace l'ancien JetBrains Mono).

Couleurs d'accent par catégorie — identité **stable entre les 3 thèmes** (seule la teinte exacte varie légèrement pour rester lisible sur chaque fond) :

```css
--accent-green   /* PKO, Takeaways, valeurs positives */
--accent-cyan    /* Postflop, SQZ, valeurs neutres */
--accent-purple  /* Concepts, Maths */
--accent-blue    /* Situations, Heads-Up */
--accent-orange  /* Citations, Quiz / Mode Révision */
--accent-red     /* Erreurs, Ranges, Check-Raise, valeurs négatives */
--accent-gold    /* Coaching Technique (Multiway) + couleur d'état actif de l'UI (onglets, sidebar) */
--accent-teal    /* ICM Préflop */
```

**Chaque accent a aussi une variante `-rgb`** (ex. `--accent-gold-rgb: 176, 141, 63;`, un triplet sans `rgba()`) pour les fonds teintés : toujours écrire `background: rgba(var(--accent-X-rgb), 0.15)` plutôt qu'un `rgba(R, G, B, 0.15)` en dur — sinon le fond ne suivra pas le changement de thème alors que le texte oui (bug déjà rencontré et corrigé une fois, ne pas le réintroduire).

Voir les valeurs exactes dans le bloc `:root` / `[data-theme="dark"]` / `[data-theme="soft"]` en tête du `<style>`.

---

## Règles de style et vocabulaire

- **Conserver le vocabulaire FR/EN** tel qu'utilisé par le coach
- **Ne jamais modifier** le système SRS (fonctions `rateSRS`, `flipSRSCard`, etc.)
- **Ne jamais modifier** le mode Libre (fonctions `startQuiz`, `flipCard`, etc.)
- **Ne jamais modifier** la logique de la sidebar dynamique (`renderSidebarSessions`, `groupSessions`, `toggleNavGroup`, `setNavGrouping`, `handleNavSearch`, `clearNavSearch`, `syncActiveNavItem`, `refreshNavStats`) — ajouter uniquement des entrées à `sessionsIndex`
- **Ne jamais modifier** la logique du toggle de thème (`setDashboardTheme`, le script inline anti-flash en tête de `<head>`) — pour une nouvelle teinte, ajouter un 4e bloc `[data-theme="..."]` + un 4e bouton, sans toucher à la fonction
- **Ne jamais coder une couleur en dur** dans une nouvelle règle CSS — toujours passer par les tokens ci-dessus (voir « Design system » plus haut)
- **Prioriser clarté > exhaustivité** dans les synthèses
- Les **citations** doivent être des verbatims réels, pas des paraphrases

---

## Sessions existantes (référence)

| ID | Titre | Catégorie | Nb cartes |
|----|-------|-----------|-----------|
| session-pko-icm | PKO & ICM + Applications Postflop | pko | 17 |
| session-sqz-80bb | Pots SQZ 80bb SB vs HJ (CO fold) | sqz | 19 |
| session-exploit-icm | Exploits ICM en TF (T. Boivin) | icm | 15 |
| session-maths | Mathématiques du Poker (T. Sacquet) | math | 28 |
| session-hu-shortstack | Jeu Heads-Up — Short Stack 7,5-15 BB (Part 1) | hu | 24 |
| session-xr-flop | Check-Raise Flop en défense BB (Cédric / Pure Poker) | xr | 24 |
| session-mw-oripbb | OR/IP/BB en Multiway (Alexis Taxigalloise, Part 1 — en cours) | mw | 20 |

**Total actuel : 147 flashcards** (dont 37 takeaways)

> Note : les comptes ont évolué après une passe de revue (cartes supprimées/reformulées via REVIEW-flashcards.xlsx).
> Catégorie `math` = violet (`--accent-purple`), classe `nav-item math`, badge `session-badge purple`.
> Catégorie `hu` (Heads-Up) = bleu (`--accent-blue` / `#6b78ff`), classe `nav-item hu`, badge `session-badge blue`, section-icon `.hu`.
> Catégorie `xr` (Check-Raise flop) = rouge (`--accent-red`), classe `nav-item xr`, badge `session-badge red`, section-icon `.xr`.
> Catégorie `mw` (Multiway, coaching technique Alexis Taxigalloise) = or (`--accent-gold` / `#ffd23f`), classe `nav-item mw`, badge `session-badge gold`, section-icon `.mw`. Section sidebar dédiée « Coaching Technique — A. Taxigalloise » (nav-section séparée des autres coachs).
> Le coaching HU se fait en plusieurs parties : Part 1 = short stack 7,5-15 BB. La Part 2 (mid/deep stack) viendra compléter la même session.
> Le coaching Multiway (A. Taxigalloise) se fait aussi en plusieurs parties : Part 1 = fréquences de c-bet IP en SRP vs MW + exploits OR/BB. La suite (probes turn, sizing tells détaillés) viendra compléter la même session `session-mw-oripbb`.
> Modes de quiz : SRS, QCM (4 choix, + builder « Mes QCM » catégorie `custom`) et Mode Libre — chacun a sa liste de filtres à mettre à jour (`filterSRS`, `filterQCM`, `filterQuiz`).

## Fonctionnalités du dashboard (ne pas modifier)

Le dashboard v4 contient deux modes de révision :
- **SRS (Révision Espacée)** : système Anki-like avec 4 niveaux (À revoir / Mauvais / Bien / Parfait), intervalles calculés, progression sauvegardée en localStorage. Fonctions : `rateSRS()`, `flipSRSCard()`, `filterSRS()`, `resetSRSData()`, `switchMode()`
- **Mode Libre** : quiz classique avec score. Fonctions : `startQuiz()`, `flipCard()`, `markCorrect()`, `markIncorrect()`, `filterQuiz()`, `shuffleAndStart()`

Ne jamais toucher ces fonctions JS. Ajouter uniquement des entrées dans le `quizData` array.

---

## Commandes utiles

```bash
# Lancer Claude Code dans ce dossier
cd ~/Desktop/"Coaching Poker" && claude

# Voir l'historique des versions
ls -lt *.html

# Compter les flashcards dans le fichier actuel
grep -c '{ q: ' poker-dashboard-LATEST.html
```

---

## Exemple de commande à donner à l'agent

> "Voici la transcription du nouveau coaching : [COLLER OU DONNER LE FICHIER].
> Ajoute une nouvelle session au dashboard, génère les cartes Anki,
> et sauvegarde une version horodatée."

L'agent devra alors exécuter toutes les étapes du workflow ci-dessus.
