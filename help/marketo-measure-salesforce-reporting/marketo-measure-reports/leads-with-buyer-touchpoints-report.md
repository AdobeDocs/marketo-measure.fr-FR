---
unique-page-id: 18874614
description: Rapport Pistes avec points de contact d’achat - [!DNL Marketo Measure] - Documentation du produit
title: Rapport Prospects avec points de contact acheteur
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 5%

---

# Rapport Prospects avec points de contact acheteur {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans notre documentation, mais toujours voir &quot;[!DNL Bizible]&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version et la nouvelle image sera bientôt répercutée dans votre CRM.

De nombreuses fonctionnalités de reporting sont à portée de main lorsqu’il s’agit d’élaborer des rapports prêts à l’emploi. [!DNL Marketo Measure], mais il existe d’autres types de rapports que nous vous recommandons de créer. Découvrez le type de rapport Pistes avec points de contact d’achat ci-dessous.

1. Accédez à l’option Configuration dans [!DNL Salesforce]. À partir de là, développez le regroupement &quot;Créer&quot; et sélectionnez **[!UICONTROL Types de rapports]**.

   ![](assets/1.jpg)

1. Sélectionner **[!UICONTROL Nouveau type de rapport personnalisé]**.

   ![](assets/2.jpg)

1. Définissez l’objet Principal comme &quot;Pistes&quot; et dans l’entrée &quot;Étiquette de type de rapport&quot; &quot;Pistes avec points de contact d’achat - Inclus&quot;. Stockez le rapport dans la catégorie &quot;Leads&quot; et modifiez l’état du déploiement en **[!UICONTROL Déployé]**. Sélectionnez **[!UICONTROL Suivant]**.

   ![](assets/3.jpg)

1. Pour les relations d’objet, sélectionnez l’événement **[!DNL Marketo Measure]Personnes** comme objet secondaire. Sélectionnez la relation A/B comme suit : &quot;Chaque enregistrement &quot;A&quot; doit comporter au moins un enregistrement &quot;B&quot; associé.&quot; A partir de là, vous associerez l’objet &quot;Point de contact de l’acheteur&quot; et sélectionnerez la même relation entre les objets B et C.

   ![](assets/4.jpg)

1. Enregistrez et commencez à créer des rapports.
