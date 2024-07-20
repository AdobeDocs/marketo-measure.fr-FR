---
unique-page-id: 18874789
description: "[!DNL Marketo Measure] Permissions Sets - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Permissions Sets"
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 3%

---

# Jeux d’autorisations [!DNL Marketo Measure] {#marketo-measure-permission-sets}

Découvrez comment accéder aux jeux d’autorisations [!DNL Marketo Measure] et les attribuer dans Salesforce.

## Jeux d’autorisations [!DNL Marketo Measure] {#marketo-measure-permission-sets-1}

Trois jeux d’autorisations sont inclus avec le package [!DNL Marketo Measure] Salesforce. Ces jeux d’autorisations permettent aux administrateurs, aux marketeurs et aux utilisateurs standard d’accéder à [!DNL Marketo Measure].

Pour accéder aux jeux d’autorisations et les attribuer dans Salesforce :

1. Cliquez sur **[!UICONTROL Configuration]**.
1. Dans la marge de gauche, cliquez sur **[!UICONTROL Utilisateurs]**, puis sur **[!UICONTROL Jeux d’autorisations]**.
1. Sélectionnez le jeu d’autorisations [!DNL Marketo Measure] que vous souhaitez affecter.
1. Cliquez sur **[!UICONTROL Gérer les affectations]**, puis **[!UICONTROL Ajouter des affectations]**.
1. Sélectionnez les utilisateurs du jeu d’autorisations et cliquez sur **[!UICONTROL Attribuer]**.

   ![](assets/1-5.png)

## [!DNL Marketo Measure] Explication des jeux d’autorisations {#marketo-measure-permission-sets-explained}

<table> 
 <tbody> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Administrateur</strong></span></td> 
   <td><span>Permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements des objets [!DNL Marketo Measure]. Ce jeu d’autorisations doit être activé pour la licence sous laquelle [!DNL Marketo Measure] envoie des données à SFDC. En outre, il est recommandé que cette licence ait la possibilité de modifier les pistes converties dans les scénarios où la piste est convertie avant l’application de données à l’enregistrement [!DNL Marketo Measure]. Cela garantit la précision des rapports entre Salesforce et [!DNL Marketo Measure]. <a href="https://help.salesforce.com/articleView?id=release-notes.rn_sales_leads_view_converted.htm&amp;type=5&amp;release=206&amp;language=en_us">En savoir plus ici</a>.</span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utilisateur marketing</strong></span></td> 
   <td><span>Permet à un utilisateur marketing de lire et d’écrire des enregistrements à partir d’objets [!DNL Marketo Measure]. L’autorisation [!DNL Marketo Measure] Utilisateur marketing doit être activée pour tous les membres de l’équipe marketing. <br></span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utilisateur standard</strong></span></td> 
   <td><span>Permet à un utilisateur de lire des enregistrements à partir d’objets [!DNL Marketo Measure].</span></td> 
  </tr> 
 </tbody> 
</table>

Les équipes de développement des ventes entrantes et les dirigeants de compte peuvent bénéficier de [!DNL Marketo Measure] données. Si ces rôles souhaitent utiliser les données [!DNL Marketo Measure] dans les rapports, activez l’ensemble d’autorisations Utilisateur standard [!DNL Marketo Measure].

>[!NOTE]
>
>En outre, le profil &quot;Utilisateur marketing&quot; [!DNL Salesforce] doit être activé au niveau de l’utilisateur pour que nous puissions accéder à l’objet Campaign. Pour vérifier cela, cliquez sur **[!UICONTROL Configuration]** > **[!UICONTROL Gérer les utilisateurs]** > **[!UICONTROL Profils]** > **[!UICONTROL Utilisateur marketing]** > **Utilisateurs affectés**.
