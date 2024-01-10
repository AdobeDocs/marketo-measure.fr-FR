---
description: Tableau de bord Vitesse de l'opportunité - [!DNL Marketo Measure] - Produit
title: Tableau de bord de la vitesse des opportunités
hide: true
hidefromtoc: true
feature: Reporting
source-git-commit: f0e6ba1166e86eeb50812914afb4116f0e0eb372
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 4%

---

# Tableau de bord de la vitesse des opportunités {#opportunity-velocity-dashboard}

Le tableau de bord Velocity offre une vue dynamique du rythme auquel les prospects se déplacent dans l’entonnoir de vente, offrant ainsi aux marketeurs et aux équipes commerciales des informations essentielles sur les temps de conversion sur divers canaux. Cet outil est inestimable pour répondre aux questions clés sur le cycle de vie des opportunités et l’efficacité de la progression au cours des étapes de vente, ce qui vous permet d’optimiser vos stratégies d’engagement pour une croissance et des conversions accélérées.

Questions : Ce tableau de bord répond :

* En moyenne, combien de temps faut-il pour convertir une piste ?
* En moyenne, pour chaque étape, combien de temps un prospect ou un contact prend-il pour passer à l’étape suivante ? Comment cette période change-t-elle au fil du temps ?

## Composants de tableau de bord {#dashboard-components}

### Mosaïque IPC {#kpi-tile}

* **Vitesse de l&#39;accord fermé**: nombre moyen de jours pour les opportunités de &quot;gains clos&quot; de la première étape à la fin.

### Vitesse des opportunités par étape {#opportunity-velocity-by-stage}

Le graphique à barres présente la durée moyenne, en jours, des opportunités passées au cours de chaque étape de vente au cours d’une période spécifique.

Questions sur le graphique :

* À quel stade les opportunités passent-elles le plus de temps en moyenne pendant la période spécifiée ?
* Comment la durée moyenne des opportunités dans l&#39;étape &#39;Création d&#39;opportunités&#39; se compare-t-elle aux étapes &#39;Prospect&#39; et &#39;Qualifications d&#39;opportunités&#39; ?

>[!NOTE]
>
>Les étapes avant &quot;Création d’opportunités&quot; utiliseront la date de point de contact la plus récente comme date de &quot;transition vers&quot;.

![](assets/lead-velocity-dashboard-1.png)

### Vitesse des opportunités au fil du temps {#opportunity-velocity-over-time}

Le graphique en courbes de série temporelle affiche la durée moyenne, en jours, des opportunités passées à chaque étape de vente au cours de la période spécifiée.

* Utilisez les fonctionnalités d’exploration et d’exploration pour classer les données par mois, trimestre ou année.
* Pointez sur une ligne pour afficher des informations détaillées.

Questions sur le graphique :

* Quelles sont les tendances du temps passé à chaque étape pour les opportunités au cours des mois observés ?
* Dans quel mois les opportunités ont-elles connu la progression la plus rapide au cours des étapes de vente ?

![](assets/lead-velocity-dashboard-2.png)

### Vitesse des opportunités par canal {#opportunity-velocity-by-channel}

Le graphique à barres présente la durée moyenne, en jours, pendant laquelle les pistes/contacts restent dans chaque étape de l’entonnoir, segmentée par Canal.

* Pointez sur une ligne pour afficher des informations détaillées.

Questions sur le graphique :

* Quel canal affiche la progression la plus rapide au cours des étapes de l’entonnoir ?
* Comment la vitesse d&#39;opportunité dans la scène &#39;Prospect&#39; varie-t-elle selon les canaux ?

![](assets/lead-velocity-dashboard-3.png)

## Volet Filtrer {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date
   * Basé sur : Transition In Date
* Étape
* Canal
* Sous-canal
* Campagne
* Segment
