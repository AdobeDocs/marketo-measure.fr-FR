---
unique-page-id: 18874789
description: "[!DNL Marketo Measure] Jeux d’autorisations - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Jeux d’autorisations"
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 3%

---

# Jeux d’autorisations [!DNL Marketo Measure] {#marketo-measure-permission-sets}

Découvrez comment accéder à et affecter [!DNL Marketo Measure] Jeux d’autorisations dans Salesforce.

## Jeux d’autorisations [!DNL Marketo Measure] {#marketo-measure-permission-sets-1}

Trois jeux d’autorisations sont inclus dans la variable [!DNL Marketo Measure] Package Salesforce. Ces jeux d’autorisations permettent d’accéder à [!DNL Marketo Measure] pour les administrateurs, les marketeurs et les utilisateurs standard.

Pour accéder aux jeux d’autorisations et les attribuer dans Salesforce :

1. Cliquez sur **[!UICONTROL Configuration]**.
1. Dans la marge de gauche, cliquez sur **[!UICONTROL Utilisateurs]**, puis **[!UICONTROL Jeux d’autorisations]**.
1. Sélectionnez la variable [!DNL Marketo Measure] Jeu d’autorisations que vous souhaitez affecter.
1. Cliquez sur **[!UICONTROL Gestion des affectations]**, puis **[!UICONTROL Ajouter des affectations]**.
1. Sélectionnez les utilisateurs du jeu d’autorisations, puis cliquez sur **[!UICONTROL Attribuer]**.

   ![](assets/1-5.png)

## [!DNL Marketo Measure] Explication des jeux d’autorisations {#marketo-measure-permission-sets-explained}

<table> 
 <tbody> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Administrateur</strong></span></td> 
   <td><span>Permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements depuis [!DNL Marketo Measure] objets. La licence sous laquelle [!DNL Marketo Measure] Ce jeu d’autorisations doit être activé pour les données envoyées à SFDC. En outre, il est recommandé que cette licence ait la possibilité de modifier les pistes converties dans les cas où la piste est convertie avant [!DNL Marketo Measure] l’application de données à l’enregistrement. Cela garantit la précision des rapports entre Salesforce et [!DNL Marketo Measure]. <a href="https://help.salesforce.com/articleView?id=release-notes.rn_sales_leads_view_converted.htm&amp;type=5&amp;release=206&amp;language=en_us">En savoir plus ici</a>.</span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utilisateur marketing</strong></span></td> 
   <td><span>Permet à un utilisateur marketing de lire et d’écrire des enregistrements depuis [!DNL Marketo Measure] objets. Tous les membres de l’équipe marketing doivent avoir la variable [!DNL Marketo Measure] Jeu d’autorisations des utilisateurs marketing activé. <br></span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utilisateur standard</strong></span></td> 
   <td><span>Permet à l’utilisateur de lire des enregistrements depuis [!DNL Marketo Measure] objets.</span></td> 
  </tr> 
 </tbody> 
</table>

Les équipes de développement des ventes entrantes et les dirigeants de compte peuvent bénéficier de [!DNL Marketo Measure] data. Si ces rôles souhaitent utiliser [!DNL Marketo Measure] données dans les rapports, activez l’option [!DNL Marketo Measure] Jeu d’autorisations Utilisateur standard.

>[!NOTE]
>
>En outre, l’utilisateur auquel nous sommes connectés doit avoir un &quot;utilisateur marketing&quot;. [!DNL Salesforce] Profil activé au niveau de l’utilisateur pour que nous puissions accéder à l’objet Campaign. Pour vérifier cela, cliquez sur **[!UICONTROL Configuration]** > **[!UICONTROL Gestion des utilisateurs]** > **[!UICONTROL Profils]** > **[!UICONTROL Utilisateur marketing]** > **Utilisateurs affectés**.
