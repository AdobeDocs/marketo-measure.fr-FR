---
description: 'Leads avec points de contact de l’acheteur : conseils pour le rapport destiné aux utilisateurs de Marketo Measure'
title: Rapport Leads avec points de contact des acheteurs
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: 32d2f1bc-61d0-598c-a8bf-f6fbc8920276
    internal-label: Touchpoints
  - id: d24e0b99-7796-5c7d-831d-d71a1d725f01
    internal-label: Reporting
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 8%
---
# Rapport Leads avec points de contact des acheteurs {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant « [!DNL Marketo Measure] » dans la documentation, mais toujours voir « [!DNL Bizible] » dans votre CRM. Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Prête à l’emploi, vous disposez de nombreuses fonctionnalités de création de rapports du bout des doigts en ce qui concerne [!DNL Marketo Measure], mais nous vous recommandons de créer d’autres types de rapports. Découvrez ci-dessous comment créer un type de rapport Leads inclusifs avec points de contact acheteur.

1. Accédez à l’option Configuration dans [!DNL Salesforce]. À partir de là, développez le regroupement « Créer » et sélectionnez **[!UICONTROL Types de rapports]**.

   ![1. Accédez à l’option Configuration dans Salesforce. À partir de là, développez ](assets/bizible-guide-1.png)

1. Sélectionnez **[!UICONTROL Nouveau type de rapport personnalisé]**.

   ![1. Sélectionnez Nouveau type de rapport personnalisé.](assets/marketo-reports-17.jpg)

1. Définissez l’objet principal en tant que « Leads » et dans l’entrée « Libellé du type de rapport » « Leads avec points de contact de l’acheteur - Inclusif ». Stockez le rapport dans la catégorie « Leads » et modifiez le statut du déploiement en **[!UICONTROL Déployé]**. Sélectionnez ensuite **[!UICONTROL Suivant]**.

   ![1. Définissez l’objet principal en tant que « Leads » et dans le « Type de rapport ](assets/marketo-reports-18.jpg)

1. Pour les relations d’objet, sélectionnez l’objet **[!DNL Marketo Measure]Personnes** comme objet secondaire. Sélectionnez la relation A à B comme suit : « Chaque enregistrement « A » doit avoir au moins un enregistrement « B » associé. » À partir de là, vous allez mettre en relation l’objet « Buyer Touchpoint » et sélectionner la même relation entre les objets B et C.

   ![1. Pour les relations d’objet, sélectionnez l’objet Personnes Marketo Measure ](assets/bizible-guide-2.png)

1. Enregistrez et commencez à créer des rapports.
