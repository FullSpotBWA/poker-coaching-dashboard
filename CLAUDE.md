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

**a) Ajouter l'onglet dans la sidebar :**
```html
<div class="nav-item pko" onclick="showSession('session-NOM-ID')">
    <div class="nav-item-icon">0N</div>
    <div class="nav-item-content">
        <div class="nav-item-title">Titre Court</div>
        <div class="nav-item-meta">Catégorie • Niveau</div>
    </div>
</div>
```

**b) Mettre à jour les statistiques sidebar :**
- Nombre de sessions
- Minutes de contenu (estimer ~35-45 min par coaching)
- Nombre de takeaways (additionner)
- Nombre de flashcards (additionner)

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

---

## Classes CSS importantes (ne pas modifier)

| Classe | Usage |
|--------|-------|
| `session-content` | Container de chaque session |
| `session-content active` | Session visible |
| `nav-item pko` | Onglet PKO (vert) |
| `nav-item postflop` | Onglet Postflop (cyan) |
| `concept-tag` | Badge catégorie sur les cards |
| `situation-block errors` | Bloc erreurs communes (rouge) |
| `checklist-box` | Checkbox takeaway |
| `srs-btn` | Boutons du système SRS |

---

## Couleurs CSS disponibles

```css
--accent-green: #00ff87    /* PKO, ICM */
--accent-cyan: #00d4ff     /* Postflop, SQZ */
--accent-purple: #a855f7   /* Concepts */
--accent-blue: #3742fa     /* Situations */
--accent-orange: #ffa502   /* Citations, Quiz */
--accent-red: #ff4757      /* Erreurs, Ranges */
```

---

## Règles de style et vocabulaire

- **Conserver le vocabulaire FR/EN** tel qu'utilisé par le coach
- **Ne jamais modifier** le système SRS (fonctions `rateSRS`, `flipSRSCard`, etc.)
- **Ne jamais modifier** le mode Libre (fonctions `startQuiz`, `flipCard`, etc.)
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

**Total actuel : 79 flashcards** (dont 21 takeaways)

> Note : les comptes ont évolué après une passe de revue (cartes supprimées/reformulées via REVIEW-flashcards.xlsx).
> Catégorie `math` = couleur violette (`--accent-purple`), classe sidebar `nav-item math`, badge `session-badge purple`.
> Modes de quiz : SRS, QCM (4 choix) et Mode Libre — chacun a sa liste de filtres à mettre à jour (`filterSRS`, `filterQCM`, `filterQuiz`).

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
