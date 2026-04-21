# bpi-skills

Plugin Claude Code pour la démarche produit design sprint BPI. Encode les patterns de la bibliothèque de prompts 2026 sous forme de skills directement invocables dans Claude Code.

## Installation

Dans Claude Code, ouvre le gestionnaire de plugins (`/plugin`) et entre la source suivante :

```
thiga-co/bpi-skills
```

### Prérequis

- Claude Code avec accès au MCP Figma (pour la skill `figjam-conception`)
- Un fichier `journal_de_bord_IA.md` à la racine du projet (pour `journal-ia`)

---

## Les 7 skills

### `/bpi:ingest-doc [chemin/vers/document]`

Extraction structurée d'un document source en 5 dimensions : objectifs explicites, objectifs implicites, critères pondérés, données business, pièges éliminatoires. Chaque ligne du tableau cite sa source exacte (§X.Y ou page N).

```
/bpi:ingest-doc cahier-des-charges-BPI.pdf
```

---

### `/bpi:benchmark [sujet] [N-métriques]`

Recherche de benchmarks sectoriels en 2 phases séquentielles avec arrêt obligatoire entre les deux :

- **Phase 1** — Collecte avec fourchettes de valeurs, sources traçables, applicabilité au contexte
- **Phase 2** — Vérification URL par URL que chaque chiffre est réellement présent dans la source

La séparation des phases est intentionnelle : elle a permis d'invalider des données lors d'itérations précédentes.

```
/bpi:benchmark "délai instruction PME" 5
/bpi:benchmark "taux abandon formulaire bancaire" 3
```

---

### `/bpi:problem-framing [acteur1] [acteur2] ...`

Génération des HMW (How Might We) et Job Stories par acteur, ancrés sur les fichiers sources du projet. Chaque statement cite une donnée chiffrée. Les acteurs sans données suffisantes sont explicitement exclus — pas d'inférence.

```
/bpi:problem-framing CA entrepreneur back-office
/bpi:problem-framing tous
```

---

### `/bpi:opportunity-map [axe-à-modifier]`

Enrichissement de l'opportunity map par itérations unitaires — une seule dimension modifiée par invocation, toutes les autres préservées. Axes supportés :

| Axe | Action |
|-----|--------|
| `metriques-operationnelles` | Ajouter min/dossier, h/semaine, ETP impacté |
| `roi` | Recalculer avec TJ, équipe, durée révisés |
| `t-shirt-sizing` | Remplacer les délais chiffrés par S/M/L/XL |
| `reformulation-gains` | Reformuler de "économies" → "opportunité de réinvestissement" |
| `reordonnancement` | Réordonner par ROI décroissant |
| `supprimer [opp]` | Retirer une opportunité avec vérification des dépendances |

```
/bpi:opportunity-map roi
/bpi:opportunity-map "supprimer InstructIA"
```

---

### `/bpi:figjam-conception [nom-opportunité]`

Conception FigJam complète en 3 livrables séquentiels avec validation humaine entre chaque :

1. **User Flow** — Post-its colorés (ENTRY/HP/ERR/ALT/EXIT) avec connecteurs annotés. ERR et ALT sont obligatoires.
2. **Zoning** — Frames annotées avec zones nommées et types de contenu
3. **Priority Guide** — Contenu réel hiérarchisé, badges contextuels, CTAs nommés, principes transversaux annotés

Requiert le MCP Figma actif dans Claude Code.

```
/bpi:figjam-conception InstructIA
/bpi:figjam-conception DossierAssist
```

---

### `/bpi:proto-build [nom-bet] [périmètre]`

Prototype HTML/CSS/JS vanilla avec le design system BPI. Le périmètre est borné explicitement avant la première ligne de code (écrans inclus, happy path only, pas d'intégration SI, interactions simulées en JS).

Contraintes : pas de framework, pas de bundler, données mockées avec noms réalistes ("Métalux SAS"), portail de navigation si multi-écrans.

```
/bpi:proto-build InstructIA happy-path-only
/bpi:proto-build DossierAssist qualification-flow
```

---

### `/bpi:journal-ia`

Mise à jour du `journal_de_bord_IA.md` avec la trace structurée de la session : livrables produits, prompts significatifs, décisions de l'équipe (validations, corrections, exclusions), tokens estimés. L'IA formalise — l'équipe décide.

```
/bpi:journal-ia
```

---

## Enchaînement type

```
ingest-doc   →   benchmark   →   problem-framing   →   opportunity-map
                                                               ↓
                                              figjam-conception → proto-build
                                                               ↓
                                                          journal-ia
```

---

## Structure du plugin

```
plugins/bpi/
├── .claude-plugin/plugin.json
└── skills/
    ├── benchmark/          SKILL.md · template.md · source-checklist.md
    ├── figjam-conception/  SKILL.md · template.md · paths-reference.md
    ├── ingest-doc/         SKILL.md · template.md
    ├── journal-ia/         SKILL.md · template.md
    ├── opportunity-map/    SKILL.md · template.md
    ├── problem-framing/    SKILL.md · template.md
    └── proto-build/        SKILL.md
```

---

## Licence

MIT — [Thiga](https://thiga.co)
