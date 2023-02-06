---
unique-page-id: 18874570
description: Structure Marketo Measure - Marketo Measure - Documentation du produit
title: Structure Marketo Measure
exl-id: fa6de27c-cdd2-4fd9-ac35-7286fe2752d8
source-git-commit: 7eb5ef616e3ae77d53056496f9a1b301ce59d6ee
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Structure Marketo Measure {#marketo-measure-framework}

En savoir plus sur les quatre composants principaux qui constituent la structure Marketo Measure. Marketo Measure s’appuie sur ces applications pour effectuer le suivi, l’organisation et l’hébergement des données, ainsi que pour fournir des fonctionnalités de création de rapports. Les quatre composants qui constituent la structure de Marketo Measure sont les suivants :

* JavaScript de Marketo Measure
* Intégrations CRM
* Applications/systèmes tiers
* Application Marketo Measure

## Marketo Measure JavaScript {#marketo-measure-javascript}

Le code JavaScript de Marketo Measure effectue le suivi de toutes les interactions marketing en ligne, également appelées points de contact, que les prospects/prospects ont avec votre entreprise. Il s’agit d’un script personnalisé ajouté avant la fermeture de la `</head>` balise sur chaque page de votre site web.

`<script type="text/javascript" src="//[cdn.bizible.com/scripts/bizible.js](http://cdn.bizible.com/scripts/bizible.js)" async=""></script>`

>[!NOTE]
>
>Pour plus d’informations sur l’ajout de Marketo Measure JS, veuillez [cliquez ici](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md).

Le JS de Marketo Measure capture les données provenant des visites web (y compris les visites web anonymes), du trafic général/de la navigation sur les pages, des téléchargements de contenu et des envois de formulaire. Ces données sont transmises dans votre CRM et chaque interaction marketing est affichée comme un point de contact.

## Intégrations CRM {#crm-integrations}

Marketo Measure s’intègre aux CRM pour héberger et organiser toutes les données capturées par Marketo Measure JS. Actuellement, Marketo Measure intègre des API à deux CRM :

![](assets/1-2.png)

En affichant les données Marketo Measure dans votre CRM, vous pourrez consulter les informations granulaires relatives à chaque point de contact et générer des rapports pour comprendre les performances de vos canaux.

## Applications tierces {#third-party-applications}

La plupart des spécialistes du marketing comptent sur quelques applications différentes pour exécuter leurs efforts marketing. Outre Salesforce et MS Dynamics, Marketo Measure est intégré à 13 applications tierces (répertoriées ci-dessous).

![](assets/2-1.png)

Si vous exécutez des actions marketing à l’aide des applications ci-dessus, vous pouvez lier ces comptes à votre compte Marketo Measure. Cela permet un suivi et un transfert aisés des données vers votre compte Marketo Measure.

## Application Marketo Measure {#marketo-measure-application}

L’application Marketo Measure est utilisée pour afficher et générer des rapports sur vos données d’attribution, configurer les paramètres du compte et mettre à jour les informations du compte. Les options de menu principales de l’application Marketo Measure sont les suivantes :

**Configuration de compte**

C’est là que vous pouvez mettre à jour les informations générales de votre entreprise et accéder au JavaScript Marketo Measure.

**Paramètres**

Cet élément de menu vous permet de configurer les paramètres d’attribution et de mappage des canaux, de gérer les intégrations avec les CRM et les applications tierces, d’afficher/ajouter des utilisateurs de compte Marketo Measure et de mettre à jour les informations de facturation.

**Tableau de bord du ROI marketing**

Le menu Tableau de bord du ROI marketing vous permet de visualiser vos données en termes de performances, d’activité et de coûts du canal.
