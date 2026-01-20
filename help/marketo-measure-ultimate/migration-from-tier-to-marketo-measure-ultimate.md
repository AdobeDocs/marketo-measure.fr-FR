---
description: Découvrez le processus de migration lors du passage de l’abonnement  [!DNL Marketo Measure]  niveau à  [!DNL Marketo Measure] Ultimate.
title: Migration du niveau vers [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
exl-id: 828c9bba-3835-484a-bd80-84b5a6b67e22
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '281'
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
