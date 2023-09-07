---
description: Tableau de bord des passeports - [!DNL Marketo Measure] - Produit
title: Tableau de bord des passeports
hide: true
hidefromtoc: true
feature: Reporting
source-git-commit: b3d4ea085d851908d52fb62fe58d860ae5c09099
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---

# Tableau de bord des passeports {#passport-dashboard}

Le tableau de bord des passeports offre aux marketeurs une vue dynamique des pistes, des contacts et des opportunités lorsqu’ils passent par différentes étapes au cours d’une période donnée. En filtrant pour une date spécifique, les utilisateurs peuvent également obtenir un instantané des enregistrements pour cette journée.

>[!NOTE]
>
>Ce tableau de bord est actuellement en version bêta. Au cours de cette phase de transition, les tableaux de bord actuels et nouveaux seront accessibles. Le tableau de bord actuel sera obsolète une fois que nous aurons entièrement effectué la transition et garanti des fonctionnalités optimales.

**Questions sur le panorama :**

* Combien de pistes, de contacts ou d’opportunités existaient dans chaque étape non terminale un jour donné ?
* Pendant une période donnée, combien de pistes ou de contacts distincts ont progressé au cours de chaque étape transitoire ?
   * _Exemple_: si le prospect A était à l’étape 1 le 1/1/2023 et passait à l’étape 5 d’ici 3/31/2023, l’analyse des passeports du 1er trimestre 2023 compterait le prospect A aux étapes 1 à 5.
* Combien d’opportunités uniques ont été transmises au cours de chaque étape transitoire au cours d’une période donnée ?

## Composants de tableau de bord {#dashboard-components}

### Opportunités par nom d’évaluation {#opportunities-in-stage-by-stage-name}

* Chaque étape affiche le nombre d’opportunités avec des points de contact qui leur ont été transmis au cours d’une période donnée.
   * Si une opportunité passe par plusieurs étapes au cours de cette période, elle est comptabilisée à chaque étape qu’elle passe.
* Les étapes terminales telles que &quot;Closed Won&quot; et &quot;Closed Lost&quot; sont exclues.
* Les dates de début et de fin sont inclusives.

![](assets/passport-dashboard-1.png)

### Contacts dans l’environnement intermédiaire par nom d’évaluation {#contacts-in-stage-by-stage-name}

* Chaque étape indique le nombre de pistes ou de contacts avec les points de contact qui les ont traversés au cours d’une période donnée.
   * L’affichage ou non de &quot;Prospère&quot; ou &quot;Contact&quot; est déterminé par les préférences définies dans : Paramètres > Paramètres d’attribution > Objet de tableau de bord par défaut.
   * Si un prospect ou un contact passe par plusieurs étapes au cours de cette période, il est comptabilisé à chaque étape qu’il franchit.
* Les étapes terminales telles que &quot;Closed Won&quot; et &quot;Closed Lost&quot; sont exclues.
* Les dates de début et de fin sont inclusives.

![](assets/passport-dashboard-2.png)

## Volet Filtrer {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date (basée sur la date de transition)
* Modèle d’attribution
* Canal, sous-canal
* Campagne
* Segments

>[!MORELIKETHIS]
>
>[Découvrir les bases d’un tableau de bord](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
