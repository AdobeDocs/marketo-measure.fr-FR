---
unique-page-id: 18874718
description: Création d'une vue Liste de campagnes pour [!DNL Salesforce Campaigns] - [!DNL Marketo Measure]
title: 'Création d’un affichage des listes des campagnes  [!DNL Salesforce] '
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
feature: Channels
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 5%

---

# Création d&#39;une vue Liste des campagnes pour les campagnes [!DNL Salesforce] {#creating-a-campaign-list-view-for-salesforce-campaigns}

Découvrez comment créer une vue Liste pour les campagnes que vous souhaitez synchroniser avec les points de contact de l’acheteur.

>[!NOTE]
>
>Cet article traite d’un processus obsolète. Nous encourageons les utilisateurs et les utilisatrices à utiliser le [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

La vue Liste des campagnes qui peut être créée vous permet d’avoir un emplacement d’accès pour afficher et gérer les champs « Type » et « Activer les points de contact de l’acheteur » afin de vous assurer que chacune de vos campagnes [!DNL Salesforce] qui informent vos canaux marketing hors ligne sont correctement configurées.

1. Accédez à l’onglet Campagnes dans [!DNL Salesforce] et créez une vue de liste
1. Nommez la vue « Campagnes à synchroniser avec [!DNL Marketo Measure] ».
1. Nous voulons que cette liste affiche uniquement les campagnes que nous voulons synchroniser avec [!DNL Marketo Measure]. Nous avons donc besoin de quelques filtres :

   * **Type** [EST ÉGAL À] &#39;Tous les types de campagne que nous avons mappés à vos canaux hors ligne&#39;. Reportez-vous à votre plan de mise en œuvre ou à l’onglet Canaux hors ligne dans [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} -> Mon compte -> Paramètres -> Canaux hors ligne). Vous pouvez sélectionner les types de votre choix (ceux qui sont mappés à un canal marketing hors ligne) à l’aide de l’icône en forme de loupe.

      * Choisissez 3 types max pour chaque filtre. Un champ de filtre comporte une limite de caractères. Commencez avec 3 types par filtre et ajoutez des lignes supplémentaires de filtres « Type » si nécessaire.

   * **Date de création** [POSTÉRIEURE OU ÉGALE] votre date de début de [!DNL Marketo Measure]. La date de début se trouve dans le tableau de bord du RSI de l’application [!DNL Marketo Measure]. Sélectionnez simplement « Depuis la date de création » dans la période du tiret et votre date de début s’affichera.
   * **&#42;Type d’enregistrement&#42;** - Pour apporter des modifications dans la vue Liste, vous devez ajouter un filtre pour le type d’enregistrement. Chaque enregistrement de campagne que vous pouvez avoir à modifier doit être du même type d’enregistrement.

1. Modifiez les champs sélectionnés pour les afficher dans la vue Liste. La configuration complète de la vue Liste doit ressembler à l’exemple ci-dessous :

   Cette vue vous permet de voir vos campagnes et de modifier les champs « Type » et « Activer les points de contact de l’acheteur » si nécessaire. Lorsque vous créez de nouvelles campagnes qui doivent être synchronisées avec [!DNL Marketo Measure], elles s’affichent dans cette vue et vous pouvez gérer tous les paramètres de ces campagnes directement depuis la liste.

   Pour effectuer des modifications intégrées à partir de la vue Liste, vous devez vous assurer que ce qui suit est également vrai dans votre configuration [!DNL Salesforce] :

   * **[!UICONTROL Configuration]** > **[!UICONTROL Interface utilisateur]** > **[!UICONTROL Activer la modification en ligne]**
   * Vous devez également activer les listes améliorées (juste sous la case pour la modification en ligne)
   * Assurez-vous d’être autorisé à accéder aux champs .

>[!MORELIKETHIS]
>
>[Résolution des problèmes courants liés à la modification en ligne dans la vue Liste](http://help.salesforce.com/articleView?id=000003911&language=en_US&type=1){target="_blank"}
