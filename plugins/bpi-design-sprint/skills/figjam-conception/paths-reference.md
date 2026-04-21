# Référence — Types de paths User Flow

## Définitions

### ENTRY — Point d'entrée
Moment où l'utilisateur entre dans le parcours. Un parcours peut avoir plusieurs points d'entrée (ex: depuis le dashboard, depuis un email de relance, depuis la page d'accueil).

Couleur conventionnelle : **vert**

Exemples :
- "Entrepreneur arrive sur le portail BEL"
- "CA ouvre la file d'instruction"
- "Notification email → clic → reprise de dossier"

---

### HP — Happy Path (chemin nominal)
Séquence d'étapes quand tout se passe bien. C'est le parcours principal, sans erreur ni exception.

Couleur conventionnelle : **bleu**

Règle : le Happy Path seul n'est pas un User Flow complet. Il doit toujours être accompagné de ERR et ALT.

---

### ERR — Error States (états d'erreur)
États dégradés, validations échouées, timeouts, services indisponibles, données manquantes. Chaque étape du HP a potentiellement un ou plusieurs ERR associés.

Couleur conventionnelle : **rouge**

Exemples :
- "OCR échoue sur document trop dégradé"
- "Score de confiance < 60% → extraction incertaine"
- "DSP2 indisponible → bascule saisie manuelle"
- "Session expirée → sauvegarde auto et message d'avertissement"

---

### ALT — Alternative Paths (chemins alternatifs)
Chemins valides qui dévient du HP sans être des erreurs. Bifurcations légitimes selon le contexte ou les choix utilisateur.

Couleur conventionnelle : **jaune**

Exemples :
- "Entrepreneur déjà client → pré-remplissage sans DSP2"
- "Dossier incomplet → sauvegarde et reprise ultérieure"
- "CA délègue à un autre CA"
- "Choix de ne pas connecter Open Finance → saisie manuelle"

---

### EXIT — Points de sortie
Moments où l'utilisateur quitte le parcours, quelle qu'en soit la raison (succès, abandon, redirection).

Couleur conventionnelle : **gris**

Types de sortie :
- **Succès** : dossier soumis, note validée, courrier envoyé
- **Abandon** : utilisateur quitte sans compléter
- **Redirection** : renvoi vers un autre service ou équipe
- **Blocage** : sortie forcée (document non conforme, délai expiré)

---

## Règle de complétude

Un User Flow est complet quand il contient **au moins** :
- [ ] 1 ENTRY (souvent plusieurs)
- [ ] Le HP end-to-end
- [ ] 1 ERR par étape critique du HP
- [ ] 1-2 ALT majeurs
- [ ] Tous les EXIT possibles

Un flow sans ERR et ALT ne représente pas la réalité du produit.
