# Cadrage du futur outil

> Proposition de travail au 12 octobre 2026. Aucun des comportements ci-dessous n'est implémenté. Les choix doivent être validés avant le développement.

## Point de départ

La branche `main` examinée au commit `ee3d677` contient uniquement le README. Celui-ci documente l'objectif envisagé, l'absence d'installation, les risques de masquage visuel et les prochaines étapes. Aucun logiciel, dépendance, test, exemple ou licence n'est présent à ce stade.

## Décisions à prendre

| Sujet | Question à résoudre | Proposition pour une première version |
| --- | --- | --- |
| Public et usage | Qui traite quels documents ? | Un utilisateur qui contrôle chaque PDF avant partage |
| Exécution | Traitement local ou service distant ? | Traitement local, sans envoi du document à un service externe |
| Sélection | Zones manuelles, liste de termes ou détection automatique ? | Sélection explicite des zones à retirer ; automatisation ultérieure |
| PDF acceptés | Texte natif, scans, OCR, formulaires ? | Commencer par les PDF à texte natif ; refuser explicitement les cas non pris en charge |
| Sortie | Suppression ou remplacement des éléments sélectionnés ? | Un nouveau PDF expurgé ; conserver l'original sans l'écraser |
| Contenus annexes | Métadonnées, annotations, pièces jointes, signets, formulaires ? | Définir pour chacun une suppression, un traitement ou un refus explicite |
| Interface | Ligne de commande ou interface graphique ? | À décider selon la méthode de sélection et les utilisateurs |
| Licence | Sous quelles conditions partager le code ? | Choisir une licence avant d'intégrer des contributions |

Ces propositions ne sont ni des exigences approuvées ni des promesses de compatibilité.

## Contrat minimal à définir

Avant d'écrire le guide d'utilisation, préciser :

- **Entrée** : formats acceptés, limites de taille/pages et représentation des zones ou données à retirer.
- **Coordonnées** : si des rectangles sont utilisés, définir unités, origine, numérotation des pages et gestion de la rotation.
- **Sortie** : nom et emplacement du PDF produit, comportement si le fichier existe et conservation du source.
- **Erreurs** : PDF corrompu, chiffré, protégé, signé, vide ou format non pris en charge ; éviter toute sortie présentée comme réussie après un traitement incomplet.
- **Confidentialité** : fichiers temporaires, journaux, durée de conservation et éventuels accès réseau.
- **Contrôle** : inspection du rendu et du contenu conformément au [protocole de validation](VALIDATION.md).

## Premier livrable proposé

Un prototype capable de supprimer réellement une zone sélectionnée dans un PDF synthétique à texte natif, avec production d'un fichier distinct et vérification de l'absence de la valeur ciblée dans le texte extrait.

Ce prototype démontrerait une expurgation ciblée. Il ne prouverait pas l'anonymisation complète d'un document : des identifiants non sélectionnés ou des informations permettant une réidentification peuvent subsister.

## Ordre de travail

1. Valider les décisions du tableau et les critères d'acceptation.
2. Comparer les bibliothèques sur des PDF synthétiques, notamment la suppression du contenu et leurs licences.
3. Développer le prototype et des contrôles reproductibles.
4. Documenter l'installation, un exemple complet et les limites effectivement observées.
5. Étendre les formats et l'automatisation uniquement avec des cas de validation adaptés.

## Documentation à compléter après le prototype

Le README devra alors fournir les versions requises, les commandes exactes d'installation et d'exécution, les options disponibles, un exemple entrée/sortie, les erreurs habituelles et les limites connues. Une documentation technique devra expliquer les dépendances, le pipeline PDF/OCR éventuel et les tests.
