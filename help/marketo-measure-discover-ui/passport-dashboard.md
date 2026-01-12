---
description: Passport Dashboard - [!DNL Marketo Measure] - Product
title: Tableau de bord Passeport
feature: Reporting
exl-id: 0fbd9714-7d9c-4330-b35f-d011e17c3bfe
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 2%

---


# Tableau de bord Passeport {#passport-dashboard}

Le tableau de bord Passeport offre aux marketeurs une vue dynamique des Leads, Contacts et Opportunités lorsqu’ils passent par différentes étapes au cours d’une période spécifiée. En filtrant pour une date spécifique, les utilisateurs et utilisatrices peuvent également obtenir un instantané des enregistrements pour cette journée.

**Questions auxquelles le forum répond :**

* Combien de leads, de contacts ou d’opportunités existaient dans chaque étape non terminale le jour choisi ?
* Au cours d’une période spécifiée, combien de leads ou contacts distincts ont progressé au cours de chaque étape transitoire ?
   * _Exemple_ : si le lead A était à l’étape 1 le 1/1/2023 et qu’il est passé à l’étape 5 le 3/31/2023, l’analyse du passeport du 1er trimestre 2023 comptabiliserait le plomb A aux étapes 1 à 5.
* Combien d’opportunités uniques ont traversé chaque étape transitoire au cours d’une période donnée ?

## Composants de tableau de bord {#dashboard-components}

### Opportunités dans l’étape par nom d’étape {#opportunities-in-stage-by-stage-name}

* Chaque étape affiche le nombre d’opportunités avec des points de contact qui leur ont été transmis au cours d’une période donnée.
   * Si une opportunité passe par plusieurs étapes au cours de cette période, elle est comptabilisée à chaque étape qu’elle passe.
* Les étapes de terminal telles que « Fermé et gagné » et « Fermé et perdu » sont exclues.
* Les dates de début et de fin sont comprises.

![Tableau de bord des passeports présentant les opportunités dans l’étape par nom d’étape](assets/passport-dashboard-1.png)

### Leads ou contacts dans l’étape par nom d’étape {#leads-or-contacts-in-stage-by-stage-name}

* Chaque étape affiche le nombre de leads ou de contacts avec des points de contact qui leur ont été transmis au cours d’une période donnée.
   * L’affichage de « Lead » ou « Contact » est déterminé par les préférences définies dans : Paramètres > Paramètres d’attribution > Objet de tableau de bord par défaut.
   * Si un lead ou un contact passe par plusieurs étapes au cours de cette période, il est comptabilisé à chaque étape.
* Les étapes de terminal telles que « Fermé et gagné » et « Fermé et perdu » sont exclues.
* Les dates de début et de fin sont comprises.

![Tableau de bord des passeports montrant les leads ou les contacts dans l’étape par nom d’étape](assets/passport-dashboard-2.png)

## Volet de filtrage {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date (en fonction de la date de transition)
* Canal, Sous-Canal
* Campagne
* Segments

>[!MORELIKETHIS]
> [Bases du tableau de bord Discover](/help/marketo-measure-discover-ui/discover-dashboard-basics.md){target="_blank"}
> [Politique de visibilité des données du tableau de bord ](/help/marketo-measure-discover-ui/dashboard-data-visibility-policy.md){target="_blank"}
