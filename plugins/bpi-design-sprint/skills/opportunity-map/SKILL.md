---
name: opportunity-map
description: Enrichissement d'une opportunity map par itérations unitaires — une seule dimension modifiée par invocation, les autres préservées. Ne jamais refaire l'ensemble.
when_to_use: À utiliser pendant la phase de priorisation, après un premier draft des opportunités. Phrases déclencheuses : "enrichis l'opportunity map", "ajoute les métriques opérationnelles", "recalcule le ROI", "reordonne par priorité", "remplace les délais par T-shirt sizing", "reformule les gains en réinvestissement", "supprime [opportunité]".
argument-hint: [axe-à-modifier] — ex: "metriques-operationnelles" | "roi" | "t-shirt-sizing" | "reformulation-gains" | "reordonnancement" | "supprimer [opportunité]"
disable-model-invocation: true
allowed-tools: Read Edit
---

# Enrichissement de l'opportunity map

Opération demandée : **$ARGUMENTS**

## Principe fondamental

Chaque invocation de cette skill corrige **un seul axe** de l'opportunity map. C'est intentionnel : les itérations unitaires préservent la cohérence des autres dimensions. Ne pas demander à l'IA de "refaire" l'ensemble — demander de corriger un axe précis.

Iterations validées dans la bibliothèque de prompts :
- `metriques-operationnelles` → Ajouter min/dossier, h/semaine, ETP impacté
- `roi` → Recalculer avec les paramètres révisés (TJ, équipe, durée)
- `t-shirt-sizing` → Remplacer les délais chiffrés par S/M/L/XL
- `reformulation-gains` → Reformuler de "économies" → "opportunité de réinvestissement"
- `reordonnancement` → Réordonner par ROI décroissant + ajouter colonne rang de priorité
- `supprimer [opportunité]` → Retirer une opportunité sans justification business suffisante

## Avant de modifier

1. Lis le fichier opportunity map actuel dans le projet
2. Identifie **uniquement** les lignes ou colonnes affectées par l'opération demandée
3. Confirme ce que tu vas changer et ce que tu ne vas **pas** changer

## Format de sortie

Présente :
1. Le diff minimal : avant / après pour les lignes modifiées uniquement
2. Un résumé : "X lignes modifiées, Y dimensions inchangées"
3. Si une modification crée une incohérence ailleurs dans le document, la signaler explicitement sans la corriger automatiquement — attendre la décision de l'équipe.

## Opération de suppression

Si l'opération est `supprimer [opportunité]`, vérifier avant suppression :
- Y a-t-il un job story associé ?
- Y a-t-il une métrique de temps documentée ?
- Y a-t-il un benchmark qui la valide ?

Si les 3 réponses sont "non", confirmer la suppression. Sinon, signaler et attendre confirmation.

## Format de sortie

Utiliser la structure définie dans [template.md](template.md).
