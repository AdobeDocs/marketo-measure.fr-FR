---
description: Bonnes pratiques pour les paramètres de point de contact - [!DNL Marketo Measure]
title: Bonnes pratiques relatives aux paramètres des points de contact
exl-id: 01e314a6-e33d-45cd-aaa3-c212afec07d1
feature: Touchpoints
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 6%

---

# Bonnes pratiques relatives aux paramètres des points de contact {#best-practices-for-touchpoint-settings}

## Vue d’ensemble {#overview}

La section [!UICONTROL Paramètres du point de contact] de votre application [!DNL Marketo Measure] vous permet de définir des règles qui supprimeront ou supprimeront les points de contact de vos données [!DNL Marketo Measure] et des systèmes associés. Ces règles peuvent vous aider à isoler certains ensembles de données qui n’ont pas besoin d’être représentés dans vos données de point de contact d’achat ou que vous ne souhaitez pas recevoir de crédit d’attribution sans perturber votre suivi et votre collecte de données.

**Touchpoint Removal** signifie que [!DNL Marketo Measure] purge (c’est-à-dire qu’il supprime) tous les points de contact de votre CRM qui correspondent aux critères de règle. Les données peuvent faire l’objet de rapports dans le tableau de bord du ROI [!DNL Marketo Measure] (Discover), mais elles ne s’affichent pas dans le CRM. Couramment utilisé pour atténuer la contrainte sur vos limites de stockage des données dans votre CRM

La **suppression de point de contact** est similaire à la suppression de point de contact, mais les données ne peuvent PAS être consignées dans le tableau de bord du retour sur investissement. Les points de contact supprimés ne seront pas accessibles dans le CRM ou Discover. La suppression garantit que vos données CRM et vos données Discover correspondent. Utilisé généralement pour affiner et spécifier davantage les données de point de contact que vous souhaitez recevoir du crédit d’attribution.

Dans votre application [!DNL Marketo Measure], la section [!UICONTROL Paramètres du point de contact] sera divisée en quatre sections clés. Chaque section supprime ou supprime un ensemble de données différent. Utilisez la touche ci-dessous pour vous assurer que vos règles suppriment ou suppriment les points de contact souhaités.

* Supprimer les Buyer Touchpoints du CRM
   * Utilisez cette section lorsque vous souhaitez créer une règle qui supprimera les **données Buyer Touchpoint** (les points de contact associés à l’individu, et non l’opportunité) de votre **CRM**
* Supprimer les Buyer Touchpoints du CRM
   * Utilisez cette section lorsque vous souhaitez créer une règle qui supprimera **les données Buyer Touchpoint** (les points de contact associés à l’individu, et non l’opportunité) de vos **CRM** et **Discover**
* Supprimer Buyer Attribution Touchpoint du CRM
   * Utilisez cette section lorsque vous souhaitez créer une règle qui supprimera les données **Buyer Attribution Touchpoint** (les points de contact associés à l’opportunité et aux recettes) de votre **CRM**
* Supprimer le Buyer Attribution Touchpoint du CRM

   * Utilisez cette section lorsque vous souhaitez créer une règle qui supprimera les données **Buyer Attribution Touchpoint** (les points de contact associés à l’opportunité et aux recettes) de vos **CRM** et **Discover**

## Bonne pratique {#best-practice}

Gardez à l’esprit les bonnes pratiques suivantes, que vous créiez des règles de définition des points de contact pour la première fois ou que vous les examiniez simplement pour vérifier leur exactitude.

* Définition de la liste des données que vous souhaitez supprimer ou supprimer avant de créer les règles
* Identifier exactement les champs qui désigneront clairement la ou les règles que vous définissez
* Assurez-vous d’avoir spécifié l’opérateur correct pour la règle.
* À l’aide de la clé ci-dessus, assurez-vous que votre règle est spécifiée dans la section appropriée des paramètres du point de contact.
* Testez vos règles avant de les implémenter en répliquant la logique de règle dans un rapport Point de contact d’acheteur dans le CRM afin de vous assurer qu’elles suppriment ou suppriment les données souhaitées.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

La révision de vos [!UICONTROL paramètres de point de contact] est importante, car ils peuvent modifier radicalement vos données lorsqu’ils ne sont pas définis correctement. En règle générale, il est recommandé de consulter vos paramètres de point de contact au moins deux fois par an. Il s’agit d’une simple révision visuelle des règles configurées dans la section Paramètres des points de contact de votre application [!DNL Marketo Measure]. Cette révision vous permet de vous assurer que vos paramètres de point de contact sont à jour et que toute modification peut être apportée en conséquence.

Les raisons de consulter vos paramètres [!UICONTROL Touchpoint] incluent...

* Changements au sein de votre équipe marketing
* Mises à jour majeures de la structure de votre site web
* Identification des données de point de contact qui ne sont plus utiles
   * Chaque fois que vous découvrez des données de point de contact qui selon vous ne devraient pas recevoir de crédit d’attribution, les règles [!DNL touchpoint suppression] sont la fonctionnalité permettant d’assurer vos données aussi propres et précises que possible.
* Modifications apportées aux champs utilisés pour définir les règles de suppression ou de suppression

>[!MORELIKETHIS]
>
>* [Présentation de la suppression et de la suppression de points de contact](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)
>* [Pourquoi les points de contact ne doivent jamais être supprimés](/help/advanced-marketo-measure-features/touchpoint-settings/why-you-should-never-delete-touchpoints.md)
>* [Points de contact d’achat (BT) et points de contact d’attribution d’achat (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md)

