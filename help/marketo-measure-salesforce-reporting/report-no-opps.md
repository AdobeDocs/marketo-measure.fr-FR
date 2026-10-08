---
description: Guide sur le type de rapport pour les contacts sans opportunités pour les utilisateurs de Marketo Measure
title: Type de rapport pour les contacts sans opportunités
exl-id: 255048be-16ff-4964-85fd-cc07888a05af
feature: Reporting
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: d24e0b99-7796-5c7d-831d-d71a1d725f01
    internal-label: Reporting
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 16%
---
# Type de rapport pour les contacts sans opportunités {#report-type-for-contacts-without-opportunities}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant « [!DNL Marketo Measure] » dans la documentation, mais toujours voir « [!DNL Bizible] » dans votre CRM. Nous travaillons à la mise à jour de ces informations et le changement de marque sera bientôt appliqué dans votre GRC.

Pour générer des rapports sur les contacts avec des points de contact acheteur qui ne sont pas associés à une opportunité, vous devez créer un type de rapport personnalisé.

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Créer]** > **[!UICONTROL Types de rapports]**.

   ![1. Accédez à Configuration de la création de types de rapports.](assets/new-types-1.png)

1. Sélectionnez **[!UICONTROL Nouveau type de rapport personnalisé]**.

   ![1. Sélectionnez Nouveau type de rapport personnalisé.](assets/new-types-10.jpg)

1. Définissez l&#39;objet de Principal  en tant que « [!UICONTROL Contacts]. » Nommez le libellé de type de rapport « Contacts avec les points de contact de l’acheteur ». Utilisez le même nom pour le nom du type de rapport. Dans l’entrée de description, « Contacts avec les points de contact de l’acheteur ». Enregistrez le rapport dans la « [!UICONTROL Autre] » et définissez-le sur « [!UICONTROL Déployé] ».

   ![1. Définissez l’objet de Principal sur « Contacts ». Nommez le rapport](assets/new-types-11.png)

1. À partir de là, vous lierez l’objet Contacts à l’objet Points de contact de l’acheteur. Assurez-vous de choisir le bouton « Chaque enregistrement « A » doit comporter au moins un enregistrement « B » associé. »

   ![1. De là, vous lierez l&#39;objet Contacts à l&#39;acheteur](assets/new-types-12.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** et vous avez terminé !
