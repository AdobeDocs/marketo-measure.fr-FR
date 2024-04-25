---
description: Tableau de bord des engagements - [!DNL Marketo Measure] - Produit
title: Tableau de bord des engagements
feature: Reporting
exl-id: dc8bcbe4-d470-4cd3-a2d9-804fdebe7121
source-git-commit: db71635a77d6e2555c442fb45371fd5a93e3c502
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Tableau de bord des engagements {#engagement-dashboard}

Le tableau de bord Engagement effectue un suivi méticuleux des mesures d’engagement des utilisateurs. Il présente les points de contact, le nombre de personnes engagées et la moyenne des points de contact par personne. Utilisez le graphique à barres des séries temporelles pour une vue mensuelle, trimestrielle ou annuelle, ainsi que le graphique à barres pour obtenir des informations détaillées sur les canaux, les sous-canaux et les campagnes. Cet outil est essentiel pour comprendre les schémas d’engagement et pour affiner vos stratégies d’engagement.

Nous effectuons le suivi de chaque interaction client en tant que points de contact utilisateur (UT), points de données collectés &quot;bruts&quot;, qui servent de base aux mesures d’engagement dans notre tableau de bord. Toutes les UT ne deviennent pas des points de contact d’achat (BAT) ou des points de contact d’attribution d’achat (BAT), car il s’agit de résultats sélectionnés pour attribuer des interactions client spécifiques à des activités liées aux recettes. Il est important de noter que les règles de suppression n’affectent pas les UT ou le tableau de bord de l’engagement.

* **Points de contact utilisateur**: points de contact créés à partir de tous les engagements.
* **Points de contact de l’utilisateur**: points de contact sélectionnés pour l’attribution de pistes et de contacts. Les BAT ne sont pas liés aux opportunités et n’ont pas de revenus associés.
* **Points de contact d’attribution des acheteurs**: points de contact sélectionnés pour l’attribution d’opportunité. Les MAT ont des répercussions sur les recettes, car elles sont liées aux opportunités.

L’utilisation de BAT ou de BAT uniquement pour mesurer l’engagement sous-estimerait l’ampleur réelle des interactions des clients, puisque l’engagement est plus large que la simple attribution.

Le tableau de bord pose les questions suivantes :

* Combien de personnes ont été engagées ? Quel est le nombre moyen de touches par personne engagée ?
* Comment le nombre de points de contact est-il comparé au nombre de personnes touchées dans un canal/sous-canal/campagne spécifique ?
* Combien de points de contact y avait-il sur un canal ou sous-canal donné ? Comment cela a-t-il changé au fil du temps ?

>[!NOTE]
>
>Les mesures d’engagement Compte et Opportunité seront publiées au premier semestre 2024.

## Composants de tableau de bord {#dashboard-components}

### Mosaïques IPC {#kpi-tiles}

* Points de contact : nombre total de points de contact bruts générés.
   * Les points de contact d’achat et les points de contact d’attribution sont des résultats d’attribution créés en sélectionnant des points de contact spécifiques pour le crédit. Tous les points de contact ne sont pas sélectionnés en tant que BAT et BT.
* Personnes connectées : nombre total de personnes qui disposent d’un point de contact.
* Points de contact par personne : nombre moyen de points de contact par personne qui ont été touchés.

### Points de contact et personnes tactiles au fil du temps {#touchpoints-and-people-touched-over-time}

Le graphique à barres de série chronologique affiche le nombre de points de contact, de points de contact avec les personnes et de points de contact par personne pour chaque mois, trimestre et année.

* utilisez les fonctionnalités d’exploration et d’exploration pour classer les données par mois, trimestre ou année.
* Pointez sur une barre ou une ligne pour afficher des informations détaillées.

Questions sur le graphique :

* Comment le nombre de points de contact et de personnes tactiles a-t-il évolué au fil du temps ?
* Comment les points de contact par personne se comparent-ils d’un trimestre/mois à l’autre ?

![](assets/engagement-dashboard-1.png)

### Points de contact/personnes touchées par le canal {#touchpoints-people-touched-by-channel}

Graphique à barres affichant les points de contact ou les personnes touchées segmenté par canal/sous-canal/campagne.

* utilisez les fonctionnalités d’analyse et d’analyse pour classer les données par sous-canal et par campagne.
* Passez la souris sur chaque barre pour afficher les points de contact ou les personnes touchées.

Questions sur le graphique :

* Quel canal/sous-canal/campagne a généré le plus d’engagement ?
* Comment le nombre de points de contact est-il comparé au nombre de personnes touchées dans un canal/sous-canal/campagne spécifique ?

![](assets/engagement-dashboard-2.png)

## Volet Filtrer {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date (basée sur la date du point de contact)
* Canal, sous-canal
* Campagne
