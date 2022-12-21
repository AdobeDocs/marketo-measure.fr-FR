---
description: Accès des Data Warehouse - Partage direct - Documentation du produit
title: Accès Data Warehouse - Partage direct
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Accès Data Warehouse - Partage direct {#data-warehouse-access-direct-share}

**Exigences**

Pour [!DNL Marketo Measure] pour configurer un partage direct vers l’entrepôt de données, vous devez respecter les conditions suivantes.

* Vous disposez de votre propre instance de Snowflake.
* Votre instance de Snowflake se trouve dans la région de Snowflake Azure East US 2.
* Vous fournissez [!DNL Marketo Measure] avec votre identifiant de compte de Snowflake.

**Limites**

[!DNL Marketo Measure] ne pourra configurer que les partages directs des Snowflake avec des comptes situés dans Azure East US 2 en raison des limitations actuelles du partage direct des Snowflake. Si vous souhaitez que vos données soient disponibles dans d’autres régions de Snowflake, nous vous recommandons d’effectuer une copie des données dans un compte de Snowflake situé dans Azure Est US 2 et d’utiliser la variable [Réplication de la base de données Snowflake](https://docs.snowflake.com/en/user-guide/database-replication-intro.html)fonction {target=&quot;_blank&quot;} pour copier vos données dans la région/le compte du Snowflake de votre choix.

**Accès au partage**

Une fois que le partage a été créé pour l’identifiant de compte fourni, vous devez renseigner la variable [étapes de configuration](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target=&quot;_blank&quot;} dans votre instance de Snowflake pour accéder aux données.

>[!NOTE]
>
>Vous pouvez choisir le nom de la base de données de votre choix. Vous pouvez attribuer les privilèges à n’importe quelle règle de votre choix, tant qu’elle existe dans votre instance de Snowflake.

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

Pour obtenir des instructions plus détaillées et pour accomplir ces étapes à partir de l’interface utilisateur de Snowflake, reportez-vous à la section [Documentation du Snowflake directement](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target=&quot;_blank&quot;}.
