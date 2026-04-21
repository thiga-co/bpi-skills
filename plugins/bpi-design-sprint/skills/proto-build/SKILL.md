---
name: proto-build
description: Génération d'un prototype HTML/CSS/JS vanilla avec le design system BPI et des données mockées nommées. Le périmètre est borné explicitement avant la première ligne de code.
when_to_use: À utiliser après validation du Priority Guide FigJam. Phrases déclencheuses : "génère le prototype", "crée le front pour", "build le prototype HTML de [bet]", "code l'interface de [opportunité]".
argument-hint: [nom-bet] [périmètre] — ex: "InstructIA happy-path-only" | "DossierAssist qualification-flow"
disable-model-invocation: true
allowed-tools: Write Edit Read Bash(open *.html)
---

# Prototype HTML — $ARGUMENTS

Génère le prototype frontend pour **$ARGUMENTS**.

## Stack obligatoire

- **HTML/CSS/JS vanilla** — pas de framework, pas de bundler
- **Design system BPI** — charger depuis `references/design-system/bpi-design-system.html` pour extraire tokens, couleurs, composants
- **Données mockées nommées** — utiliser une entreprise fictive avec un nom réaliste (ex: "Métalux SAS", "Duchamp & Fils SARL") pour toutes les données de test. Pas de "Lorem Ipsum", pas de "Entreprise X".
- **Portail de navigation** — si plusieurs écrans, créer un `index.html` avec des cards cliquables vers chaque prototype

## Périmètre à borner avant de coder

Avant d'écrire la première ligne de HTML, confirme :
1. **Scope inclus** : quels écrans du Priority Guide sont dans ce build ?
2. **Happy path only** : pas d'états d'erreur en V1 sauf si explicitement demandé
3. **Pas d'intégration SI** : tout est mocké côté client, aucun appel API réel
4. **Interactions simulées** : les transitions entre états sont simulées en JS (setTimeout, toggles), pas en backend

## Structure de fichiers

```
[nom-bet]/
├── index.html           (portail de navigation si multi-écrans)
├── [ecran-1].html
├── [ecran-2].html
├── css/
│   └── styles.css       (tokens BPI + styles spécifiques)
└── js/
    └── app.js           (interactions et mocked data)
```

## Données mockées

Définir en haut de `app.js` un objet `MOCK_DATA` avec des données réalistes :

```js
const MOCK_DATA = {
  company: { name: "Métalux SAS", siren: "824 351 097", ca: "2.3M€", sector: "Métallurgie" },
  contact: { name: "Pierre Fontaine", role: "Directeur Général" },
  // ... étendre selon le contexte du bet
};
```

## Après le build

1. Ouvre le prototype dans le navigateur (`open index.html`)
2. Teste le happy path complet
3. Vérifie l'application des tokens BPI (couleurs, typographie, espacements)
4. Signale les écarts par rapport au Priority Guide validé
