---
description: Tableau de bord de l’engagement - [!DNL Marketo Measure] - Produit
title: Tableau de bord des engagements
feature: Reporting
exl-id: dc8bcbe4-d470-4cd3-a2d9-804fdebe7121
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Tableau de bord des engagements {#engagement-dashboard}

Le tableau de bord de l’engagement suit méticuleusement les mesures d’engagement des utilisateurs. Il présente les points de contact, le nombre de personnes engagées et les points de contact moyens par personne. Utilisez le graphique à barres de la série temporelle pour une vue mensuelle, trimestrielle ou annuelle et le graphique à barres pour obtenir des informations détaillées sur les canaux, les sous-canaux et les campagnes. Cet outil est essentiel pour comprendre les schémas d’engagement et affiner vos stratégies d’engagement.

Nous suivons chaque interaction client sous la forme de points de contact utilisateur (UT), les points de données collectés « bruts », qui servent de base aux mesures d’engagement sur notre tableau de bord. Tous les utilisateurs n’évoluent pas vers les points de contact de l’acheteur (BT) ou les points de contact d’attribution de l’acheteur (BAT), car il s’agit de résultats sélectionnés pour attribuer des interactions client spécifiques aux activités liées au chiffre d’affaires. Il est important de noter que les règles de suppression n’affectent pas les utilisateurs et utilisatrices ni le tableau de bord de l’engagement.

* **Points de contact utilisateur** : points de contact créés à partir de tous les engagements.
* **Points de contact de l’acheteur** : points de contact sélectionnés pour l’attribution du lead et du contact. Les BT ne sont pas liés aux Opportunités et n’ont aucun chiffre d’affaires associé.
* **Points de contact d’attribution de l’acheteur** : points de contact sélectionnés pour l’attribution de l’opportunité. Les MTD ont des répercussions sur les recettes, car elles sont liées aux opportunités.

Utiliser uniquement des BT ou des BAT pour mesurer l’engagement sous-estimerait la véritable ampleur des interactions client, car l’engagement est plus large que la simple attribution.

Questions auxquelles le tableau de bord répond :

* Combien de personnes étaient fiancées ? Quel est le nombre moyen de contacts par personne engagée ?
* Comment le nombre de points de contact se compare-t-il aux personnes touchées dans un canal/sous-canal/campagne spécifique ?
* Combien de points de contact y avait-il par canal ou sous-canal donné ? Comment cela a-t-il changé au fil du temps ?

>[!NOTE]
>
>Les mesures d’engagement des comptes et des opportunités devraient sortir au cours du premier semestre 2024.

## Composants de tableau de bord {#dashboard-components}

### Mosaïques de KPI {#kpi-tiles}

* Points de contact : nombre total de points de contact bruts générés.
   * Les points de contact d’acheteur et les points de contact d’attribution d’acheteur sont des résultats d’attribution créés en sélectionnant des points de contact spécifiques pour le crédit. Tous les points de contact ne sont pas sélectionnés comme BT et BAT.
* Personnes touchées : nombre total de personnes qui ont des points de contact.
* Points de contact par personne : nombre moyen de points de contact par personne ayant été touchée.

### Points de contact et personnes touchées au fil du temps {#touchpoints-and-people-touched-over-time}

Le graphique à barres de la série temporelle affiche le nombre de points de contact, de personnes touchées et de points de contact par personne pour chaque mois, trimestre et année.

* Utilisez les fonctionnalités d’analyse et d’élévation pour classer les données par mois, trimestre ou année.
* Survolez une barre ou une ligne pour afficher des informations détaillées.

Questions auxquelles le graphique répond :

* Comment le nombre de points de contact et de personnes touchées a-t-il évolué au fil du temps ?
* Comment les points de contact par personne se comparent-ils d’un trimestre/mois à l’autre ?

![](assets/engagement-dashboard-1.png)

### Points de contact/personnes touchées par le canal {#touchpoints-people-touched-by-channel}

Graphique à barres affichant les points de contact ou les personnes touchées, segmenté par canal/sous-canal/campagne.

* Utilisez les fonctionnalités d’analyse et de classement vers le haut pour classer les données par sous-canal et campagne.
* Pointez sur chaque barre pour afficher les points de contact ou les personnes touchées.

Questions auxquelles le graphique répond :

* Quel canal/sous-canal/campagne a suscité le plus d’engagement ?
* Comment le nombre de points de contact se compare-t-il aux personnes touchées dans un canal/sous-canal/campagne spécifique ?

![](assets/engagement-dashboard-2.png)

## Volet de filtrage {#filter-pane}

Ce tableau de bord est équipé des paramètres et filtres suivants :

* Date (en fonction de la date du point de contact)
* Canal, Sous-Canal
* Campagne
