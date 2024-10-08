---
unique-page-id: 18874767
description: Configuration des étapes Boomerang - [!DNL Marketo Measure]
title: Configuration d’étapes de boomerang
exl-id: 00dd2826-27a3-462e-a70e-4cec90d07f92
feature: Boomerang
source-git-commit: e5931d783d8aad9ab0b32b4e30bbbfdfd46230dd
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 3%

---

# Configuration d’étapes de boomerang {#setting-up-boomerang-stages}

>[!AVAILABILITY]
>
>La fonction Boomerang n’est activée que pour les clients de niveau 2. Pour demander un niveau de compte supérieur, contactez l’équipe Compte d’Adobe (votre gestionnaire de compte).

Pour activer les étapes [!UICONTROL Boomerang] pour votre compte, vous devez être un administrateur de compte. Ou, il peut être activé en contactant le [support Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}. Une fois la fonction activée, suivez ces instructions pour la configurer.

## Configuration de l’étape Boomerang {#boomerang-stage-setup}

1. Accédez à [!UICONTROL Mappage dans l’environnement intermédiaire]. Sous la colonne intitulée &quot;[!UICONTROL Boomerang]&quot;, cochez les cases en regard des scènes dont vous souhaitez effectuer le suivi.

   ![](assets/1-2.png)

1. Accédez à l’onglet [!UICONTROL Paramètres d’attribution] et saisissez le nombre de points de contact pour chaque étape que vous souhaitez voir. Nous autorisons un maximum de 10. La valeur par défaut est 1.

   ![](assets/2-2.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Prévoyez de 24 à 48 heures le retraitement de vos données en fonction de ces modifications.

## Configuration de l’état Boomerang avec attribution de modèle personnalisée {#boomerang-stage-setup-with-custom-model-attribution}

1. Accédez à [!UICONTROL Mappage dans l’environnement intermédiaire]. Sous la colonne intitulée &quot;[!UICONTROL Boomerang]&quot;, cochez les cases en regard des scènes dont vous souhaitez effectuer le suivi.

   ![](assets/3-1.png)

1. Si vous souhaitez également que ces scènes Boomerang soient incluses dans votre modèle personnalisé et reçoivent un crédit d’attribution, veillez également à cocher la case située sous la colonne &quot;[!UICONTROL Modèle personnalisé]&quot;.

   ![](assets/4-1.png)

1. Accédez à l’onglet [!UICONTROL Paramètres d’attribution]. Déterminez comment vous souhaitez pondérer l’attribution pour vos scènes de boomerang. Les options consistent à pondérer l’attribution sur la première occurrence, la dernière occurrence ou à la diviser uniformément entre toutes les occurrences.

   ![](assets/5-1.png)

1. Saisissez le nombre d’occurrences de chaque étape que vous souhaitez voir. Nous pouvons autoriser un maximum de 10. La valeur par défaut est 1.

   ![](assets/6-1.png)

1. Définissez le pourcentage d’attribution que vous souhaitez allouer aux étapes Boomerang que vous avez incluses dans le modèle personnalisé. Assurez-vous que l’attribution totale pour toutes les étapes s’élève à 100 %. Cliquez sur **[!UICONTROL Save and Process]**.

   ![](assets/7-1.png)

   >[!NOTE]
   >
   >Prévoyez de 24 à 48 heures le retraitement de vos données en fonction de ces modifications.
