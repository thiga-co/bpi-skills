---
name: ingest-doc
description: Extraction structurée d'un document source en 5 dimensions — objectifs explicites/implicites, critères pondérés, données business, pièges éliminatoires.
when_to_use: À utiliser dès qu'un document entre dans le projet, avant tout livrable aval. Phrases déclencheuses : "lis ce document", "analyse ce fichier", "extrais les sections critiques", "qu'est-ce que dit ce doc", "structure ce document".
argument-hint: [chemin/vers/document.pdf ou description-du-document]
context: fork
agent: Explore
allowed-tools: Read Glob Grep
---

# Extraction structurée de document

Analyse `$ARGUMENTS`.

## Protocole (ne pas lire linéairement)

**Étape 1 — Cartographie rapide**
Lis d'abord la table des matières ou les titres de sections. Identifie les 5–8 sections à forte valeur avant de plonger dans le détail. Note les sections déprioritisées et pourquoi.

**Étape 2 — Extraction en 5 dimensions**

Pour chaque section critique, remplis ce tableau :

| Dimension | Ce qu'on cherche |
|-----------|-----------------|
| Objectifs explicites | Ce qui est demandé textuellement |
| Objectifs implicites | Ce qui est attendu sans être dit |
| Critères pondérés | Métriques, seuils, priorités, pondérations |
| Données business | Chiffres, volumes, benchmarks mentionnés dans le doc |
| Pièges éliminatoires | Conditions rédhibitoires, exclusions, limites dures |

**Étape 3 — Sortie obligatoire**
- Tableau structuré (5 colonnes ci-dessus)
- TL;DR de 3 phrases maximum
- Liste des sections non lues + justification de la déprioritisation

## Règle absolue

Chaque ligne du tableau cite sa source exacte (§X.Y ou page N). Aucune inférence sans référence. Si une dimension ne s'applique pas à une section, écrire explicitement "N/A — [raison]".

## Format de sortie

Utiliser la structure définie dans [template.md](template.md).
