---
unique-page-id: 18874570
description: Structure de Marketo Measure - Marketo Measure - Documentation du produit
title: Structure de Marketo Measure
exl-id: fa6de27c-cdd2-4fd9-ac35-7286fe2752d8
feature: Fundamentals
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Structure de Marketo Measure {#marketo-measure-framework}

Découvrez plus d’informations sur les quatre principaux composants qui constituent la structure de Marketo Measure. Marketo Measure s’appuie sur ces applications pour effectuer le suivi, l’organisation et l’hébergement des données, ainsi que pour fournir des fonctionnalités de création de rapports. Les quatre composants constituant la structure de Marketo Measure sont les suivants :

* Code JavaScript de Marketo Measure
* Intégrations CRM
* Applications/systèmes tiers
* Application Marketo Measure

## Code JavaScript Marketo Measure {#marketo-measure-javascript}

Le code JavaScript de Marketo Measure effectue le suivi de toutes les interactions marketing en ligne, également appelées points de contact, que les prospects/clients potentiels ont avec votre entreprise. Il s’agit d’un script personnalisé, ajouté avant la balise `</head>` fermante sur chaque page de votre site web.

`<script type="text/javascript" src="//[cdn.bizible.com/scripts/bizible.js](http://cdn.bizible.com/scripts/bizible.js)" async=""></script>`

>[!NOTE]
>
>Pour plus d’informations sur l’ajout du code JS Marketo Measure, [cliquez ici](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md).

Le code JS de Marketo Measure capture les données provenant des visites web (y compris les visites anonymes), du trafic général, de la navigation sur les pages, des téléchargements de contenu et des envois de formulaire. Ces données sont transmises à votre CRM et chaque interaction marketing est affichée comme un point de contact.

## Intégrations CRM {#crm-integrations}

Marketo Measure dispose d’intégrations CRM pour héberger et organiser toutes les données capturées par le code JS. Actuellement, Marketo Measure dispose d’API d’intégration pour deux CRM :

![](assets/1-2.png)

En intégrant les données Marketo Measure dans votre CRM, vous pouvez consulter les informations granulaires relatives à chaque point de contact et générer des rapports pour comprendre les performances de vos canaux.

## Applications tierces {#third-party-applications}

La plupart des responsables marketing utilisent différentes applications pour mettre en œuvre leur stratégie. Outre Salesforce et MS Dynamics, Marketo Measure dispose d’intégrations pour 13 applications tierces, répertoriées ci-dessous.

![](assets/2-1.png)

Si vous utilisez ces applications dans le cadre de vos efforts marketing, vous pouvez lier ces comptes à Marketo Measure, ce qui simplifie le suivi et le transfert des données.

## Application Marketo Measure {#marketo-measure-application}

L’application Marketo Measure sert à afficher des données d’attribution, générer des rapports sur ces mêmes données, configurer les paramètres du compte et mettre à jour vos informations. Les principales options du menu de l’application Marketo Measure sont les suivantes :

**Configuration de compte**

C’est ici que vous pouvez mettre à jour les informations générales portant sur votre entreprise et accéder au code JavaScript Marketo Measure.

**Paramètres**

Cet élément de menu vous permet de configurer les paramètres d’attribution et de mappage des canaux, de gérer les intégrations avec les CRM et les applications tierces, d’afficher/ajouter des utilisateurs et des utilisatrices de compte Marketo Measure et de mettre à jour les informations de facturation.

**Tableau de bord de retour sur investissement marketing**

Le tableau de bord de retour sur investissement marketing vous permet de visualiser vos données en termes de performances, d’activité et de coûts pour chaque canal.
