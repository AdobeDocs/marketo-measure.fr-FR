---
unique-page-id: 18874539
description: Création de [!DNL Marketo Measure] types de rapports personnalisés - [!DNL Marketo Measure]
title: Création de types de rapports personnalisés dans [!DNL Marketo Measure]
exl-id: 1d72a04f-6a2d-4607-ad09-3b025125156a
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 5%

---

# Création de types de rapports [!DNL Marketo Measure] personnalisés {#creating-custom-marketo-measure-report-types}

>[!NOTE]
>
>Des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; peuvent s’afficher dans la documentation, mais toujours &quot;[!DNL Bizible]&quot; dans votre gestion de la relation client. Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Découvrez comment créer des types de rapports [!DNL Marketo Measure] [!DNL Salesforce] personnalisés. Il existe trois types de rapports différents que nous vous recommandons de créer : Pistes avec points de contact d’achat (personnalisés), [!DNL Marketo Measure] Personne avec points de contact d’achat (personnalisés), Opportunités avec Buyer Attribution Touchpoint (personnalisées).

## Pistes avec points de contact d’achat (personnalisés) {#leads-with-buyer-touchpoints-custom}

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/1.png)

1. Définissez le Type de rapport personnalisé.

   * [!UICONTROL Type de rapport Focus] > [!UICONTROL [!UICONTROL Objet Principal]] : piste
   * Identification > [!UICONTROL Étiquette de type de rapport] : Pistes avec points de contact d’achat (personnalisé)
   * [!UICONTROL Stocker dans la catégorie] : autres rapports
   * [!UICONTROL Déploiement] > [!UICONTROL État de déploiement] : déployé

   ![](assets/2.png)

1. Définissez les relations entre les objets.

   * Associez l’objet Lead (A) à l’objet persone [!DNL Marketo Measure] (B), puis à l’objet Buyer Touchpoint (C).
   * Assurez-vous que &quot;[!UICONTROL Chaque enregistrement A/B doit avoir au moins un enregistrement B/C]&quot; est sélectionné.
   * [!UICONTROL Enregistrer]

   ![](assets/3.png)

## [!DNL Marketo Measure] Personne avec points de contact d’achat (personnalisés) {#marketo-measure-person-with-buyer-touchpoints-custom}

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/4.png)

1. Définissez le Type de rapport personnalisé.

   * [!UICONTROL  Type de rapport Focus] > [!UICONTROL Objet Principal] : [!DNL Marketo Measure] Personnes
   * [!UICONTROL Identification] > [!UICONTROL Étiquette de type de rapport] : [!DNL Marketo Measure] Personne avec points de contact d’achat (personnalisé)
   * [!UICONTROL Stocker dans la catégorie] : autres rapports
   * [!UICONTROL Déploiement] > [!UICONTROL État de déploiement] : déployé

   ![](assets/5.png)

1. Définissez les relations entre les objets.

   * Associer l’objet [!DNL Marketo Measure] Personne (A) à l’objet Buyer Touchpoint (B)
   * Assurez-vous que &quot;[!UICONTROL Chaque enregistrement A doit avoir au moins un enregistrement B]&quot; est sélectionné.
   * [!UICONTROL Enregistrer]

   ![](assets/6.png)

## Opportunités avec Buyer Attribution Touchpoint (personnalisé) {#opportunities-with-buyer-attribution-touchpoint-custom}

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/7.png)

1. Définissez le Type de rapport personnalisé.

   * [!UICONTROL Type de rapport Focus] > [!UICONTROL Objet Principal] : opportunités
   * [!UICONTROL Identification] > [!UICONTROL Étiquette de type de rapport] : opportunités avec Buyer Attribution Touchpoint (personnalisé)
   * [!UICONTROL Stocker dans la catégorie] : autres rapports
   * [!UICONTROL Déploiement] > [!UICONTROL État de déploiement] : déployé

   ![](assets/8.png)

1. Définissez les relations entre les objets.

   * Relation de l’objet Opportunités (A) à l’objet Buyer Attribution Touchpoint (B)
   * Assurez-vous que &quot;[!UICONTROL Chaque enregistrement A doit avoir au moins un enregistrement B]&quot; est sélectionné.
   * [!UICONTROL Enregistrer]

   ![](assets/9.png)

## Ajout de champs personnalisés aux types de rapports personnalisés {#adding-custom-fields-to-custom-report-types}

1. Une fois les rapports créés, vous êtes redirigé vers une vue d&#39;ensemble du type de rapport. Cliquez sur **[!UICONTROL Modifier la mise en page]**.

   ![](assets/10.png)

1. Assurez-vous que les champs personnalisés que vous souhaitez ajouter au rapport apparaissent dans la section Propriétés de la disposition du champ . Si vous souhaitez ajouter d’autres champs, utilisez l’option &quot;[!UICONTROL Ajouter des champs associés via la recherche]&quot;.

   ![](assets/11.png)
