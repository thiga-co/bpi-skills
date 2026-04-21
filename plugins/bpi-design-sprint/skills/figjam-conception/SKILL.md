---
name: figjam-conception
description: Conception FigJam complète pour une opportunité — User Flow (HP+ERR+ALT+ENTRY+EXIT) + Zoning + Priority Guide, avec validation humaine entre chaque livrable.
when_to_use: À utiliser après validation de l'opportunité et avant tout travail frontend. Phrases déclencheuses : "crée le user flow dans FigJam", "génère la conception FigJam pour [bet]", "démarre la phase FigJam", "user flow zoning priority guide pour [opportunité]".
argument-hint: [nom-opportunité-ou-bet] — ex: "InstructIA" | "DossierAssist" | "DashboardParcours"
disable-model-invocation: true
allowed-tools: mcp__claude_ai_Figma__get_figjam mcp__claude_ai_Figma__use_figma mcp__claude_ai_Figma__generate_diagram mcp__claude_ai_Figma__create_new_file mcp__claude_ai_Figma__get_metadata mcp__claude_ai_Figma__get_screenshot Write Edit
---

# Conception FigJam — $ARGUMENTS

Génère la conception complète Phase 1 pour l'opportunité **$ARGUMENTS** dans FigJam.

La conception se déroule en 3 livrables séquentiels avec validation humaine entre chaque.

Consulter [paths-reference.md](paths-reference.md) pour les définitions et conventions de chaque type de path.

---

## Livrable 1 — User Flow

**Attendre la validation humaine avant de passer au Livrable 2.**

Crée le User Flow avec les post-its colorés (`figma.createSticky()` ou `figma_execute` fallback) :

| Type | Couleur | Contenu |
|------|---------|---------|
| ENTRY | Vert | Point(s) d'entrée dans le parcours |
| HP (Happy Path) | Bleu | Étapes nominales du parcours principal |
| ERR (Error) | Rouge | États d'erreur, validations échouées, timeouts |
| ALT (Alternative) | Jaune | Chemins alternatifs valides (ex: reprise de dossier) |
| EXIT | Gris | Points de sortie (succès, abandon, redirection) |

Connecteurs avec magnets explicites entre chaque nœud. Annoter chaque connecteur avec la condition de transition.

**Exhaustivité obligatoire** : un User Flow sans paths ERR et ALT est incomplet. La complétude est intégrée dans la demande, pas vérifiée après.

---

## Livrable 2 — Zoning

*(Démarre après validation du User Flow)*

Pour chaque écran clé identifié dans le User Flow :
- Frame annotée avec zones nommées (header, nav, contenu principal, actions, feedback)
- Indication du type de contenu dans chaque zone (pas le contenu lui-même)
- Annotations sur les interactions et transitions inter-écrans

---

## Livrable 3 — Priority Guide

*(Démarre après validation du Zoning)*

Pour chaque frame du Zoning :
- Contenu réel hiérarchisé (pas de lorem ipsum)
- Badges contextuels si nécessaire (ex: DSP2, SIREN, IA)
- CTAs nommés avec leur libellé exact
- Principes transversaux annotés (ex: P1 — Réversibilité, P2 — Transparence IA)

---

## Connexion FigJam

Les outils `figjam_*` natifs peuvent ne pas détecter le type FigJam. Utiliser `figma_execute` comme fallback si nécessaire (cf. CLAUDE.md projet).

## Fichier de suivi

Créer ou mettre à jour le fichier de suivi opérationnel en utilisant [template.md](template.md).
