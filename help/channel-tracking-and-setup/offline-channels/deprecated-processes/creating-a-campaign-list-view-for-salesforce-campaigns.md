---
unique-page-id: 18874718
description: Création d’une vue de liste de campagnes pour [!DNL Salesforce Campaigns] - [!DNL Marketo Measure] - Documentation du produit
title: Création d’un affichage en liste des campagnes [!DNL Salesforce]
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
feature: Channels
source-git-commit: 31ffb58f5318b71d478056f9b914eb1d42c7719a
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---

# Création d’un affichage en liste des campagnes[!DNL Salesforce] {#creating-a-campaign-list-view-for-salesforce-campaigns}

Découvrez comment créer un mode Liste pour les campagnes que vous souhaitez synchroniser avec les points de contact d’achat.

La vue Liste des campagnes qui peut être créée vous permet d’avoir un emplacement d’accès pour afficher et gérer les champs &quot;Type&quot; et &quot;Activer les points de contact du client&quot; afin de vous assurer que chacun de vos [!DNL Salesforce] les campagnes qui informent vos canaux marketing hors ligne sont correctement configurées.

1. Accédez à l’onglet Campagnes dans [!DNL Salesforce] et créer une nouvelle vue de liste
1. Nommez la vue &quot;Campagnes à synchroniser avec [!DNL Marketo Measure].&quot;
1. Nous voulons que cette liste affiche uniquement les campagnes avec lesquelles nous voulons nous synchroniser. [!DNL Marketo Measure] nous avons donc besoin de quelques filtres :

   * **Type** [ÉGAL] &quot;Tous les types de campagne que nous avons mappés à vos canaux hors ligne&quot;. Reportez-vous à votre plan de mise en oeuvre ou à l’onglet Canaux hors ligne dans [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} -> Mon compte -> Paramètres -> Canaux hors ligne). Vous pouvez sélectionner les types de votre choix (ceux qui sont associés à un canal marketing hors ligne) à l’aide de l’icône en forme de loupe.

      * Sélectionnez 3 types max pour chaque filtre. Il existe une limite de caractères dans un champ de filtre. Commencez par 3 types par filtre et ajoutez des lignes supplémentaires de filtres &#39;Type&#39; si nécessaire.

   * **Date de création** [SUPÉRIEUR OU ÉGAL À] your [!DNL Marketo Measure] date de début. La date de début se trouve dans le tableau de bord du retour sur investissement au sein de la variable [!DNL Marketo Measure] Application. Sélectionnez simplement &quot;Depuis la date de création&quot; dans la plage de dates du tiret pour afficher votre date de début.
   * **&#42;Type d’enregistrement&#42;** - Pour apporter des modifications en mode Liste, vous devez ajouter un filtre pour le type d’enregistrement. Chaque enregistrement de campagne que vous devrez peut-être modifier doit être du même type d’enregistrement.

1. Modifiez les champs Sélectionné à afficher en mode Liste. La configuration complète du mode Liste doit ressembler à l’exemple ci-dessous :

   Cette vue vous permet d’afficher vos campagnes et de modifier les champs &quot;Type&quot; et &quot;Activer les points de contact de l’acheteur&quot; si nécessaire. Lorsque vous créez des campagnes qui doivent être synchronisées avec [!DNL Marketo Measure], elles s’affichent dans cette vue et vous pouvez gérer tous les paramètres de ces campagnes directement dans la liste.

   Pour effectuer des modifications intégrées depuis le mode Liste, vous devez vous assurer que les conditions suivantes sont également vraies dans votre [!DNL Salesforce] setup :

   * **[!UICONTROL Configuration]** > **[!UICONTROL Interface utilisateur]** > **[!UICONTROL Activer la modification en ligne]**
   * Activez également les listes améliorées cochées (directement sous la case pour la modification en ligne).
   * Assurez-vous de disposer des autorisations pour les champs

>[!MORELIKETHIS]
>
>[Résolution des problèmes courants liés à la modification en ligne du mode Liste](http://help.salesforce.com/articleView?id=000003911&amp;language=en_US&amp;type=1){target="_blank"}
