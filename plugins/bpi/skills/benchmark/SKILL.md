---
name: benchmark
description: Recherche de benchmarks sectoriels en 2 phases séquentielles — collecte avec sources et fourchettes, puis vérification des URLs séparément. Les 2 phases ne sont jamais fusionnées dans une seule réponse.
when_to_use: À utiliser en début de discovery ou de problem framing, avant de citer la moindre donnée marché. Phrases déclencheuses : "cherche des benchmarks sur", "trouve des données sectorielles", "quels sont les chiffres du marché", "benchmark [sujet] [N métriques]".
argument-hint: [sujet] [N-métriques] — ex: "délai instruction PME 5" ou "taux abandon formulaire bancaire 3"
disable-model-invocation: true
---

# Benchmark en 2 phases séquentielles

**CONTRAINTE ABSOLUE** : les 2 phases sont des étapes distinctes avec un arrêt entre elles. Ne jamais les fusionner dans une seule réponse. Cette séparation existe parce que les données de benchmarks sont fréquemment mal sourcées — la vérification séparée a permis d'invalider des données lors d'itérations précédentes.

---

## Phase 1 — Collecte

Recherche $ARGUMENTS.

Pour chaque métrique, fournis :
- La valeur **en fourchette** (pas un chiffre unique — ex: "entre 45% et 65%")
- Source exacte : nom de l'organisation + URL directe + date de publication
- Applicabilité au contexte projet : Haute / Moyenne / Faible + justification en 1 phrase
- Périmètre de la donnée : pays, secteur, taille d'entreprise concernée

Voir [source-checklist.md](source-checklist.md) pour le protocole de collecte complet.

**À la fin de la phase 1**, présente les résultats sous forme de tableau et écris :

> "Phase 1 terminée — [N] métriques collectées. Tapez `go` pour lancer la vérification des sources (Phase 2)."

---

## Phase 2 — Vérification des sources

*(Ne démarre qu'après confirmation explicite de l'utilisateur)*

Pour chaque source de la Phase 1 :
1. Ouvre l'URL et vérifie que le chiffre cité est **réellement présent** dans le document source
2. Classe chaque donnée : ✅ Confirmée / ⚠️ Partiellement confirmée / ❌ Non trouvée dans la source

Pour chaque donnée invalidée (❌) :
- Note le chiffre retiré et la raison
- Propose une donnée de remplacement si disponible, sinon marque "donnée supprimée"

Fournis un tableau de synthèse final avec uniquement les données confirmées ou partiellement confirmées, plus la liste des données invalidées avec motif.

## Format de sortie

Utiliser la structure définie dans [template.md](template.md).
