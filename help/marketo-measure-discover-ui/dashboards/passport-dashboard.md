---
description: Tableau de bord des passeports - [!DNL Marketo Measure]  - Produit
title: Tableau de bord Passeport
feature: Reporting
exl-id: 0fbd9714-7d9c-4330-b35f-d011e17c3bfe
source-git-commit: 403b31acce25ddc9c1dcafbd53008b6e2868b3df
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# Tableau de bord Passeport {#passport-dashboard}

Le tableau de bord des passeports offre aux marketeurs une vue dynamique des pistes, des contacts et des opportunités lorsqu’ils passent par différentes étapes au cours d’une période donnée. En filtrant pour une date spécifique, les utilisateurs peuvent également obtenir un instantané des enregistrements pour cette journée.

**Questions sur les réponses du panorama :**

* Combien de pistes, de contacts ou d’opportunités existaient dans chaque étape non terminale un jour donné ?
* Pendant une période donnée, combien de pistes ou de contacts distincts ont progressé au cours de chaque étape transitoire ?
   * _Exemple_ : si le prospect A était à l’étape 1 le 1/1/2023 et passait à l’étape 5 d’ici 3/31/2023, l’analyse du passeport du 1er trimestre 2023 comptabiliserait le prospect A aux étapes 1 à 5.
* Combien d’opportunités uniques ont été transmises au cours de chaque étape transitoire au cours d’une période donnée ?

## Composants de tableau de bord {#dashboard-components}

### Opportunités par nom d’évaluation {#opportunities-in-stage-by-stage-name}

* Chaque étape affiche le nombre d’opportunités avec des points de contact qui leur ont été transmis au cours d’une période donnée.
   * Si une opportunité passe par plusieurs étapes au cours de cette période, elle est comptabilisée à chaque étape qu’elle passe.
* Les étapes terminales telles que &quot;Closed Won&quot; et &quot;Closed Lost&quot; sont exclues.
* Les dates de début et de fin sont inclusives.

![](assets/passport-dashboard-1.png)

### Prospects ou contacts dans l’environnement intermédiaire par nom d’étape {#leads-or-contacts-in-stage-by-stage-name}

* Chaque étape indique le nombre de pistes ou de contacts avec les points de contact qui les ont traversés au cours d’une période donnée.
   * L’affichage ou non de &quot;Prospère&quot; ou &quot;Contact&quot; est déterminé par les préférences définies dans : Paramètres > Paramètres d’attribution > Objet de tableau de bord par défaut.
   * Si un prospect ou un contact passe par plusieurs étapes au cours de cette période, il est comptabilisé à chaque étape qu’il franchit.
* Les étapes terminales telles que &quot;Closed Won&quot; et &quot;Closed Lost&quot; sont exclues.
* Les dates de début et de fin sont inclusives.

![](assets/passport-dashboard-2.png)

## Volet Filtrer {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date (basée sur la date de transition)
* Canal, sous-canal
* Campagne
* Segments

>[!MORELIKETHIS]
>
>* [Bases du tableau de bord Discover](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
>* [Stratégie de visibilité des données du tableau de bord](/help/marketo-measure-discover-ui/dashboards/dashboard-data-visibility-policy.md){target="_blank"}
