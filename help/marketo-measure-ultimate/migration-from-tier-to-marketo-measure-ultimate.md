---
description: Découvrez le processus de migration lorsque vous passez de l’abonnement  [!DNL Marketo Measure]  à l’abonnement  [!DNL Marketo Measure] Ultimate.
title: Migration de Niveau vers  [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
source-git-commit: d62eb377a6abe8a01de7ad2aba34b85fb74ad461
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 1%

---

# Migration de Niveau 1-2 vers [!DNL Marketo Measure] Ultimate {#migration-from-tier-to-marketo-measure-ultimate}

Cet article décrit le processus de migration pour les utilisateurs qui passent de l’abonnement de niveau 1 ou 2 à [!DNL Marketo Measure] Ultimate.

>[!IMPORTANT]
>
>Pensez à conserver votre instance de niveau existant jusqu’à ce que la migration soit terminée.

## Collecte de données {#data-collection}

### Données de trafic web {#web-traffic-data}

* Aucune modification n’est requise pour le déploiement de JavaScript.

* Activez les domaines dans la nouvelle instance Ultimate.

* Si nécessaire, envoyez un ticket pour migrer et retraiter les données web historiques.

* Les intégrations publicitaires restent inchangées, mais n’oubliez pas de les reconnecter dans Ultimate. Avant de procéder, assurez-vous de déconnecter vos comptes publicitaires du client Niveau.

>[!NOTE]
>
>Les données historiques sur le coût des publicités ne seront pas importées. Nous n’importerons les données de coûts publicitaires qu’à partir du moment où les comptes publicitaires seront reconnectés.

### Enterprise Data Connection {#enterprise-data-connection}

Mettez à nouveau en oeuvre toutes les connexions de données source dans AEP, y compris les connexions CRM et Marketo Engage.

## Transformation des données {#data-transformation}

* Les fonctionnalités Account-Based Marketing, y compris la correspondance de piste vers compte et les scores d’engagement prédictifs, ne sont pas disponibles dans Ultimate.

   * Vous pouvez toutefois importer les résultats correspondants de piste à compte via AEP et les utiliser dans la plateforme.

* En fin de compte, les transitions de l&#39;historique CRM sont déduites plutôt que lues directement, car il n&#39;existe pas de connexion CRM directe.

   * Nous lisons les enregistrements d’opportunité et les horodatages, nous voyons l’étape actuelle, puis nous en déduisons les étapes historiques.

## Création de rapports {#reporting}

* Ultimate ne repousse pas les données vers les CRM.

   * Si vous souhaitez renvoyer les données vers le CRM, un pipeline ETL personnalisé est nécessaire pour extraire les données du Snowflake Marketo Measure vers le CRM. Vous devez configurer un modèle de données personnalisé dans le CRM.

* Tous les tableaux de bord de Discover restent identiques à ceux de la solution à plusieurs niveaux, avec l’ajout de tableaux de bord Attribution AI.
