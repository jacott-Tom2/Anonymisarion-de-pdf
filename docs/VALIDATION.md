# Protocole de validation proposé

> Ce document décrit des contrôles à mettre en place pour le futur outil. Aucun test n'a été exécuté : le dépôt ne contient pas encore de programme.

## But et limites

Vérifier que les données ciblées sont retirées du PDF produit et que le document restant est lisible. Un rectangle visible ou une recherche textuelle négative ne suffit pas, à lui seul, à prouver l'anonymisation.

Utiliser uniquement des documents synthétiques et des valeurs fictives dans les exemples et les tests du dépôt public. Ne jamais publier un PDF source contenant des données personnelles réelles, un résultat insuffisamment vérifié ou une table de correspondance.

## Jeu de cas à construire

Chaque cas doit contenir une valeur fictive unique, son emplacement, le traitement attendu et un résultat vérifiable.

| Cas synthétique | Contrôle attendu |
| --- | --- |
| Texte natif, valeur répétée sur plusieurs pages | Toutes les occurrences ciblées sont supprimées ; les autres textes sont préservés |
| Page tournée, texte proche d'une limite de zone | La zone correspond à la bonne page et au bon emplacement |
| Image scannée contenant un identifiant | Les pixels ciblés sont retirés si ce format est pris en charge ; sinon le document est explicitement refusé |
| Scan avec couche OCR | L'image et le texte OCR ciblés sont traités ensemble |
| Métadonnées du document, y compris XMP | Les champs concernés sont supprimés ou neutralisés selon une politique définie |
| Annotation, commentaire, lien ou signet contenant la valeur | Aucun contenu ciblé ne subsiste dans ces objets |
| Formulaire rempli | La valeur et son apparence sont traitées conformément au périmètre |
| Pièce jointe intégrée | Suppression ou refus explicite selon la politique définie |
| PDF chiffré, corrompu ou signé | Comportement explicite et documenté ; aucune réussite trompeuse |
| Exécution répétée ou sortie déjà existante | Le fichier source est conservé et la politique d'écrasement est respectée |

Un cas non pris en charge peut être validé par un refus clair. Il ne doit pas être compté comme une anonymisation réussie.

## Contrôles pour chaque sortie

1. **Rendu visuel** : ouvrir ou rendre toutes les pages. Vérifier les zones retirées, la lisibilité, la pagination et l'absence de suppression accidentelle.
2. **Recherche et copie** : rechercher la valeur ciblée dans un lecteur PDF ; tenter la sélection et le copier-coller.
3. **Extraction indépendante** : extraire le texte avec un outil distinct du moteur de traitement et rechercher les valeurs ciblées.
4. **Images et OCR** : lorsqu'ils sont pris en charge, inspecter les images de sortie et leur couche OCR. Une extraction textuelle seule ne détecte pas un identifiant encore visible dans une image.
5. **Objets annexes** : examiner les métadonnées, annotations, formulaires, signets et pièces jointes selon la politique définie.
6. **Structure et sauvegarde** : vérifier que la sortie a été réécrite selon les capacités du moteur choisi, sans anciennes révisions contenant les données retirées. Une recherche brute dans le fichier ne couvre pas tous les contenus compressés ou encodés.
7. **Traces de traitement** : vérifier que les journaux et fichiers temporaires respectent la politique de confidentialité.

## Critères d'acceptation

Un résultat peut être accepté dans le périmètre testé lorsque :

- les contrôles applicables réussissent et les formats non pris en charge sont signalés ;
- les valeurs ciblées ne sont plus récupérables par les méthodes de contrôle définies ;
- le contenu à conserver reste lisible ;
- le source n'est pas altéré ;
- les erreurs et traitements incomplets sont signalés ;
- les limites de couverture sont documentées.

Ces critères concernent la suppression des données ciblées. Ils ne démontrent pas l'impossibilité de réidentifier une personne à partir d'autres informations conservées.

## Trace de validation à conserver

Pour chaque exécution de test, enregistrer : identifiant du cas synthétique, version du logiciel et des dépendances, contrôles réalisés, résultat attendu/observé et anomalies. Les rapports ne doivent pas recopier de données personnelles réelles.

Avant de partager un document sensible, prévoir une relecture humaine portant aussi sur les informations indirectement identifiantes.
