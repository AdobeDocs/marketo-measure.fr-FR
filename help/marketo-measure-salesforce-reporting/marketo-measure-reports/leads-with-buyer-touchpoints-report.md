---
unique-page-id: 18874614
description: Rapport Leads avec points de contact des acheteurs - [!DNL Marketo Measure]
title: Rapport Leads avec points de contact des acheteurs
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
TQID: https://experienceleague.adobe.com/pr-ldAGFJZVvB-gv2JyCAs4DUefL7byUfffY1wiLOZs
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 196
ht-degree: 8%

---

# Rapport Leads avec points de contact des acheteurs {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant « [!DNL Marketo Measure] » dans la documentation, mais toujours voir « [!DNL Bizible] » dans votre CRM. Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Prête à l’emploi, vous disposez de nombreuses fonctionnalités de création de rapports du bout des doigts en ce qui concerne [!DNL Marketo Measure], mais nous vous recommandons de créer d’autres types de rapports. Découvrez ci-dessous comment créer un type de rapport Leads inclusifs avec points de contact acheteur.

1. Accédez à l’option Configuration dans [!DNL Salesforce]. À partir de là, développez le regroupement « Créer » et sélectionnez **[!UICONTROL Types de rapports]**.

   ![](assets/1.jpg)

1. Sélectionnez **[!UICONTROL Nouveau type de rapport personnalisé]**.

   ![](assets/2.jpg)

1. Définissez l’objet principal en tant que « Leads » et dans l’entrée « Libellé du type de rapport » « Leads avec points de contact de l’acheteur - Inclusif ». Stockez le rapport dans la catégorie « Leads » et modifiez le statut du déploiement en **[!UICONTROL Déployé]**. Sélectionnez ensuite **[!UICONTROL Suivant]**.

   ![](assets/3.jpg)

1. Pour les relations d’objet, sélectionnez l’objet **[!DNL Marketo Measure]Personnes** comme objet secondaire. Sélectionnez la relation A à B comme suit : « Chaque enregistrement « A » doit avoir au moins un enregistrement « B » associé. » À partir de là, vous allez mettre en relation l’objet « Buyer Touchpoint » et sélectionner la même relation entre les objets B et C.

   ![](assets/4.jpg)

1. Enregistrez et commencez à créer des rapports.
