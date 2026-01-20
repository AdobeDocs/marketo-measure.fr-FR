---
unique-page-id: 18874523
description: Schéma [!DNL Marketo Measure] Dynamics - [!DNL Marketo Measure]
title: Schéma de Dynamics et de [!DNL Marketo Measure]
exl-id: f8da47b1-d844-4bd2-8125-8689cbb5cc30
feature: Microsoft Dynamics
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 66%

---

# Schéma de Dynamics et de [!DNL Marketo Measure] {#marketo-measure-dynamics-schema}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Vous trouverez ci-dessous le schéma Dynamics requis pour commencer à utiliser [!DNL Marketo Measure]. Toutes les entités et tous les champs sont répertoriés, ainsi que l’accès en lecture et/ou écriture requis.

## Buyer Touchpoints {#buyer-touchpoints}

Le Buyer Touchpoint est une entité personnalisée [!DNL Marketo Measure] pour encapsuler les interactions marketing pour les contacts et les leads.

## Relations de Buyer Touchpoint {#buyer-touchpoint-relationships}

Ce diagramme est une visualisation générale des relations entre les entités Dynamics Stock et le Buyer Touchpoint.

## Buyer Touchpoint {#buyer-touchpoint}

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Content</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Destination_URL</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_TouchpointId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Browser</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_CampaignId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_ContactId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_First_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Lead_Conversion_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_U_Shaped</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL_Raw</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Geo_City</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Geo_Country</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Geo_Region</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_MatchType</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Text</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_Raw</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_LeadId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_Path</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Medium</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Platform</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page_Raw</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Search_Phrase</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Segment</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Site_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Site_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Position</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Type</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_UniqueId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>compte_bizible2</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

Le Buyer Attribution Touchpoint est une entité personnalisée [!DNL Marketo Measure] pour encapsuler l’influence du marketing sur les opportunités.

## Relations de Buyer Attribution Touchpoint {#buyer-attribution-touchpoint-relationships}

Ce diagramme est une visualisation générale des relations entre les entités Dynamics Stock et le Buyer Attribution Touchpoint.

## Buyer Attribution Touchpoints {#buyer-attribution-touchpoints}

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2_AccountId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Content</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Destination_URL</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_Custom_Model</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_Custom_Model_2</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_First_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_Lead_Conversion_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_U_Shaped</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_W_Shaped</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Attribution_TouchpointId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Browser</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_CampaignId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_ContactId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Custom_Model</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Custom_Model_2</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_First_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Lead_Creation_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_U_Shaped</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_W_Shaped</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL_Raw</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Geo_City</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Geo_Country</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Geo_Region</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_MatchType</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Text</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_Raw</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_Path</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Medium</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_OpportunityId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Platform</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page_Raw</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_Custom_Model</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_Custom_Model_2</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_revenue_custom_model_2_Base</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_revenue_custom_model_Base</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_First_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_revenue_first_touch_Base</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_Lead_Conversion_Touch</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_revenue_lead_conversion_Base</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_U_Shaped</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_revenue_u_form_Base</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_W_Shaped</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_revenue_w_form_Base</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Search_Phrase</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Segment</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Site_Id</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Site_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Position</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Type</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_UniqueId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

## Tests AB [!DNL Marketo Measure] {#marketo-measure-ab-tests}

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_ABTestId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_BizibleId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_ContactId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_DateReported</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Experiment</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_ExperimentId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_LeadId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_OpportunityId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_UserId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Variation</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_VariationId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

## [!DNL Marketo Measure] Événements {#marketo-measure-events}

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_EventId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_BizibleId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_ContactId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_DateReported</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_EventName</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_EventValue</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_LeadId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_OpportunityId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

## Historique des [!DNL Marketo Measure] {#marketo-measure-history}

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_HistoryId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Entity_Type</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_EntityId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_EntityLogicalName</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Name</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

## Entités Dynamics Standard {#dynamics-standard-entities}

Cette liste fournit les entités Dynamics Standard avec lesquelles [!DNL Marketo Measure] interagit, ainsi que les champs personnalisés que nous ajoutons à ces entités.

**Lead**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>leadid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>emailaddress1</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>code d'état</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>statuscode</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>contactid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>qualificationopportunityid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>websiteurl</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>nom de la société</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>compte_bizible2</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_BizibleId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**Contact**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>contactid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>emailaddress1</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>accountid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_BizibleId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**Compte**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>accountid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>websiteurl</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Engagement_Score</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**Opportunité**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>opportunityid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>accountid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>code d'état</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>statecodename</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>salesstage</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>salesstagecode</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>estimatedclosedate</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>valeur réelle</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Opportunity_Amount</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_bizible_opportunité_amount_Base</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**Campagne**

Les autorisations « Créer » de Campaign sont également requises, en plus des autorisations de lecture/écriture ci-dessous.

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>campaignid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>typecode</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>typecodename</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Attribution_SyncType</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Lists_Sync</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_UniqueId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_End_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Start_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**Réponse de la campagne**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>activityid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>activitytypecode</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>activitytypecodename</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>code de réponse</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>responsecodename</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>client ou cliente</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>concernant objectid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Touchpoint_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Contact</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Leade</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Opportunity</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**Liste**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>listid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>createdfromcode</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>membertype</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Touchpoint_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**ListMember**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>listid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>entityid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>listmemberid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Appel téléphonique**

<table> 
 <tbody> 
  <tr> 
   <th><p>Nom du schéma</p></th> 
   <th><p>Standard/Personnalisé</p></th> 
   <th><p>Lecture</p></th> 
   <th><p>Écriture</p></th> 
  </tr> 
  <tr> 
   <td><p>activityid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>activitytypecode</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>activitytypecodename</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>créé le</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>modifiedon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>client ou cliente</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>concernant objectid</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Touchpoint_Date</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_BizibleId</p></td> 
   <td><p>Personnalisé</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

[] = clients hérités de la version V1 uniquement
