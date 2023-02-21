---
unique-page-id: 35586140
description: Schéma du Data Warehouse - Marketo Measure - Documentation du produit
title: Schéma du Data Warehouse
exl-id: f1895eb1-a32d-4c43-93fb-0aa838527946
source-git-commit: 6e2d438da273511c3465d02eef6813f64e7aec5d
workflow-type: tm+mt
source-wordcount: '22615'
ht-degree: 6%

---

# Schéma du Data Warehouse {#data-warehouse-schema}

Data Warehouse vous permet d’effectuer le suivi de votre choix, de créer des rapports sur vos données d’attribution où vous le souhaitez et de les connecter à d’autres jeux de données.

>[!IMPORTANT]
>
>Les lignes dont la valeur est _DELETED_DATE sont conservées pendant 15 jours, puis supprimées du Snowflake. Les fuseaux horaires Snowflake sont en UTC.

>[!NOTE]
>
>[Cliquez ici](#sample-queries) pour afficher des exemples de requêtes au bas de cet article.

## Diagrammes de relation d’entité {#entity-relationship-diagrams}

Le _Modèle de données Data Warehouse_ L’outil ERD indique comment les données de l’entrepôt de données sont destinées à s’enchaîner et à être liées. Ce diagramme n’inclut pas toutes les tables disponibles dans l’entrepôt de données, car certaines d’entre elles représentent des tables de mappage, des vues d’autres tables déjà présentes ou des tables obsolètes que nous vous déconseillons d’utiliser. Consultez les descriptions détaillées des tableaux et colonnes présents dans l’entrepôt de données ci-dessous. La plupart de ces tableaux contiennent des champs dénormalisés. Cependant, ce diagramme est le modèle de données recommandé, en exploitant plutôt les données des tableaux dimensionnels.

Le supplément _Modèle de données Dimensionnel Publicités_ ERD présente une vue de la meilleure façon de lier les tableaux pour les dimensions spécifiques aux publicités aux tableaux dans le modèle de données principal. Bien que les dimensions publicitaires soient également dénormalisées dans d’autres tableaux, cela représente le modèle recommandé pour joindre ces dimensions.

_Cliquez sur une image pour sa version agrandie_

<table style="table-layout:auto"> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><strong>Modèle de données Data Warehouse</strong></td> 
   <td><strong>Modèle de données Dimensionnel Publicités</strong></td> 
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

## Affichages {#views}

### BIZ_ACCOUNTS {#biz-accounts}

Comptes importés du système source.

<table>
  <tbody>
    <tr>
      <th><strong>Colonne</strong></th>
      <th><strong>Type de données</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Données d’exemple</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Identifiant de compte du système source.</td>
      <td>0013100001kpAZxAAM</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création du Compte, à partir du système source.</td>
      <td>2016-08-28 00:32:55.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de dernière modification du compte, à partir du système source.</td>
      <td>2018-08-01 17:38:30.000</td>
    </tr>
    <tr>
      <td>NOM</td>
      <td>varchar</td>
      <td>Nom du compte, à partir du système source.</td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>WEB_SITE</td>
      <td>varchar</td>
      <td>Site web du compte, tel qu’il est enregistré dans le système source, utilisé pour la mise en correspondance de piste vers compte.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_RATING</td>
      <td>varchar</td>
      <td>Une note de lettre (A, B, C, D, N/A) générée à partir de la variable [!DNL Marketo Measure] Modèle d’apprentissage automatique. Cette valeur est nulle si ABM est désactivé.</td>
      <td>B</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_SCORE</td>
      <td>number(38,19)</td>
      <td>Score numérique calculé par [!DNL Marketo Measure] Apprentissage automatique pour générer le score d’engagement prédictif (Engagement_Rating). Cette valeur est nulle si ABM est désactivé.</td>
      <td>0.1417350147058800000</td>
    </tr>
    <tr>
      <td>DOMAINE</td>
      <td>varchar</td>
      <td>Version analysée du site web, qui stocke uniquement le domaine.</td>
      <td>adobe</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booléenne</td>
      <td>Si l’enregistrement est supprimé ou non dans le système source.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées qui [!DNL Marketo Measure] a été importé à partir du système source, au format JSON.</td>
      <td>{"Account_Type__c": "Security", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Table de mappage entre les adresses email de prospect/contact connues et les comptes. Cette table sera vide si ABM est désactivé.

<table>
  <tbody>
    <tr>
    <th><strong>Colonne</strong></th>
      <th><strong>Type de données</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Données d’exemple</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Identifiant unique de l’enregistrement.</td>
      <td>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13 000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID du compte du système source.</p>
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
        <p>Adresse électronique qui a été mappée au compte, soit par le biais des relations de contact, soit par le mappage "prospect vers compte".</p>
      </td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Date de dernière modification du compte, à partir du système source.</p>
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
        <p>Date de création du Compte, à partir du système source.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement est considéré comme supprimé ou non.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
    <th><strong>Données d’exemple</strong></th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID d’activité du système source.</p>
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
        <p>Identifiant du type d’activité, à partir du système source.</p>
      </td>
      <td>
        <p>104</p>
      </td>
    </tr>
    <tr>
      <td>ACTIVITY_TYPE_NAME</td>
      <td>varchar</td>
      <td>Nom de l’activité, depuis le système source.</td>
      <td>
        <p>changement d’état en progression</p>
      </td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de début de l’activité, à partir du système source.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestapm_ntz</td>
      <td>Date de fin de l’activité, à partir du système source.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>CAMPAIGN_ID</td>
      <td>varchar</td>
      <td>Identifiant de la campagne dont fait partie l’activité, à partir du système source.</td>
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
      <td>Date de la dernière modification de la ligne dans le système source.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IS_DELETD</td>
      <td>booléenne</td>
      <td>si l’enregistrement est considéré comme supprimé dans le système source.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>AD_FORM_ID</td>
      <td>varchar</td>
      <td>Identifiant du formulaire de publicité dont fait partie l’activité, à partir du système source.</td>
      <td>li.507063119.3757704</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
        <p><strong>Données d’exemple</strong></p>
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
        <p>Identifiant de publicité du système source.</p>
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
        <p>Identifiant de l’annonceur pour la publicité, en particulier pour Doubleclick.</p>
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
        <p>Nom de l’annonceur pour la publicité, en particulier pour Doubleclick.</p>
      </td>
      <td>
        <p>Analyses marketing</p>
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
        <p>Identifiant du groupe publicitaire pour la publicité.</p>
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
        <p>Nom du groupe publicitaire pour la publicité.</p>
      </td>
      <td>
        <p>Visionneuse de publicités pour la publicité B</p>
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
        <p>Identifiant de la campagne pour la publicité.</p>
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
        <p>Nom de la campagne pour la publicité.</p>
      </td>
      <td>
        <p>Campagne de génération de pistes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la publicité est toujours principale ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la publicité a été supprimée ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la publicité, à partir du système source.</p>
      </td>
      <td>
        <p>Publicité 2</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la publicité doit être mise à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé par le traitement interne.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Publicité".</p>
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
        <p>Nom du fournisseur de publicités pour la publicité.</p>
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
        <p>URL de la landing page.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>L’URL qui sera décorée [!DNL Marketo Measure] paramètres.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>Importé à partir du système source.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Publicitaires importés depuis n’importe quel compte publicitaire connecté.

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
        <p>Données d’exemple</p>
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
      <td>Identifiant publicitaire du système source.</td>
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
        <p>Identifiant de l’annonceur, en particulier pour Doubleclick.</p>
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
        <p>Nom de l’annonceur, en particulier pour Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Analyses marketing</p>
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
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de l’annonceur dans une hiérarchie d’annonces.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de l’annonceur dans une hiérarchie d’annonces.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Être nul, puisqu’il n’y a aucune campagne publicitaire au-dessus de l’annonceur dans une hiérarchie de publicités.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Être nul, car il n’y a aucune campagne au-dessus de l’annonceur publicitaire dans une hiérarchie d’annonces.</p>
      </td>
      <td>
        <p>nul</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Que l’annonceur soit ou non encore principal dans le système source.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’annonceur a été supprimé dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’annonceur, à partir du système source.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Analyses marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’annonceur doit être mis à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé par le traitement interne.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Annonceur".</p>
      </td>
      <td>
        <p>Publicitaire</p>
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
        <p>Fournisseur d’annonces publicitaires pour l’annonceur.</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
        <p>Données d’exemple</p>
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
      <td>Identifiant du compte publicitaire du système source.</td>
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
      <td>La valeur est attendue comme nulle puisqu’il s’agit de l’enregistrement pour les comptes publicitaires dans la hiérarchie des publicités.</td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur est attendue comme nulle puisqu’il s’agit de l’enregistrement pour les comptes publicitaires dans la hiérarchie des publicités.</td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’y a aucun annonceur au-dessus des comptes publicitaires dans une hiérarchie de publicités.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’y a aucun annonceur au-dessus des comptes publicitaires dans une hiérarchie de publicités.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur est attendue comme nulle puisqu’il n’y a aucun groupe publicitaire au-dessus des comptes publicitaires dans n’importe quelle hiérarchie publicitaire.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur est attendue comme nulle puisqu’il n’y a aucun groupe publicitaire au-dessus des comptes publicitaires dans n’importe quelle hiérarchie publicitaire.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur est attendue comme nulle puisqu’il n’y a aucune campagne publicitaire au-dessus des comptes publicitaires dans n’importe quelle hiérarchie publicitaire.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur est attendue comme nulle puisqu’il n’y a aucune campagne publicitaire au-dessus des comptes publicitaires dans n’importe quelle hiérarchie publicitaire.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le compte publicitaire est toujours principal ou non dans le système source.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le compte publicitaire a été supprimé ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du compte publicitaire, provenant du système source.</td>
      <td>
        <p>[!DNL Marketo Measure] Compte publicitaire</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’annonceur doit être mis à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé par le traitement interne.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Compte".</p>
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
        <p>Nom du fournisseur de publicités pour le compte publicitaire.</p>
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
        <p>Code de devise utilisé pour le compte publicitaire, à partir du système source.</p>
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
      <td>Utilisé pour le traitement interne.</td>
      <td>1933789</td>
    </tr>
    <tr>
      <td>
        <p>SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Analysé à partir de l’URL de utm_source.</td>
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
      <td>Analysé à partir de l’URL de utm_medium.</td>
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
        <p>Montant des dépenses importées au cours des 30 derniers jours, applicable uniquement à AdWords.</p>
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
        <p>Nombre d’impressions des 30 derniers jours, applicable uniquement à AdWords.</p>
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
        <p>Nombre de clics des 30 derniers jours, applicable uniquement à AdWords.</p>
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
        <p>Nombre de conversions signalé au cours des 30 derniers jours, applicable uniquement à AdWords.</p>
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
      <td>Utilisé pour les diagnostics internes.</td>
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
      <td>Utilisé pour les diagnostics internes.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
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
        <p>Le modèle de suivi ajouté au niveau du compte publicitaire pour AdWords ou Bing pour le balisage des landing pages.</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Campagnes importées à partir des comptes publicitaires, des systèmes sources, de l’utm et des rapports automatiques connectés.

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
        <p>Données d’exemple</p>
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
      <td>Identifiant de campagne du système source.</td>
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
        <p>Identifiant de l’annonceur pour la campagne, en particulier pour Doubleclick.</p>
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
        <p>Nom de l’annonceur pour la campagne, en particulier pour Doubleclick.</p>
      </td>
      <td>
        <p>Analyses marketing</p>
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
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de la campagne dans une hiérarchie de publicités.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de la campagne dans une hiérarchie de publicités.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la campagne, utilisez plutôt le champ Identifiant .</p>
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
        <p>Nom de la campagne, utilisez plutôt le champ Nom .</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la campagne est toujours principale ou non dans le système source.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la campagne a été supprimée ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la campagne.</p>
      </td>
      <td>
        <p>Reciblage des partenaires</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la campagne doit être mise à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé par le traitement interne.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Campaign".</p>
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
        <p>Nom du fournisseur de publicités pour la campagne.</p>
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
        <p>Budget quotidien défini dans la plateforme publicitaire de la campagne.</p>
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
      <td>Utilisé pour les diagnostics internes.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
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
        <p>Le modèle de suivi ajouté au niveau de la campagne pour AdWords ou Bing pour le balisage des landing pages.</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Forms d’annonce importée depuis n’importe quel compte publicitaire connecté.

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
      <p>Données d’exemple</p>
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
        <p>Identifiant unique du formulaire de publicité.</p>
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
        <p>Identifiant du compte publicitaire à partir duquel le formulaire de publicité a été importé.</p>
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
        <p>Nom du compte publicitaire à partir duquel le formulaire de publicité a été importé.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>État supprimé du système source. Défini sur supprimé si l’état est Brouillon, Archivé ou Annulé.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du formulaire de publicité.</p>
      </td>
      <td>
        <p>NSPA Ebook LGF (mai 2020)</p>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "AdForm".</p>
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
        <p>Nom du fournisseur de publicités pour le formulaire de publicité.</p>
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
        <p>Description du formulaire de publicité.</p>
      </td>
      <td>
        <p>Découvrez comment une automatisation intelligente peut augmenter l’efficacité des processus dans les demandes de refinancement de prêts hypothécaires.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HEADLINE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Titre du formulaire de publicité.</td>
      <td>
        <p>Il est temps d'automatiser le processus de demande de refinancement</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL d’entrée du formulaire de publicité.</td>
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
      <td>Liste des questions du formulaire de publicité.</td>
      <td>
        <p>Prénom : Nom : Adresse électronique : Pays/Région : Titre de la tâche : Nom de la société</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATUT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>État du formulaire de publicité.</p>
      </td>
      <td>
        <p>submit</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
        <p>Données d’exemple</p>
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
      <td>Identifiant du groupe publicitaire du système source.</td>
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
        <p>La valeur est attendue comme nulle puisqu’il n’y a aucun groupe publicitaire dans la hiérarchie des publicités double-clic.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>La valeur est attendue comme nulle puisqu’il n’y a aucun groupe publicitaire dans la hiérarchie des publicités double-clic.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Valeur nulle attendue, car il s’agit de l’enregistrement du groupe publicitaire dans la hiérarchie.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Valeur nulle attendue, car il s’agit de l’enregistrement du groupe publicitaire dans la hiérarchie.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Identifiant de la campagne pour le groupe publicitaire.</p>
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
        <p>Nom de la campagne pour le groupe publicitaire.</p>
      </td>
      <td>
        <p>Affectation des recettes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le compte publicitaire est toujours principal ou non dans le système source.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le compte publicitaire a été supprimé ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du groupe publicitaire.</p>
      </td>
      <td>
        <p>Attribution des recettes - Basé sur un compte</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’annonceur doit être mis à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé par le traitement interne.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "AdGroup".</p>
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
        <p>Nom du fournisseur de publicités pour le groupe publicitaire.</p>
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
        <p>Support(s) sur lequel le groupe publicitaire s’exécute.</p>
      </td>
      <td>
        <p>Recherche, affichage, YouTube_Search, YouTube_Watch</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
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
        <p>Le modèle de suivi ajouté au niveau du compte publicitaire pour AdWords ou Bing pour le balisage des landing pages.</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

<p>Fournisseurs d’annonces depuis n’importe quel compte publicitaire connecté, y compris une entrée pour les rapports personnels, le cas échéant.</p>

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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique du fournisseur d’annonces publicitaires.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur de publicités.</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

<p>Points de contact d’attribution de l’achat, tous les points de contact associés à une opportunité.</p>
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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique du point de contact d’attribution de l’acheteur (BAT).</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
      <td>Adresse électronique associée au BAT.</td>
      <td>person@adobe.com</td>
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
        <p>person@adobe.com_00v1B00003ZbWzHQAV</p>
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
      <td>Identifiant du visiteur associé au MTA.</td>
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
        <p>Type d’activité, Visite Web, Formulaire Web, Chat Web, Appel téléphonique, Campagne [CRM] ou Activité [CRM]. Appelé dans le CRM "Type de point de contact".</p>
      </td>
      <td>
        <p>Formulaire Web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal dans lequel se trouve le point de contact, tel que défini dans les définitions de canal personnalisées dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Canal marketing - Chemin".</p>
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
        <p>La valeur de segment de la 1ère catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>La valeur de segment de la 2e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>La valeur de segment de la 3e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
      </td>
      <td>
        <p>Small &amp; Medium Business</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY4</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 4e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
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
      <td>La valeur du segment de la 5e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY6</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 6e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY7</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur du segment de la 7e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur du segment de la 8e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur du segment de la 9e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 10e catégorie dans laquelle se trouve le point de contact, telle que définie dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 11e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 12e catégorie dans laquelle se trouve le point de contact, telle que définie dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur du segment de la 13e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY14</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 14e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY15</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 15e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
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
        <p>À partir du javascript et de l’adresse IP, le navigateur détecté par l’utilisateur pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la version détectée du navigateur que l’utilisateur a utilisé pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la plateforme détectée par l’utilisateur pendant la session.</p>
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
        <p>À partir du code JavaScript et de l’adresse IP, la version détectée de la plateforme sur laquelle l’utilisateur s’était rendu au cours de la session.</p>
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
        <p>Première page d’entrée de la session qui a généré un point de contact. On parle dans le CRM de "Landing Page".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover- vérité-en-arrière-coût-par-piste</p>
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
        <p>Première page d’entrée de la session qui a généré un point de contact. Une landing page brute contiendra tous les paramètres de requête dans l’URL. On parle dans le CRM de "Landing Page - Raw" (Page d’entrée - Brut).</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-truth -under-cost-per-lead?utm_content=27322869&amp;utm_ medium=social&amp;utm_source=linkedin</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Référencé dans le CRM sous le nom de "Page de référent".</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Une page de référent brute peut contenir des paramètres de requête dans l’URL. Référencé dans le CRM sous le nom "Page du référent - Brut".</p>
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
        <p>Premier formulaire enregistré dans une session qui générait un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans le tableau Attribution_Touchpoints , mais plutôt dans le tableau Form_Submits . Appelé dans le CRM "URL du formulaire".</p>
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
        <p>Premier formulaire enregistré dans une session qui générait un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans le tableau Attribution_Touchpoints , mais plutôt dans le tableau Form_Submits . Une page de formulaire brut peut contenir des paramètres de requête dans l’URL. Référencé dans le CRM sous le nom "URL du formulaire - Brut".</p>
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
        <p>VILLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du javascript et de l’adresse IP, la ville détectée dans laquelle se trouvait l’utilisateur au cours de la session.</p>
      </td>
      <td>
        <p>San Francisco</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RÉGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du javascript et de l’adresse IP, la région détectée de l’utilisateur au cours de la session.</p>
      </td>
      <td>
        <p>Californie</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAYS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du code JavaScript et de l’adresse IP, le pays dans lequel l’utilisateur se trouvait pendant la session a été détecté.</p>
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
        <p>Utilisé pour définir le support qui a généré le point de contact. Cela peut être analysé à partir de l’URL à partir de utm_medium. Ou, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que "cpc" ou "display".</p>
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
        <p>Utilisé pour définir la source qui a généré le point de contact. Il peut être analysé à partir de l’URL de utm_source, défini de manière générique comme "Campaign CRM" s’il a été synchronisé à partir du CRM ou si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que "Google AdWords" ou "Facebook". On parle dans le CRM de "source du point de contact".</p>
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
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour rechercher et qui a fini sur le site web. En fonction des achats de mots-clés, cela peut correspondre ou non aux mots-clés achetés sur la plateforme de recherche payante.</p>
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
        <p>Plateforme publicitaire [!DNL Marketo Measure] a pu résoudre à partir de, généralement l’un de nos partenaires d’intégration.</p>
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
        <p>Identifiant du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Identifiant de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Analyses marketing</p>
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
        <p>Identifiant du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Identifiant de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>barrage routier</p>
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
        <p>Identifiant de la campagne du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom de la campagne à partir du compte publicitaire duquel la publicité a été résolue.</p>
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
        <p>Identifiant du groupe publicitaire du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement aux mots-clés Google.</p>
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
        <p>Nom du groupe publicitaire du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement à Google AdWords.</p>
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
        <p>Identifiant de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Nom de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Identifiant du créatif du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du créatif du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>La première ligne du créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Téléchargement du guide des CMO</p>
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
        <p>La deuxième ligne de l’élément créatif de la recherche dans l’annonce provient du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Découvrez comment l’attribution mesure le ROI en connectant les activités marketing aux recettes</p>
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
        <p>La page d’entrée qui clique à partir de la publicité de recherche, extraite du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom d’URL convivial affiché dans la publicité de recherche, extrait du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Identifiant du mot-clé acheté à partir de la recherche payante, tiré du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du mot-clé acheté à partir de la recherche payante, tiré du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Type de correspondance trouvé entre l’expression recherchée et le mot-clé acheté.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la première touche du parcours d’opportunité.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la touche de création de piste du parcours d’opportunité.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la touche de création d’opportunités du parcours d’opportunité.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si ce point de contact est traité ou non comme la touche fermée du parcours d’opportunité.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGES_TOUCHED</p>
      </td>
      <td>varchar</td>
      <td>Ce champ est obsolète. Utilisez les tableaux Stage_Transitions pour obtenir des informations sur l’étape.</td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact a été rempli par un formulaire au cours de la session.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si ce point de contact est traité ou non comme la première impression du parcours d’opportunité</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit d’une Première touche (voir Is_First_Touch).</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit d’une touche de création de piste (voir Is_Lead_Creation_Touch).</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’une touche en forme de U (voir Is_First_Touch et Is_Lead_Creation_Touch).</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’une touche en forme de w (voir Is_First_Touch, Is_Lead_Creation_Touch et Is_Opp_Creation_Touch).</p>
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
        <p>Le pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle de chemin complet (voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</p>
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
      <td>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle personnalisé (Voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</td>
      <td>0.0143061513081193</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si ce point de contact est supprimé.</p>
      </td>
      <td>
        <p>faux</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Membres de Campaign importés à partir du système source. Cette table sera vide si la synchronisation des campagnes est désactivée.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant de membre Campaign du système source.</p>
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
        <p>Date de dernière modification du membre Campaign, à partir du système source.</p>
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
        <p>Date de création du membre de campagne, à partir du système source.</p>
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
        <p>Date et heure définies par le client pour remplacer la date de la campagne et utiliser cette valeur pour la date du point de contact à la place.</p>
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
        <p>Identifiant du prospect auquel le membre de campagne est lié.</p>
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
        <p>Email pour le prospect auquel le membre de campagne est lié.</p>
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
        <p>Identifiant du contact auquel le membre de campagne est associé.</p>
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
        <p>Email pour le contact auquel le membre de campagne est associé.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATUT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>État du membre de campagne, généralement défini sur Envoyé ou Répondu ou sur une autre valeur personnalisée. Cet état est lié à Campaign_Sync_Type pour déterminer les membres de campagne pour lesquels créer des points de contact.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si le membre de la campagne a été marqué comme "Répondu" dans le sélecteur d’état.</p>
      </td>
      <td>
        <p>vrai</p>
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
        <p>Nom de la campagne associée dont fait partie le membre de la campagne.</p>
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
        <p>Identifiant de la campagne associée dont fait partie le membre de la campagne.</p>
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
        <p>Type sélectionné dans la campagne associée dont fait partie le membre de la campagne. Le type est utilisé pour mapper le canal marketing.</p>
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
        <p>Détermine les membres de campagne pour lesquels créer des points de contact. Les valeurs possibles sont les suivantes : Include_All, Include_Responded, Exclude_All.</p>
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
        <p>Le champ Audit indique si un point de contact d’achat a été généré pour le prospect. Si aucun point de contact n’a été créé, la raison pour laquelle il n’a pas été admissible est donnée.</p>
      </td>
      <td>
        <p>Aucun point de contact : Date en dehors du modèle</p>
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
        <p>Le champ Audit indique si un point de contact d’acheteur a été généré ou non pour le contact. Si aucun point de contact n’a été créé, la raison pour laquelle il n’a pas été admissible est donnée.</p>
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
        <p>Le champ Audit indique si un point de contact d’attribution d’achat a été généré ou non pour l’opportunité. Si aucun point de contact n’a été créé, la raison pour laquelle il n’a pas été admissible est donnée.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>si l’enregistrement est considéré comme supprimé ou non dans le système source ;</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées qui [!DNL Marketo Measure] a été importé à partir du système source, au format JSON.</td>
      <td>{"Campaign_Type__c":"Dinners","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Canaux marketing, comme créé dans la variable [!DNL Marketo Measure] application.

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
        <p>Données d’exemple</p>
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
        <p>Recherche naturelle.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du canal.</p>
      </td>
      <td>
        <p>Recherche naturelle.Google</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Contacts importés depuis le système source.

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
        <p>Données d’exemple</p>
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
        <p>ID de contact du système source.</p>
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
        <p>Date de la dernière modification de l’enregistrement Contact depuis le système source.</p>
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
        <p>Date de création de l’enregistrement Contact, à partir du système source.</p>
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
        <p>Adresse électronique du contact, depuis le système source.</p>
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
        <p>Source dans laquelle le prospect a été créé.</p>
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
        <p>Étape actuelle du contact, reconnue comme étape personnalisée pouvant être créée dans la variable [!DNL Marketo Measure] application.</p>
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
        <p>Toutes les étapes précédentes du contact, reconnues comme des étapes personnalisées qui peuvent être créées dans la [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Ouvrir – Contact</p>
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
        <p>Le [!DNL Marketo Measure] algorithme permettant d’estimer si un contact permettra la fermeture d’une opportunité en fonction de l’âge et de l’étape.</p>
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
        <p>Le [!DNL Marketo Measure] ID de cookie utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Condition requise : Activer le suivi des appels : True</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement est supprimé ou non dans le système source.</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>booléenne</td>
      <td>Utilisé pour dédupliquer les enregistrements si une intégration CRM et Marketo sont configurées. S’il existe des doublons, le contact Marketo est marqué comme vrai.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indique si l’enregistrement provient d’une intégration CRM ou Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>Other_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappe une personne d’une intégration Marketo à un contact d’une intégration CRM ; Si une intégration CRM et Marketo existent, la valeur est l’identifiant correspondant.</td>
      <td>1234 / 00Q0Z00001OohgTUAR</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées qui [!DNL Marketo Measure] a été importé à partir du système source au format JSON.</td>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
      <th>Données d’exemple</th>
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
      <td>Valeur d’identifiant pour la devise.</td>
      <td>7493833133899044458</td>
    </tr>
    <tr>
      <td>SOURCE_ISO_CODE</td>
      <td>varchar</td>
      <td>Code ISO de devise, à partir du système source.</td>
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
      <td>Date de début suivante pour le taux de conversion. (La date de fin du taux de conversion est end_date moins 1 jour.)</td>
      <td>2018-09-01 00:00:00.000</td>
    </tr>
    <tr>
      <td>CONVERSION_RATE</td>
      <td>number(38,0)</td>
      <td>Taux utilisé pour convertir la devise en devise de l’entreprise.</td>
      <td>0.76728300</td>
    </tr>
    <tr>
      <td>IS_CURRENT</td>
      <td>booléenne</td>
      <td>La sémantique de ce champ a été corrompue. N’utilisez pas .</td>
      <td>vrai</td>
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
      <td>Date de la dernière modification de l’enregistrement dans le système source.</td>
      <td>2019-03-30 00:54:50.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booléenne</td>
      <td>si l’enregistrement est considéré comme supprimé dans le système source.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Données de coût importées à partir des comptes d’annonce connectés ou dépenses marketing auto-déclarées.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Données d’exemple</th>
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
      <td>Date de la dernière modification de l’enregistrement.</td>
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
      <td>Source du coût reporté.</td>
      <td>[Affichage AdWords]</td>
    </tr>
    <tr>
      <td>COST_IN_MICRO</td>
      <td>number(38,0)</td>
      <td>Coût en millions. L’utilisateur devra diviser la valeur par 1000000.</td>
      <td>1410000</td>
    </tr>
    <tr>
      <td>Clics</td>
      <td>number(38,0)</td>
      <td>Nombre de clics signalés pour le groupe pour la journée.</td>
      <td>4</td>
    </tr>
    <tr>
      <td>IMPRESSIONS</td>
      <td>number(38,0)</td>
      <td>Nombre d’impressions consignées pour le groupe pour la journée.</td>
      <td>4187</td>
    </tr>
    <tr>
      <td>ESTIMATED_TOTAL_POSSIBLE_IMPRESSIONS</td>
      <td>number(38,0)</td>
      <td>Nombre total d’impressions estimées à partir de DCM pour le groupe pour la journée.</td>
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
      <td>Nom du canal marketing, créé par le client dans la variable [!DNL Marketo Measure] application.</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_IS_AGGREGATABLE_COST</td>
      <td>booléenne</td>
      <td>Indique si la ligne contient le coût qui peut être additionné par Canal. (c.-à-d. pour obtenir le coût du canal, additionnez les lignes où cette colonne est égale à true.)</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Identifiant de l’annonceur extrait de la connexion à la publicité, en particulier pour les connexions Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>ADVERTISER_NAME</td>
      <td>varchar</td>
      <td>Nom de l’annonceur extrait de la connexion à la publicité, en particulier pour les connexions Doubleclick.</td>
      <td>[!DNL Marketo Measure] Analyses marketing</td>
    </tr>
    <tr>
      <td>ADVERTISER_IS_AGGREGATABLE_COST</td>
      <td>booléenne</td>
      <td>Indique si la ligne contient le coût qui peut être additionné par l’annonceur. (Pour obtenir le coût du publicitaire, additionnez les lignes où cette colonne est égale à true.)</td>
      <td>faux</td>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par Compte. (c.-à-d. pour obtenir le coût du compte, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Identifiant de la campagne extrait de la connexion à la publicité.</p>
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
        <p>Nom de la campagne extrait de la connexion à la publicité.</p>
      </td>
      <td>
        <p>Reciblage des partenaires</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être calculé par Campaign. (c.-à-d. pour obtenir le coût de la campagne, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>vrai</p>
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
        <p>Logiciel de gestion des attributs | Expression</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par le groupe d’annonces. (Pour obtenir le coût du groupe publicitaire, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Identifiant de la publicité extraite de la connexion à la publicité.</p>
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
        <p>Nom de la publicité issue de la connexion à la publicité.</p>
      </td>
      <td>
        <p>Nom de la publicité : Ad3-320x50.gif; 320 x 50</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par l’annonce. (Pour obtenir le coût de la publicité, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Identifiant de l’élément créatif extrait de la connexion à l’annonce.</p>
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
        <p>Nom du créatif extrait de la connexion à la publicité.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être calculé par Creative. (c’est-à-dire pour obtenir le coût créatif, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Identifiant du mot-clé extrait de la connexion à la publicité.</p>
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
        <p>Nom du mot-clé extrait de la connexion à la publicité.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être calculé par le mot-clé. (Pour obtenir le coût du mot-clé, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Identifiant de l’emplacement extrait de la connexion à la publicité.</p>
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
        <p>Nom de l’emplacement extrait de la connexion à la publicité.</p>
      </td>
      <td>
        <p>barrage routier</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par Emplacement. (c.-à-d. pour obtenir le coût du référencement, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Identifiant du site extrait de la connexion à la publicité.</p>
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
        <p>Nom du site extrait de la connexion à la publicité.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par Site . (c.-à-d. pour obtenir le coût du site, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>si l’enregistrement est considéré comme supprimé ou non dans le système source ;</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>ISO_CURRENCY_CODE</td>
      <td>varchar</td>
      <td>Code ISO de la devise, importé à partir du système source.</td>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Créatifs importés depuis n’importe quel compte publicitaire connecté.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique de l’élément créatif.</p>
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
      <td>ID de création du système source.</td>
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
        <p>Identifiant du compte publicitaire à partir duquel l’élément créatif a été importé.</p>
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
        <p>Nom du compte publicitaire à partir duquel l’élément créatif a été importé.</p>
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
        <p>Identifiant de l’annonceur pour le créatif, en particulier pour Doubleclick.</p>
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
        <p>Nom de l’annonceur pour le créatif, plus particulièrement pour Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Analyses marketing</p>
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
        <p>Identifiant du groupe publicitaire pour le créatif.</p>
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
        <p>Nom du groupe publicitaire pour le créatif.</p>
      </td>
      <td>Visionneuse de publicités pour la publicité B</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne pour le créatif.</p>
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
        <p>Nom de la campagne de l’élément créatif.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si Creative est toujours principal ou non dans le système source.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si le créatif a été supprimé ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’élément créatif, à partir du système source.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’élément créatif doit être mis à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé par le traitement interne.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Creative".</p>
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
        <p>Nom du fournisseur de publicités pour le créatif.</p>
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
        <p>La version actuelle de l’URL, y compris toutes les balises.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>URL abrégée et conviviale qui s’affiche sur l’élément créatif.</p>
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
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>L’URL qui sera décorée [!DNL Marketo Measure] paramètres.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
      <td>URL abrégée et conviviale qui s’affiche sur l’élément créatif. (Utilisé uniquement pour LinkedIn Ads.)</td>
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
        <p>Type de contenu créatif : texte ou affichage</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si le créatif utilise des URL mises à niveau.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Le titre du créatif</p>
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
        <p>Copie de la première ligne du créatif</p>
      </td>
      <td>
        <p>Connectez-Vous Et Apprenez Grâce Aux Spécialistes Du Marketing B2B Basé Sur Les Recettes. Rejoignez la communauté.</p>
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
        <p>Copie de la deuxième ligne du créatif</p>
      </td>
      <td>
        <p>Avez-Vous Utilisé Analytics ? Laissons une critique aujourd'hui !</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ Diagnostics pour le traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ Diagnostics pour le traitement interne.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ Diagnostics pour le traitement interne.</td>
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
        <p>Champ Diagnostics pour le traitement interne.</p>
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
        <p>Identifiant du partage. (Utilisé uniquement pour LinkedIn Ads.)</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Événements importés du système source. Cette table sera vide si la synchronisation des activités est désactivée.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant d’événement du système source.</p>
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
        <p>Date de création de l’événement, à partir du système source.</p>
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
        <p>Date de la dernière modification de l’événement depuis le système source.</p>
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
        <p>Courrier électronique pour le prospect associé à l’événement.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Adresse électronique du contact associé à l’événement.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Le [!DNL Marketo Measure] ID de cookie utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Condition requise : Activer le suivi des appels : True</p>
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
        <p>Nom du type d’activité, depuis le système source.</p>
      </td>
      <td>
        <p>Adresse e-mail</p>
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
        <p>Date de début de l’événement, l’une des options utilisées pour déterminer la date du point de contact.</p>
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
        <p>Date de fin de l’événement, l’une des options utilisées pour déterminer la date du point de contact.</p>
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
        <p>booléenne</p>
      </td>
      <td>si l’enregistrement est considéré comme supprimé dans le système source.</td>
      <td>
        <p>False</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées qui [!DNL Marketo Measure] a été importé à partir du système source, au format JSON.</td>
      <td>{"Contact_Type__c":"CMO","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Tâches importées du système source. Ce tableau s’affiche si la synchronisation des activités OU le suivi des appels sont activés.

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
        <p>Données d’exemple</p>
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
        <p>L’identifiant de tâche du système source.</p>
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
        <p>Date de création de la tâche, à partir du système source.</p>
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
        <p>Date de dernière modification de la tâche, à partir du système source.</p>
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
        <p>Courrier électronique pour le prospect associé à la tâche.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Adresse électronique du contact associé à la tâche.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Le [!DNL Marketo Measure] ID de cookie utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Condition requise : Activer le suivi des appels : True</p>
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
        <p>Nom du type d’activité, depuis le système source.</p>
      </td>
      <td>
        <p>Appelez</p>
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
        <p>Date à laquelle la tâche a eu lieu, l’une des options utilisées pour déterminer la date du point de contact.</p>
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
        <p>booléenne</p>
      </td>
      <td>si l’enregistrement est considéré comme supprimé dans le système source.</td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Propriétés personnalisées qui [!DNL Marketo Measure] a été importé à partir du système source, au format JSON.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Table de toutes les devises ISO.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Données d’exemple</th>
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
      <td>Code ISO de la devise.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>IS_CORPORATE</td>
      <td>booléenne</td>
      <td>Indique si la devise est la devise de l’entreprise.</td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>IS_ENABLED</td>
      <td>booléenne</td>
      <td>Indique si la devise est activée dans le système source.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement dans [!DNL Marketo Measure].</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement dans le système source.</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé dans [!DNL Marketo Measure]</td>
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
      <td>Code numérique standard ISO.</td>
      <td>048</td>
    </tr>
    <tr>
      <td>EXPONENT</td>
      <td>number(38,0)</td>
      <td>Nombre de décimales entre la plus petite unité de devise définie et une unité de devise entière.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>NOM</td>
      <td>varchar</td>
      <td>Nom de la devise.</td>
      <td>Peso argentin</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Tests AB enregistrés. Ce tableau sera vide si les tests AB ne sont pas activés.

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
      <th>Données d’exemple</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Le premier ID de cookie de l’ID de visiteur associé.</p>
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
        <p>ID de cookie enregistré au moment où l’événement a été consigné.</p>
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
      <td>Date de la dernière modification de l’enregistrement.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au moment où l’expérience a été consignée.</p>
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
        <p>ID de l’expérience extraite de la plateforme de test AB.</p>
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
        <p>Nom de l’expérience extrait de la plateforme de test AB.</p>
      </td>
      <td>Expérience A</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID de variation de l’expérience extrait de la plateforme de test AB.</p>
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
        <p>Nom de variation de l’expérience extrait de la plateforme de test AB.</p>
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
        <p>Identifiant de l’utilisateur qui a effectué l’expérience extrait de la plateforme de test AB.</p>
      </td>
      <td>584d64et</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement a été supprimé ou non, il est utilisé à des fins de diagnostic et d’audit.</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Événements Web enregistrés à l’aide d’événements personnalisés dans le code JavaScript. Cette table sera vide si [!DNL Marketo Measure] Les événements ne sont pas activés.

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
      <th>Données d’exemple</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Le premier ID de cookie de l’ID de visiteur associé.</p>
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
        <p>ID de cookie enregistré au moment où l’événement a été déclenché à partir du code JavaScript personnalisé.</p>
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
        <p>Adresse IP enregistrée au moment où l’événement a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>CLÉ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom donné à l’événement qui a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>Vue vidéo</td>
    </tr>
    <tr>
      <td>
        <p>VALEUR</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur donnée à l’événement qui a été déclenché à partir du code JavaScript personnalisé.</p>
      </td>
      <td>75 % visionné</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement a été supprimé ou non, il est utilisé à des fins de diagnostic et d’audit.</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Pages d’entrée téléchargées à partir de n’importe quel compte publicitaire connecté.

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
      <th>Données d’exemple</th>
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
      <td>Identifiant du compte publicitaire à partir duquel la landing page a été importée.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du compte publicitaire à partir duquel la landing page a été importée.</td>
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
        <p>Identifiant de l’annonceur pour la page d’entrée, en particulier pour le double-clic.</p>
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
        <p>Nom de l’annonceur pour la page d’entrée, en particulier pour le double-clic.</p>
      </td>
      <td>
        <p>Analyses marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du groupe publicitaire pour la landing page.</td>
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
        <p>Nom du groupe publicitaire pour la page d’entrée.</p>
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
        <p>Identifiant de la campagne pour la landing page.</p>
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
        <p>Nom de la campagne pour la landing page.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
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
        <p>Date de dernière modification de la ligne</p>
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
        <p>NOM</p>
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
        <p>booléenne</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Tableau de correspondance pour les adresses électroniques et les identifiants de visiteur.

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
        <p>Données d’exemple</p>
      </th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Identifiant unique de l’enregistrement.</td>
      <td>
        <p>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13 000</p>
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
        <p>Adresse électronique connue liée à un identifiant visiteur donné d’une session</p>
      </td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Le premier cookie de l’identifiant visiteur associé</p>
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
        <p>Date de dernière modification de la ligne</p>
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
        <p>Date de création de la ligne</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement est considéré comme supprimé ou non, il est utilisé à des fins de diagnostic et d’audit.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>IS_IGNORE</td>
      <td>booléenne</td>
      <td>Indique si l’email ou l’identifiant visiteur est considéré comme du bruit ou du spam, utilisé pour le traitement interne.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Les unions regroupent les données Impressions, Pages vues, Visites, Envois de formulaire, Points de contact utilisateur, Point de contact (BT), Points de contact d’attribution (MTA) et Coût. Utilisé en interne pour la prise en charge [!DNL Marketo Measure] création de rapports.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Données d’exemple</th>
    </tr>
    <tr>
      <td>COST_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour rejoindre le tableau Coûts.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>ATP_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour rejoindre le tableau Points de contact d’attribution.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>TP_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure aux tables Points de contact ou Points de contact utilisateur.</td>
      <td>5028390208679093800</td>
    </tr>
    <tr>
      <td>PAGE_VIEW_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Pages vues.</td>
      <td>-8044063242541720607</td>
    </tr>
    <tr>
      <td>SESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure à la table Sessions.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Le premier ID de cookie de l’ID de visiteur associé.</td>
      <td>v_530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>COOKIE_ID</td>
      <td>varchar</td>
      <td>ID de cookie enregistré au moment où l’événement a été consigné.</td>
      <td>530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>FORM_SUBMIT_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour se joindre au tableau Envois de formulaire.</td>
      <td>-8659572802702769670</td>
    </tr>
    <tr>
      <td>IMPRESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Impressions.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour se joindre à la table Urls.</td>
      <td>4079876040770132443</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour se joindre à la table Urls.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour se joindre à la table Urls.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>AD_PROVIDER_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour rejoindre le tableau Fournisseurs d’annonces publicitaires.</td>
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
        <p>Utilisé pour se joindre à la table Canaux.</p>
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
        <p>Utilisé pour rejoindre la table Campagnes publicitaires.</p>
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
        <p>Utilisé pour la jointure au tableau Mots-clés.</p>
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
        <p>Utilisé pour se joindre à la table Publicités.</p>
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
        <p>Utilisé pour rejoindre le tableau Groupes publicitaires.</p>
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
        <p>Utilisé pour rejoindre la table des créatifs.</p>
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
        <p>Utilisé pour effectuer une jointure sur la table Sites.</p>
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
        <p>Utilisé pour rejoindre la table Advertisers.</p>
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
        <p>Utilisé pour rejoindre la table Comptes publicitaires.</p>
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
        <p>Utilisé pour la jointure à la table Emplacements.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>CATEGORY_01_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_02_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_03_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_04_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_05_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_06_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_07_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_08_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_09_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_10_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_11_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_12_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_13_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_14_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_15_KEY</td>
      <td>number(38,0)</td>
      <td>Utilisé pour la jointure au tableau Segments.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>TYPE</td>
      <td>number(38,0)</td>
      <td>Indique le type de fait de la ligne. 1 = Point de contact d’attribution de l’acheteur 2 = Coût 3 = point de contact de l’acheteur 4 = point de contact de l’utilisateur 5 = Page vue 6 = Session 7 = Envoi de formulaire 8 = Impression</td>
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
        <p>Date de la dernière modification de la ligne.</p>
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
        <p>Coût en millions. L’utilisateur devra diviser la valeur par 1000000.</p>
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
        <p>Nombre d’impressions consignées pour le groupe pour la journée.</p>
      </td>
      <td>
        <p>340</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Clics</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Nombre de clics signalés pour le groupe pour la journée.</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit d’une première touche.</p>
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
        <p>Le pourcentage calculé attribué à ce point de contact, car il s’agit d’une touche de création de piste.</p>
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
        <p>Le pourcentage calculé qui est alloué à ce point de contact parce qu’il fait partie d’une touche en forme de u.</p>
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
        <p>Le pourcentage calculé qui est alloué à ce point de contact parce qu’il fait partie d’une touche en forme de w.</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle de chemin complet.</p>
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
        <p>MONTANT</p>
      </td>
      <td>
        <p>number(38,8)</p>
      </td>
      <td>
        <p>Montant de l'opportunité, provenant du système source.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’opportunité a été déplacée vers une étape classée comme gagnante.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CLOSED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’opportunité a été déplacée vers une étape classée comme fermée.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Identifiant d’opportunité du système source.</p>
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
        <p>Date de création de l’opportunité, à partir du système source.</p>
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
        <p>Date de fermeture de l’ opportunité, depuis le système source.</p>
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
        <p>Date de création de l’enregistrement Contact, à partir du système source.</p>
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
        <p>Identifiant de contact du système source.</p>
      </td>
      <td>
        <p>0030Z00003ORVJmQAP</p>
      </td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Adresse électronique pour l’enregistrement.</td>
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
        <p>Date de création de l’enregistrement de piste à partir du système source.</p>
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
        <p>Identifiant de piste du système source.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par l’annonce. (Pour obtenir le coût de la publicité, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_ADVERTISER</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par l’annonceur. (Pour obtenir le coût du publicitaire, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_ACCOUNT</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par Compte. (c.-à-d. pour obtenir le coût du compte, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_GROUP</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par le groupe d’annonces. (Pour obtenir le coût du groupe publicitaire, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CAMPAIGN</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être calculé par Campaign. (c.-à-d. pour obtenir le coût de la campagne, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CHANNEL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par Canal. (c.-à-d. pour obtenir le coût du canal, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CREATIVE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être calculé par Creative. (c’est-à-dire pour obtenir le coût créatif, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_KEYWORD</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être calculé par le mot-clé. (Pour obtenir le coût du mot-clé, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_PLACEMENT</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par Emplacement. (c.-à-d. pour obtenir le coût du référencement, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_SITE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne contient le coût qui peut être additionné par Site . (c.-à-d. pour obtenir le coût du site, additionnez les lignes où cette colonne est égale à true.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’enregistrement a été supprimé ou non, utilisé comme journal d’audit.</p>
      </td>
      <td>
        <p>faux</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique pour l’envoi du formulaire.</p>
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
        <p>ID de cookie enregistré au moment où l’envoi du formulaire a été consigné.</p>
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
        <p>Le premier ID de cookie de l’ID de visiteur associé. Si l’enregistrement est marqué comme is_duplicated = true, ce champ sera nul.</p>
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
        <p>ID de session enregistré au moment où l’envoi du formulaire a été consigné. Si l’enregistrement est marqué comme is_duplicated = true, ce champ sera nul.</p>
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
        <p>Date à laquelle le formulaire a été envoyé.</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>URL vers laquelle le formulaire a été envoyé, sans paramètres de requête.</p>
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
        <p>URL dans laquelle le formulaire a été envoyé, y compris les paramètres de requête.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDd PdXh4Q0RmcnBJWXhwZTF1Z0RbXlDVmxJNzIwNkhW</p>
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
        <p>Adresse IP enregistrée au moment de l’envoi du formulaire.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
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
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, comme Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique l’ordre dans lequel la page vue s’est produite au cours de la session.</td>
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
      <td>Utilisé pour le contrôle et le traitement internes.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Utilisé pour le traitement interne.</td>
      <td>
        <p>vrai</p>
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
        <p>Adresse électronique fournie dans le formulaire, telle qu’elle est capturée dans le code JavaScript.</p>
      </td>
      <td>
        <p>personc@adobe.com</p>
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
        <p>Chat</p>
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
        <p>Indique la méthode dans laquelle le formulaire a été reconnu, par exemple onSubmit ou AjaxIntercept</p>
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
      <td>Valeur d’identifiant pour le formulaire.</td>
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
      <td>Clé étrangère dans la table d’URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Impressions déclenchées et enregistrées. Ce tableau nécessite une connexion DoubleClick et l’option Activer la vue publicitaire définie sur True.

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
        <p>Données d’exemple</p>
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
        <p>6acd7b43290490fe5c53eed31281d09a|2020-05-18:22:20:59|000|0|2869369052</p>
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
        <p>ID de cookie enregistré au moment de l’impression.</p>
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
        <p>Le premier ID de cookie de l’ID de visiteur associé.</p>
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
        <p>ID de session enregistré au moment où l’impression a été enregistrée.</p>
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
        <p>Date à laquelle l’impression a été diffusée.</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>URL où l’impression a été diffusée, sans paramètres de requête.</p>
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
        <p>URL dans laquelle l’impression a été diffusée, y compris les paramètres de requête.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDd PdXh4Q0RmcnBJWXhwZTF1Z0RbXlDVmxJNzIwNkhW</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Adresse IP enregistrée au moment de l’impression.</p>
      </td>
      <td>174.127.184.158</td>
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
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, comme Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indique l’ordre dans lequel la page vue s’est produite au cours de la session.</td>
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
      <td>Utilisé pour le contrôle et le traitement internes.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Utilisé pour le traitement interne.</td>
      <td>
        <p>vrai</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Référencé dans le CRM sous le nom de "Page de référent".</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Une page de référent brute peut contenir des paramètres de requête dans l’URL. Référencé dans le CRM sous le nom "Page du référent - Brut".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>VILLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ville résolue à partir de l’adresse IP.</p>
      </td>
      <td>
        <p>Seattle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RÉGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La région résolue de l’adresse IP.</p>
      </td>
      <td>
        <p>Washington</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAYS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Pays résolu à partir de l’adresse IP.</p>
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
        <p>Le nom du fournisseur d’accès Internet, utilisé par les clients qui disposent d’un suivi Geo IP avancé.</p>
      </td>
      <td>
        <p>AT&amp;T-verse</p>
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
        <p>Plateforme publicitaire [!DNL Marketo Measure] a pu résoudre à partir de, généralement l’un de nos partenaires d’intégration.</p>
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
        <p>Identifiant du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Identifiant de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>Analyses marketing de mesure du marché</p>
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
        <p>Identifiant du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Identifiant de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>barrage routier</p>
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
        <p>Identifiant de la campagne du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom de la campagne à partir du compte publicitaire duquel la publicité a été résolue.</p>
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
        <p>Nul attendu puisqu’il n’existe aucun groupe publicitaire dans la hiérarchie Doubleclick pour les impressions</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Nul attendu puisqu’il n’existe aucun groupe publicitaire dans la hiérarchie Doubleclick pour les impressions</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Identifiant de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Nom de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Être nul, car il n’existe aucun élément créatif dans la hiérarchie Doubleclick pour les impressions.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Être nul, car il n’existe aucun élément créatif dans la hiérarchie Doubleclick pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’existe aucun élément créatif dans la hiérarchie Doubleclick pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’existe aucun élément créatif dans la hiérarchie Doubleclick pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’existe aucun élément créatif dans la hiérarchie Doubleclick pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’existe aucun élément créatif dans la hiérarchie Doubleclick pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur est attendue comme nulle puisqu’il n’existe aucun mot-clé dans la hiérarchie de double clic pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur est attendue comme nulle puisqu’il n’existe aucun mot-clé dans la hiérarchie de double clic pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La valeur est attendue comme nulle puisqu’il n’existe aucun mot-clé dans la hiérarchie de double clic pour les impressions.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du javascript et de l’adresse IP, le navigateur détecté par l’utilisateur pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la version détectée du navigateur que l’utilisateur a utilisé pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la plateforme détectée par l’utilisateur pendant la session.</p>
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
        <p>À partir du code JavaScript et de l’adresse IP, la version détectée de la plateforme sur laquelle l’utilisateur s’était rendu au cours de la session.</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
        <p>Données d’exemple</p>
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
      <td>Identifiant du mot-clé du système source.</td>
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
        <p>La valeur est attendue comme nulle puisqu’il n’existe aucun mot-clé dans la hiérarchie de double clic pour les impressions.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>La valeur est attendue comme nulle puisqu’il n’existe aucun mot-clé dans la hiérarchie de double clic pour les impressions.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Identifiant du groupe publicitaire pour le mot-clé.</p>
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
        <p>Nom du groupe publicitaire pour le mot-clé.</p>
      </td>
      <td>
        <p>Attribution des recettes - B2B</p>
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
        <p>Identifiant de la campagne pour le mot-clé.</p>
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
        <p>Nom de la campagne pour le mot-clé.</p>
      </td>
      <td>
        <p>Affectation des recettes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le mot-clé est toujours principal ou non dans le système source.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le mot-clé a été supprimé ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>
        <p>2018-08-02 06:37:29.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du mot-clé, à partir du système source.</p>
      </td>
      <td>
        <p>[attribution des recettes b2b]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le mot-clé doit être mis à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé pour le traitement interne.)</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Mot-clé".</p>
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
        <p>Nom du fournisseur de publicités pour le mot-clé.</p>
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
        <p>URL de la landing page.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_REQUESTED</td>
      <td>varchar</td>
      <td>
        <p>L’URL de la page d’entrée avec [!DNL Marketo Measure] paramètres.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Champ de diagnostic, pour le traitement interne.</td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WORD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La phase de recherche que l’utilisateur a saisie.</td>
      <td>
        <p>attribution de recettes b2b</p>
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
        <p>Type de correspondance trouvé entre l’expression recherchée et le mot-clé.</p>
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
      <td>Utilisé pour les diagnostics internes.</td>
      <td>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilisé pour les diagnostics internes.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Le modèle de tracking URL [!DNL Marketo Measure] ajouté au mot-clé.</td>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Pages d’entrée importées depuis n’importe quel compte publicitaire connecté.

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
      <th>Données d’exemple</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique de la page d’entrée.</p>
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
      <td>Identifiant du compte publicitaire à partir duquel la landing page a été importée.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du compte publicitaire à partir duquel la landing page a été importée.</td>
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
        <p>Identifiant de l’annonceur pour la page d’entrée, en particulier pour le double-clic.</p>
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
        <p>Nom de l’annonceur pour la page d’entrée, en particulier pour le double-clic.</p>
      </td>
      <td>Analyses marketing</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant du groupe publicitaire pour la landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom du groupe publicitaire pour la page d’entrée.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Identifiant de la campagne pour la landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nom de la campagne pour la landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
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
        <p>Date de la dernière modification de la ligne.</p>
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
        <p>NOM</p>
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
        <p>booléenne</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Pistes importées du système source.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant de piste du système source.</p>
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
        <p>Date de la dernière modification de l’enregistrement de piste depuis le système source.</p>
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
        <p>Date de création de l’enregistrement de piste à partir du système source.</p>
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
        <p>Adresse électronique du prospect, à partir du système source.</p>
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
        <p>Site Web saisi pour le prospect, à partir du système source, utilisé pour la mise en correspondance du compte Lead2Account.</p>
      </td>
      <td>
        <p>adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SOCIÉTÉ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de la société saisi pour le prospect, à partir du système source, utilisé pour le mappage du compte Lead2Account.</p>
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
        <p>Source dans laquelle le prospect a été créé.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le prospect a été converti en contact ou non.</p>
      </td>
      <td>
        <p>vrai</p>
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
        <p>Identifiant du compte mappé. Conditions requises : Activer ABM</p>
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
        <p>Étape actuelle du prospect, reconnue comme une étape personnalisée pouvant être créée dans la variable [!DNL Marketo Measure] application.</p>
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
        <p>Toutes les étapes précédentes du prospect, reconnues comme des étapes personnalisées qui peuvent être créées dans la variable [!DNL Marketo Measure] application.</p>
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
        <p>Le [!DNL Marketo Measure] algorithme d’estimation de la conversion d’une piste en fonction de l’âge et de l’étape.</p>
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
        <p>(obsolète)</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>(obsolète)</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Le [!DNL Marketo Measure] ID de cookie utilisé pour renseigner un partenaire d’intégration afin de mapper un événement hors ligne à une session web. Condition requise : Activer le suivi des appels : True</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement est supprimé ou non dans le système source.</p>
      </td>
      <td>
        <p>faux</p>
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
      <td>Propriétés personnalisées qui [!DNL Marketo Measure] a été importé à partir du système source au format JSON.</td>
      <td>{"Lead_Type__c":"Ventes créées", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>booléenne</td>
      <td>Utilisé pour dédupliquer les enregistrements si une intégration CRM et Marketo sont configurées. S’il existe des doublons, le prospect Marketo est marqué comme vrai.</td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indique si l’enregistrement provient d’une intégration CRM ou Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>Other_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Met en correspondance une personne d’une intégration Marketo avec un prospect d’une intégration CRM. Si une intégration CRM et Marketo existent, la valeur est l’identifiant correspondant.</td>
      <td>1234</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Transitions intermédiaires pour les pistes ou les contacts.

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
        <p>Données d’exemple</p>
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
        <p>persone@adobe.com</p>
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
        <p>Identifiant du Contact associé à la transition.</p>
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
        <p>Identifiant du point de contact de l’acheteur lié à la transition.</p>
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
        <p>Date à laquelle l’enregistrement a été transféré dans la scène.</p>
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
        <p>Valeur d’identifiant de l’étape pour la transition.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ÉTAPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’étape de la transition.</p>
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
        <p>Classement numérique de la scène, tel que trié dans la variable [!DNL Marketo Measure] Paramètres de mappage des environnements intermédiaires.</p>
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
        <p>Utilisé dans le traitement interne pour l'indexation et la commande des étapes boomerang.</p>
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
      <td>Utilisé dans le traitement interne pour l'indexation et la commande des étapes boomerang.</td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si le point de contact est considéré comme en attente et non encore fermé. Cela s’affiche uniquement pour les clients qui disposent d’un modèle d’attribution de chemin d’accès complet.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITOR</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne est liée à une transition d’étape de jalon. Par exemple, s’il existe 3 étapes/entrées (FT, LC, MQL) et 4 points de contact, le point de contact 1 sans scène est considéré comme "non transitoire", de sorte que la valeur est égale à true.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de transition de l’étape précédente, en fonction de l’ordre de classement.</p>
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
        <p>Date de transition de l’étape suivante, en fonction de l’ordre de classement.</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement de transition est considéré comme supprimé ou non.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Opportunités importées du système source.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant d’opportunité du système source.</p>
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
        <p>Date de dernière modification de l’opportunité, à partir du système source.</p>
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
        <p>Date de création de l’ opportunité, à partir du système source.</p>
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
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’opportunité, depuis le système source.</p>
      </td>
      <td>
        <p>Mesurer le renouvellement de Mareketo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’opportunité a atteint une étape considérée comme gagnée.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’opportunité a été déplacée vers une étape considérée comme fermée.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de fermeture prévue ou réelle de l’opportunité, depuis le système source.</p>
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
        <p>(obsolète)</p>
      </td>
      <td>
        <p>nul</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MONTANT</p>
      </td>
      <td>
        <p>number(38,8)</p>
      </td>
      <td>
        <p>Montant de l'opération qui est attendu ou fermé à partir de l'opportunité, à partir du système source.</p>
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
        <p>Identifiant du prospect associé qui a converti dans cette opportunité.</p>
        <p>Notez que ce champ n’est pas défini et renvoie null dans Snowflake pour tous les clients.</p>
      </td>
      <td>
        <p>nul</p>
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
        <p>Adresse électronique du prospect associé qui a converti dans cette opportunité.</p>
        <p>Notez que ce champ n’est pas défini et renvoie null dans Snowflake pour tous les clients.</p>
      </td>
      <td>
        <p>nul</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRINCIPAL_CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si Rôle contact Principal est utilisé, l’identifiant du contact associé est répertorié comme rôle contact Principal.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRINCIPAL_CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si Rôle contact Principal est utilisé, l’email du contact associé est répertorié comme rôle contact Principal.</p>
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
        <p>Le [!DNL Marketo Measure] algorithme d’estimation de la fermeture d’une opportunité en fonction de l’âge et de l’étape.</p>
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
        <p>Étape actuelle de l’opportunité, telle que définie dans la variable [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Démonstration DM</p>
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
        <p>Chaîne de toutes les étapes précédentes de l’opportunité, comme défini dans la variable [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Découverte qualifiée, démonstration planifiée</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement est supprimé ou non dans le système source.</p>
      </td>
      <td>faux</td>
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
      <td>Code ISO de la devise, importé à partir du système source.</td>
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
      <td>Propriétés personnalisées qui [!DNL Marketo Measure] a été importé à partir du système source au format JSON.</td>
      <td>{"Opportunity_Location__c":"Seattle", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Transitions intermédiaires pour les opportunités.

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
        <p>Données d’exemple</p>
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
        <p>ST_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_Demo Scheduled-1_BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec56e 7757</p>
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
        <p>Identifiant de l’ opportunité associée à la transition.</p>
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
        <p>Identifiant du Contact associé à la transition.</p>
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
        <p>persone@adobe.com</p>
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
        <p>Identifiant du point de contact d’attribution de l’acheteur lié à la transition.</p>
      </td>
      <td>
        <p>BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e757</p>
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
        <p>Date à laquelle l’enregistrement a été transféré dans la scène.</p>
      </td>
      <td>
        <p>2018-05-26 07:29:43.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ÉTAPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’étape de la transition.</p>
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
        <p>Valeur d’identifiant de l’étape pour la transition.</p>
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
        <p>Classement numérique de la scène, tel que trié dans la variable [!DNL Marketo Measure] Paramètres de mappage des environnements intermédiaires.</p>
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
        <p>Utilisé dans le traitement interne pour l'indexation et la commande des étapes boomerang.</p>
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
        <p>Utilisé dans le traitement interne pour l'indexation et la commande des étapes boomerang.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si le point de contact est considéré comme en attente et non encore fermé. Cela s’affiche uniquement pour les clients qui disposent d’un modèle d’attribution de chemin d’accès complet.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITOR</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si la ligne est liée à une transition d’étape de jalon. Par exemple, s’il existe 3 étapes/entrées (FT, LC, MQL) et 4 points de contact, le point de contact 1 sans scène est considéré comme "non transitoire", de sorte que la valeur est égale à true.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Date de transition de l’étape précédente, en fonction de l’ordre de classement.</p>
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
        <p>Date de transition de l’étape suivante, en fonction de l’ordre de classement.</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’enregistrement de transition est considéré comme supprimé ou non.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Pages vues collectées lors de visites web. Plusieurs pages vues peuvent composer une seule session.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique de la page vue.</p>
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
        <p>ID de cookie enregistré au moment où la page vue a été consignée.</p>
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
        <p>Le premier cookie de l’identifiant visiteur associé.</p>
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
        <p>L’ID de session est corrélé avec la page vue.</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>URL de la page vue, y compris les paramètres de requête.</p>
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
        <p>Adresse IP enregistrée au moment de l’envoi du formulaire.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
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
        <p>PageVue</p>
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
        <p>Mozilla/5.0 (X11) Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0</p>
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
        <p>Indique l’ordre dans lequel la page vue s’est produite au cours de la session.</p>
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
      <td>Utilisé pour le contrôle et le traitement internes.</td>
      <td>
        <p>103532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Utilisé pour le traitement interne.</td>
      <td>vrai</td>
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
        <p>URL d’où provient la page vue, y compris les paramètres de requête.</p>
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
        <p>Guide du CMO pour le téléchargement d’attribution marketing B2B</p>
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
        <p>Adresse électronique fournie sur un formulaire, telle qu’elle est capturée dans le JavaScript.</p>
      </td>
      <td>personc@adobe.com</td>
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
      <td>Clé étrangère dans la table d’URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Clé étrangère dans la table d’URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>HAS_USER_CONSENT</td>
      <td>booléenne</td>
      <td>Indique si l’utilisateur a consenti au suivi. False signifie que la page vue a été collectée, car le consentement de l’utilisateur n’est pas obligatoire. True signifie que la page vue a été collectée et que l’utilisateur a donné son consentement pour le suivi.</td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Tableau qui stocke tous les emplacements téléchargés à partir de n’importe quel compte de publicité connecté, un objet de l’intégration Doubleclick.

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
      <th>Données d’exemple</th>
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
      <td>Identifiant de référencement du système source.</td>
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
        <p>Identifiant de l’annonceur pour l’emplacement, en particulier pour le double-clic.</p>
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
        <p>Nom de l’annonceur pour l’emplacement, plus particulièrement pour Doubleclick.</p>
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
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de l’emplacement dans une hiérarchie de publicités.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de l’emplacement dans une hiérarchie de publicités.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne pour l’emplacement.</p>
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
        <p>Nom de la campagne pour l’emplacement.</p>
      </td>
      <td>Marketing pipeline</td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’emplacement est toujours principal dans le système source.</p>
      </td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’emplacement a été supprimé ou non dans le système source.</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom de l’emplacement, à partir du système source.</p>
      </td>
      <td>Marché</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’emplacement doit être mis à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé par le traitement interne.)</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Placement".</p>
      </td>
      <td>Positionnement</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du fournisseur de publicités pour l’emplacement.</p>
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
      <td>Date de création de l’enregistrement par le Snowflake</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de modification de l’enregistrement par le Snowflake</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake date de suppression de l’enregistrement si celle-ci a été supprimée</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENTS {#biz-segments}

Valeurs de segment telles que définies dans la variable [!DNL Marketo Measure] application.

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
        <p>Données d’exemple</p>
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
        <p>NOM</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Mappe le nom du segment personnalisé à sa valeur de catégorie. (Cela mappe les noms de colonne aux en-têtes de colonne Catégorie 1 à 15 trouvés dans les tableaux de points de contact.)

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
        <p>Données d’exemple</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>CATÉGORIE</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
      <td>IS_PRINCIPAL</td>
      <td>booléenne</td>
      <td>Indique si la catégorie est en cours d’utilisation.</td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booléenne</td>
      <td>Indique si l’enregistrement est supprimé.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Sessions telles qu’elles sont traitées à partir des pages vues. Plusieurs pages vues peuvent constituer une session et un seul identifiant visiteur peut être associé à plusieurs sessions.

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
        <p>Données d’exemple</p>
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
        <p>Le premier cookie de l’identifiant visiteur associé.</p>
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
        <p>ID de cookie enregistré de la session.</p>
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
        <p>DATE DE MODIFICATION</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de la dernière modification de l’enregistrement.</p>
      </td>
      <td>
        <p>2018-09-01 03:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>IS_FIRST_SESSION</td>
      <td>booléenne</td>
      <td>Indique s’il s’agit de la première session de l’identifiant visiteur.</td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>
        <p>CANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal attribué à la session, tel que défini par les définitions de canal définies dans la variable [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Recherche payante.AdWords</p>
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
        <p>Google Analytics Salesforce | [!DNL Marketo Measure]</p>
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
        <p>URL de la première page vue de la session, sans paramètres de requête.</p>
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
        <p>URL de la première page vue de la session, y compris les paramètres de requête.</p>
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
        <p>URL d’où provient la session, sans paramètres de requête.</p>
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
        <p>URL d’où provient la session, y compris les paramètres de requête.</p>
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
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour rechercher et qui a fini sur le site web.</p>
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
        <p>Utilisé pour définir la source qui a abouti à la session. Il peut être analysé à partir de l’URL à partir de utm_source ou défini sur un fournisseur de publicités si [!DNL Marketo Measure] peut résoudre une publicité.</p>
      </td>
      <td>
        <p>Google AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_FORM</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la Session contenait ou non un Form fill,</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CHAT</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la Session contenait ou non une discussion web.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_EMAIL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la session avait ou non une adresse électronique.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CRM_ACTIVITY</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si la session provient ou non d'un enregistrement d'activité CRM.</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Navigateur et système d’exploitation de l’utilisateur pendant la session.</p>
      </td>
      <td>
        <p>Chrome (6.5.0), Windows (6.1)</p>
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
        <p>La plateforme publicitaire [!DNL Marketo Measure] résolu à partir de, généralement l’un de nos partenaires d’intégration.</p>
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
        <p>Identifiant du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Identifiant de l’annonceur à partir duquel la publicité a été résolue, en particulier à partir de la connexion Doubleclick.</p>
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
        <p>Nom de l’annonceur à partir duquel la publicité a été résolue, en particulier à partir de la connexion Doubleclick.</p>
      </td>
      <td>
        <p>Analyses marketing</p>
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
        <p>Identifiant du site à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom du site à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Identifiant du lieu à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’emplacement à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>barrage routier</p>
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
        <p>Identifiant de la campagne à partir de laquelle la publicité a été résolue.</p>
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
        <p>Nom de la campagne à partir de laquelle la publicité a été résolue.</p>
      </td>
      <td>
        <p>Planification de votre webinaire sur le budget</p>
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
        <p>Identifiant du groupe publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement aux mots-clés Google.</p>
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
        <p>Nom du groupe publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement aux mots-clés Google.</p>
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
        <p>Identifiant de la publicité résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Nom de la publicité résolue depuis. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
      </td>
      <td>Promo d’hiver - Vert</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant du créatif à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du créatif à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Intégrer GA et Salesforce</p>
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
        <p>La première ligne du créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Intégration de Salesforce et Analytics à</p>
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
        <p>La deuxième ligne de l’élément créatif de la recherche dans l’annonce provient du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Optimisez les recettes. Découvrez comment.</p>
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
        <p>La page d’entrée qui clique à partir de la publicité de recherche, extraite du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom d’URL convivial affiché dans la publicité de recherche, extrait du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Identifiant du mot-clé à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du mot-clé à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>google analytics Salesforce</p>
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
        <p>Type de correspondance trouvé entre l’expression recherchée et le mot-clé acheté.</p>
      </td>
      <td>
        <p>Expression</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAGNE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Analysé à partir de l’URL d’utm_campaign.</p>
      </td>
      <td>
        <p>SU - Comptes ABC - Compétences médiatiques payantes</p>
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
        <p>Analysé à partir de l’URL de utm_source.</p>
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
        <p>Analysé à partir de l’URL de utm_medium.</p>
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
        <p>Analysé à partir de l’URL de utm_term.</p>
      </td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTENU</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Analysé à partir de l’URL à partir de utm_content.</p>
      </td>
      <td>
        <p>Rapport de référence AdWords 2016</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VILLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ville résolue à partir de l’adresse IP.</p>
      </td>
      <td>Vancouver</td>
    </tr>
    <tr>
      <td>
        <p>RÉGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La région résolue de l’adresse IP.</p>
      </td>
      <td>Colombie-Britannique</td>
    </tr>
    <tr>
      <td>
        <p>PAYS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Pays résolu à partir de l’adresse IP.</p>
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
        <p>Le fournisseur d'accès Internet de l'utilisateur</p>
      </td>
      <td>
        <p>AT&amp;T-verse</p>
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
        <p>Adresse IP enregistrée au moment de la session.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Détermine si cette session a été fusionnée avec une autre session et doit être supprimée.</p>
      </td>
      <td>
        <p>faux</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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
        <p>Données d’exemple</p>
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
      <td>Identifiant du site du système source.</td>
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
        <p>Identifiant de l’annonceur pour le site, en particulier pour Doubleclick.</p>
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
        <p>Nom de l’annonceur du site, en particulier pour Doubleclick.</p>
      </td>
      <td>
        <p>Analyses marketing</p>
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
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de Site dans une hiérarchie de publicités.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Être nul, car il n’y a aucun groupe publicitaire au-dessus de Site dans une hiérarchie de publicités.</p>
      </td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne pour le site.</p>
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
        <p>Nom de la campagne du site.</p>
      </td>
      <td>Attribution des recettes</td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le site est toujours principal ou non dans le système source.</p>
      </td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le site a été supprimé ou non dans le système source.</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Date à laquelle l’enregistrement a été importé pour la première fois à partir du système source.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du site, à partir du système source.</p>
      </td>
      <td>Chiffre d'affaires</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le site doit être mis à jour ou non pour [!DNL Marketo Measure] balisage.</p>
        <p>(Champ de diagnostic, utilisé pour le traitement interne.)</p>
      </td>
      <td>faux</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Champ de diagnostic, utilisé pour le traitement interne.</td>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "Site".</p>
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
        <p>Nom du fournisseur de publicités du site.</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Liens de sites à partir de n’importe quel compte publicitaire connecté.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique du lien du site</p>
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
        <p>L’identifiant du compte de publicités connecté pour le lien du site</p>
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
        <p>Nom du compte de publicités connectées pour le lien du site.</p>
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
        <p>Identifiant de l’annonceur pour le lien du site, en particulier pour Doubleclick.</p>
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
        <p>Nom de l’annonceur pour le lien du site, en particulier pour Doubleclick.</p>
      </td>
      <td>
        <p>Analyses marketing</p>
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
        <p>Identifiant du groupe publicitaire pour le lien du site.</p>
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
        <p>Nom du groupe publicitaire pour le lien du site</p>
      </td>
      <td>Marque - Core</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant de la campagne pour le lien du site</p>
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
        <p>Nom de la campagne pour le lien du site</p>
      </td>
      <td>
        <p>Brand Marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PRINCIPAL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le lien du site est toujours principal ou non dans le compte publicitaire</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le lien du site a été supprimé ou non dans le compte publicitaire</p>
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
        <p>Date de dernière modification de la ligne</p>
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
        <p>NOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nom du lien du site.</p>
      </td>
      <td>Lien A</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le lien du site doit être mis à jour ou non pour obtenir le balisage Markto Mesurer</p>
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
        <p>Objet ou entité principal de ce tableau. Dans ce cas, "SiteLink"</p>
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
        <p>Nom du fournisseur d’annonces pour le lien du site</p>
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
        <p>URL de la landing page.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
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
        <p>L’URL qui sera décorée [!DNL Marketo Measure] paramètres.</p>
        <p>(Champ de diagnostic, pour le traitement interne.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de création de l’enregistrement par le Snowflake</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de modification de l’enregistrement par le Snowflake</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake date de suppression de l’enregistrement si celle-ci a été supprimée</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_STAGE_DEFINITIONS {#biz-stage-definitions}

Liste des étapes, telles qu&#39;importées ou définies dans la [!DNL Marketo Measure] application.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique de la scène.</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Verbal</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_INACTIVE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Indique si l’environnement intermédiaire est considéré comme inactif.</td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IN_CUSTOM_MODEL</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’évaluation est sélectionnée pour le suivi dans le modèle personnalisé.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_BOOMERANG</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’étape est sélectionnée pour le suivi en tant qu’étape de boomerang.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_TRANSITION_TRACKING</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Indique si l’évaluation est sélectionnée pour effectuer le suivi des transitions.</td>
      <td>
        <p>faux</p>
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
        <p>État de l’étape, tel que défini dans la variable [!DNL Marketo Measure] mappage des environnements intermédiaires de l’application.</p>
      </td>
      <td>
        <p>Ouvrir</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FROM_SALESFORCE</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si l’environnement intermédiaire est importé à partir d’un système source externe.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DEFAULT</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>Indique si l’environnement intermédiaire est défini comme valeur par défaut.</td>
      <td>
        <p>faux</p>
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
        <p>Classement numérique de la scène, utilisé pour trier les étapes par ordre transitoire.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Si l’environnement intermédiaire a été supprimé ou non.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Points de contact d’achat, tous les points de contact associés à un prospect ou à un contact. Cette table sera vide si les points de contact de piste ou de contact sont désactivés.

<table>
  <tbody>
    <tr>
      <th>Colonne</th>
      <th>Type de données</th>
      <th>Description</th>
      <th>Données d’exemple</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Identifiant unique du point de contact de l’acheteur (BT).</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
      <td>Adresse électronique associée au BT.</td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Enregistrement de personne parente relatif à un prospect ou à un contact.</p>
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
        <p>Identifiant du point de contact utilisateur qui a généré le BT.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-08-29:18-14-53-8102030.10df92cbb414</p>
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
        <p>Type d’activité, Visite Web, Formulaire Web, Chat Web, Appel téléphonique, Campagne [CRM] ou Activité [CRM]. Appelé dans le CRM "Type de point de contact".</p>
      </td>
      <td>
        <p>Formulaire Web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal dans lequel se trouve le point de contact, tel que défini dans les définitions de canal personnalisées dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Canal marketing - Chemin".</p>
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
        <p>La valeur de segment de la 1ère catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>La valeur de segment de la 2e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>La valeur de segment de la 3e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
      </td>
      <td>
        <p>Autre</p>
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
        <p>La valeur de segment de la 4e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>La valeur du segment de la 5e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>La valeur de segment de la 6e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
      <td>La valeur du segment de la 7e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur du segment de la 8e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur du segment de la 9e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 10e catégorie dans laquelle se trouve le point de contact, telle que définie dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 11e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur de segment de la 12e catégorie dans laquelle se trouve le point de contact, telle que définie dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La valeur du segment de la 13e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</td>
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
        <p>La valeur de segment de la 14e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>La valeur de segment de la 15e catégorie dans laquelle se trouve le point de contact, comme défini dans les définitions de segment dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Segments".</p>
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
        <p>À partir du javascript et de l’adresse IP, le navigateur détecté par l’utilisateur pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la version détectée du navigateur que l’utilisateur a utilisé pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la plateforme détectée par l’utilisateur pendant la session.</p>
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
        <p>À partir du code JavaScript et de l’adresse IP, la version détectée de la plateforme sur laquelle l’utilisateur s’était rendu au cours de la session.</p>
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
        <p>Première page d’entrée de la session qui a généré un point de contact. On parle dans le CRM de "Landing Page".</p>
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
        <p>Première page d’entrée de la session qui a généré un point de contact. Une landing page brute contiendra tous les paramètres de requête dans l’URL. On parle dans le CRM de "Landing Page - Raw" (Page d’entrée - Brut).</p>
      </td>
      <td>
        <p>https://info.adpbe.com/definitive-guide-to-pipeline-marketing?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU_COM_Demand_/Skills&amp;utm_content=DGPM&amp;utm_term=lisu03151846&amp;_bl=66452504</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Référencé dans le CRM sous le nom de "Page de référent".</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Une page de référent brute peut contenir des paramètres de requête dans l’URL. Référencé dans le CRM sous le nom "Page du référent - Brut".</p>
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
        <p>Premier formulaire enregistré dans une session qui générait un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans le tableau Points de contact, mais dans le tableau Form_Submits . Appelé dans le CRM "URL du formulaire".</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>FORM_PAGE_RAW</td>
      <td>varchar</td>
      <td>Premier formulaire enregistré dans une session qui générait un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans le tableau Points de contact, mais dans le tableau Form_Submits . Une page de formulaire brut peut contenir des paramètres de requête dans l’URL. Référencé dans le CRM sous le nom "URL du formulaire - Brut".</td>
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
        <p>VILLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du javascript et de l’adresse IP, la ville détectée dans laquelle se trouvait l’utilisateur au cours de la session.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RÉGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du javascript et de l’adresse IP, la région détectée de l’utilisateur au cours de la session.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAYS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du code JavaScript et de l’adresse IP, le pays dans lequel l’utilisateur se trouvait pendant la session a été détecté.</p>
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
        <p>Utilisé pour définir le support qui a généré le point de contact. Cela peut être analysé à partir de l’URL à partir de utm_medium. Ou, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que "cpc" ou "display".</p>
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
        <p>Utilisé pour définir la source qui a généré le point de contact. Il peut être analysé à partir de l’URL de utm_source, défini de manière générique comme "Campaign CRM" s’il a été synchronisé à partir du CRM ou si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que "Google AdWords" ou "Facebook". On parle dans le CRM de "source du point de contact".</p>
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
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour rechercher et qui a fini sur le site web. En fonction des achats de mots-clés, cela peut correspondre ou non aux mots-clés achetés sur la plateforme de recherche payante.</p>
      </td>
      <td>
        <p>mesure de l’attribution par markeot</p>
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
        <p>Plateforme publicitaire [!DNL Marketo Measure] a pu résoudre à partir de, généralement l’un de nos partenaires d’intégration.</p>
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
        <p>Identifiant du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Identifiant de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Identifiant du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Identifiant de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>barrage routier</p>
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
        <p>Identifiant de la campagne du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom de la campagne à partir du compte publicitaire duquel la publicité a été résolue.</p>
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
        <p>Identifiant du groupe publicitaire du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement aux mots-clés Google.</p>
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
        <p>Nom du groupe publicitaire du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement à Google AdWords.</p>
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
        <p>Identifiant de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Nom de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Identifiant du créatif du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du créatif du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>La première ligne du créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Génération de piste terminée</p>
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
        <p>La deuxième ligne de l’élément créatif de la recherche dans l’annonce provient du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Téléchargez le guide définitif sur le marketing de pipeline : https://lnkd.in/e9xYj5M</p>
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
        <p>La page d’entrée qui clique à partir de la publicité de recherche, extraite du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom d’URL convivial affiché dans la publicité de recherche, extrait du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Identifiant du mot-clé acheté à partir de la recherche payante, tiré du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du mot-clé acheté à partir de la recherche payante, tiré du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Type de correspondance trouvé entre l’expression recherchée et le mot-clé acheté.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la première touche du parcours d’opportunité.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la touche de création de piste du parcours d’opportunité.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la touche de création d’opportunités du parcours d’opportunité.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si ce point de contact est traité ou non comme la touche fermée du parcours d’opportunité.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>STAGES_TOUCHED</td>
      <td>varchar</td>
      <td>Ce champ est obsolète. Utilisez les tableaux Stage_Transitions pour obtenir des informations sur l’étape.</td>
      <td>nul</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact a été rempli par un formulaire au cours de la session.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si ce point de contact est traité ou non comme la première impression du parcours d’opportunité</p>
      </td>
      <td>
        <p>faux</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit d’une Première touche (voir Is_First_Touch).</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il s’agit d’une touche de création de piste (voir Is_Lead_Creation_Touch).</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’une touche en forme de U (voir Is_First_Touch et Is_Lead_Creation_Touch).</p>
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
        <p>Pourcentage calculé attribué à ce point de contact, car il fait partie d’une touche en forme de w (voir Is_First_Touch, Is_Lead_Creation_Touch et Is_Opp_Creation_Touch). Il devrait être égal à 0 car il s'agit d'un BT.</p>
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
        <p>Le pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle de chemin complet (voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Il devrait être égal à 0 car il s'agit d'un BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_MODEL_PERCENTAGE</td>
      <td>number(22,19)</td>
      <td>Pourcentage calculé attribué à ce point de contact, car il fait partie d’un modèle personnalisé (Voir Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Il devrait être égal à 0 car il s'agit d'un BT.</p>
      </td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si ce point de contact est supprimé.</p>
      </td>
      <td>
        <p>faux</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Agrégation des URL à partir des landing pages, des pages référentes et des pages vues.

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
        <p>Données d’exemple</p>
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
        <p>L’URL complète,</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/strategic-marketing-plangoals</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SCHÉMA</p>
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
        <p>HÔTE</p>
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
        <p>CHEMIN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Partie de l’URL qui pointe vers un emplacement spécifique sur l’hôte.</p>
      </td>
      <td>
        <p>/blog/strategy-marketing-plangoals</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Tous les points de contact créés à partir de n’importe quel événement lié à un email.

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
        <p>Données d’exemple</p>
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
        <p>Identifiant unique du point de contact de l’utilisateur.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-01-05:16-47-02-8803320.ddf67c101f58</p>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
        <p>Adresse électronique associée au point de contact de l’utilisateur.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
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
        <p>Identifiant de la session qui a créé le point de contact de l’utilisateur.</p>
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
        <p>Identifiant du membre de campagne qui a créé le point de contact de l’utilisateur.</p>
      </td>
      <td>
        <p>00v0Z00001VTgv1QAD</p>
      </td>
    </tr>
    <tr>
      <td>CRM_ACTIVITY_ID</td>
      <td>varchar</td>
      <td>Identifiant de l’activité qui a créé le point de contact de l’utilisateur.</td>
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
        <p>Identifiant de l’événement qui a créé le point de contact de l’utilisateur.</p>
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
        <p>Identifiant de la tâche qui a créé le point de contact de l’utilisateur.</p>
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
        <p>Identifiant de l’impression qui a créé le point de contact de l’utilisateur.</p>
      </td>
      <td>00T0Z00004Qbd1jUAB</td>
    </tr>
    <tr>
      <td>IS_FIRST_KNOWN_TOUCH</td>
      <td>booléenne</td>
      <td>Indique si ce point de contact est traité comme la première touche du parcours d’opportunité.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Le premier ID de cookie de l’ID de visiteur associé.</td>
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
        <p>Date à laquelle le point de contact de l’utilisateur s’est produit.</p>
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
        <p>Type d’activité, Visite Web, Formulaire Web, Chat Web, Appel téléphonique, Campagne [CRM] ou Activité [CRM]. Appelé dans le CRM "Type de point de contact".</p>
      </td>
      <td>
        <p>Formulaire Web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canal dans lequel se trouve le point de contact, tel que défini dans les définitions de canal personnalisées dans la variable [!DNL Marketo Measure] Application. Appelé dans le CRM "Canal marketing - Chemin".</p>
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
        <p>À partir du javascript et de l’adresse IP, le navigateur détecté par l’utilisateur pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la version détectée du navigateur que l’utilisateur a utilisé pendant la session.</p>
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
        <p>À partir du javascript et de l’adresse IP, la plateforme détectée par l’utilisateur pendant la session.</p>
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
        <p>À partir du code JavaScript et de l’adresse IP, la version détectée de la plateforme sur laquelle l’utilisateur s’était rendu au cours de la session.</p>
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
        <p>Première page d’entrée de la session qui a généré un point de contact. On parle dans le CRM de "Landing Page".</p>
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
        <p>Première page d’entrée de la session qui a généré un point de contact. Une landing page brute contiendra tous les paramètres de requête dans l’URL. On parle dans le CRM de "Landing Page - Raw" (Page d’entrée - Brut).</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Référencé dans le CRM sous le nom de "Page de référent".</p>
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
        <p>En règle générale, la page d’entrée externe juste avant que l’utilisateur ne vienne sur le site web. Une page de référent brute peut contenir des paramètres de requête dans l’URL. Référencé dans le CRM sous le nom "Page du référent - Brut".</p>
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
        <p>Premier formulaire enregistré dans une session qui générait un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans le tableau Attribution_Touchpoints , mais plutôt dans le tableau Form_Submits . Appelé dans le CRM "URL du formulaire".</p>
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
        <p>Premier formulaire enregistré dans une session qui générait un point de contact. Les envois de formulaire suivants ne s’afficheront pas dans le tableau Attribution_Touchpoints , mais plutôt dans le tableau Form_Submits . Une page de formulaire brut peut contenir des paramètres de requête dans l’URL. Référencé dans le CRM sous le nom "URL du formulaire - Brut".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation?utm_source=linkedin&amp;utm_medium=paid&amp;utm_content=sfskill&amp;utm_campaign=Content%20-%20AdWords%20Guide</p>
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
        <p>VILLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du javascript et de l’adresse IP, la ville détectée dans laquelle se trouvait l’utilisateur au cours de la session.</p>
      </td>
      <td>
        <p>Oakland</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RÉGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du javascript et de l’adresse IP, la région détectée de l’utilisateur au cours de la session.</p>
      </td>
      <td>
        <p>Californie</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAYS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>À partir du code JavaScript et de l’adresse IP, le pays dans lequel l’utilisateur se trouvait pendant la session a été détecté.</p>
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
        <p>Utilisé pour définir le support qui a généré le point de contact. Cela peut être analysé à partir de l’URL à partir de utm_medium. Ou, si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que "cpc" ou "display".</p>
      </td>
      <td>
        <p>paid</p>
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
        <p>Utilisé pour définir la source qui a généré le point de contact. Il peut être analysé à partir de l’URL de utm_source, défini de manière générique comme "Campaign CRM" s’il a été synchronisé à partir du CRM ou si [!DNL Marketo Measure] peut résoudre une publicité, il peut s’agir de valeurs telles que "Google AdWords" ou "Facebook". On parle dans le CRM de "source du point de contact".</p>
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
        <p>Valeur que l’utilisateur a saisie dans le navigateur pour rechercher et qui a fini sur le site web. En fonction des achats de mots-clés, cela peut correspondre ou non aux mots-clés achetés sur la plateforme de recherche payante.</p>
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
        <p>Plateforme publicitaire [!DNL Marketo Measure] a pu résoudre à partir de, généralement l’un de nos partenaires d’intégration.</p>
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
        <p>Identifiant du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Identifiant de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’annonceur du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>Analyses marketing</p>
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
        <p>Identifiant du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom du site du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Identifiant de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
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
        <p>Nom de l’emplacement du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement au double-clic sur le Gestionnaire de campagnes.</p>
      </td>
      <td>
        <p>barrage routier</p>
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
        <p>Identifiant de la campagne du compte publicitaire à partir duquel la publicité a été résolue.</p>
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
        <p>Nom de la campagne à partir du compte publicitaire duquel la publicité a été résolue.</p>
      </td>
      <td>
        <p>Brand Marketing</p>
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
        <p>Identifiant du groupe publicitaire du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement aux mots-clés Google.</p>
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
        <p>Nom du groupe publicitaire du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique uniquement à Google AdWords.</p>
      </td>
      <td>
        <p>Marque - Core</p>
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
        <p>Identifiant de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Nom de la publicité du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique au double-clic sur Gestionnaire de campagnes et Facebook (affichage).</p>
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
        <p>Identifiant du créatif du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du créatif du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>La première ligne du créatif de l’annonce de recherche, extraite du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Planification et attribution des recettes</p>
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
        <p>La deuxième ligne de l’élément créatif de la recherche dans l’annonce provient du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
      </td>
      <td>
        <p>Découvrez pourquoi plus de 250 entreprises choisissent [!DNL Marketo Measure] pour l’attribution marketing. Faites une démonstration !</p>
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
        <p>La page d’entrée qui clique à partir de la publicité de recherche, extraite du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom d’URL convivial affiché dans la publicité de recherche, extrait du compte publicitaire à partir duquel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Identifiant du mot-clé acheté à partir de la recherche payante, tiré du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Nom du mot-clé acheté à partir de la recherche payante, tiré du compte publicitaire dans lequel la publicité a été résolue. Cela s’applique à Google AdWords et Bing Ads (recherche).</p>
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
        <p>Type de correspondance trouvé entre l’expression recherchée et le mot-clé acheté.</p>
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
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact a été rempli par un formulaire au cours de la session.</p>
      </td>
      <td>
        <p>vrai</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Indique si ce point de contact est traité comme la première touche d’impression du parcours d’opportunité.</p>
      </td>
      <td>
        <p>faux</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booléenne</p>
      </td>
      <td>
        <p>Si le point de contact est supprimé ou non.</p>
      </td>
      <td>
        <p>faux</p>
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
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

Mappage d’un tableau à un mappage [!DNL Marketo Measure] Identifiant de session pour l’Adobe de l’ECID et de l’ID Munckin.

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
        <p>Données d’exemple</p>
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
      <td>Le [!DNL Marketo Measure] identifiant de cookie enregistré.</td>
      <td>0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Le premier ID de cookie de l’ID de visiteur associé.</td>
      <td>v_0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Le [!DNL Marketo Measure] ID de session.</td>
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
        <p>Date de la dernière modification de l’enregistrement.</p>
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
      <td>URL de la page vue, y compris les paramètres de requête.</td>
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
        <p>159.203.142.127</p>
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
      <td>Appareil et navigateur enregistrés au moment de la consultation de page.</td>
      <td>
        <p>Mozilla/5.0 (Windows NT 10.0 ; Win64 ; x64) AppleWebKit/537.36 (KHTML, comme Gecko) Chrome/79.0.3945.130 Safari/537.36</p>
      </td>
    </tr>
    <tr>
      <td>CLIENT_SEQUENCE</td>
      <td>varchar</td>
      <td>Indique l’ordre dans lequel la page vue s’est produite au cours de la session.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>CLIENT_RANDOM</td>
      <td>varchar</td>
      <td>Utilisé pour le contrôle et le traitement internes.</td>
      <td>566868</td>
    </tr>
    <tr>
      <td>IS_DUPLICATED</td>
      <td>booléenne</td>
      <td>Indique si l’enregistrement est considéré comme un doublon.</td>
      <td>faux</td>
    </tr>
    <tr>
      <td>IS_PROCESSED</td>
      <td>booléenne</td>
      <td>Utilisé pour le traitement interne.</td>
      <td>vrai</td>
    </tr>
    <tr>
      <td>MAPPING_TYPE</td>
      <td>varchar</td>
      <td>Le type d’ID associé au [!DNL Marketo Measure] ID de cookie.</td>
      <td>Adobe_OrgId_Ecid</td>
    </tr>
    <tr>
      <td>MAPPING_ORD_ID</td>
      <td>varchar</td>
      <td>Identifiant de l’organisation Adobe IMS.</td>
      <td>8CC867C25245ADC30A490D4C</td>
    </tr>
    <tr>
      <td>MAPPING_COOKIE_ID</td>
      <td>varchar</td>
      <td>Adobe de l’ECID pour l’ID d’organisation donné.</td>
      <td>09860926390077352923264316157493772857</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date à laquelle l’enregistrement a été créé en Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date de la dernière modification de l’enregistrement en Snowflake.</td>
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

**Combien de points de contact d’achat (BT) y avait-il pour chaque canal/sous-canal le mois dernier ?**

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

**Quel est le montant des recettes attribuées pour chaque canal qui a été fermé le mois dernier, pour le modèle d’attribution de chemin complet ?**

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

**Quel est le parcours complet d&#39;une seule personne ?  (Afficher tous les points de contact pour une seule adresse électronique.)**

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

**Afficher tous les points de contact d’attribution d’achat et leurs recettes affectées pour une seule opportunité.**

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

[Retour haut de page](#data-warehouse-schema)
