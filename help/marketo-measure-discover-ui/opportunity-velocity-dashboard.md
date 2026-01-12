---
description: Tableau de bord de la vitesse des opportunités - [!DNL Marketo Measure] - Produit
title: Tableau de bord de la vitesse des opportunités
feature: Reporting
exl-id: d02455fd-8fca-435e-8ded-69abbbdcb3a4
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 4%

---


# Tableau de bord de la vitesse des opportunités {#opportunity-velocity-dashboard}

Le tableau de bord Velocity offre une vue dynamique du rythme auquel les prospects évoluent dans le funnel des ventes, fournissant aux spécialistes marketing et aux équipes commerciales des informations essentielles sur les temps de conversion sur différents canaux. Cet outil est inestimable pour répondre aux questions clés sur le cycle de vie des opportunités et l’efficacité de la progression à travers les étapes de vente, ce qui vous permet d’optimiser vos stratégies d’engagement pour accélérer la croissance et les conversions.

Questions auxquelles répond ce tableau de bord :

* En moyenne, combien de temps faut-il pour convertir un prospect ?
* En moyenne, pour chaque étape, combien de temps faut-il à un prospect ou à un contact pour passer à l’étape suivante ? Comment cette période change-t-elle au fil du temps ?

## Composants de tableau de bord {#dashboard-components}

### Mosaïque KPI {#kpi-tile}

* **Vitesse des affaires conclues** : nombre moyen de jours pour les opportunités « conclues et confirmées », de la première étape à la conclusion.

### Vitesse des opportunités par étape {#opportunity-velocity-by-stage}

Le graphique à barres affiche la durée moyenne, en jours, des opportunités passées à chaque étape de vente au cours d’une période spécifique.

Questions auxquelles le graphique répond :

* À quelle étape les opportunités passent-elles le plus de temps en moyenne au cours de la période spécifiée ?
* Comment la durée moyenne des opportunités à l’étape « Création d’opportunité » se compare-t-elle aux étapes « Prospect » et « Qualifications de l’opportunité » ?

>[!NOTE]
>Les étapes précédant la « création d’opportunité » utiliseront la date de point de contact la plus récente comme date de « transition entrante ».

![Graphique à barres Vitesse des opportunités par étape de vente](assets/lead-velocity-dashboard-1.png)

### Vitesse des opportunités au fil du temps {#opportunity-velocity-over-time}

Le graphique en courbes de séries temporelles affiche le temps moyen, en jours, passé par les opportunités à chaque étape de vente sur la période spécifiée.

* Utilisez les fonctionnalités d’analyse et d’élévation pour classer les données par mois, trimestre ou année.
* Passez la souris sur une ligne pour afficher des informations détaillées.

Questions auxquelles le graphique répond :

* Quelles sont les tendances du temps passé à chaque étape pour les opportunités au cours des mois observés ?
* Au cours de quel mois les opportunités ont-elles connu la progression la plus rapide au cours des étapes de vente ?

![Graphique chronologique des tendances de vitesse des opportunités](assets/lead-velocity-dashboard-2.png)

### Vitesse des opportunités par canal {#opportunity-velocity-by-channel}

Le graphique à barres affiche la durée moyenne, en jours, pendant laquelle les prospects/contacts restent dans chaque étape de funnel, segmentés par canal.

* Passez la souris sur une ligne pour afficher des informations détaillées.

Questions auxquelles le graphique répond :

* Quel canal affiche la progression la plus rapide à travers les étapes de funnel ?
* Comment la vitesse des opportunités dans l’étape « Prospect » varie-t-elle selon les différents canaux ?

![Graphique de comparaison de la vitesse des opportunités par canal](assets/lead-velocity-dashboard-3.png)

## Volet de filtrage {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date
   * Basé sur : date de transition entrante
* Étape
* Canal
* Sous-canal
* Campagne
* Segment
