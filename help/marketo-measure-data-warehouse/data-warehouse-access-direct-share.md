---
description: Accès des Data Warehouse - Partage direct - Documentation du produit
title: Accès Data Warehouse - Partage direct
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
source-git-commit: 36ee02b2dfc2651987f72fc7f02fe629717f02a0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Accès Data Warehouse - Partage direct {#data-warehouse-access-direct-share}

## Exigences {#requirements}

Pour [!DNL Marketo Measure] pour configurer un partage direct vers l’entrepôt de données, vous devez respecter les conditions suivantes.

* Vous disposez de votre propre instance de Snowflake.
* Votre instance de Snowflake se trouve dans la région de Snowflake Azure East US 2.
* Vous fournissez [!DNL Marketo Measure] avec votre identifiant de compte de Snowflake.

## Limites {#limitations}

[!DNL Marketo Measure] ne pourra configurer que les partages directs des Snowflake avec des comptes situés dans Azure East US 2 en raison des limitations actuelles du partage direct des Snowflake. Si vous souhaitez que vos données soient disponibles dans d’autres régions de Snowflake, nous vous recommandons d’effectuer une copie des données dans un compte de Snowflake situé dans Azure Est US 2 et d’utiliser la variable [Réplication de la base de données Snowflake](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} pour copier vos données dans la région/le compte du Snowflake de votre choix.

## Saisie d’un ID de compte Snowflake {#enter-snowflake-account-id}

Ouvrez le **Paramètres** dans l’application Marketo Measurement et accédez à la section **Data Warehouse** page. Dans le **Partage direct** , saisissez votre [ID de compte Snowflake](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} dans la zone fournie, puis cliquez sur **Connexion**.

![](assets/data-warehouse-access-direct-share-1.png)

## Accès au partage {#accessing-the-share}

Une fois que le partage a été créé pour l’identifiant de compte fourni, vous devez renseigner la variable [étapes de configuration](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} dans votre instance de Snowflake pour accéder aux données.

>[!NOTE]
>
>Vous pouvez choisir le nom de la base de données de votre choix. Vous pouvez attribuer les privilèges à n’importe quel rôle de votre choix, tant qu’il existe dans votre instance de Snowflake.

* Utilisation du rôle d’administrateur de compte

```
USE ROLE ACCOUNTADMIN
```

* Afficher les partages disponibles (le nom du partage accordé s’affiche)

```
SHOW SHARES
```

* Création d’une base de données pour le partage

```
CREATE DATABASE <database_name> FROM SHARE <provider_account>.<share_name>
```

* Octroi de privilèges sur la base de données partagée

```
GRANT IMPORTED PRIVILEGES ON DATABASE <database_name> TO ROLE <role_name>
GRANT IMPORTED PRIVILEGES ON ALL SCHEMAS IN DATABASE <database_name> TO ROLE <role_name>
```

Pour obtenir des instructions plus détaillées et pour accomplir ces étapes à partir de l’interface utilisateur de Snowflake, reportez-vous à la section [Documentation du Snowflake directement](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
