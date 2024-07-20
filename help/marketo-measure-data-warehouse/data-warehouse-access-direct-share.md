---
description: Accès des Data Warehouse - Partage direct - Documentation du produit
title: Accès à Data Warehouse - Partage direct
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
feature: Data Warehouse
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 4%

---

# Accès à Data Warehouse - Partage direct {#data-warehouse-access-direct-share}

## Exigences {#requirements}

Pour que [!DNL Marketo Measure] configure un partage direct vers l’entrepôt de données, vous devez répondre aux exigences suivantes.

* Vous disposez de votre propre instance de Snowflake.
* Votre instance de Snowflake se trouve dans la région de Snowflake Azure East US 2.
* Vous fournissez [!DNL Marketo Measure] avec votre ID de compte de Snowflake.

## Limites {#limitations}

[!DNL Marketo Measure] pourra uniquement configurer des partages directs Snowflake avec des comptes situés dans Azure Est US 2 en raison des restrictions actuelles du partage direct Snowflake. Si vous souhaitez que vos données soient disponibles dans d’autres régions de Snowflake, nous vous recommandons de faire une copie des données d’un compte de Snowflake situé dans Azure East US 2 et d’utiliser la fonction [Réplication de la base de données Snowflake](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} pour copier vos données dans la région/le compte de Snowflake de votre choix.

## Saisie d’un ID de compte Snowflake {#enter-snowflake-account-id}

Ouvrez la section **Paramètres** dans l’application Marketo Measure et accédez à la page **Data Warehouse**. Dans la section **Direct Share** , saisissez l’ [ ID de compte de Snowflake](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} dans la zone fournie, puis cliquez sur **Connect**.

![](assets/data-warehouse-access-direct-share-1.png)

## Accès au partage {#accessing-the-share}

Une fois le partage créé pour l’ID de compte fourni, vous devez effectuer les [étapes de configuration](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} dans votre instance de Snowflake pour accéder aux données.

>[!NOTE]
>
>Vous pouvez choisir le nom de la base de données de votre choix. Vous pouvez attribuer les privilèges à n’importe quel rôle de votre choix, tant qu’il existe dans votre instance de Snowflake.

* Utilisation du rôle d’administrateur de compte

```
USE ROLE ACCOUNTADMIN
```

* Afficher les partages disponibles (indique le nom du partage accordé)

```
SHOW SHARES
```

* Créer une base de données pour le partage

```
CREATE DATABASE <database_name> FROM SHARE <provider_account>.<share_name>
```

* Octroi de privilèges sur la base de données partagée

```
GRANT IMPORTED PRIVILEGES ON DATABASE <database_name> TO ROLE <role_name>
GRANT IMPORTED PRIVILEGES ON ALL SCHEMAS IN DATABASE <database_name> TO ROLE <role_name>
```

Pour obtenir des instructions et des étapes plus détaillées afin d’accomplir ces étapes à partir de l’interface utilisateur du Snowflake, reportez-vous directement à la [documentation du Snowflake](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
