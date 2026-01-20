---
description: Accès à Data Warehouse - Partage direct - Documentation du produit
title: Accès à Data Warehouse - Partage direct
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
feature: Data Warehouse
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 4%

---

# Accès à Data Warehouse - Partage direct {#data-warehouse-access-direct-share}

## Exigences {#requirements}

Pour [!DNL Marketo Measure] configurer un partage direct vers l’entrepôt de données, vous devez répondre aux exigences suivantes.

* Vous disposez de votre propre instance Snowflake.
* Votre instance Snowflake se trouve dans la région Azure East US 2 Snowflake.
* Vous [!DNL Marketo Measure] fournissez l’identifiant de votre compte Snowflake.

## Limites {#limitations}

[!DNL Marketo Measure] ne pourra configurer les partages directs Snowflake qu’avec des comptes situés dans Azure East US 2 (il s’agit d’une limitation dans Marketo Measure, et non avec Snowflake). Si vous avez besoin que vos données soient disponibles dans d’autres régions de Snowflake, nous vous recommandons de les copier dans un compte Snowflake situé dans Azure East US 2 et d’utiliser la fonction [Réplication de base de données Snowflake](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} pour copier vos données dans la région/le compte Snowflake de votre choix.

## Saisir l’ID de compte Snowflake {#enter-snowflake-account-id}

Ouvrez la section **Paramètres** dans l’application Marketo Measure et accédez à la page **Data Warehouse**. Dans la section **Partage direct**, saisissez votre [ID de compte Snowflake](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} dans la zone prévue à cet effet, puis cliquez sur **Connecter**.

![](assets/data-warehouse-access-direct-share-1.png)

## Accès au partage {#accessing-the-share}

Une fois le partage créé pour l’identifiant de compte fourni, vous devez suivre les [étapes de configuration](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} dans votre instance Snowflake pour accéder aux données.

>[!NOTE]
>
>Vous pouvez choisir le nom de base de données de votre choix. Vous pouvez attribuer les privilèges à n’importe quel rôle de votre choix, à condition qu’il existe dans votre instance Snowflake.

* Utiliser le rôle d’administrateur de compte

```
USE ROLE ACCOUNTADMIN
```

* Afficher les partages disponibles (ceci affiche le nom du partage accordé)

```
SHOW SHARES
```

* Créer une base de données pour le partage

```
CREATE DATABASE <database_name> FROM SHARE <provider_account>.<share_name>
```

* Octroi de privilèges sur la base partagée

```
GRANT IMPORTED PRIVILEGES ON DATABASE <database_name> TO ROLE <role_name>
GRANT IMPORTED PRIVILEGES ON ALL SCHEMAS IN DATABASE <database_name> TO ROLE <role_name>
```

Pour obtenir des instructions et des étapes plus détaillées pour accomplir ces étapes à partir de l’interface utilisateur de Snowflake, consultez [la documentation de Snowflake directement](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
