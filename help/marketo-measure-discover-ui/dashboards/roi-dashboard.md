---
description: Tableau de bord du ROI - [!DNL Marketo Measure] - Produit
title: Tableau de bord Retour sur investissement
feature: Reporting
exl-id: 878db6e0-3ac7-4f4c-b993-bd7a1cfa0638
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 3%

---

# Tableau de bord Retour sur investissement {#roi-dashboard}

Le tableau de bord du ROI offre aux marketeurs une vue granulaire des retours sur investissement sur les canaux, sous-canaux et campagnes. Il ventile méticuleusement les schémas de coûts et de recettes, tout en mettant en avant des mesures telles que le coût par prospect, l’offre et les opportunités, afin d’assurer une compréhension complète de l’attribution marketing.

>[!NOTE]
>
>Ce tableau de bord est actuellement en version bêta. Au cours de cette phase de transition, les tableaux de bord actuels et nouveaux seront accessibles. Le tableau de bord actuel sera obsolète une fois que nous aurons entièrement effectué la transition et garanti des fonctionnalités optimales.

**Questions sur les réponses du panorama**

* Quelles étaient les valeurs de ROI pour chaque canal, sous-canal et campagne ?
* Comment les coûts et les revenus ont-ils été répartis sur chaque canal, sous-canal et campagne ?
* Quel était le coût par piste, le coût par transaction et le coût par opportunité ?

## Composants de tableau de bord {#dashboard-components}

### Mosaïques IPC {#kpi-tiles}

* **Coût**: coûts totaux provenant des sources de données connectées et coûts téléchargés manuellement.
* **Recettes affectées**: contribution totale aux recettes, basée sur le modèle d’attribution sélectionné, provenant d’ Opportunités avec points de contact qui se sont terminés au cours de la période filtrée.
* **Recettes affectées réalisées**: contribution totale des recettes, basée sur le modèle d’attribution sélectionné, provenant des opportunités avec points de contact au cours de la période filtrée, quelle que soit la date à laquelle elles ont été fermées.
* **Total des nouvelles pistes**: nombre total de nouvelles pistes générées, y compris les pistes touchées et non touchées.
* **Coût par nouvelle piste**: coût moyen par nouveau prospect, dérivé du coût total divisé par le nombre total de nouvelles pistes.
* **Nouvelles opportunités totales**: nombre total de nouvelles opportunités générées, y compris les opportunités touchées et non touchées.
* **Coût par nouvelle opportunité**: coût moyen par nouvelle opportunité, dérivé du coût total divisé par le nombre total de nouvelles opportunités.
* **Total des affaires**: nombre d’opportunités de &quot;gains fermés&quot;, y compris les opportunités sans points de contact.
* **ROI simple**: recettes attribuées divisées par les coûts au cours de la période filtrée.
* **ROI réalisé**: chiffre d’affaires attribué réalisé divisé par les coûts au cours de la période filtrée.

![](assets/roi-dashboard-1.png)

### Coût et recettes par graphique de canal {#cost-and-revenue-by-channel-graph}

Graphique à barres illustrant les coûts et les recettes, conçu pour offrir une perspective comparative de leur ampleur par rapport à divers canaux, sous-canaux et campagnes.

* utilisez les fonctionnalités d’analyse et d’analyse pour classer les données par sous-canal et par campagne.
* Passez la souris sur chaque barre pour afficher le ROI simple et réel.

**Questions aux réponses du graphique**

* Quelles étaient les valeurs de ROI pour chaque canal, sous-canal et campagne ?
* Existe-t-il des canaux ou des sous-canaux aberrants avec des coûts exceptionnellement élevés ou faibles par rapport à leurs recettes ?

![](assets/roi-dashboard-2.png)

### Retour sur investissement réalisé ou simple au fil du temps {#realized-vs-simple-roi-over-time}

Graphique en courbes de série temporelle présentant la comparaison entre le retour sur investissement réel et simple, en suivant leur progression au fil du temps.

* Passez la souris sur une section du graphique pour afficher le ROI simple et réel.

**Questions aux réponses du graphique**

* Comment le ROI réalisé se compare-t-il au ROI simple sur des périodes spécifiques ?
* Comment la tendance du ROI réalisé est-elle liée à des événements marketing significatifs au cours de la même période ?

![](assets/roi-dashboard-3.png)

### Graphique de coûts dans le temps {#cost-over-time-graph}

Graphique à barres empilées affichant les coûts totaux, segmenté par canaux associés pour chaque mois/trimestre/année.

* utilisez les fonctionnalités d’exploration et d’exploration pour classer les données par mois, trimestre ou année.
* Passez la souris sur un segment de barre ou l’espace entre les barres pour afficher des informations détaillées.

**Questions aux réponses du graphique**

* Comment le coût combiné de tous les canaux se compare-t-il d&#39;un trimestre/mois au suivant ?
* Comment les coûts d’un canal spécifique ont-ils évolué au fil du temps ?

![](assets/roi-dashboard-4.png)

### Coût par graphique de canal {#cost-by-channel-graph}

Graphique à barres affichant les dépenses marketing segmentées par canal/sous-canal/campagne.

* utilisez les fonctionnalités d’analyse et d’analyse pour classer les données par canal/sous-canal/campagne.

**Questions aux réponses du graphique**

* Quels sous-canaux ou campagnes d’un canal principal ont la distribution la plus élevée ?
* Quels sont les moyens marketing (canal, sous-canal ou campagne) qui semblent sous-financés par rapport aux autres ?

![](assets/roi-dashboard-5.png)

### Tableau récapitulatif du ROI {#roi-summary-table}

Tableau présentant les recettes attribuées, les coûts et le retour sur investissement segmentés par canaux individuels pour une ventilation détaillée.

* Cliquez sur l’icône &quot;+&quot; en regard de chaque canal pour afficher la ventilation par sous-canal et par campagne.

**Colonnes**

* Canal/Subchannel/Campaign
* Coût
* Revenu attribué
* Recettes affectées réalisées
* ROI simple
* ROI réalisé
* Recettes non réalisées du pipeline : recettes du pipeline liées aux points de contact (opportunités ouvertes) créés au cours de la période filtrée.

### Tableau des dépenses marketing {#marketing-spend-table}

Tableau présentant les coûts, les nouvelles pistes, les opportunités et les offres clôturées par canaux individuels pour une ventilation détaillée.

* Cliquez sur l’icône &quot;+&quot; en regard de chaque canal pour afficher la ventilation par sous-canal et par campagne.

**Colonnes**

* Canal/Subchannel/Campaign
* Coût
* Nouveaux leads
* Coût par nouvelle piste
* Nouvelles opportunités
* Coût par nouvelle opportunité
* Affaires
* Coût par contrat

## Volet Filtrer {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date
   * Basé sur :
      * Date de création : Pistes d’actualités, nouvelles opportunités
      * Date de prise en charge : coût
      * Date de clôture : recettes attribuées (ROI simple), offres
      * Date du point de contact : points de contact des recettes attribuées réalisées (retour sur investissement réalisé)
* Modèle d’attribution
* Canal, sous-canal
* Campagne

>[!MORELIKETHIS]
>
>* [Bases du tableau de bord Discover](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
>* [Politique de visibilité des données du tableau de bord](/help/marketo-measure-discover-ui/dashboards/dashboard-data-visibility-policy.md){target="_blank"}

