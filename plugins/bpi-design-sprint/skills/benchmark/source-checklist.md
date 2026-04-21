# Protocole de collecte de sources — Phase 1

## Hiérarchie des sources (par ordre de fiabilité décroissante)

1. **Études primaires** : Banque de France, BCE, Eurostat, INSEE, organismes réglementaires
2. **Cabinets de conseil grands comptes** : McKinsey, BCG, Bain, Deloitte, KPMG, PwC — avec nom de l'étude et année
3. **Associations professionnelles** : FBF (Fédération Bancaire Française), ASF, Médiateur du crédit
4. **Études académiques** : SSRN, Google Scholar, revues à comité de lecture
5. **Études commanditées par éditeurs** : Salesforce, SAP, Adobe — acceptable avec mention du biais
6. **Presse spécialisée** : Les Échos, L'Agefi, Revue Banque — pour contexte uniquement

## Sources à éviter

- Articles sans auteur identifié
- Chiffres relayés en chaîne sans source primaire traçable (ex: "selon une étude...")
- Données antérieures à 2020 sauf si référence historique explicite
- Études dont l'URL ne résout pas directement vers le document

## Format de collecte attendu

Pour chaque métrique :

```
Métrique : [nom]
Valeur : entre X% et Y% (ou entre X et Y [unité])
Source : [nom organisation] — [titre étude] — [année]
URL : [lien direct vers la page ou le PDF]
Périmètre : [pays / secteur / taille d'entreprise]
Applicabilité au projet : Haute / Moyenne / Faible
Justification applicabilité : [1 phrase]
```

## Cas particuliers

**Données BPIFrance** : privilégier les rapports annuels BPIFrance, les études BPI Lab, et les données de l'Observatoire du financement des entreprises.

**Données sur l'abandon de formulaires** : sources fiables incluent Baymard Institute, Formisimo (désormais Zuko), et les études UX de Nielsen Norman Group.

**Données sur l'IA et le traitement documentaire** : McKinsey Global Institute "The Age of AI" (2023), Gartner Magic Quadrant IDP, études Forrester sur l'automatisation bancaire.
