---
unique-page-id: 35586140
description: Schéma de Data Warehouse - Marketo Measure - Documentation du produit
title: Schéma de Data Warehouse
exl-id: f1895eb1-a32d-4c43-93fb-0aa838527946
source-git-commit: 6e2d438da273511c3465d02eef6813f64e7aec5d
workflow-type: tm+mt
source-wordcount: '22615'
ht-degree: 99%

---

# Schéma de Data Warehouse {#data-warehouse-schema}

Data Warehouse vous permet d’effectuer le suivi de toutes les données de votre choix, de créer des rapports sur vos données d’attribution où vous le souhaitez et d’établir des connexions avec d’autres jeux de données.

>[!IMPORTANT]
>
>Les lignes contenant une valeur pour _DELETED_DATE sont conservées pendant 15 jours, puis supprimées de Snowflake. Les fuseaux horaires pour Snowflake sont indiqués en UTC.

>[!NOTE]
>
>[Cliquez ici](#sample-queries) pour afficher des exemples de requêtes en bas de cet article.

## Diagrammes de relation d’entité {#entity-relationship-diagrams}

L’ERD du _modèle de données Data Warehouse_ indique comment les données de l’entrepôt de données sont destinées à s’organiser sous forme de flux et à être liées. Ce diagramme n’inclut pas toutes les tables disponibles dans l’entrepôt de données, car certaines d’entre elles représentent des tables de mappage, des vues correspondant à des tables déjà présentes ou des tables obsolètes que nous vous déconseillons d’utiliser. Consultez les descriptions détaillées des tables et des colonnes présentes dans l’entrepôt de données ci-dessous. La plupart de ces tables contiennent des champs dénormalisés. Cependant, ce diagramme correspond au modèle de données recommandé : il exploite les données des tables dimensionnelles à la place.

Le second ERD, qui correspond au _modèle de données dimensionnel pour les publicités_, présente la meilleure façon de lier les tables pour les dimensions spécifiques aux publicités à celles présentes dans le modèle de données principal. Bien que les dimensions publicitaires soient également dénormalisées dans d’autres tables, ce modèle est recommandé pour joindre ces dimensions.

_Cliquez sur une image pour sa version agrandie_

<table style="table-layout:auto"> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><strong>Modèle de données Data Warehouse</strong></td> 
   <td><strong>Modèle de données dimensionnel pour les publicités</strong></td> 
  </tr> 
  <tr> 
   <td> 
    <div> 
     <p><a href="assets/data-warehouse-data-model.pdf"><img src="assets/data-warehouse-data-model-thumb.png"></a></p> 
    </div></td>
   <td> 
    <div> 
     <p><a href="assets/ads-dimensional-data-model.pdf"><img src="assets/ads-dimensional-data-model-thumb.png"></a></p>
    </div></td> 
  </tr> 
 </tbody> 
</table>

## Vues {#views}

### BIZ_ACCOUNTS {#biz-accounts}

Comptes importés à partir du système source.

<table>
  <tbody>
    <tr>
      <th><strong>Colonne</strong></th>
      <th><strong>Type de données</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Exemple de données</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Identifiant du compte dans le système source.</td>
      <td>0013100001kpAZxAAM</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création du compte dans le système source.</td>
      <td>2016-08-28 00:32:55.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification du compte dans le système source.</td>
      <td>2018-08-01 17:38:30.000</td>
    </tr>
    <tr>
      <td>NAME</td>
      <td>varchar</td>
      <td>Nom du compte dans le système source.</td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>WEB_SITE</td>
      <td>varchar</td>
      <td>Site web du compte, tel qu’enregistré dans le système source, utilisé pour la mise en correspondance des prospects avec le compte.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_RATING</td>
      <td>varchar</td>
      <td>Note sous forme de lettre (A, B, C, D, N/A) générée à partir du modèle de machine learning [!DNL Marketo Measure]. Cette valeur est nulle si ABM est désactivé.</td>
      <td>B</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_SCORE</td>
      <td>number(38,19)</td>
      <td>Score numérique calculé par le système de machine learning [!DNL Marketo Measure] pour générer le score d’engagement prédictif (Engagement_Rating). Cette valeur est nulle si ABM est désactivé.</td>
      <td>0.1417350147058800000</td>
    </tr>
    <tr>
      <td>DOMAIN</td>
      <td>varchar</td>
      <td>Version analysée du site web, qui stocke uniquement le domaine.</td>
      <td>adobe</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Indique si l’enregistrement est supprimé du système source.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées importées par [!DNL Marketo Measure] à partir du système source au format JSON.</td>
      <td>{"Account_Type__c": "Sécurité, "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACCOUNT_TO_EMAILS {#biz-account-to-emails}

Table de mappage entre les adresses e-mail des prospects (adresses e-mail de contact) et les comptes. Cette table sera vide si ABM est désactivé.

<table>
  <tbody>
    <tr>
    <th><strong>Colonne</strong></th>
      <th><strong>Type de données</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Exemple de données</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Identifiant unique de l’enregistrement.</td>
      <td>0013800001MMPPiAAP_personne@adobe.com|2022-01-05 17:22:13.000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte dans le système source.</p>
      </td>
      <td>
        <p>0013100001phrBAAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse électronique qui a été mappée au compte, soit par le biais des relations de contact, soit par la mise en correspondance des prospects avec le compte.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification du compte dans le système source.</p>
      </td>
      <td>
        <p>2018-08-31 23:53:39.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création du compte dans le système source.</p>
      </td>
      <td>
        <p>2018-08-18 22:01:32.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Inique si l’enregistrement est considéré comme supprimé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACTIVITIES {#biz-activities}

Activités importées depuis un système source ou un compte publicitaire connecté.

<table>
  <tbody>
  <tr>
    <th><strong>Colonne</strong></th>
    <th><strong>Type de données</strong></th>
    <th><strong>Description</strong></th>
    <th><strong>Exemple de données</strong></th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant d’activité du système source.</p>
      </td>
      <td>
        <p>1678625515</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du prospect associé à l’activité.</td>
      <td>
        <p>15530482</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé à l’activité.</p>
      </td>
      <td>
        <p>13792552</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du type d’activité dans le système source.</p>
      </td>
      <td>
        <p>104</p>
      </td>
    </tr>
    <tr>
      <td>ACTIVITY_TYPE_NAME</td>
      <td>varchar</td>
      <td>Nom de l’activité dans le système source.</td>
      <td>
        <p>changement de statut en cours</p>
      </td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de début de l’activité dans le système source.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestapm_ntz</td>
      <td>Date de fin de l’activité dans le système source.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>CAMPAIGN_ID</td>
      <td>varchar</td>
      <td>Identifiant de la campagne à laquelle l’activité appartient dans le système source.</td>
      <td>
        <p>li.508038570.147643566</p>
      </td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Identifie le type de système source.</td>
      <td>Marketo</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création de la ligne dans le système source.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de la ligne dans le système source.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IS_DELETD</td>
      <td>boolean</td>
      <td>Indique si l’enregistrement est considéré comme supprimé du système source.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>AD_FORM_ID</td>
      <td>varchar</td>
      <td>Identifiant du formulaire publicitaire à laquelle l’activité appartient dans le système source.</td>
      <td>li.507063119.3757704</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADS {#biz-ads}

Publicités importées depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p><strong>Colonne</strong></p>
      </th>
      <th>
        <p><strong>Type de données</strong></p>
      </th>
      <th>
        <p><strong>Description</strong></p>
      </th>
      <th>
        <p><strong>Exemple de données</strong></p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la publicité.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804.6052044290004.6053457066804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la publicité dans le système source.</p>
      </td>
      <td>
        <p>6053457066804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel la publicité a été importée.</p>
      </td>
      <td>
        <p>fb.106851586409075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel la publicité a été importée.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Compte</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur de la publicité, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur de la publicité, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire dont dépend la publicité.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804.6052044290004</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire dont dépend la publicité.</p>
      </td>
      <td>
        <p>Ensemble de publicités pour la publicité B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont dépend la publicité.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont dépend la publicité.</p>
      </td>
      <td>
        <p>Campagne de génération de prospects</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la publicité est toujours active dans le système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la publicité a été supprimée du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la publicité dans le système source.</p>
      </td>
      <td>
        <p>Publicité 2</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la publicité doit être mise à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td>
        <p>fb.106851586409075.6052044288804.6052044290004</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Publicité ».</p>
      </td>
      <td>
        <p>Publicité</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire correspondant à la publicité.</p>
      </td>
      <td>
        <p>Facebook</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse URL de la page de destination.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur précédente pour URL_CURRENT.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL qui recevra les paramètres [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_ALTENATIVES</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Importées du système source.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADVERTISERS {#biz-advertisers}

Annonceurs importés depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de l’annonceur.</p>
      </td>
      <td>
        <p>dc.6114.9143143</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant de l’annonceur dans le système source.</td>
      <td>9143143</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel la publicité a été importée.</p>
      </td>
      <td>
        <p>fb.106851586409075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel la publicité a été importée.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Compte</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus de l’annonceur.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus de l’annonceur.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met la campagne publicitaire au-dessus de l’annonceur.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met la campagne au-dessus de l’annonceur de la publicité.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’annonceur est toujours actif dans le système source.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’annonceur a été supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur dans le système source.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’annonceur doit être mis à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Annonceur ».</p>
      </td>
      <td>
        <p>Annonceur</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Le fournisseur de publicité pour l’annonceur.</p>
      </td>
      <td>
        <p>Doubleclick</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_ACCOUNTS {#biz-ad-accounts}

Comptes publicitaires importés depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du compte publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du compte publicitaire dans le système source.</td>
      <td>
        <p>6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Cette valeur doit normalement être nulle, car il s’agit de l’enregistrement correspondant aux comptes publicitaires dans la hiérarchie d’annonces.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Cette valeur doit normalement être nulle, car il s’agit de l’enregistrement correspondant aux comptes publicitaires dans la hiérarchie d’annonces.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met l’annonceur au-dessus des comptes publicitaires.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met l’annonceur au-dessus des comptes publicitaires.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus des comptes publicitaires.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus des comptes publicitaires.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met la campagne publicitaire au-dessus des comptes publicitaires.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met la campagne publicitaire au-dessus des comptes publicitaires.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le compte publicitaire est toujours actif dans le système source.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le compte publicitaire a été supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-09-06 12:54:37.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du compte publicitaire dans le système source.</td>
      <td>
        <p>[!DNL Marketo Measure] Compte publicitaire</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’annonceur doit être mis à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Compte ».</p>
      </td>
      <td>
        <p>Compte</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire correspondant au compte publicitaire.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_CURRENCY_UNIT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Code de devise utilisé pour le compte publicitaire dans le système source.</p>
      </td>
      <td>
        <p>USD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COMPANY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le traitement interne.</td>
      <td>1933789</td>
    </tr>
    <tr>
      <td>
        <p>SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur provenant d’une analyse de l’URL contenue dans utm_source.</td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur provenant d’une analyse de l’URL contenue dans utm_medium.</td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_COST</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>Montant des dépenses importées au cours des 30 derniers jours. Applicable uniquement à AdWords.</p>
      </td>
      <td>
        <p>17260.000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_IMPRESSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Nombre d’impressions au cours des 30 derniers jours. Applicable uniquement à AdWords.</p>
      </td>
      <td>
        <p>730060</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CLICKS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Nombre de clics au cours des 30 derniers jours. Applicable uniquement à AdWords.</p>
      </td>
      <td>
        <p>3400</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CONVERSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Nombre de conversions signalées au cours des 30 derniers jours. Applicable uniquement à AdWords.</p>
      </td>
      <td>
        <p>180</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Modèle de suivi ajouté au niveau du compte publicitaire pour AdWords ou Bing pour le balisage des pages de destination.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_CAMPAIGNS {#biz-ad-campaigns}

Campagnes importées à partir des comptes publicitaires connectés, des systèmes source, de l’UTM et des auto-déclarations.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la campagne.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant de campagne dans le système source.</td>
      <td>
        <p>285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel la campagne a été importée.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel la campagne a été importée.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur de la campagne, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur de la campagne, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus de la campagne.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus de la campagne.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la campagne. Utilisez plutôt le champ ID (identifiant).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne. Utilisez plutôt le champ NAME (nom).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la campagne est toujours active dans le système source.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la campagne a été supprimée du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne.</p>
      </td>
      <td>
        <p>Reciblage pour les partenaires</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la campagne doit être mise à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Campagne ».</p>
      </td>
      <td>
        <p>Campagne</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire correspondant à la campagne.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DAILY_BUDGET</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>Budget quotidien défini dans la plateforme publicitaire pour la campagne.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Modèle de suivi ajouté au niveau de la campagne pour AdWords ou Bing pour le balisage des pages de destination.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_FORMS {#biz-ad-forms}

Formulaires publicitaires importés depuis n’importe quel compte publicitaire connecté.

<table>
  <tr>
    <th>
      <p>Colonne</p>
    </th>
    <th>
      <p>Type de données</p>
    </th>
    <th>
      <p>Description</p>
    </th>
    <th>
      <p>Exemple de données</p>
    </th>
  </tr>
  <tbody>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du formulaire publicitaire.</p>
      </td>
      <td>
        <p>li.507063119.3757704</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel le formulaire publicitaire a été importé.</p>
      </td>
      <td>
        <p>li.507063119</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel le formulaire publicitaire a été importé.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>État de suppression, d’après le système source. Un objet est considéré comme supprimé s’il est en brouillon, archivé ou annulé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du formulaire publicitaire.</p>
      </td>
      <td>
        <p>NSPA Ebook LGF (mai 2020)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « AdForm ».</p>
      </td>
      <td>
        <p>AdForm</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire correspondant au formulaire publicitaire.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Description du formulaire publicitaire.</p>
      </td>
      <td>
        <p>Découvrez comment une automatisation intelligente peut optimiser les processus dans le cadre des demandes de refinancement de prêts hypothécaires.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HEADLINE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Titre du formulaire publicitaire.</td>
      <td>
        <p>Il est temps d’automatiser le processus de demande de refinancement</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL de la page de destination correspondant au formulaire publicitaire.</td>
      <td>
        <p>https://adobe.com/blog/refinancing-application-process/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>QUESTIONS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Liste des questions du formulaire publicitaire.</td>
      <td>
        <p>Prénom:Nom:Adresse e-mail:Pays/zone géographique:Poste occupé:Nom de l’entreprise</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Statut du formulaire publicitaire.</p>
      </td>
      <td>
        <p>envoyé</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>Identifiant de la source d’où provient l’enregistrement.</td>
      <td>aw.3284209</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_GROUPS {#biz-ad-groups}

Groupes publicitaires importés depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du groupe publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955.23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du groupe publicitaire dans le système source.</td>
      <td>
        <p>23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel le groupe publicitaire a été importé.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel le groupe publicitaire a été importé.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les groupes publicitaires n’existent pas dans la hiérarchie publicitaire de Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les groupes publicitaires n’existent pas dans la hiérarchie publicitaire de Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car il s’agit de l’enregistrement correspondant au groupe publicitaire dans la hiérarchie.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car il s’agit de l’enregistrement correspondant au groupe publicitaire dans la hiérarchie.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont dépend le groupe publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont dépend le groupe publicitaire.</p>
      </td>
      <td>
        <p>Affectation des recettes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le compte publicitaire est toujours actif dans le système source.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le compte publicitaire a été supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire.</p>
      </td>
      <td>
        <p>Affectation des recettes - En fonction des comptes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’annonceur doit être mis à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « AdGroup ».</p>
      </td>
      <td>
        <p>AdGroup</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire correspondant au groupe publicitaire.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NETWORK_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Le ou les supports sur lesquels le groupe publicitaire s’exécute.</p>
      </td>
      <td>
        <p>Recherche, Affichage, YouTube_Search, YouTube_Watch</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Modèle de suivi ajouté au niveau du compte publicitaire pour AdWords ou Bing pour le balisage des pages de destination.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-5594512713562690000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_PROVIDERS

<p>Fournisseurs d’annonces provenant de n’importe quel compte publicitaire connecté. Comprend une entrée pour les auto-déclarations, le cas échéant.</p>

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du fournisseur publicitaire.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>4783788151269206864</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ATTRIBUTION_TOUCHPOINTS {#biz-attribution-touchpoints}

<p>Points de contact d’attribution acheteur (Buyer Attribution Touchpoints), tous les points de contact associés à une opportunité.</p>
<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du point de contact d’attribution acheteur (BAT, Buyer Attribution Touchpoint).</p>
      </td>
      <td>
        <p>BAT2_0060Z00000lFHtOQAW_</p>
        <p>0030Z00003K5bpKQAR_2017-06-20:01-05-20-6193330.0b5c5678807c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-09-01 04:53:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’opportunité à laquelle le BAT est attribué.</p>
      </td>
      <td>
        <p>0060Z00000lFHtOQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé au BAT.</p>
      </td>
      <td>
        <p>0030Z00003K5bpKQAR</p>
      </td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Adresse e-mail associée au BAT.</td>
      <td>personne@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte auquel le BAT est attribué.</p>
      </td>
      <td>
        <p>0013100001otbIAAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du point de contact de l’utilisateur qui a généré le BAT.</p>
      </td>
      <td>
        <p>personne@adobe.com_00v1B00003ZbWzHQAV</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date du point de contact.</p>
      </td>
      <td>
        <p>2017-06-20 01:05:20.000</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Identifiant du visiteur associé au BAT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type d’activité, Visite web, Formulaire web, Chat web, Appel téléphonique, Campagne [CRM] ou Activité [CRM]. Dans le CRM, cette valeur est appelée « Type de point de contact ».</p>
      </td>
      <td>
        <p>Formulaire web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal dont dépend le point de contact, tel que défini dans les définitions de canal personnalisées dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Chemin de canal marketing ».</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la première catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td>
        <p>ABC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la deuxième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td>
        <p>Oui</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY3</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la troisième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td>
        <p>PME</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY4</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la quatrième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td>
        <p>Nouvelle entreprise</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY5</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la cinquième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY6</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la sixième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY7</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la septième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la huitième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la neuvième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la dixième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la onzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la douzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la treizième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY14</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la quatorzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY15</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la quinzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Navigateur utilisé au cours de la session, détecté à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version du navigateur utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version de la plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours de la session, première page de destination qui a généré un point de contact. Dans le CRM, cette valeur est appelée « Page de destination ».</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-truth-behind-cost-per-lead</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours de la session, première page de destination qui a généré un point de contact. Une page de destination brute contiendra tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « Page de destination brute ».</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-truth-behind-cost-per-lead?utm_content=27322869&amp;utm_medium=social&amp;utm_source=linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Dans le CRM, cette valeur est appelée « Page du référent ».</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Une page de référent brute contient parfois tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « Page brute du référent ».</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours d’une session, premier formulaire enregistré qui a généré un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans la table Attribution_Touchpoints, mais plutôt dans Form_Submits. Dans le CRM, cette valeur est appelée « URL du formulaire ».</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours d’une session, premier formulaire enregistré qui a généré un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans la table Attribution_Touchpoints, mais plutôt dans Form_Submits. Une page de formulaire brute contient parfois tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « URL brute du formulaire ».</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date d’envoi du formulaire.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ville dans laquelle se trouvait l’utilisateur au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>San Francisco</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Zone géographique dans laquelle se trouvait l’utilisateur au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Californie</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Pays dans lequel se trouvait l’utilisateur au cours de la session, détecté à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>États-Unis</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur utilisée pour définir le support qui a généré le point de contact. Cette valeur peut être issue d’une analyse de l’URL contenue dans utm_medium. Autrement, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que « cpc » ou « affichage ».</p>
      </td>
      <td>
        <p>social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur utilisée pour définir la source qui a généré le point de contact. Cette valeur peut être issue d’une analyse de l’URL contenue dans utm_medium, définie de manière générique (par exemple « CRM Campaign ») si elle est issue d’une synchronisation avec le CRM, ou, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que « Google AdWords » ou « Facebook ». Dans le CRM, cette valeur est appelée « Source du point de contact ».</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour lancer la recherche qui lui a permis d’atteindre le site web. En fonction des achats de mots-clés, cette valeur peut correspondre ou non aux mots-clés achetés sur la plateforme de référencement payant.</p>
      </td>
      <td>
        <p>google [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme publicitaire sur laquelle [!DNL Marketo Measure] a pu s’appuyer pour faire aboutir une résolution. Généralement, il s’agit de l’un de nos partenaires d’intégration.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>Attribution marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>
        <p>Attribution marketing - Général</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>
        <p>dc.6114.8882972.25272734.492579576</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>
        <p>Webinaire budgétaire - barre latérale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contenu créatif correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.182716179597</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du contenu créatif correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Attribution marketing B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Première ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Téléchargez le guide du CMO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Deuxième ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Découvrez comment l’attribution mesure le retour sur investissement en faisant correspondre les activités marketing aux recettes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Page de destination vers laquelle pointe l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse URL conviviale affichée sur l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>http://info.adobe.com/CMOs-Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du mot-clé acheté pour le référencement payant, extrait du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.4838421670</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du mot-clé acheté pour le référencement payant, extrait du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>"attribution marketing"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type de correspondance trouvée entre l’expression recherchée et le mot-clé acheté.</p>
      </td>
      <td>
        <p>Exact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme le premier du parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme celui étant à l’origine de la création du prospect dans le parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme celui étant à l’origine de la création de l’opportunité dans le parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la conclusion du parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGES_TOUCHED</p>
      </td>
      <td>varchar</td>
      <td>Ce champ n’est plus utilisé. Pour obtenir des informations sur les étapes, utilisez les tables Stage_Transitions.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact s’est soldé par un remplissage de formulaire au cours de la session.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme le premier contact d’impression du parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit du premier (voir Is_First_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit du point à l’origine de la création du prospect (voir Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un point en U (voir Is_First_Touch et Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un point en W (voir Is_First_Touch, Is_Lead_Creation_Touch et Is_Opp_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0153374234214425</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle en chemin complet (voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch et Is_Closed_Touch).</p>
      </td>
      <td>
        <p>0.0143061513081193</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>number(22,19)</td>
      <td>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle personnalisé (voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch et Is_Closed_Touch).</td>
      <td>0.0143061513081193</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est supprimé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_ROW_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CAMPAIGN_MEMBERS {#biz-campaign-members}

Membres de la campagne importés à partir du système source. Cette table sera vide si la synchronisation de la campagne est désactivée.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du membre de la campagne dans le système source.</p>
      </td>
      <td>
        <p>00v0Z00001VVzdLQAT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification du membre de la campagne dans le système source.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création du membre de la campagne dans le système source.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_TOUCH_POINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date et heure définies par le client pour remplacer la date de la campagne. Cette valeur sert alors de date pour le point de contact.</p>
      </td>
      <td>
        <p>2018-08-30 18:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect auquel le membre de la campagne est lié.</p>
      </td>
      <td>
        <p>00Q0Z000013dw4GUAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du prospect auquel le membre de la campagne est lié.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact auquel le membre de la campagne est lié.</p>
      </td>
      <td>
        <p>00331000032hMxRAAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du contact auquel le membre de la campagne est lié.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Statut du membre de la campagne, généralement défini sur Envoyé ou Répondu, ou sur une autre valeur personnalisée. Ce statut est lié à Campaign_Sync_Type pour déterminer les membres de la campagne pour lesquels créer des points de contact.</p>
      </td>
      <td>
        <p>Envoyé</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_RESPONDED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le membre de la campagne a été marqué comme « Répondu » dans le sélecteur de statut.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_RESPONDED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle le membre de la campagne a répondu pour la première fois.</p>
      </td>
      <td>
        <p>2018-08-30 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont fait partie le membre.</p>
      </td>
      <td>
        <p>Interviews CMO rapides</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont fait partie le membre.</p>
      </td>
      <td>
        <p>7010Z000001TcKlQAK</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type sélectionné pour la campagne dont fait partie le membre. Le type est utilisé pour mapper le canal marketing.</p>
      </td>
      <td>
        <p>Hors ligne</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_SYNC_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Détermine les membres de la campagne pour lesquels créer des points de contact. Les valeurs possibles sont les suivantes : Include_All, Include_Responded et Exclude_All.</p>
      </td>
      <td>
        <p>Include_All</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Champ d’audit. Indique si un point de contact acheteur a été généré pour le prospect. Si aucun point de contact n’a été créé, le motif de ce rejet est donné.</p>
      </td>
      <td>
        <p>Pas de point de contact : date extérieure au modèle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Champ d’audit. Indique si un point de contact acheteur a été généré pour le contact. Si aucun point de contact n’a été créé, le motif de ce rejet est donné.</p>
      </td>
      <td>
        <p>Point de contact créé</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Champ d’audit. Indique si un point de contact d’attribution acheteur a été généré pour l’opportunité. Si aucun point de contact n’a été créé, le motif de ce rejet est donné.</p>
      </td>
      <td>
        <p>Point de contact créé</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement est considéré comme supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées importées par [!DNL Marketo Measure] à partir du système source au format JSON.</td>
      <td>{"Campaign_Type__c":"Dîners","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CHANNELS {#biz-channels}

Canaux marketing, tels que créés dans l’application [!DNL Marketo Measure].

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du canal.</p>
      </td>
      <td>
        <p>Organic Search.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du canal.</p>
      </td>
      <td>
        <p>Organic Search.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONTACTS {#biz-contacts}

Contacts importés à partir du système source.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact dans le système source.</p>
      </td>
      <td>
        <p>0030Z00003OzioeQAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement correspondant au contact dans le système source.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de l’enregistrement correspondant au contact dans le système source.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:51.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du contact dans le système source.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte associé au contact.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Source ayant permis la création du prospect.</p>
      </td>
      <td>
        <p>Publicité</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Étape actuelle du contact. Des étapes personnalisées peuvent être créées dans l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Démo programmée</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Toutes les étapes précédentes du contact. Des étapes personnalisées peuvent être créées dans l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Ouvert - Contact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>Algorithme [!DNL Marketo Measure] permettant d’estimer la probabilité qu’un contact permettra la concrétisation d’une opportunité en fonction de l’âge et de l’étape.</p>
      </td>
      <td>
        <p>.290034</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie [!DNL Marketo Measure] utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Prérequis : valeur « true » pour l’activation du suivi des appels.</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement est supprimé du système source.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>boolean</td>
      <td>Utilisé pour supprimer les doublons dans les enregistrements si une intégration CRM et Marketo sont configurées. Si un doublon est identifié, le contact Marketo est marqué comme « true » (vrai).</td>
      <td>false</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indique si l’enregistrement provient d’une intégration CRM ou Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappe une personne provenant d’une intégration Marketo à un contact issu d’une intégration CRM. Si une intégration CRM et Marketo coexistent, la valeur correspond à l’identifiant.</td>
      <td>1234 / 00Q0Z00001OohgTUAR</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées importées par [!DNL Marketo Measure] à partir du système source au format JSON.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>3263982503087870000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONVERSION_RATES {#biz-conversion-rates}

Taux de conversion des devises importés à partir du système source.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>number(38,0)</td>
      <td>Identifiant unique de l’enregistrement.</td>
      <td>-5942345438803054604</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valeur d’identifiant de la devise.</td>
      <td>7493833133899044458</td>
    </tr>
    <tr>
      <td>SOURCE_ISO_CODE</td>
      <td>varchar</td>
      <td>Code ISO de la devise dans le système source.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de début du taux de conversion.</td>
      <td>2018-11-01 00:00:00.000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date suivante de début du taux de conversion. (La date de fin du taux de conversion correspond à la valeur end_date moins 1 jour.)</td>
      <td>2018-09-01 00:00:00.000</td>
    </tr>
    <tr>
      <td>CONVERSION_RATE</td>
      <td>number(38,0)</td>
      <td>Taux utilisé pour convertir les montants en devise de l’entreprise.</td>
      <td>0.76728300</td>
    </tr>
    <tr>
      <td>IS_CURRENT</td>
      <td>boolean</td>
      <td>La sémantique de ce champ a été corrompue. Ne l’utilisez pas.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création de l’enregistrement dans le système source.</td>
      <td>2019-03-30 00:54:50.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans le système source.</td>
      <td>2019-03-30 00:54:50.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Indique si l’enregistrement est considéré comme supprimé du système source.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_COSTS {#biz-costs}

Données de coût importées à partir des comptes publicitaires connectés, ou dépenses marketing auto-déclarées.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Identifiant unique de l’enregistrement de coût.</td>
      <td>aw.6601259029.285114995.21703163075.[Affichage AdWords]_2018-09-06</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement.</td>
      <td>2018-09-06 12:22:45.000</td>
    </tr>
    <tr>
      <td>COST_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle le coût a été engagé (ou attribué).</td>
      <td>2018-09-06 00:00:00.000</td>
    </tr>
    <tr>
      <td>SOURCE</td>
      <td>varchar</td>
      <td>Source du coût indiqué.</td>
      <td>[Affichage AdWords]</td>
    </tr>
    <tr>
      <td>COST_IN_MICRO</td>
      <td>number(38,0)</td>
      <td>Montant du coût en millions. L’utilisateur devra diviser la valeur par 1 000 000.</td>
      <td>1410000</td>
    </tr>
    <tr>
      <td>CLICKS</td>
      <td>number(38,0)</td>
      <td>Nombre de clics signalés pour le groupe au cours de la journée.</td>
      <td>4</td>
    </tr>
    <tr>
      <td>IMPRESSIONS</td>
      <td>number(38,0)</td>
      <td>Nombre d’impressions signalées pour le groupe au cours de la journée.</td>
      <td>4187</td>
    </tr>
    <tr>
      <td>ESTIMATED_TOTAL_POSSIBLE_IMPRESSIONS</td>
      <td>number(38,0)</td>
      <td>Nombre total d’impressions estimées à partir de DCM pour le groupe au cours de la journée.</td>
      <td>5024</td>
    </tr>
    <tr>
      <td>AD_PROVIDER</td>
      <td>varchar</td>
      <td>Fournisseur pour lequel le coût a été extrait.</td>
      <td>Google</td>
    </tr>
    <tr>
      <td>CHANNEL_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Identifiant du canal marketing, créé par [!DNL Marketo Measure].</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_NAME</td>
      <td>varchar</td>
      <td>Nom du canal marketing, créé par le client dans l’application [!DNL Marketo Measure].</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_IS_AGGREGATABLE_COST</td>
      <td>boolean</td>
      <td>Indique si la ligne contient un coût qui peut être additionné en fonction du canal. (Pour obtenir le coût total correspondant au canal, le système additionne les lignes où cette colonne contient la valeur « true ».)</td>
      <td>false</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Identifiant de l’annonceur extrait de la connexion publicitaire, spécifiquement pour Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>ADVERTISER_NAME</td>
      <td>varchar</td>
      <td>Nom de l’annonceur extrait de la connexion publicitaire, spécifiquement pour Doubleclick.</td>
      <td>[!DNL Marketo Measure] Marketing Analytics</td>
    </tr>
    <tr>
      <td>ADVERTISER_IS_AGGREGATABLE_COST</td>
      <td>boolean</td>
      <td>Indique si la ligne contient un coût qui peut être additionné en fonction de l’annonceur. (Pour obtenir le coût total correspondant à l’annonceur, le système additionne les lignes où cette colonne contient la valeur « true ».)</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du compte. (Pour obtenir le coût total correspondant au compte, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>Reciblage pour les partenaires</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction de la campagne. (Pour obtenir le coût total correspondant à la campagne, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.21703163075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>Logiciel de gestion des attributions | Phrase</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du groupe publicitaire. (Pour obtenir le coût total correspondant au groupe publicitaire, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>dc.6114.9131003.24149929.467969200</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>Nom de la publicité : Ad3-320x50.gif ; 320 x 50</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction de l’annonce. (Pour obtenir le coût total correspondant à l’annonce, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contenu créatif extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.51749608028.266050115160</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du contenu créatif extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>Gartner Magic Quadrant 2019</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du contenu créatif. (Pour obtenir le coût total correspondant au contenu créatif, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du mot-clé extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>aw.6601259029.669328935.39419128772.99608705795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du mot-clé extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>attribution marketing sfdc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du contenu mot-clé. (Pour obtenir le coût total correspondant au mot-clé, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’emplacement extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction de l’emplacement. (Pour obtenir le coût total correspondant à l’emplacement, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du site extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site extrait de la connexion publicitaire.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du site. (Pour obtenir le coût total correspondant au site, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement est considéré comme supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ISO_CURRENCY_CODE</td>
      <td>varchar</td>
      <td>Code ISO de la devise, importé à partir du système source.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>Identifiant de la source d’où provient l’enregistrement.</td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ROW_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valeur d’identifiant de la devise pour l’enregistrement.</td>
      <td>
        <p>-3253183181619994799</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CREATIVES {#biz-creatives}

Contenus créatifs importés depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du contenu créatif.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du contenu créatif dans le système source.</td>
      <td>
        <p>10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel le contenu créatif a été importé.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel le contenu créatif a été importé.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur du contenu créatif, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur du contenu créatif, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire dont dépend le contenu créatif.</p>
      </td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire dont dépend le contenu créatif.</p>
      </td>
      <td>Ensemble de publicités pour la publicité B</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont dépend le contenu créatif.</p>
      </td>
      <td>
        <p>ba.3284209.132855866</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont dépend le contenu créatif.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le contenu créatif est toujours actif dans le système source.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le contenu créatif a été supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du contenu créatif dans le système source.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le contenu créatif doit être mis à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Contenu publicitaire ».</p>
      </td>
      <td>
        <p>Contenu publicitaire</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire dont dépend le contenu créatif.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version actuelle de l’URL, avec toutes les balises.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>cdn.adobe.com/redir?lp=http%3a%2f%2fwww.pipelinemarketing.com%2f&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}&amp;utm_content={adid}&amp;utm_term={keyword}&amp;utm_campaign=PipelineMarketing.com&amp;utm_source=bing&amp;utm_medium=cpc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_DISPLAY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version abrégée et conviviale de l’URL, qui s’affiche sur le contenu créatif.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur précédente pour URL_CURRENT.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL qui recevra les paramètres [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_SHORTENED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Version abrégée et conviviale de l’URL, qui s’affiche sur le contenu créatif. (Ce champ est utilisé uniquement pour LinkedIn Ads.)</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type de contenu créatif (texte ou affichage).</p>
      </td>
      <td>
        <p>Texte</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le contenu créatif utilise des URL mises à niveau.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HEADLINE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Titre du contenu créatif (texte principal).</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Première ligne de corps de texte du contenu créatif.</p>
      </td>
      <td>
        <p>Connectez-vous et formez-vous auprès de responsables marketing B2B qui mettent l’accent sur la génération de recettes. Rejoignez la communauté.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Deuxième ligne de corps de texte du contenu créatif.</p>
      </td>
      <td>
        <p>Vous avez utilisé les services d’analyse ? Donnez votre avis !</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Champ de diagnostic, utilisé par le système de traitement interne.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SHARE_URN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du partage. (Ce champ est utilisé uniquement pour LinkedIn Ads.)</p>
      </td>
      <td>
        <p>urn:li:share:6376987561897848832</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_EVENTS {#biz-crm-events}

Événements importés à partir du système source. Cette table sera vide si la synchronisation des activités est désactivée.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’événement dans le système source.</p>
      </td>
      <td>
        <p>00U3100000VLUnEEAX</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de l’événement dans le système source.</p>
      </td>
      <td>
        <p>2016-12-12 19:32:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’événement dans le système source.</p>
      </td>
      <td>
        <p>2018-09-03 08:39:51.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect associé à l’événement.</p>
      </td>
      <td>
        <p>00Q0Z000013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du prospect associé à l’événement.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé à l’événement.</p>
      </td>
      <td>
        <p>0030Z00003OyjbOQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du contact associé à l’événement.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie [!DNL Marketo Measure] utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Prérequis : valeur « true » pour l’activation du suivi des appels.</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du type d’activité dans le système source.</p>
      </td>
      <td>
        <p>E-mail</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_START_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de début de l’événement. Il s’agit de l’une des options utilisées pour déterminer la date du point de contact.</p>
      </td>
      <td>
        <p>2016-12-16 19:30:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_END_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de fin de l’événement. Il s’agit de l’une des options utilisées pour déterminer la date du point de contact.</p>
      </td>
      <td>
        <p>2016-12-16 21:30:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme supprimé du système source.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées importées par [!DNL Marketo Measure] à partir du système source au format JSON.</td>
      <td>{"Contact_Type__c":"CMO","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_TASKS {#biz-crm-tasks}

Tâches importées à partir du système source. Cette table se remplit si la synchronisation des activités OU le suivi des appels sont activés.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la tâche dans le système source.</p>
      </td>
      <td>
        <p>00T0Z00004Rf62rUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de la tâche dans le système source.</p>
      </td>
      <td>
        <p>2018-08-27 18:30:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de la tâche dans le système source.</p>
      </td>
      <td>
        <p>2018-08-27 18:31:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect associé à la tâche.</p>
      </td>
      <td>
        <p>00Q0Z000013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du prospect associé à la tâche.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé à la tâche.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du contact associé à la tâche.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie [!DNL Marketo Measure] utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Prérequis : valeur « true » pour l’activation du suivi des appels.</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du type d’activité dans le système source.</p>
      </td>
      <td>
        <p>Appel</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de réalisation de la tâche. Il s’agit de l’une des options utilisées pour déterminer la date du point de contact.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme supprimé du système source.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées importées par [!DNL Marketo Measure] à partir du système source au format JSON.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CURRENCIES {#biz-currencies}

Table contenant toutes les devises ISO.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>number(38,0)</td>
      <td>Identifiant unique de l’enregistrement de devise.</td>
      <td>139474809945095870</td>
    </tr>
    <tr>
      <td>ISO_CODE</td>
      <td>varchar</td>
      <td>Code ISO de la devise.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>IS_CORPORATE</td>
      <td>boolean</td>
      <td>Indique si la devise est celle de l’entreprise.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_ENABLED</td>
      <td>boolean</td>
      <td>Indique si la devise est activée dans le système source.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans [!DNL Marketo Measure].</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans le système source.</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création de l’enregistrement dans [!DNL Marketo Measure]</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Date de création de l’enregistrement dans le système source.</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>ISO_NUMERIC</td>
      <td>number(38,0)</td>
      <td>Code ISO numérique standard.</td>
      <td>048</td>
    </tr>
    <tr>
      <td>EXPONENT</td>
      <td>number(38,0)</td>
      <td>Nombre de décimales entre la plus petite unité de devise définie et une unité de devise entière.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>NAME</td>
      <td>varchar</td>
      <td>Nom de la devise.</td>
      <td>Peso argentin</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_AB_TESTS {#biz-customer-ab-tests}

Tests AB enregistrés. Cette table sera vide si les tests AB ne sont pas activés.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du premier cookie correspondant à l’identifiant visiteur.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie enregistré au moment où l’événement a été consigné.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle la conversation a été consignée.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au moment où l’expérience a été consignée.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’expérience extraite de la plateforme de test AB.</p>
      </td>
      <td>123</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’expérience extraite de la plateforme de test AB.</p>
      </td>
      <td>Expérience A</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la variation de l’expérience extraite de la plateforme de test AB.</p>
      </td>
      <td>456</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la variation de l’expérience extraite de la plateforme de test AB.</p>
      </td>
      <td>Test bleu</td>
    </tr>
    <tr>
      <td>
        <p>ABTEST_USER_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’utilisateur qui a reçu l’expérience extraite de la plateforme de test AB.</p>
      </td>
      <td>584d64et</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement a été supprimé. Ce champ est utilisé à des fins de diagnostic et d’audit.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_EVENTS {#biz-customer-events}

Événements web enregistrés à l’aide d’événements personnalisés dans le code JavaScript. Cette table sera vide si les événements [!DNL Marketo Measure] ne sont pas activés.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du premier cookie correspondant à l’identifiant visiteur.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie enregistré au moment où l’événement a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle l’événement a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au moment où l’événement a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom donné à l’événement qui a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>Vue sur la vidéo</td>
    </tr>
    <tr>
      <td>
        <p>VALUE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur donnée à l’événement qui a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>Vidéo vue à 75 %</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement a été supprimé. Ce champ est utilisé à des fins de diagnostic et d’audit.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOM_LANDING_PAGES {#biz-custom-landing-pages}

Pages de destination téléchargées à partir de n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de l’enregistrement.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du compte publicitaire à partir duquel la page de destination a été importée.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du compte publicitaire à partir duquel la page de destination a été importée.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur de la page de destination, spécifiquement pour Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur de la page de destination, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du groupe publicitaire dont dépend la page de destination.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire dont dépend la page de destination.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont dépend la page de destination.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont dépend la page de destination.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de la ligne.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_EMAIL_TO_VISITOR_IDS {#biz-email-to-visitor-ids}

Table de correspondance entre les adresses e-mail et les identifiants visiteur.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Identifiant unique de l’enregistrement.</td>
      <td>
        <p>0013800001MMPPiAAP_personne@adobe.com|2022-01-05 17:22:13.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail connue liée à un identifiant visiteur donné d’une session.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Premier cookie correspondant à l’identifiant visiteur.</p>
      </td>
      <td>
        <p>v_36ec805b4db344d6e92c972c86aee34a</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de la ligne.</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de la ligne.</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement est considéré comme supprimé. Ce champ est utilisé à des fins de diagnostic et d’audit.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_IGNORE</td>
      <td>boolean</td>
      <td>Indique si l’adresse e-mail ou l’identifiant visiteur est considéré comme du bruit ou du spam. Ce champ est utilisé pour le traitement interne.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FACTS {#biz-facts}

Regroupe les données de type Impressions, Pages vues, Visites, Envois de formulaire, Points de contact utilisateur, Point de contact (BT), Points de contact d’attribution (BAT) et Coût. Ce champ est utilisé par le système pour la création de rapports [!DNL Marketo Measure].

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>COST_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des coûts.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>ATP_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des points de contact d’attribution.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>TP_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec les tables des points de contact ou des points de contact utilisateur.</td>
      <td>5028390208679093800</td>
    </tr>
    <tr>
      <td>PAGE_VIEW_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des pages vues.</td>
      <td>-8044063242541720607</td>
    </tr>
    <tr>
      <td>SESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des sessions.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Identifiant du premier cookie correspondant à l’identifiant visiteur.</td>
      <td>v_530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>COOKIE_ID</td>
      <td>varchar</td>
      <td>Identifiant du cookie enregistré au moment où l’événement a été consigné.</td>
      <td>530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>FORM_SUBMIT_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des envois de formulaire.</td>
      <td>-8659572802702769670</td>
    </tr>
    <tr>
      <td>IMPRESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des impressions.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des URL.</td>
      <td>4079876040770132443</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des URL.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des URL.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>AD_PROVIDER_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des fournisseurs publicitaires.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des canaux.</p>
      </td>
      <td>
        <p>-1921844114032355934</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des campagnes publicitaires.</p>
      </td>
      <td>
        <p>252687814634577606</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des mots-clés.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des annonces.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des groupes publicitaires.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des contenus créatifs.</p>
      </td>
      <td>
        <p>-2333871387956621113</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des sites.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des annonceurs.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des comptes publicitaires.</p>
      </td>
      <td>
        <p>1825012532740770032</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilisé pour la jonction avec la table des emplacements.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>CATEGORY_01_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_02_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_03_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_04_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_05_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_06_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_07_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_08_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_09_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_10_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_11_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_12_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_13_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_14_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_15_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jonction avec la table des segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>TYPE</td>
      <td>number(38,0)</td>
      <td>Indique le type d’information correspondant à la ligne. 1 = Point de contact d’attribution acheteur ; 2 = Coût ; 3 = Point de contact acheteur ; 4 = Point de contact utilisateur ; 5 = Page vue ; 6 = Session ; 7 = Envoi de formulaire ; 8 = Impression.</td>
      <td>3</td>
    </tr>
    <tr>
      <td>DATE</td>
      <td>date</td>
      <td>Date à laquelle l’événement s’est produit.</td>
      <td>2018-08-28</td>
    </tr>
    <tr>
      <td>TIMESTAMP</td>
      <td>timestamp_ntz</td>
      <td>Date et heure auxquelles l’événement s’est produit.</td>
      <td>2018-08-28 19:39:15.000</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de la ligne.</p>
      </td>
      <td>
        <p>2018-08-29 00:46:47.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COST_IN_MICRO</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Montant du coût en millions. L’utilisateur devra diviser la valeur par 1 000 000.</p>
      </td>
      <td>
        <p>27370000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Nombre d’impressions signalées pour le groupe au cours de la journée.</p>
      </td>
      <td>
        <p>340</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLICKS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Nombre de clics signalés pour le groupe au cours de la journée.</p>
      </td>
      <td>4</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit du premier.</p>
      </td>
      <td>0.0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit du point à l’origine de la création du prospect.</p>
      </td>
      <td>100.0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un point en U.</p>
      </td>
      <td>
        <p>100.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un point en W.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle en chemin complet.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle personnalisé.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AMOUNT</p>
      </td>
      <td>
        <p>number(38,8)</p>
      </td>
      <td>
        <p>Montant de l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>42000.00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’opportunité a été déplacée vers une étape classée comme gagnante.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CLOSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’opportunité est passée à une étape classée comme terminée.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>0060Z00000nFEfEQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>2018-08-31 15:45:47.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CLOSE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de clôture de l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>2018-12-31 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de l’enregistrement correspondant au contact dans le système source.</p>
      </td>
      <td>2017-04-28 00:21:52.000</td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact dans le système source.</p>
      </td>
      <td>
        <p>0030Z00003ORVJmQAP</p>
      </td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Adresse e-mail correspondant à l’enregistrement.</td>
      <td>personb@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>LEAD_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de l’enregistrement correspondant au prospect dans le système source.</p>
      </td>
      <td>
        <p>2017-04-28 00:21:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect dans le système source.</p>
      </td>
      <td>
        <p>00Q3100001GMPIsEAP</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction de l’annonce. (Pour obtenir le coût total correspondant à l’annonce, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_ADVERTISER</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction de l’annonceur. (Pour obtenir le coût total correspondant à l’annonceur, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_ACCOUNT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du compte. (Pour obtenir le coût total correspondant au compte, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_GROUP</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du groupe publicitaire. (Pour obtenir le coût total correspondant au groupe publicitaire, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CAMPAIGN</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction de la campagne. (Pour obtenir le coût total correspondant à la campagne, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CHANNEL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du canal. (Pour obtenir le coût total correspondant au canal, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CREATIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du contenu créatif. (Pour obtenir le coût total correspondant au contenu créatif, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_KEYWORD</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du contenu mot-clé. (Pour obtenir le coût total correspondant au mot-clé, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_PLACEMENT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction de l’emplacement. (Pour obtenir le coût total correspondant à l’emplacement, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_SITE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne contient un coût qui peut être additionné en fonction du site. (Pour obtenir le coût total correspondant au site, le système additionne les lignes où cette colonne contient la valeur « true ».)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement a été supprimé. Ce champ est utilisé comme journal d’audit.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valeur d’identifiant de la devise pour l’enregistrement.</td>
      <td>-3253183181619994799</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FORM_SUBMITS {#biz-forms-submits}

Envois de formulaire capturés.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de l’envoi de formulaire.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-21-927280.9bc63c34482f4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie enregistré au moment où l’envoi de formulaire a été consigné.</p>
      </td>
      <td>
        <p>9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du premier cookie correspondant à l’identifiant visiteur. Si l’enregistrement est marqué comme is_duplicated = true, ce champ sera nul.</p>
      </td>
      <td>
        <p>v_9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de session enregistré au moment où l’envoi de formulaire a été consigné. Si l’enregistrement est marqué comme is_duplicated = true, ce champ sera nul.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-24-1231230.9bc63c34482f</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date d’envoi du formulaire.</p>
      </td>
      <td>
        <p>2018-08-06 01:35:21.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-07 23:09:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL à partir de laquelle le formulaire a été envoyé, sans paramètres de requête.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL à partir de laquelle le formulaire a été envoyé, avec les paramètres de requête.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDdPdXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au moment où le formulaire a été envoyé.</p>
      </td>
      <td>
        <p>174 127 184 158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique le type d’événement.</td>
      <td>
        <p>FormSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Appareil et navigateur enregistrés au moment de l’envoi du formulaire.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique l’ordre dans lequel l’événement de page vue s’est déroulé au cours de la session.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour contrôle et traitement internes.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Valeur utilisée pour le traitement interne.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail fournie dans le formulaire, capturée dans le code JavaScript.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique le type de formulaire envoyé.</td>
      <td>
        <p>Messagerie instantanée</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indique la méthode utilisée pour reconnaître le formulaire, par exemple onSubmit ou AjaxIntercept.</p>
      </td>
      <td>
        <p>onSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_IDENTIFIER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur d’identifiant du formulaire.</td>
      <td>
        <p>-956012665</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Clé étrangère de la table d’URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_IMPRESSIONS {#biz-impressions}

Impressions déclenchées et enregistrées. Cette table nécessite une connexion DoubleClick, et l’option d’activation de visionnage moyen doit être définie sur True.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de l’impression.</p>
      </td>
      <td>
        <p>6acd7b43290490fe5c53eed31281d09a|2020-05-18:22:20:59|0000|0|2869369052</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie enregistré au moment de l’impression.</p>
      </td>
      <td>08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du premier cookie correspondant à l’identifiant visiteur.</p>
      </td>
      <td>v_08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de session enregistré au moment où l’impression a été consignée.</p>
      </td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle l’impression a été générée.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL à partir de laquelle l’impression a été générée, sans paramètres de requête.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL à partir de laquelle l’impression a été générée, avec les paramètres de requête.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDdPdXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au moment de l’impression.</p>
      </td>
      <td>174 127 184 158</td>
    </tr>
    <tr>
      <td>
        <p>TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique le type d’événement.</td>
      <td>Impression</td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Appareil et navigateur enregistrés au moment de l’envoi du formulaire.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique l’ordre dans lequel l’événement de page vue s’est déroulé au cours de la session.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour contrôle et traitement internes.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Valeur utilisée pour le traitement interne.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Dans le CRM, cette valeur est appelée « Page du référent ».</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE-RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Une page de référent brute contient parfois tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « Page brute du référent ».</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ville résolue à partir de l’adresse IP.</p>
      </td>
      <td>
        <p>Seattle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Zone géographique résolue à partir de l’adresse IP.</p>
      </td>
      <td>
        <p>Washington</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Pays résolu à partir de l’adresse IP.</p>
      </td>
      <td>
        <p>États-Unis</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur d’accès Internet. Champ utilisé par les clients qui disposent d’un suivi géographique avancé de l’adresse IP.</p>
      </td>
      <td>
        <p>AT&amp;T U-verse</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme publicitaire sur laquelle [!DNL Marketo Measure] a pu s’appuyer pour faire aboutir une résolution. Généralement, il s’agit de l’un de nos partenaires d’intégration.</p>
      </td>
      <td>Google</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>aw.6601259029</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Market Measure Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>aw.6601259029.317738075</td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>Attribution marketing</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les groupes publicitaires n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les groupes publicitaires n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>
        <p>68035923</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>
        <p>centurylink_banner_98121</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les contenus créatifs n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les contenus créatifs n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les contenus créatifs n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les contenus créatifs n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les contenus créatifs n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les contenus créatifs n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les mots-clés n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les mots-clés n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les mots-clés n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Navigateur utilisé au cours de la session, détecté à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version du navigateur utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version de la plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue BIZ_FACTS.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_KEYWORDS {#biz-keywords}

Mots-clés importés depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du mot-clé.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365.39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du mot-clé dans le système source.</td>
      <td>
        <p>39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel le mot-clé a été importé.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel le mot-clé a été importé.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les mots-clés n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car les mots-clés n’existent pas dans la hiérarchie des impressions de Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire dont dépend le mot-clé.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire dont dépend le mot-clé.</p>
      </td>
      <td>
        <p>Affectation des recettes - B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont dépend le mot-clé.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont dépend le mot-clé.</p>
      </td>
      <td>
        <p>Affectation des recettes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le mot-clé est toujours actif dans le système source.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le mot-clé a été supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:37:29.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du mot-clé dans le système source.</p>
      </td>
      <td>
        <p>[affectation des recettes b2b]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le mot-clé doit être mis à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Mot-clé ».</p>
      </td>
      <td>
        <p>Mot-clé</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire dont dépend le mot-clé.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse URL de la page de destination.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur précédente pour URL_CURRENT.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_REQUESTED</td>
      <td>varchar</td>
      <td>
        <p>Adresse URL de la page de destination avec les paramètres [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WORD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Expression de recherche saisie par l’utilisateur.</td>
      <td>
        <p>affectation des recettes b2b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type de correspondance trouvée entre l’expression recherchée et le mot-clé.</p>
      </td>
      <td>
        <p>Exact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur utilisée pour le diagnostic interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Modèle de suivi d’URL [!DNL Marketo Measure] ajouté au mot-clé.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>-2712935512233520000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LANDING_PAGES {#biz-landing-pages}

Pages de destination importées depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la page de destination.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du compte publicitaire à partir duquel la page de destination a été importée.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du compte publicitaire à partir duquel la page de destination a été importée.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur de la page de destination, spécifiquement pour Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur de la page de destination, spécifiquement pour Doubleclick.</p>
      </td>
      <td>Marketing Analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du groupe publicitaire dont dépend la page de destination.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du groupe publicitaire dont dépend la page de destination.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant de la campagne dont dépend la page de destination.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom de la campagne dont dépend la page de destination.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de la ligne.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEADS {#biz-leads}

Prospects importés à partir du système source.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect dans le système source.</p>
      </td>
      <td>
        <p>00Q0Z00001MZcj8UAD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement correspondant au prospect dans le système source.</p>
      </td>
      <td>
        <p>2018-08-27 21:52:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de l’enregistrement correspondant au prospect dans le système source.</p>
      </td>
      <td>2018-08-27 21:52:10.000</td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du prospect dans le système source.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>WEB_SITE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Site web saisi pour le prospect dans le système source. Champ utilisé pour le mappage Lead2Account.</p>
      </td>
      <td>
        <p>adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COMPANY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la société saisi pour le prospect dans le système source. Champ utilisé pour le mappage Lead2Account.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Source ayant permis la création du prospect.</p>
      </td>
      <td>
        <p>Publicité</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CONVERTED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le prospect a été converti en contact ou non.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’opportunité associée une fois que le prospect a été converti.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle le prospect a été converti en contact.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé une fois que le prospect a été converti.</p>
      </td>
      <td>
        <p>0030Z00003Oyp25QAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte mappé. ABM doit être activé.</p>
      </td>
      <td>
        <p>0010Z0000236F9GQAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Étape actuelle du prospect. Des étapes personnalisées peuvent être créées dans l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Démo programmée</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Toutes les étapes précédentes du prospect. Des étapes personnalisées peuvent être créées dans l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>MQL</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>Algorithme [!DNL Marketo Measure] permettant d’estimer la probabilité qu’un prospect soit converti en fonction de l’âge et de l’étape.</p>
      </td>
      <td>
        <p>.290034</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_MODEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>(Ce champ n’est plus utilisé.)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_RESULTS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>(Ce champ n’est plus utilisé.)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie [!DNL Marketo Measure] utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Prérequis : valeur « true » pour l’activation du suivi des appels.</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement est supprimé du système source.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>3263982503087870000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées importées par [!DNL Marketo Measure] à partir du système source au format JSON.</td>
      <td>{"Lead_Type__c":"Vente créée", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>boolean</td>
      <td>Utilisé pour supprimer les doublons dans les enregistrements si une intégration CRM et Marketo sont configurées. Si un doublon est identifié, le prospect Marketo est marqué comme « true » (vrai).</td>
      <td>true</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indique si l’enregistrement provient d’une intégration CRM ou Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappe une personne provenant d’une intégration Marketo à un prospect issu d’une intégration CRM. Si une intégration CRM et Marketo coexistent, la valeur correspond à l’identifiant.</td>
      <td>1234</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEAD_STAGE_TRANSITIONS {#biz-lead-stage-transitions}

Transitions d’étape pour les prospects ou les contacts.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la transition.</p>
      </td>
      <td>
        <p>ST_0030Z00003FhkRXQAZ__FT-1_TP2_Person_0030Z00003FhkRXQAZ_2018-08-27:17-05-45-9474800.0d5c18c29d7b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse électronique fournie pour le prospect/contact associé.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect associé à la transition.</p>
      </td>
      <td>
        <p>00Q3100001Fx6AlEAJ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé à la transition.</p>
      </td>
      <td>
        <p>0033100003Aq9grAAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du point de contact acheteur associé à la transition.</p>
      </td>
      <td>
        <p>TP2_Person_00Q3100001Fx6AlEAJ_2018-08-28:14-41-06-1674260.d00ceb09fbd3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle l’enregistrement est passé à cette étape.</p>
      </td>
      <td>
        <p>2018-08-27 16:05:34.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur d’identifiant de l’étape correspondant à la transition.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’étape correspondant à la transition.</p>
      </td>
      <td>
        <p>FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Classement numérique de l’étape, en fonction du triage opéré dans les paramètres de mappage d’étape [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>5</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Champ utilisé par le système de traitement interne pour l’indexation et l’organisation des étapes de boomerang.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>Champ utilisé par le système de traitement interne pour l’indexation et l’organisation des étapes de boomerang.</td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le point de contact est considéré comme en attente et non fermé. Ce champ s’affiche uniquement pour les clients qui disposent d’un modèle d’attribution en chemin complet.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne est liée à une transition d’étape correspondant à un jalon. Par exemple, s’il existe 3 étapes/entrées (FT, LC, MQL) et 4 points de contact, le point de contact sans étape est considéré comme « non transitoire ». Sa valeur est alors égale à « true » (vrai).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de transition depuis l’étape précédente, en fonction de l’ordre de classement.</p>
      </td>
      <td>
        <p>2017-11-28 21:26:44.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de transition vers l’étape suivante, en fonction de l’ordre de classement.</p>
      </td>
      <td>
        <p>2017-12-11 22:39:17.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-28 15:31:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Inique si l’enregistrement de transition est considéré comme supprimé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPPORTUNITIES {#biz-opportunities}

Opportunités importées à partir du système source.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>0060Z00000o89I4QAI</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’opportunité dans le système source.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de création de l’opportunité dans le système source.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte associé.</p>
      </td>
      <td>
        <p>001i000000qbyeoAAA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>Renouvellement Marketo Measure</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’opportunité est passée à une étape considérée comme gagnante.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’opportunité est passée à une étape considérée comme terminée.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLOSE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de clôture réelle ou prévue de l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>2019-08-28 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_CUSTOM_MODEL_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>(Ce champ n’est plus utilisé.)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AMOUNT</p>
      </td>
      <td>
        <p>number(38,8)</p>
      </td>
      <td>
        <p>Montant attendu ou obtenu de l’opération faisant suite à l’opportunité dans le système source.</p>
      </td>
      <td>
        <p>8988.00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect dont la conversion a été à l’origine de cette opportunité.</p>
        <p>Notez que ce champ n’est pas défini et renvoie « null » dans Snowflake pour tous les clients.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail du prospect dont la conversion a été à l’origine de cette opportunité.</p>
        <p>Notez que ce champ n’est pas défini et renvoie « null » dans Snowflake pour tous les clients.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si le rôle de contact principal est utilisé, ce champ correspond à l’identifiant du contact principal.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si le rôle de contact principal est utilisé, ce champ correspond à l’adresse e-mail du contact principal.</p>
      </td>
      <td>
        <p>personb@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>Algorithme [!DNL Marketo Measure] permettant d’estimer la probabilité qu’une opportunité aboutisse en fonction de l’âge et de l’étape.</p>
      </td>
      <td>
        <p>0.8225108385086060000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Étape actuelle de l’opportunité, telle que définie dans l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Démo DM</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Chaîne contenant toutes les étapes précédentes de l’opportunité, comme défini dans l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Découverte qualifiée, Démonstration planifiée</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’enregistrement est supprimé du système source.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ISO_CODE</td>
      <td>varchar</td>
      <td>Code ISO de la devise, importé à partir du système source.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valeur d’identifiant de la devise pour l’enregistrement.</td>
      <td>4609512587744160000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées importées par [!DNL Marketo Measure] à partir du système source au format JSON.</td>
      <td>{"Opportunity_Location__c":"Seattle", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPP_STAGE_TRANSITIONS {#biz-opp-stage-transitions}

Transitions d’étape pour les opportunités.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la transition.</p>
      </td>
      <td>
        <p>ST_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_Demo Scheduled-1_BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte associé à l’opportunité.</p>
      </td>
      <td>
        <p>0013100001b44nTAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’opportunité associée à la transition.</p>
      </td>
      <td>
        <p>0060Z00000nEgjlQAC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé à la transition.</p>
      </td>
      <td>
        <p>0030Z00003IjojKQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse électronique fournie pour le contact associé.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du point de contact d’attribution acheteur associé à la transition.</p>
      </td>
      <td>
        <p>BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle l’enregistrement est passé à cette étape.</p>
      </td>
      <td>
        <p>2018-05-26 07:29:43.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’étape correspondant à la transition.</p>
      </td>
      <td>
        <p>Démo programmée</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur d’identifiant de l’étape correspondant à la transition.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Classement numérique de l’étape, en fonction du triage opéré dans les paramètres de mappage d’étape [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Champ utilisé par le système de traitement interne pour l’indexation et l’organisation des étapes de boomerang.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Champ utilisé par le système de traitement interne pour l’indexation et l’organisation des étapes de boomerang.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le point de contact est considéré comme en attente et non fermé. Ce champ s’affiche uniquement pour les clients qui disposent d’un modèle d’attribution en chemin complet.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la ligne est liée à une transition d’étape correspondant à un jalon. Par exemple, s’il existe 3 étapes/entrées (FT, LC, MQL) et 4 points de contact, le point de contact sans étape est considéré comme « non transitoire ». Sa valeur est alors égale à « true » (vrai).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de transition depuis l’étape précédente, en fonction de l’ordre de classement.</p>
      </td>
      <td>
        <p>2015-07-16 17:41:49.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de transition vers l’étape suivante, en fonction de l’ordre de classement.</p>
      </td>
      <td>
        <p>2018-08-27 19:40:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-28 03:53:33.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Inique si l’enregistrement de transition est considéré comme supprimé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PAGE_VIEWS {#biz-page-views}

Pages vues collectées lors de visites web. Plusieurs pages vues peuvent correspondre à une seule session.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la vue sur une page.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie enregistré au moment où la page vue a été consignée.</p>
      </td>
      <td>
        <p>277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Premier cookie correspondant à l’identifiant visiteur.</p>
      </td>
      <td>
        <p>v_277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de session associé à la page vue.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de consultation de la page.</p>
      </td>
      <td>
        <p>2018-08-19 16:49:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-19 16:55:37.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL de la page vue, sans paramètres de requête.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL de la page vue, avec les paramètres de requête.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo?hsCtaTracking=207219e9-87b6-4105-8f4b-0a3b62ae1af8%7C48060522-3aeb-4c72-8ce5-fd4b1017f069</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au moment où le formulaire a été envoyé.</p>
      </td>
      <td>
        <p>174 127 184 158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique le type d’événement.</td>
      <td>
        <p>PageView</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Appareil et navigateur enregistrés au moment de l’envoi du formulaire.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (X11; Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Indique l’ordre dans lequel l’événement de page vue s’est déroulé au cours de la session.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour contrôle et traitement internes.</td>
      <td>
        <p>103532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Valeur utilisée pour le traitement interne.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL d’où provient la page vue, sans paramètres de requête.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL d’où provient la page vue, avec les paramètres de requête.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU%20-%20CMO%20JT&amp;utm_content=CMOs%20Guide&amp;utm_term=lisu05091601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Titre de la page.</p>
      </td>
      <td>
        <p>Téléchargement du guide du CMO pour l’attribution marketing B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail fournie dans un formulaire, capturée dans le code JavaScript.</p>
      </td>
      <td>personne@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Clé étrangère de la table d’URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Clé étrangère de la table d’URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>HAS_USER_CONSENT</td>
      <td>boolean</td>
      <td>Indique si l’utilisateur a consenti au suivi. La valeur « false » signifie que la page vue a été collectée car le consentement de l’utilisateur n’est pas nécessaire. La valeur « true » signifie que la page vue a été collectée et que l’utilisateur a donné son consentement au suivi.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PLACEMENTS {#biz-placements}

Cette table stocke tous les emplacements téléchargés à partir de n’importe quel compte publicitaire connecté. Cet objet provient de l’intégration Doubleclick.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de l’emplacement.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant de l’emplacement dans le système source.</td>
      <td>10426699711</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel l’emplacement a été importé.</p>
      </td>
      <td>fb. 106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel l’emplacement a été importé.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur de l’emplacement, spécifiquement pour Doubleclick.</p>
      </td>
      <td>300184624</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur de l’emplacement, spécifiquement pour Doubleclick.</p>
      </td>
      <td>[!DNL Marketo Measure] Analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus de l’emplacement.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus de l’emplacement.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont dépend l’emplacement.</p>
      </td>
      <td>ba.3284209.132855866</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont dépend l’emplacement.</p>
      </td>
      <td>Pipeline Marketing</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’emplacement est toujours actif dans le système source.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’emplacement a été supprimé du système source.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement dans le système source.</p>
      </td>
      <td>Marché</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’emplacement doit être mis à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Emplacement ».</p>
      </td>
      <td>Emplacement</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire dont dépend l’emplacement.</p>
      </td>
      <td>BingAds</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de suppression de l’enregistrement dans Snowflake, le cas échéant.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENTS {#biz-segments}

Valeurs des segments, telles que définies dans l’application [!DNL Marketo Measure].

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du segment.</p>
      </td>
      <td>
        <p>Nouvelle entreprise</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du segment.</p>
      </td>
      <td>
        <p>Nouvelle entreprise</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENT_NAMES {#biz-segment-names}

Mappe le nom du segment personnalisé avec la valeur de sa catégorie. (Mappe les noms de colonne aux en-têtes Category1 à Category15 trouvés dans la table des points de contact.)

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>CATEGORY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indique la catégorie à laquelle le nom du segment est mappé.</p>
      </td>
      <td>
        <p>CategoryOne</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2022-02-28 18:12:35.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEGMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du segment mappé à la catégorie.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>boolean</td>
      <td>Indique si la catégorie est en cours d’utilisation.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Indique si l’enregistrement est supprimé.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SESSIONS {#biz-sessions}

Sessions traitées à partir des pages vues. Plusieurs pages vues peuvent constituer une session, et un identifiant visiteur unique peut être associé à plusieurs sessions.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la session.</p>
      </td>
      <td>
        <p>2016-08-01:14-24-21-9079480.33163948f0a3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Premier cookie correspondant à l’identifiant visiteur.</p>
      </td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du cookie enregistré au cours de la session.</p>
      </td>
      <td>277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de la session.</p>
      </td>
      <td>
        <p>2016-08-01 14:24:21.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-09-01 03:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>IS_FIRST_SESSION</td>
      <td>boolean</td>
      <td>Indique s’il s’agit de la première session correspondant à cet identifiant visiteur.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal attribué à la session, tel que défini par les définitions de canal dans l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Référencement payant.AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la page web.</p>
      </td>
      <td>
        <p>Salesforce Google Analytics | [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL de la première page vue au cours de la session, sans paramètres de requête.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL de la première page vue au cours de la session, avec les paramètres de requête.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics?_bt=83558988035&amp;_bk=google%20analytics%20salesforce&amp;_bm= p&amp;gclid=CMvd5YTLo84CFUI9gQodd-kLEQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL de départ de la session, sans paramètres de requête.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL de départ de la session, avec les paramètres de requête.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la page du référent.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour lancer la recherche qui lui a permis d’atteindre le site web.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] google salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur utilisée pour définir la source qui a été à l’origine de la session. Cette valeur peut être issue d’une analyse de l’URL contenue dans utm_source ou définie sur un fournisseur publicitaire si [!DNL Marketo Measure] peut résoudre une publicité.</p>
      </td>
      <td>
        <p>Google AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_FORM</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la session contient un remplissage de formulaire.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CHAT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la session contient une discussion par messagerie instantanée.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_EMAIL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la session contient une adresse e-mail.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CRM_ACTIVITY</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si la session provient ou non d’un enregistrement d’activité CRM.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DEVICE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Navigateur et système d’exploitation de l’utilisateur au cours de la session.</p>
      </td>
      <td>
        <p>Chrome (65.0), Windows (6.1)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme publicitaire sur laquelle [!DNL Marketo Measure] a pu s’appuyer pour faire aboutir une résolution. Généralement, il s’agit de l’un de nos partenaires d’intégration.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur à partir duquel la publicité a été résolue. Ce champ est spécifique aux connexions Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur à partir duquel la publicité a été résolue. Ce champ est spécifique aux connexions Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du site dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’emplacement dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dans laquelle la publicité a été résolue.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dans laquelle la publicité a été résolue.</p>
      </td>
      <td>
        <p>Webinaire de planification budgétaire</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>
        <p>Salesforce - Google Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la publicité résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>aw.6601259029.321586235.23182235435</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la publicité résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>Winter Promo - Green</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contenu créatif dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.83558988035</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du contenu créatif dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Intégration GA et Salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Première ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Intégrez Salesforce et Analytics pour</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Deuxième ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Optimiser les recettes. Suivez notre guide.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Page de destination vers laquelle pointe l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse URL conviviale affichée sur l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>adobe.com/Salesforce-for-GA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du mot-clé dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.35934468937</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du mot-clé dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>google analytics salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type de correspondance trouvée entre l’expression recherchée et le mot-clé acheté.</p>
      </td>
      <td>
        <p>Expression</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur provenant d’une analyse de l’URL contenue dans utm_campaign.</p>
      </td>
      <td>
        <p>SU - Comptes ABC - Compétences paid media</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur provenant d’une analyse de l’URL contenue dans utm_source.</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur provenant d’une analyse de l’URL contenue dans utm_medium.</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TERM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur provenant d’une analyse de l’URL contenue dans utm_term.</p>
      </td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur provenant d’une analyse de l’URL contenue dans utm_content.</p>
      </td>
      <td>
        <p>Rapport de référence AdWords 2016</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ville résolue à partir de l’adresse IP.</p>
      </td>
      <td>Vancouver</td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Zone géographique résolue à partir de l’adresse IP.</p>
      </td>
      <td>Colombie-Britannique</td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Pays résolu à partir de l’adresse IP.</p>
      </td>
      <td>Canada</td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Fournisseur d’accès Internet de l’utilisateur.</p>
      </td>
      <td>
        <p>AT&amp;T U-verse</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au cours de la session.</p>
      </td>
      <td>
        <p>174 127 184 158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Détermine si cette session a été fusionnée avec une autre et doit être supprimée.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITES {#biz-sites}

Sites importés depuis n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du site.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du site dans le système source.</td>
      <td>39464932147</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire à partir duquel le site a été importé.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire à partir duquel le site a été importé.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur du site, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur du site, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus du site.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Cette valeur doit normalement être nulle, car aucune hiérarchie publicitaire ne met le groupe publicitaire au-dessus du site.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne dont dépend le site.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne dont dépend le site.</p>
      </td>
      <td>Affectation des recettes</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le site est toujours actif dans le système source.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le site a été supprimé du système source.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de première importation de l’enregistrement à partir du système source.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site dans le système source.</p>
      </td>
      <td>Recettes</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le site doit être mis à jour pour le balisage [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé par le système de traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « Site ».</p>
      </td>
      <td>Site</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire correspondant au site.</p>
      </td>
      <td>AdWords</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITE_LINKS {#biz-site-links}

Liens de sites provenant de n’importe quel compte publicitaire connecté.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du lien du site.</p>
      </td>
      <td>
        <p>aw.6601259029.285077795.1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td>
        <p>1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire connecté correspondant au lien du site.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire connecté correspondant au lien du site.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur correspondant au lien du site, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur correspondant au lien du site, spécifiquement pour Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire correspondant au lien du site.</p>
      </td>
      <td>aw.6601259029.208548635.16750166675</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire correspondant au lien du site.</p>
      </td>
      <td>Marque - Principale</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne correspondant au lien du site.</p>
      </td>
      <td>
        <p>aw.6601259029.285077795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne correspondant au lien du site.</p>
      </td>
      <td>
        <p>Marque</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le lien du site est toujours actif dans le compte publicitaire.</p>
      </td>
      <td>
        <p>TRUE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le lien du site a été supprimé du compte publicitaire.</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de la ligne.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle le lien du site a été téléchargé pour la première fois par [!DNL Marketo Measure]</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du lien du site.</p>
      </td>
      <td>Lien A</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si le lien du site doit être mis à jour pour le balisage Marketo Measure.</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td>
        <p>aw.6601259029.285077795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Entité ou objet principal de cette table. Dans le cas présent, « SiteLink ».</p>
      </td>
      <td>
        <p>SiteLink</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur publicitaire correspondant au lien du site.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse URL de la page de destination.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td>
        <p>http://adobe.com/b2b-marketing-attribution?_bt =</p>
        <p>{creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur précédente pour URL_CURRENT.</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL qui recevra les paramètres [!DNL Marketo Measure].</p>
        <p>(Champ de diagnostic, utilisé par le système de traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de suppression de l’enregistrement dans Snowflake, le cas échéant.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_STAGE_DEFINITIONS {#biz-stage-definitions}

Liste des étapes, telles qu’importées ou définies dans l’application [!DNL Marketo Measure].

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de l’étape.</p>
      </td>
      <td>
        <p>01J3100000QE753EAD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-22 17:27:27.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’étape.</p>
      </td>
      <td>
        <p>Argumentaire</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_INACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’étape est considérée comme inactive.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IN_CUSTOM_MODEL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’étape est sélectionnée pour le suivi dans le modèle personnalisé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_BOOMERANG</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’étape est sélectionnée pour le suivi comme étape de boomerang.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_TRANSITION_TRACKING</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’étape est sélectionnée pour le suivi des transitions.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Statut de l’étape, tel que défini dans le mappage d’étape de l’application [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Ouverte</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FROM_SALESFORCE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si l’étape est importée à partir d’un système source externe.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DEFAULT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indique si l’étape est définie par défaut.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Classement numérique de l’étape, utilisé pour trier les étapes par ordre de transition.</p>
      </td>
      <td>
        <p>53</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Inique si l’étape a été supprimée.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_TOUCHPOINTS {#biz-touchpoints}

Points de contact acheteur, tous les points de contact associés à un prospect ou à un contact. Cette table sera vide si les points de contact correspondant à des prospects ou à des contacts sont désactivés.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Exemple de données</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du point de contact acheteur (BT, Buyer Touchpoint).</p>
      </td>
      <td>
        <p>TP2_Person_00Q0Z000013e2PYUAY_2018-08-27:20-04-40-5655690.1ee8567c175a</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-08-29 22:29:30.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Adresse e-mail associée au BT.</td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contact associé au BT.</p>
      </td>
      <td>0030Z00003K5bpKQAR</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte associé au BT.</p>
      </td>
      <td>
        <p>0013100001lSLScAAO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du prospect associé au BT.</p>
      </td>
      <td>
        <p>00Q0Z000013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>UNIQUE_ID_PERSON</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Enregistrement de la personne parente associée à un prospect ou à un contact.</p>
      </td>
      <td>
        <p>Person_00Q0Z000013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du point de contact de l’utilisateur qui a généré le BT.</p>
      </td>
      <td>
        <p>personne@adobe.com_2018-08-29:18-14-53-8102030.10df92cbb414</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Identifiant du visiteur associé au BT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date du point de contact.</p>
      </td>
      <td>
        <p>2018-08-27 20:04:40.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type d’activité, Visite web, Formulaire web, Chat web, Appel téléphonique, Campagne [CRM] ou Activité [CRM]. Dans le CRM, cette valeur est appelée « Type de point de contact ».</p>
      </td>
      <td>
        <p>Formulaire web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal dont dépend le point de contact, tel que défini dans les définitions de canal personnalisées dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Chemin de canal marketing ».</p>
      </td>
      <td>Social.LinkedIn</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la première catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td>ABC</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la deuxième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td>
        <p>Oui</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY3</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la troisième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td>
        <p>Autres</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY4</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la quatrième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td>
        <p>Partenaire</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY5</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la cinquième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY6</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la sixième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY7</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la septième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la huitième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la neuvième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la dixième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la onzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la douzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valeur de segment de la treizième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY14</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la quatorzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY15</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur de segment de la quinzième catégorie dont dépend le point de contact, tel que défini dans les définitions de segment dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Segments ».</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Navigateur utilisé au cours de la session, détecté à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>Chrome</td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version du navigateur utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>68</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Windows</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version de la plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>10_12</td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours de la session, première page de destination qui a généré un point de contact. Dans le CRM, cette valeur est appelée « Page de destination ».</p>
      </td>
      <td>
        <p>https://info.adobe.com/definitive-guide-to-pipeline-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours de la session, première page de destination qui a généré un point de contact. Une page de destination brute contiendra tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « Page de destination brute ».</p>
      </td>
      <td>
        <p>https://info.adpbe.com/definitive-guide-to-pipeline-marketing?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU_COM_Demand_ Skills&amp;utm_content=DGPM&amp;utm_term=lisu03151846&amp;_bl=66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Dans le CRM, cette valeur est appelée « Page du référent ».</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Une page de référent brute contient parfois tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « Page brute du référent ».</p>
      </td>
      <td>
        <p>https://www.linkedin.com/feed</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours d’une session, premier formulaire enregistré qui a généré un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans la table Touchpoints, mais plutôt dans Form_Submits. Dans le CRM, cette valeur est appelée « URL du formulaire ».</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>FORM_PAGE_RAW</td>
      <td>varchar</td>
      <td>Au cours d’une session, premier formulaire enregistré qui a généré un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans la table Touchpoints, mais plutôt dans Form_Submits. Une page de formulaire brute contient parfois tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « URL brute du formulaire ».</td>
      <td>https://info.adobe.com/demo?hsCtaTracking=98adcc2f-afe2-40c4-9d79-40dcc41663ee%7C3cfaa909-39cb-4f5d-93eb-be05de6b0180</td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date d’envoi du formulaire.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ville dans laquelle se trouvait l’utilisateur au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Zone géographique dans laquelle se trouvait l’utilisateur au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Pays dans lequel se trouvait l’utilisateur au cours de la session, détecté à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>États-Unis</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur utilisée pour définir le support qui a généré le point de contact. Cette valeur peut être issue d’une analyse de l’URL contenue dans utm_medium. Autrement, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que « cpc » ou « affichage ».</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur utilisée pour définir la source qui a généré le point de contact. Cette valeur peut être issue d’une analyse de l’URL contenue dans utm_medium, définie de manière générique (par exemple « CRM Campaign ») si elle est issue d’une synchronisation avec le CRM, ou, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que « Google AdWords » ou « Facebook ». Dans le CRM, cette valeur est appelée « Source du point de contact ».</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour lancer la recherche qui lui a permis d’atteindre le site web. En fonction des achats de mots-clés, cette valeur peut correspondre ou non aux mots-clés achetés sur la plateforme de référencement payant.</p>
      </td>
      <td>
        <p>attribution marketo measure</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme publicitaire sur laquelle [!DNL Marketo Measure] a pu s’appuyer pour faire aboutir une résolution. Généralement, il s’agit de l’un de nos partenaires d’intégration.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>li.502664737</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>MM SC 2016_14605342_3/7-3/31/16</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Marketo Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>li.502664737.138949954</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>SU - Comptes COM - Compétences à la demande</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>aw.6601259029.317738075.23105327435</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>Attribution marketing - Général</td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>Webinaire budgétaire - barre latérale</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contenu créatif correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>li.502664737.138949954.66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du contenu créatif correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Première ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Génération de prospect terminée</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Deuxième ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Téléchargez le guide définitif du marketing de pipeline : https://lnkd.in/e9xYj5M</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Page de destination vers laquelle pointe l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>https://image-store.slidesharecdn.com/d29165c0-1e0b-4ffc-a494-d2c77e7cd4a6-large.jpeg</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse URL conviviale affichée sur l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>marektomeasure.com/guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du mot-clé acheté pour le référencement payant, extrait du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>__GAId__lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du mot-clé acheté pour le référencement payant, extrait du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type de correspondance trouvée entre l’expression recherchée et le mot-clé acheté.</p>
      </td>
      <td>
        <p>Large</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme le premier du parcours d’opportunité.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme celui étant à l’origine de la création du prospect dans le parcours d’opportunité.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme celui étant à l’origine de la création de l’opportunité dans le parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la conclusion du parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>STAGES_TOUCHED</td>
      <td>varchar</td>
      <td>Ce champ n’est plus utilisé. Pour obtenir des informations sur les étapes, utilisez les tables Stage_Transitions.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact s’est soldé par un remplissage de formulaire au cours de la session.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme le premier contact d’impression du parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit du premier (voir Is_First_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit du point à l’origine de la création du prospect (voir Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un point en U (voir Is_First_Touch et Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un point en W (voir Is_First_Touch, Is_Lead_Creation_Touch et Is_Opp_Creation_Touch). Cette valeur doit être égale à 0, car elle se réfère à un BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle en chemin complet (voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch et Is_Closed_Touch). Cette valeur doit être égale à 0, car elle se réfère à un BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_MODEL_PERCENTAGE</td>
      <td>number(22,19)</td>
      <td>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle personnalisé (voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch et Is_Closed_Touch). Cette valeur doit être égale à 0, car elle se réfère à un BT.</p>
      </td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est supprimé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>-9004910726709710000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_URLS {#biz-urls}

Agrégation des URL correspondant aux pages de destination, aux pages du référent et aux pages vues.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL complète.</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/strategic-marketing-plangoals</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SCHEME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Communication sécurisée de la page web sur le réseau.</p>
      </td>
      <td>
        <p>https</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HOST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Domaine de l’URL, avec tous les sous-domaines.</p>
      </td>
      <td>
        <p>www.adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PORT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Port d’un hôte Internet, facultatif dans une URL.</p>
      </td>
      <td>
        <p>584</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PATH</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Partie de l’URL qui pointe vers un emplacement spécifique sur l’hôte.</p>
      </td>
      <td>
        <p>/blog/strategic-marketing-plangoals</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Clé étrangère de la vue Biz_Facts.</p>
      </td>
      <td>
        <p>5686109553536636820</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_USER_TOUCHPOINTS {#biz-user-touchpoints}

Tous les points de contact créés à partir de n’importe quel événement lié à un e-mail.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du point de contact utilisateur.</p>
      </td>
      <td>
        <p>personne@adobe.com_2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-09-05 23:30:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse e-mail associée au point de contact utilisateur.</p>
      </td>
      <td>
        <p>personne@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la session à l’origine du point de contact utilisateur.</p>
      </td>
      <td>
        <p>2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_MEMBER_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du membre de la campagne à l’origine du point de contact utilisateur.</p>
      </td>
      <td>
        <p>00v0Z00001VTgv1QAD</p>
      </td>
    </tr>
    <tr>
      <td>CRM_ACTIVITY_ID</td>
      <td>varchar</td>
      <td>Identifiant de l’activité à l’origine du point de contact utilisateur.</td>
      <td>1678625515</td>
    </tr>
    <tr>
      <td>
        <p>CRM_EVENT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’événement à l’origine du point de contact utilisateur.</p>
      </td>
      <td>
        <p>00U0Z00000pCZmyUAG</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CRM_TASK_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la tâche à l’origine du point de contact utilisateur.</p>
      </td>
      <td>
        <p>00T0Z00004Qbd1jUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’impression à l’origine du point de contact utilisateur.</p>
      </td>
      <td>00T0Z00004Qbd1jUAB</td>
    </tr>
    <tr>
      <td>IS_FIRST_KNOWN_TOUCH</td>
      <td>boolean</td>
      <td>Indique si ce point de contact est traité comme le premier du parcours d’opportunité.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Identifiant du premier cookie correspondant à l’identifiant visiteur.</td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date à laquelle le point de contact utilisateur s’est produit.</p>
      </td>
      <td>
        <p>2018-01-05 16:47:02.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type d’activité, Visite web, Formulaire web, Chat web, Appel téléphonique, Campagne [CRM] ou Activité [CRM]. Dans le CRM, cette valeur est appelée « Type de point de contact ».</p>
      </td>
      <td>
        <p>Formulaire web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal dont dépend le point de contact, tel que défini dans les définitions de canal personnalisées dans l’application [!DNL Marketo Measure]. Dans le CRM, cette valeur est appelée « Chemin de canal marketing ».</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Navigateur utilisé au cours de la session, détecté à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Firefox</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version du navigateur utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>33</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Version de la plateforme utilisée au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours de la session, première page de destination qui a généré un point de contact. Dans le CRM, cette valeur est appelée « Page de destination ».</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours de la session, première page de destination qui a généré un point de contact. Une page de destination brute contiendra tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « Page de destination brute ».</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing?utm_source=feedburner&amp;utm_medium=feed&amp;utm_campaign=Feed%3A+ marketo+%maeasure%27s+Pipeline+Marketing+Blog%29</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Dans le CRM, cette valeur est appelée « Page du référent ».</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En règle générale, il s’agit de la page de destination externe sur laquelle l’utilisateur se trouvait juste avant d’accéder au site web. Une page de référent brute contient parfois tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « Page brute du référent ».</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours d’une session, premier formulaire enregistré qui a généré un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans la table Attribution_Touchpoints, mais plutôt dans Form_Submits. Dans le CRM, cette valeur est appelée « URL du formulaire ».</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Au cours d’une session, premier formulaire enregistré qui a généré un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans la table Attribution_Touchpoints, mais plutôt dans Form_Submits. Une page de formulaire brute contient parfois tous les paramètres de requête dans l’URL. Dans le CRM, cette valeur est appelée « URL brute du formulaire ».</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation?utm_source=linkedin&amp;utm_medium=paid&amp;utm_content=sfskill&amp;utm _campaign=Content%20-%20AdWords%20Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date d’envoi du formulaire.</p>
      </td>
      <td>
        <p>2015-06-03 17:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ville dans laquelle se trouvait l’utilisateur au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Oakland</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Zone géographique dans laquelle se trouvait l’utilisateur au cours de la session, détectée à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>Californie</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Pays dans lequel se trouvait l’utilisateur au cours de la session, détecté à l’aide du JavaScript et de l’adresse IP.</p>
      </td>
      <td>
        <p>États-Unis</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur utilisée pour définir le support qui a généré le point de contact. Cette valeur peut être issue d’une analyse de l’URL contenue dans utm_medium. Autrement, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que « cpc » ou « affichage ».</p>
      </td>
      <td>
        <p>référencement payant</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur utilisée pour définir la source qui a généré le point de contact. Cette valeur peut être issue d’une analyse de l’URL contenue dans utm_medium, définie de manière générique (par exemple « CRM Campaign ») si elle est issue d’une synchronisation avec le CRM, ou, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que « Google AdWords » ou « Facebook ». Dans le CRM, cette valeur est appelée « Source du point de contact ».</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour lancer la recherche qui lui a permis d’atteindre le site web. En fonction des achats de mots-clés, cette valeur peut correspondre ou non aux mots-clés achetés sur la plateforme de référencement payant.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Plateforme publicitaire sur laquelle [!DNL Marketo Measure] a pu s’appuyer pour faire aboutir une résolution. Généralement, il s’agit de l’un de nos partenaires d’intégration.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Compte</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne correspondant au compte publicitaire dans lequel la publicité a été résolue.</p>
      </td>
      <td>
        <p>Marque</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du groupe publicitaire correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement à Google AdWords.</p>
      </td>
      <td>
        <p>Marque - Principale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la publicité correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable uniquement au gestionnaire de campagne Doubleclick et à Facebook (affichage).</p>
      </td>
      <td>Webinaire budgétaire - barre latérale</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du contenu créatif correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675.195329631298</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du contenu créatif correspondant au compte publicitaire dans lequel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Site officiel</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Première ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Planification et affectation des recettes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Deuxième ligne du contenu créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Découvrez pourquoi plus de 250 entreprises choisissent [!DNL Marketo Measure] pour leur attribution marketing. Essayez par vous-même avec notre version de démonstration !</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Page de destination vers laquelle pointe l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>http://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse URL conviviale affichée sur l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du mot-clé acheté pour le référencement payant, extrait du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675.46267805426</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du mot-clé acheté pour le référencement payant, extrait du compte publicitaire à partir duquel la publicité a été résolue. Applicable à Google AdWords et à Bing Ads (recherche).</p>
      </td>
      <td>
        <p>[marketo]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Type de correspondance trouvée entre l’expression recherchée et le mot-clé acheté.</p>
      </td>
      <td>
        <p>Exact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact s’est soldé par un remplissage de formulaire au cours de la session.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme le premier contact d’impression du parcours d’opportunité.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Inique si le point de contact est supprimé.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>Clé étrangère de la vue Biz_Facts.</td>
      <td>-5269090762570690000</td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_WEB_HOST_MAPPINGS {#biz-web-host-mappings}

Table de mappage permettant de faire correspondre l’ID de session [!DNL Marketo Measure] avec l’ECID Adobe et l’identifiant Munchkin.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonne</p>
      </th>
      <th>
        <p>Type de données</p>
      </th>
      <th>
        <p>Description</p>
      </th>
      <th>
        <p>Exemple de données</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant unique de l’enregistrement de mappage.</td>
      <td>
        <p>0d643578c0c74753eff91abe668ed328|2020-06-17:19:03:36|0002|0|568668</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant de cookie enregistré pour [!DNL Marketo Measure].</td>
      <td>0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du premier cookie correspondant à l’identifiant visiteur.</td>
      <td>v_0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant de session [!DNL Marketo Measure].</td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>Date d’enregistrement du mappage.</td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date de dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE</td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL de la page vue, sans paramètres de requête.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_RAW</td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL de la page vue, avec les paramètres de requête.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html?x=nGfrBF&amp;utm_medium=cpc&amp;utm_source=intensify</p>
      </td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Adresse IP enregistrée.</td>
      <td>
        <p>159 203 142 127</p>
      </td>
    </tr>
    <tr>
      <td>TYPE</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique le type d’événement.</td>
      <td>
        <p>HostMapping</p>
      </td>
    </tr>
    <tr>
      <td>USER_AGENT_STRING</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Appareil et navigateur enregistrés au moment de l’événement de page vue.</td>
      <td>
        <p>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36</p>
      </td>
    </tr>
    <tr>
      <td>CLIENT_SEQUENCE</td>
      <td>varchar</td>
      <td>Indique l’ordre dans lequel l’événement de page vue s’est déroulé au cours de la session.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>CLIENT_RANDOM</td>
      <td>varchar</td>
      <td>Utilisé pour contrôle et traitement internes.</td>
      <td>566868</td>
    </tr>
    <tr>
      <td>IS_DUPLICATED</td>
      <td>boolean</td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_PROCESSED</td>
      <td>boolean</td>
      <td>Valeur utilisée pour le traitement interne.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>MAPPING_TYPE</td>
      <td>varchar</td>
      <td>Type d’identifiant mappé à l’identifiant de cookie [!DNL Marketo Measure].</td>
      <td>Adobe_OrgId_Ecid</td>
    </tr>
    <tr>
      <td>MAPPING_ORD_ID</td>
      <td>varchar</td>
      <td>Identifiant d’organisation Adobe IMS.</td>
      <td>8CC867C25245ADC30A490D4C</td>
    </tr>
    <tr>
      <td>MAPPING_COOKIE_ID</td>
      <td>varchar</td>
      <td>ECID Adobe pour l’identifiant d’organisation donné.</td>
      <td>09860926390077352923264316157493772857</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification de l’enregistrement dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été marqué comme supprimé dans Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

## Exemples de requêtes {#sample-queries}

**Combien de points de contact acheteur (BT) y a-t-il pour chaque canal/sous-canal le mois dernier ?**

```
--Note: This query can quickly be modified to show Buyer Attribution Touchpoint (BAT) counts by switching the biz_touchpoints table to the biz_attribution_touchpoints table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,trim(split(ch.name,'.')[1])  as subchannel
      ,count(bt.id)                 as buyer_touchpoint_count
  from biz_user_touchpoints     ut
       left outer join
       biz_touchpoints          bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_channels             ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
   and ut.touchpoint_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
group by 1,2
```

**Quel est le montant des recettes attribuées pour chaque canal le mois dernier, pour le modèle d’attribution en chemin complet ?**

```
--Note: This query does not perform any currency conversion.  If your data contains multiple currencies, you will need to add in logic to perform the conversion to the desired currency using the biz_conversion_rates table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,sum(opp.amount*(bat.full_path_percentage/100))   as attributed_revenue
  from biz_user_touchpoints         ut
       inner join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       inner join
       biz_opportunities            opp
        on bat.opportunity_id       = opp.id
       and opp._deleted_date        is null
       and opp.is_closed            = true
       and opp.is_won               = true
       and opp.close_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
       left outer join
       biz_channels                 ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
group by 1
```

**Quel est le parcours complet d’une personne spécifique ? (Afficher tous les points de contact pour une adresse e-mail unique.)**

```
select ut.touchpoint_date
      ,ut.marketing_touch_type
      ,listagg(distinct ifnull(sdl.stage_name,sdo.stage_name),',')           as touchpoint_position
  from biz_user_touchpoints         ut
       left outer join
       biz_touchpoints              bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       left outer join
       biz_lead_stage_transitions   lst
        on lst.touchpoint_id        = bt.id
       and lst._deleted_date        is null
       and lst.is_pending           = false
       and lst.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdl
        on lst.stage_id             = sdl.id
       and sdl._deleted_date        is null
       left outer join
       biz_opp_stage_transitions    ost
        on ost.touchpoint_id        = bat.id
       and ost._deleted_date        is null
       and ost.is_pending           = false
       and ost.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdo
        on ost.stage_id             = sdo.id
       and sdo._deleted_date        is null
 where ut._deleted_date     is null
   and ut.email             = [email address]
group by 1,2
order by 1
```

**Afficher tous les points de contact d’attribution acheteur et leurs recettes attribuées pour une opportunité unique.**

>[!NOTE]
>
>Cette requête renvoie les recettes attribuées pour le modèle w de forme. Modifiez le modèle en mettant à jour le champ dans le calcul des recettes attribuées.

```
select bat.id
      ,bat.touchpoint_date
      ,bat.email
      ,opp.amount*(bat.w_shape_percentage/100)             as attributed_revenue
      ,listagg(osd.stage_name,', ')                        as touchpoint_position
  from biz_opportunities               opp
       inner join
       biz_attribution_touchpoints     bat
        on bat.opportunity_id      = opp.id
       and bat._deleted_date       is null
       left outer join
       biz_opp_stage_transitions       ost
        on ost.touchpoint_id       = bat.id
       and ost._deleted_date       is null
       and ost.is_pending          = false
       and ost.is_non_transitional = false
       left outer join
       biz_stage_definitions            osd
        on ost.stage_id             = osd.id
       and osd._deleted_date        is null
 where opp._deleted_date    is null
   and opp.id               = [opportunity id]
group by 1,2,3,4
order by touchpoint_date
```

[Revenir en haut de la page](#data-warehouse-schema)
