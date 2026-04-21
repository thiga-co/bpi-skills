---
name: problem-framing
description: Génération des HMW et Job Stories pour chaque acteur, à partir des fichiers sources du projet. Chaque statement est ancré sur une donnée chiffrée. Les exclusions volontaires sont formulées explicitement dans le prompt.
when_to_use: À utiliser après validation des fichiers discovery et du benchmark. Phrases déclencheuses : "génère les problem statements", "crée les HMW pour", "formule les job stories", "problem framing pour [acteur]".
argument-hint: [acteur1] [acteur2] ... — ex: "CA entrepreneur back-office" ou "tous"
disable-model-invocation: true
allowed-tools: Read
---

# Problem framing — HMW + Job Stories

Génère les problem statements pour les acteurs : $ARGUMENTS.

## Règles avant de commencer

1. **Lis d'abord les fichiers sources** disponibles dans le projet (fichiers 1.x et 2.x si présents, benchmark validé). Ne génère rien à froid.
2. **Exclusions volontaires** : si un acteur mentionné dans $ARGUMENTS manque de données dans les sources, écris explicitement "Acteur X exclu — données insuffisantes dans les sources : [raison]". Ne crée pas de problem statement par inférence.
3. **Chaque statement est ancré** sur une donnée chiffrée du benchmark ou de la source primaire. Pas de statement flottant.

## Structure de sortie par acteur

Pour chaque acteur dans $ARGUMENTS :

### [Nom de l'acteur]

**HMW (How Might We)**
> Comment pourrions-nous [verbe d'action] pour [acteur] afin de [résultat mesurable] ?

Source de la donnée : [fichier §X.Y ou benchmark ligne N]

**Job Story**
> Quand [situation déclenchante précise], je veux [action souhaitée], pour [résultat attendu].

Source de la donnée : [fichier §X.Y ou benchmark ligne N]

**Périmètre inclus** : [ce que couvre ce statement]
**Exclusions volontaires** : [ce qui a été explicitement écarté de ce statement et pourquoi]

---

## Vérification finale

Avant de soumettre, vérifie pour chaque statement :
- [ ] Ancré sur une donnée chiffrée sourcée
- [ ] Acteur nommé et rôle précisé
- [ ] Résultat mesurable (pas vague comme "améliorer l'expérience")
- [ ] Exclusions documentées

## Format de sortie

Utiliser la structure définie dans [template.md](template.md).
