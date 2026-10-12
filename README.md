# Anonymisation de PDF

Projet consacré à l’anonymisation de documents PDF.

> **État au 12 octobre 2026 :** ce dépôt est encore au stade initial. La branche `main` ne contient qu’un fichier `README.md` (ce document) et aucun code, script, dépendance, test ou fichier PDF d’exemple. Le dépôt ne fournit donc pas encore d’outil installable ou utilisable.

## Objectif envisagé

Le nom du dépôt suggère un outil pour retirer des informations identifiantes de fichiers PDF. C’est une interprétation du nom, pas une fonctionnalité déjà définie ou livrée. Le périmètre précis reste à décider : anonymisation automatique ou manuelle, types d’informations à traiter, langues, formats PDF acceptés et environnement d’exécution.

## Utilisation

Il n’y a actuellement aucune commande d’installation ou d’exécution : aucun programme n’est présent dans le dépôt.

Les consignes d’utilisation, les dépendances, les systèmes compatibles et les formats pris en charge devront être ajoutés ici lorsqu’une première version du logiciel existera.

## Anonymisation et sécurité

Masquer visuellement un nom avec un rectangle noir ne suffit pas nécessairement : le texte peut rester sélectionnable, extractible ou présent dans la couche OCR. Un PDF peut aussi contenir des informations dans ses métadonnées, annotations, champs de formulaire, signets ou pièces jointes.

Avant de présenter un futur outil comme anonymisant, il faudra définir et vérifier précisément les données qu’il supprime. Les contrôles devraient inclure au minimum :

- vérifier que le texte masqué ne peut plus être recherché, sélectionné ou extrait ;
- examiner les métadonnées, annotations, formulaires, signets et pièces jointes ;
- contrôler le rendu de chaque page après traitement ;
- tester des PDF avec texte natif, pages scannées/OCR et cas limites ;
- documenter les limites connues et rappeler qu’une vérification humaine reste nécessaire pour les documents sensibles.

Aucune garantie de confidentialité ou d’anonymisation n’est revendiquée pour le dépôt dans son état actuel.

## Contenu actuel

```text
.
└── README.md
```

Il n’y a actuellement ni documentation technique séparée, ni code source, ni tests, ni workflow d’intégration continue, ni licence déclarée.

## Prochaines étapes proposées

1. **Définir le besoin** : traitement manuel ou automatique, catégories de données personnelles, langues, utilisateurs visés et plateformes.
2. **Choisir la méthode** : outils PDF et OCR, traitement local ou service distant, formats acceptés et stratégie de suppression réelle des données.
3. **Construire un prototype** : préciser les entrées/sorties, les erreurs, la conservation du fichier source et les limites.
4. **Tester la suppression** : créer des PDF synthétiques contenant texte, OCR, métadonnées, annotations et formulaires, puis vérifier le contenu extrait et le rendu.
5. **Documenter la version** : installation, exemples d’utilisation, résultats attendus, sécurité, limites, compatibilité et licence.
6. **Automatiser les contrôles** : tests reproductibles et vérifications exécutées à chaque modification.

Ces étapes sont des pistes de travail, pas des fonctionnalités déjà disponibles.

## Contributions

Les contributions pourront commencer lorsque le périmètre et les choix techniques seront établis. Pour l’instant, les améliorations les plus utiles sont de préciser l’objectif du projet et de choisir une première fonctionnalité vérifiable.
