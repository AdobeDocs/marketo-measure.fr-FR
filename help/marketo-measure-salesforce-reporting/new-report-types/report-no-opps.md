---
description: Type de rapport pour les contacts sans opportunités
title: Type de rapport pour les contacts sans opportunités
exl-id: 255048be-16ff-4964-85fd-cc07888a05af
feature: Reporting
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 18%

---


# Type de rapport pour les contacts sans opportunités {#report-type-for-contacts-without-opportunities}

>[!NOTE]
>Vous pouvez voir des instructions spécifiant « [!DNL Marketo Measure] » dans la documentation, mais toujours voir « [!DNL Bizible] » dans votre CRM. Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Pour générer des rapports sur les contacts avec des points de contact acheteur qui ne sont pas associés à une opportunité, vous devez créer un type de rapport personnalisé.

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Créer]** > **[!UICONTROL Types de rapports]**.

   ![Page Types de rapports dans la configuration de Salesforce ](assets/1.jpg)

1. Sélectionnez **[!UICONTROL Nouveau type de rapport personnalisé]**.

   ![Écran de sélection Nouveau type de rapport personnalisé](assets/2.jpg)

1. Définissez l&#39;objet de Principal  en tant que « [!UICONTROL Contacts]. » Nommez le libellé de type de rapport « Contacts avec les points de contact de l’acheteur ». Utilisez le même nom pour le nom du type de rapport. Dans l’entrée de description, « Contacts avec les points de contact de l’acheteur ». Enregistrez le rapport dans la « [!UICONTROL Autre] » et définissez-le sur « [!UICONTROL Déployé] ».

   ![Détails du type de rapport avec les contacts comme objet principal](assets/3.jpg)

1. À partir de là, vous lierez l’objet Contacts à l’objet Points de contact de l’acheteur. Assurez-vous de choisir le bouton « Chaque enregistrement « A » doit comporter au moins un enregistrement « B » associé. »

   ![Configuration de la relation d’objet liant les contacts aux points de contact de l’acheteur](assets/4.jpg)

1. Cliquez sur **[!UICONTROL Enregistrer]** et vous avez terminé !
