---
unique-page-id: 18874570
description: Structure de mesure Marketo - Mesure Marketo - Documentation du produit
title: Structure de mesure Marketo
exl-id: fa6de27c-cdd2-4fd9-ac35-7286fe2752d8
source-git-commit: 7eb5ef616e3ae77d53056496f9a1b301ce59d6ee
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Structure de mesure Marketo {#marketo-measure-framework}

En savoir plus sur les quatre composants principaux qui constituent la structure de mesure Marketo. Marketo Measurement s’appuie sur ces applications pour effectuer le suivi, l’organisation et l’hébergement des données, ainsi que pour fournir des fonctionnalités de création de rapports. Les quatre composants qui constituent la structure de Marketo Measurement sont les suivants :

* JavaScript de Marketo Measurement
* Intégrations CRM
* Applications/systèmes tiers
* Application de mesure Marketo

## Marketo Measurement JavaScript {#marketo-measure-javascript}

Le code JavaScript de mesure Marketo effectue le suivi de toutes les interactions marketing en ligne, également appelées points de contact, que les prospects/prospects possèdent avec votre entreprise. Il s’agit d’un script personnalisé ajouté avant la fermeture de la `</head>` balise sur chaque page de votre site web.

`<script type="text/javascript" src="//[cdn.bizible.com/scripts/bizible.js](http://cdn.bizible.com/scripts/bizible.js)" async=""></script>`

>[!NOTE]
>
>Pour plus d’informations sur l’ajout de Marketo Measurement JS, veuillez [cliquez ici](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md).

Le fichier JS de Marketo Measurement capture les données provenant des visites web (y compris les visites web anonymes), du trafic général/de la navigation sur les pages, des téléchargements de contenu et des envois de formulaire. Ces données sont transmises dans votre CRM et chaque interaction marketing est affichée comme un point de contact.

## Intégrations CRM {#crm-integrations}

Marketo Measurement s’intègre aux CRM pour héberger et organiser toutes les données capturées par Marketo Measurement JS. Actuellement, Marketo Measurement comporte des intégrations API avec deux CRM :

![](assets/1-2.png)

En affichant les données de mesure Marketo dans votre CRM, vous pourrez voir les informations granulaires liées à chaque point de contact et générer des rapports pour comprendre les performances de vos canaux.

## Applications tierces {#third-party-applications}

La plupart des spécialistes du marketing comptent sur quelques applications différentes pour exécuter leurs efforts marketing. Outre Salesforce et MS Dynamics, Marketo Measurement est intégré à 13 applications tierces (répertoriées ci-dessous).

![](assets/2-1.png)

Si vous exécutez des actions marketing à l’aide des applications ci-dessus, vous pouvez lier ces comptes à votre compte Marketo Measurement. Cela permet un suivi et un transfert aisés des données vers votre compte de mesure Marketo.

## Application de mesure Marketo {#marketo-measure-application}

L’application Marketo Measurement est utilisée pour afficher et générer des rapports sur vos données d’attribution, configurer les paramètres du compte et mettre à jour les informations du compte. Les options de menu principales de l’application Marketo Measurement sont les suivantes :

**Configuration de compte**

C’est là que vous pouvez mettre à jour les informations générales de votre entreprise et accéder au JavaScript de mesure Marketo.

**Paramètres**

Cet élément de menu vous permet de configurer les paramètres d’attribution et de mappage des canaux, de gérer les intégrations avec les CRM et les applications tierces, d’afficher/ajouter les utilisateurs du compte de mesure Marketo et de mettre à jour les informations de facturation.

**Tableau de bord du ROI marketing**

Le menu Tableau de bord du ROI marketing vous permet de visualiser vos données en termes de performances, d’activité et de coûts du canal.
