---
unique-page-id: 18874614
description: Rapport Pistes avec points de contact d’achat - [!DNL Marketo Measure]
title: Rapport Pistes avec points de contact d’achat
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 8%

---

# Rapport Pistes avec points de contact d’achat {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>Des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; peuvent s’afficher dans la documentation, mais toujours &quot;[!DNL Bizible]&quot; dans votre gestion de la relation client. Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

De nombreuses fonctionnalités de création de rapports sont à portée de main lorsqu’il s’agit de [!DNL Marketo Measure], mais nous vous recommandons de créer d’autres types de rapports. Découvrez le type de rapport Pistes avec points de contact d’achat ci-dessous.

1. Accédez à l’option Configuration dans [!DNL Salesforce]. À partir de là, développez le groupe &quot;Créer&quot; et sélectionnez **[!UICONTROL Types de rapports]**.

   ![](assets/1.jpg)

1. Sélectionnez **[!UICONTROL Nouveau type de rapport personnalisé]**.

   ![](assets/2.jpg)

1. Définissez l’objet principal comme &quot;Pistes&quot; et dans l’entrée &quot;Étiquette de type de rapport&quot; &quot;Pistes avec points de contact d’achat - Inclus&quot;. Stockez le rapport dans la catégorie &quot;Leads&quot; et remplacez l’état du déploiement par **[!UICONTROL Deployed]**. Sélectionnez ensuite **[!UICONTROL Suivant]**.

   ![](assets/3.jpg)

1. Pour les relations d’objet, sélectionnez l’objet **[!DNL Marketo Measure]Personnes** comme objet secondaire. Sélectionnez la relation A/B comme suit : &quot;Chaque enregistrement &quot;A&quot; doit comporter au moins un enregistrement &quot;B&quot; associé.&quot; A partir de là, vous associerez l’objet &quot;Buyer Touchpoint&quot; et sélectionnerez la même relation entre les objets B et C.

   ![](assets/4.jpg)

1. Enregistrez et commencez à créer des rapports.
