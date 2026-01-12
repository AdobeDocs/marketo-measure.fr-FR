---
description: Bonnes pratiques relatives aux paramètres de point de contact - [!DNL Marketo Measure]
title: Bonnes pratiques relatives aux paramètres des points de contact
exl-id: 01e314a6-e33d-45cd-aaa3-c212afec07d1
feature: Touchpoints
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 6%

---


# Bonnes pratiques relatives aux paramètres des points de contact {#best-practices-for-touchpoint-settings}

## Vue d’ensemble {#overview}

La section [!UICONTROL Paramètres de point de contact] de votre application [!DNL Marketo Measure] vous permet de définir des règles qui supprimeront ou supprimeront les points de contact de vos données [!DNL Marketo Measure] et des systèmes associés. Ces règles peuvent vous aider à isoler certains ensembles de données qui n’ont pas besoin d’être représentées dans vos données de point de contact de l’acheteur ou que vous ne souhaitez pas recevoir de crédit d’attribution sans perturber votre suivi et votre collecte de données.

**Suppression de point de contact** signifie [!DNL Marketo Measure] purgera (c’est-à-dire supprimera) tous les points de contact de votre CRM qui correspondent aux critères de la règle. Les données peuvent faire l’objet de rapports dans le tableau de bord du retour sur investissement [!DNL Marketo Measure] (Discover), mais elles n’apparaissent pas dans le CRM. Généralement utilisé pour atténuer le stress sur vos limites de stockage de données dans votre CRM

La **suppression de point de contact** est similaire à la suppression de point de contact, mais les données NE PEUVENT PAS être consignées dans le tableau de bord du retour sur investissement. Les points de contact supprimés ne sont pas accessibles dans le CRM ou Discover. La suppression garantira la correspondance entre vos données CRM et vos données Discover. Généralement utilisé pour affiner et spécifier davantage les données de point de contact qui doivent recevoir un crédit d’attribution.

Dans votre application [!DNL Marketo Measure], la section [!UICONTROL Paramètres de point de contact] est divisée en quatre sections clés. Chaque section supprime un jeu de données différent. Utilisez la touche ci-dessous pour vous assurer que vos règles suppriment les points de contact souhaités.

* Supprimer les Buyer Touchpoints du CRM
   * Utilisez cette section lorsque vous souhaitez créer une règle qui supprimera **les données Buyer Touchpoint** (les points de contact associés à l’individu, et non l’opportunité) de votre **CRM**
* Supprimer les Buyer Touchpoints du CRM
   * Utilisez cette section lorsque vous souhaitez créer une règle qui supprimera **les données Buyer Touchpoint** (les points de contact associés à l’individu, et non l’opportunité) de votre **CRM** et **Discover**
* Supprimer Buyer Attribution Touchpoint du CRM
   * Utilisez cette section pour créer une règle qui supprimera les données **Buyer Attribution Touchpoint** (les points de contact associés à l’opportunité et au chiffre d’affaires) de votre **CRM**
* Supprimer le Buyer Attribution Touchpoint du CRM

   * Utilisez cette section lorsque vous souhaitez créer une règle qui supprimera les données **Buyer Attribution Touchpoint** (les points de contact associés à l’opportunité et au chiffre d’affaires) de vos **CRM** et **Discover**

## Bonne pratique {#best-practice}

Que vous établissiez des règles de définition de point de contact pour la première fois ou que vous les examiniez simplement pour vérifier leur exactitude, gardez à l’esprit les bonnes pratiques suivantes.

* Établissez la liste des données à supprimer avant de créer les règles
* Identifiez exactement les champs qui indiquent clairement la ou les règles que vous configurez
* Vérifiez que vous avez spécifié l’opérateur correct pour la règle
* À l’aide de la touche ci-dessus, assurez-vous que votre règle est spécifiée dans la section appropriée des paramètres de point de contact
* Testez vos règles avant de les mettre en œuvre en répliquant la logique des règles dans un rapport de point de contact Acheteur dans CRM pour vous assurer qu’elles suppriment les données souhaitées

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Il est important de vérifier vos [!UICONTROL paramètres de point de contact], car ils peuvent modifier considérablement vos données lorsqu’ils ne sont pas définis correctement. Nous vous recommandons, en règle générale, de vérifier vos paramètres de point de contact au moins deux fois par an. Il s’agit d’une simple révision visuelle des règles configurées dans la section Paramètres de point de contact de votre application [!DNL Marketo Measure]. Grâce à cette révision, vous aurez l’assurance que vos paramètres de point de contact sont à jour et que des modifications peuvent être apportées en conséquence.

Les raisons pour lesquelles vérifier vos paramètres [!UICONTROL Point de contact] incluent :

* Changements au sein de votre équipe marketing
* Mises à jour majeures de la structure de votre site web
* Identification des données de point de contact devenues inutiles
   * Chaque fois que vous rencontrez des données de point de contact qui, selon vous, ne devraient pas recevoir de crédit d’attribution, les règles de [!DNL touchpoint suppression] sont la fonctionnalité permettant de garantir que vos données sont aussi propres et précises que possible.
* Les modifications apportées aux champs utilisés pour définir vos règles de suppression

>[!MORELIKETHIS]
> [Présentation de la suppression des points de contact](/help/advanced-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)
> [Pourquoi les points de contact ne doivent jamais être supprimés &#x200B;](/help/advanced-features/touchpoint-settings/why-you-should-never-delete-touchpoints.md)
> [Points de contact de l’acheteur (BT) par rapport aux points de contact d’attribution de l’acheteur (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-differences.md)

