---
name: journal-ia
description: Mise à jour du journal_de_bord_IA.md avec la trace structurée de la session. L'IA formalise les décisions déjà prises par l'équipe — elle ne décide pas.
when_to_use: À utiliser en fin de session IA significative. Phrases déclencheuses : "mets à jour le journal", "trace cette session", "ajoute au journal de bord IA", "récapitulatif de la session IA".
disable-model-invocation: true
allowed-tools: Read Edit
---

# Journal de bord IA — Mise à jour

Met à jour `journal_de_bord_IA.md` avec la trace de la session en cours.

## Règle fondamentale

L'IA est positionnée comme secrétaire de la décision, jamais comme décideur. Chaque entrée du journal spécifie **ce que l'équipe a validé ou décidé**, pas seulement ce que l'IA a produit. La décision est toujours antérieure à l'entrée.

## Protocole

1. **Lis d'abord** `journal_de_bord_IA.md` pour connaître la structure existante et le numéro de la dernière session
2. **Identifie** dans la conversation actuelle :
   - Les prompts significatifs utilisés (résumé en 1 ligne chacun)
   - Les livrables produits (fichiers créés ou modifiés)
   - Les décisions humaines prises (validations, corrections, exclusions volontaires)
   - Les tokens estimés (approximation raisonnée basée sur la longueur des échanges)
3. **Ajoute** une nouvelle entrée à la fin du journal

## Format d'entrée

```markdown
## Session [N+1] — [Date] — [Skill ou contexte]

**Livrable(s)** : [liste des fichiers produits ou modifiés]
**Tokens estimés** : ~[N]k

### Prompts significatifs
- [Résumé prompt 1 en 1 ligne]
- [Résumé prompt 2 en 1 ligne]

### Décisions humaines
- [Ce que l'équipe a validé, corrigé, ou explicitement écarté]
- [Exclusions volontaires documentées]

### Ajouts humains post-IA
- [Ce qui a été modifié ou complété à la main après génération]
```

## Ce qu'on ne met pas dans le journal

- Les détails techniques des prompts (le journal est une trace de démarche, pas un log de tokens)
- Les erreurs et corrections intermédiaires (sauf si elles ont changé la direction)
- Les tâches mineures sans décision associée

## Format d'entrée

Utiliser la structure définie dans [template.md](template.md).
