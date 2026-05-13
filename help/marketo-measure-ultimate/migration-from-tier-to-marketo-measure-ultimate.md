---
description: Découvrez le processus de migration lors du passage de l’abonnement  [!DNL Marketo Measure]  niveau à  [!DNL Marketo Measure] Ultimate.
title: Migration du niveau vers [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
exl-id: 828c9bba-3835-484a-bd80-84b5a6b67e22
TQID: https://experienceleague.adobe.com/Q-VV8-RWaGb-lk-vr3y9KK9SjTlsugPJ-N4HrSH5uxA
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
feature_v2:
  - id: c8f57308-7e33-4e41-a385-b55041c78939
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 283
ht-degree: 1%

---

# Migration du niveau 1-2 vers [!DNL Marketo Measure] Ultimate {#migration-from-tier-to-marketo-measure-ultimate}

Cet article décrit le processus de migration pour les utilisateurs qui passent de l’abonnement de niveau 1 ou 2 à [!DNL Marketo Measure] Ultimate.

>[!IMPORTANT]
>
>N’oubliez pas de conserver votre instance de niveau existante jusqu’à ce que la migration soit terminée.

## Collecte de données {#data-collection}

### Données de trafic Web {#web-traffic-data}

* Aucune modification n’est requise pour le déploiement de JavaScript.

* Activez les domaines dans la nouvelle instance Ultimate.

* Si nécessaire, envoyez un ticket pour migrer et retraiter les données web historiques.

* Les intégrations d’annonces restent inchangées, mais pensez à les reconnecter dans Ultimate. Avant de procéder, assurez-vous de déconnecter vos comptes publicitaires dans le client de niveau .

>[!NOTE]
>
>Les données historiques et de coûts ne seront pas importées. À l’avenir, nous n’importerons les données relatives aux coûts publicitaires qu’après la reconnexion des comptes publicitaires.

### Connexion aux données de l’entreprise {#enterprise-data-connection}

Réimplémentez toutes les connexions de données sources dans AEP, y compris les connexions CRM et Marketo Engage.

## Transformation des données {#data-transformation}

* Les fonctionnalités de Account-Based Marketing, notamment la correspondance entre les prospects et les comptes et les scores d’engagement prédictifs, ne sont pas disponibles dans Ultimate.

   * Vous pouvez toutefois importer vos résultats de correspondance entre les prospects et les comptes par l’intermédiaire d’AEP et les utiliser dans la plateforme.

* Dans Ultimate, les transitions d’étape historiques CRM sont déduites plutôt que lues directement, car il n’existe aucune connexion CRM directe.

   * Nous lisons les enregistrements d’opportunités et les horodatages et voyons l’étape actuelle, puis déduisons les étapes historiques.

## Rapports {#reporting}

* Ultimate ne renvoie pas les données aux CRM.

   * Si vous souhaitez renvoyer des données au CRM, un pipeline ETL personnalisé est nécessaire pour extraire des données de Marketo Measure Snowflake vers le CRM. Vous devez configurer un modèle de données personnalisé dans votre CRM.

* Tous les tableaux de bord Discover restent identiques à ceux de la solution hiérarchisée, avec l’ajout de tableaux de bord Attribution AI.
