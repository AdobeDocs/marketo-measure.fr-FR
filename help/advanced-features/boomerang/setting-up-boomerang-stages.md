---
description: Configuration des étapes de boomerang - [!DNL Marketo Measure]
title: Configuration d’étapes de boomerang
exl-id: 00dd2826-27a3-462e-a70e-4cec90d07f92
feature: Boomerang
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 2%

---


# Configuration d’étapes de boomerang {#setting-up-boomerang-stages}

>[!AVAILABILITY]
>La fonction Boomerang est uniquement activée pour les clients de niveau 2 et 3. Pour demander un niveau de compte supérieur, contactez l’équipe du compte Adobe (votre gestionnaire de compte).

Pour activer les étapes [!UICONTROL Boomerang] pour votre compte, vous devez être un administrateur de compte. Vous pouvez également l’activer en contactant le support technique de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}. Une fois la fonctionnalité activée, suivez ces instructions pour la configurer.

## Configuration de l’étape de boomerang {#boomerang-stage-setup}

1. Accédez à [!UICONTROL &#x200B; Mappage d’étape &#x200B;]. Sous la colonne intitulée « [!UICONTROL Boomerang] », cochez les cases en regard des étapes que vous souhaitez suivre.

   ![Interface du mappage d’étape affichant la colonne Boomerang avec des cases à cocher pour la sélection d’étape](assets/1-2.png)

1. Accédez à l’onglet [!UICONTROL Paramètres d’attribution] et saisissez le nombre de points de contact pour chaque étape que vous souhaitez voir. Nous autorisons un maximum de 10. La valeur par défaut est définie sur 1.

   ![Onglet Paramètres d’attribution affichant les champs d’entrée du nombre de points de contact pour chaque étape de boomerang](assets/2-2.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**

   >[!NOTE]
   >Comptez 24 à 48 heures pour que vos données soient retraitées en fonction de ces modifications.

## Configuration de l’étape de boomerang avec attribution de modèle personnalisé {#boomerang-stage-setup-with-custom-model-attribution}

1. Accédez à [!UICONTROL &#x200B; Mappage d’étape &#x200B;]. Sous la colonne intitulée « [!UICONTROL Boomerang] », cochez les cases en regard des étapes que vous souhaitez suivre.

   ![Interface de mappage d’étape avec des colonnes de boomerang et de modèle personnalisé pour la sélection d’étape](assets/3-1.png)

1. Si vous souhaitez également que ces étapes de boomerang soient incluses dans votre modèle personnalisé et reçoivent un crédit d’attribution, veillez également à sélectionner la case sous la colonne « [!UICONTROL Modèle personnalisé] ».

   ![Mappage d’étape affichant les cases à cocher de colonne de modèle personnalisé sélectionnées pour les étapes de boomerang](assets/4-1.png)

1. Accédez à l’onglet [!UICONTROL Paramètres d’attribution]. Déterminez la manière dont vous souhaitez pondérer l’attribution pour vos étapes de boomerang. Les options consistent à pondérer l’attribution sur la première occurrence, la dernière occurrence, ou à la répartir uniformément sur toutes les occurrences.

   ![Paramètres d’attribution affichant les options de pondération de boomerang pour le premier, le dernier ou même le fractionnement](assets/5-1.png)

1. Saisissez le nombre d’occurrences de chaque étape que vous souhaitez voir. On peut en permettre 10 maximum. La valeur par défaut est définie sur 1.

   ![Paramètres d’attribution affichant les champs d’entrée du nombre d’occurrences pour chaque étape de boomerang](assets/6-1.png)

1. Définissez le pourcentage d’attribution que vous souhaitez allouer aux étapes de boomerang que vous avez incluses dans le modèle personnalisé. Assurez-vous que l’attribution totale pour toutes les étapes atteint 100 %. Cliquez sur **[!UICONTROL Enregistrer et traiter]**.

   ![Paramètres d’attribution affichant les champs d’attribution en pourcentage pour les étapes de boomerang dans le modèle personnalisé](assets/7-1.png)

   >[!NOTE]
   >Comptez 24 à 48 heures pour que vos données soient retraitées en fonction de ces modifications.
