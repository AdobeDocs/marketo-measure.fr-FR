---
unique-page-id: 18874789
description: Jeux D’Autorisations [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Jeux d’autorisations [!DNL Marketo Measure]
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
feature: Salesforce
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 4%

---

# Jeux d’autorisations [!DNL Marketo Measure] {#marketo-measure-permission-sets}

Découvrez comment accéder aux jeux d’autorisations [!DNL Marketo Measure] et les attribuer dans Salesforce.

## Jeux d’autorisations [!DNL Marketo Measure] {#marketo-measure-permission-sets-1}

Trois jeux d’autorisations sont inclus dans le package Salesforce [!DNL Marketo Measure]. Ces jeux d’autorisations permettent aux administrateurs, aux spécialistes du marketing et aux utilisateurs standard d’accéder à [!DNL Marketo Measure].

Pour accéder aux jeux d’autorisations et les attribuer dans Salesforce :

1. Cliquez sur **[!UICONTROL Configurer]**.
1. Dans la marge de gauche, cliquez sur **[!UICONTROL Utilisateurs]**, puis **[!UICONTROL Jeux d’autorisations]**.
1. Sélectionnez le jeu d’autorisations [!DNL Marketo Measure] que vous souhaitez affecter.
1. Cliquez sur **[!UICONTROL Gérer les affectations]**, puis sur **[!UICONTROL Ajouter des affectations]**.
1. Sélectionnez les utilisateurs pour le jeu d’autorisations et cliquez sur **[!UICONTROL Attribuer]**.

   ![](assets/1-5.png)

## Explication des jeux d’autorisations [!DNL Marketo Measure] {#marketo-measure-permission-sets-explained}

<table> 
 <tbody> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Administrateur</strong></span></td> 
   <td><span>Permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements des objets [!DNL Marketo Measure]. Ce jeu d’autorisations doit être activé pour la licence sous laquelle [!DNL Marketo Measure] transmet des données à SFDC. En outre, il est recommandé que cette licence ait la possibilité de modifier les prospects convertis dans les scénarios où le prospect est converti avant d’appliquer [!DNL Marketo Measure] données à l’enregistrement. Cela garantit la précision des rapports entre Salesforce et [!DNL Marketo Measure]. <a href="https://help.salesforce.com/articleView?id=release-notes.rn_sales_leads_view_converted.htm&amp;type=5&amp;release=206&amp;language=en_us">En savoir plus ici</a>.</span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utilisateur marketing</strong></span></td> 
   <td><span>Permet à un utilisateur ou une utilisatrice marketing de lire et d’écrire des enregistrements à partir d’objets [!DNL Marketo Measure]. Tous les membres de l’équipe marketing doivent disposer du jeu d’autorisations Utilisateur marketing [!DNL Marketo Measure] activé. <br></span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utilisateur standard</strong></span></td> 
   <td><span>Permet à l’utilisateur de lire des enregistrements provenant d’objets [!DNL Marketo Measure].</span></td> 
  </tr> 
 </tbody> 
</table>

Les équipes de développement des ventes entrantes et les directeurs de compte peuvent bénéficier des données [!DNL Marketo Measure]. Si ces rôles souhaitent utiliser des données [!DNL Marketo Measure] dans les rapports, activez le jeu d’autorisations Utilisateur [!DNL Marketo Measure] Standard .

>[!NOTE]
>
>En outre, l’utilisateur avec lequel nous sommes connectés doit disposer du profil [!DNL Salesforce] « Utilisateur marketing » activé au niveau utilisateur pour pouvoir accéder à l’objet Campaign. Pour vérifier, cliquez sur **[!UICONTROL Configuration]** > **[!UICONTROL Gérer les utilisateurs]** > **[!UICONTROL Profils]** > **[!UICONTROL Utilisateur marketing]** > **Utilisateurs affectés**.
