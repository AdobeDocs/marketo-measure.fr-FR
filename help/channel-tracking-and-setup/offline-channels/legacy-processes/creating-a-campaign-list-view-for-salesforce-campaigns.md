---
unique-page-id: 18874718
description: Création d’une vue de liste de campagnes pour [!DNL Salesforce Campaigns] - [!DNL Marketo Measure]
title: Création d’un affichage des listes des campagnes  [!DNL Salesforce]
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
feature: Channels
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 5%

---

# Création d’une vue de liste de campagnes pour [!DNL Salesforce] campagnes {#creating-a-campaign-list-view-for-salesforce-campaigns}

Découvrez comment créer un mode Liste pour les campagnes que vous souhaitez synchroniser avec les points de contact d’achat.

>[!NOTE]
>
>Cet article traite d’un processus obsolète. Nous encourageons les utilisateurs et les utilisatrices à utiliser le [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

La vue Liste des campagnes qui peut être créée vous permet de disposer d’un emplacement d’&quot;accès&quot; pour afficher et gérer les champs &quot;Type&quot; et &quot;Activer les points de contact de l’acheteur&quot; afin de vous assurer que chacune de vos campagnes [!DNL Salesforce] qui informent vos canaux marketing hors ligne sont correctement configurées.

1. Accédez à l’onglet Campagnes dans [!DNL Salesforce] et créez un nouveau mode Liste.
1. Nommez la vue &quot;Campagnes à synchroniser avec [!DNL Marketo Measure]&quot;.
1. Nous voulons que cette liste affiche uniquement les campagnes que nous voulons synchroniser avec [!DNL Marketo Measure]. Nous avons donc besoin de quelques filtres :

   * **Type** [ ] &#39;Tous les types de campagne que nous avons mappés à vos canaux hors ligne&#39;. Reportez-vous à votre plan d’implémentation ou à l’onglet Canaux hors ligne dans [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} -> Mon compte -> Paramètres -> Canaux hors ligne). Vous pouvez sélectionner les types de votre choix (ceux qui sont associés à un canal marketing hors ligne) à l’aide de l’icône en forme de loupe.

      * Sélectionnez 3 types max pour chaque filtre. Il existe une limite de caractères dans un champ de filtre. Commencez par 3 types par filtre et ajoutez des lignes supplémentaires de filtres &#39;Type&#39; si nécessaire.

   * **Date de création** [GREATER OR Equal] : date de début de [!DNL Marketo Measure]. Vous pouvez trouver votre date de début dans le tableau de bord du retour sur investissement dans l’application [!DNL Marketo Measure]. Sélectionnez simplement &quot;Depuis la date de création&quot; dans la plage de dates du tiret pour afficher votre date de début.
   * **&#42;Type d’enregistrement&#42;** - Pour apporter des modifications en mode Liste, vous devez ajouter un filtre pour le type d’enregistrement. Chaque enregistrement de campagne que vous devrez peut-être modifier doit être du même type d’enregistrement.

1. Modifiez les champs Sélectionné à afficher en mode Liste. La configuration complète du mode Liste doit ressembler à l’exemple ci-dessous :

   Cette vue vous permet d’afficher vos campagnes et de modifier les champs &quot;Type&quot; et &quot;Activer les points de contact de l’acheteur&quot; si nécessaire. Lorsque vous créez des campagnes qui doivent être synchronisées avec [!DNL Marketo Measure], elles s’affichent dans cette vue et vous pouvez gérer tous les paramètres de ces campagnes directement dans la liste.

   Pour effectuer des modifications intégrées depuis le mode Liste, vous devez vous assurer que les conditions suivantes sont également vraies dans votre configuration [!DNL Salesforce] :

   * **[!UICONTROL Configuration]** > **[!UICONTROL Interface utilisateur]** > **[!UICONTROL Activer l’édition en ligne]**
   * Activez également les listes améliorées cochées (directement sous la case pour la modification en ligne).
   * Assurez-vous de disposer des autorisations pour les champs

>[!MORELIKETHIS]
>
>[Résolution des problèmes courants liés à l’édition en mode Liste](http://help.salesforce.com/articleView?id=000003911&language=en_US&type=1){target="_blank"}
