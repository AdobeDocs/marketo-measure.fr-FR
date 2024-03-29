---
unique-page-id: 18874539
description: Création d’une [!DNL Marketo Measure] Types de rapports - [!DNL Marketo Measure]
title: Création de types de rapports personnalisés dans [!DNL Marketo Measure]
exl-id: 1d72a04f-6a2d-4607-ad09-3b025125156a
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 5%

---

# Création d’une [!DNL Marketo Measure] Types de rapports {#creating-custom-marketo-measure-report-types}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans la documentation, mais toujours voir &quot;[!DNL Bizible]&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version. Notre nouvelle identité (rebranding) sera bientôt répercutée dans votre CRM.

Découvrez comment créer des [!DNL Marketo Measure] [!DNL Salesforce] types de rapports. Il existe trois types de rapports différents que nous vous recommandons de créer : Pistes avec points de contact d’achat (personnalisés), [!DNL Marketo Measure] Personne avec points de contact d’achat (personnalisés), opportunités avec point de contact d’attribution d’achat (personnalisé).

## Pistes avec points de contact d’achat (personnalisés) {#leads-with-buyer-touchpoints-custom}

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Build]** > **[!UICONTROL Types de rapports]** > **[!UICONTROL Nouveaux types de rapports personnalisés]**.

   ![](assets/1.png)

1. Définissez le Type de rapport personnalisé.

   * [!UICONTROL Focus sur le type de rapport] > [!UICONTROL [!UICONTROL Objet Principal]]: piste
   * Identification > [!UICONTROL Étiquette du type de rapport]: Pistes avec points de contact d’achat (personnalisés)
   * [!UICONTROL Stocker dans la catégorie]: autres rapports
   * [!UICONTROL Déploiement] > [!UICONTROL État du déploiement]: déployé

   ![](assets/2.png)

1. Définissez les relations entre les objets.

   * Associez l’objet Lead (A) à la variable [!DNL Marketo Measure] Objet Personne (B), puis objet point de contact Acheteur (C)
   * Assurez-vous que &quot;[!UICONTROL Chaque enregistrement A/B doit avoir au moins un enregistrement B/C]&quot; enregistrement sélectionné
   * [!UICONTROL Enregistrer]

   ![](assets/3.png)

## [!DNL Marketo Measure] Personne avec points de contact d’achat (personnalisés) {#marketo-measure-person-with-buyer-touchpoints-custom}

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Build]** > **[!UICONTROL Types de rapports]** > **[!UICONTROL Nouveaux types de rapports personnalisés]**.

   ![](assets/4.png)

1. Définissez le Type de rapport personnalisé.

   * [!UICONTROL Focus sur le type de rapport] > [!UICONTROL Objet Principal]: [!DNL Marketo Measure] Personnes
   * [!UICONTROL Identification] > [!UICONTROL Étiquette du type de rapport]: [!DNL Marketo Measure] Personne avec points de contact d’achat (personnalisés)
   * [!UICONTROL Stocker dans la catégorie]: autres rapports
   * [!UICONTROL Déploiement] > [!UICONTROL État du déploiement]: déployé

   ![](assets/5.png)

1. Définissez les relations entre les objets.

   * Relation de la variable [!DNL Marketo Measure] Objet Personne (A) pour l’objet point de contact de l’acheteur (B)
   * Assurez-vous que &quot;[!UICONTROL Chaque enregistrement A doit comporter au moins un B]&quot; enregistrement sélectionné
   * [!UICONTROL Enregistrer]

   ![](assets/6.png)

## Opportunités avec un point de contact d’attribution d’achat (personnalisé) {#opportunities-with-buyer-attribution-touchpoint-custom}

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Build]** > **[!UICONTROL Types de rapports]** > **[!UICONTROL Nouveaux types de rapports personnalisés]**.

   ![](assets/7.png)

1. Définissez le Type de rapport personnalisé.

   * [!UICONTROL Focus sur le type de rapport] > [!UICONTROL Objet Principal]: opportunités
   * [!UICONTROL Identification] > [!UICONTROL Étiquette du type de rapport]: opportunités avec point de contact d’attribution de l’achat (personnalisé)
   * [!UICONTROL Stocker dans la catégorie]: autres rapports
   * [!UICONTROL Déploiement] > [!UICONTROL État du déploiement]: déployé

   ![](assets/8.png)

1. Définissez les relations entre les objets.

   * Associer l’objet Opportunités (A) à l’objet Point de contact d’attribution de l’acheteur (B)
   * Assurez-vous que &quot;[!UICONTROL Chaque enregistrement A doit comporter au moins un B]&quot; enregistrement sélectionné
   * [!UICONTROL Enregistrer]

   ![](assets/9.png)

## Ajout de champs personnalisés aux types de rapports personnalisés {#adding-custom-fields-to-custom-report-types}

1. Une fois les rapports créés, vous êtes redirigé vers une vue d&#39;ensemble du type de rapport. Cliquez sur **[!UICONTROL Modifier la mise en page]**.

   ![](assets/10.png)

1. Assurez-vous que les champs personnalisés que vous souhaitez ajouter au rapport apparaissent dans la section Propriétés de la disposition du champ . Si vous souhaitez ajouter d’autres champs, utilisez le[!UICONTROL Ajouter des champs liés via la recherche]&quot;.

   ![](assets/11.png)
