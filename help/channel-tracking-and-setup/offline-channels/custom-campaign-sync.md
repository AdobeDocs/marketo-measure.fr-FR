---
unique-page-id: 18874588
description: Synchronisation de campagne personnalisée - [!DNL Marketo Measure]
title: Synchronisation de campagne personnalisée
exl-id: 66f0e4e3-c1b6-443e-8ffa-06b67862b855
feature: Channels
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# Synchronisation de campagne personnalisée {#custom-campaign-sync}

Aujourd’hui, avec le package [!DNL Marketo Measure] installé, vous pouvez indiquer les campagnes à inclure comme point de contact éligible. Il y a plusieurs obstacles à cela, tels qu&#39;ils existaient auparavant. Une fois le package [!DNL Marketo Measure] installé dans le CRM, il peut s&#39;écouler un certain temps avant que votre équipe de sécurité puisse l&#39;approuver. En outre, l’utilisation d’une seule liste de sélection sur l’objet Campaign manque de flexibilité. Avec cette nouvelle fonctionnalité, l’installation d’un package n’est pas nécessaire pour commencer à utiliser les enregistrements Campaign et Campaign Member . Des règles peuvent être créées pour définir exactement les enregistrements qui peuvent être créés pour définir exactement les enregistrements éligibles.

## Exigences {#requirements}

* La synchronisation des campagnes est disponible dans tous les niveaux
* Pour importer des données, vous devez toujours connecter votre CRM à votre compte [!DNL Marketo Measure].

## Fonctionnement {#how-it-works}

1. Avec les autorisations AccountAdmin, vous pouvez accéder à **[!UICONTROL Paramètres]** > **[!UICONTROL Campagnes]** et voir l’interface utilisateur des règles Synchroniser les membres de campagne.
1. Cliquez sur l’icône **+** pour commencer à créer une règle.

   ![](assets/1-1.png)

1. Vous avez la possibilité de créer une règle à partir des champs [!UICONTROL Campaign] ou [!UICONTROL Campaign Member]. Remplissez le reste de la règle avec l’ opérateur et la valeur que nous sommes censés valider. Dans l&#39;exemple ci-dessous, nous recherchons une campagne spécifique par son nom.

   ![](assets/2-1.png)

   >[!NOTE]
   >
   >Les champs de formule ne peuvent pas être utilisés dans vos règles et n’apparaîtront pas dans la liste de sélection. Comme les formules sont calculées en arrière-plan et ne modifient pas d’enregistrement, [!DNL Marketo Measure] ne peut pas détecter si un enregistrement correspond ou non à une règle.

1. Sélectionnez la Date du point de contact. La liste des dates possibles s’affiche une fois que vous avez saisi une accolade `{`. Vous pouvez ensuite sélectionner la date à appliquer à tous les points de contact créés à partir de la règle.

   ![](assets/3-1.png)

   >[!NOTE]
   >
   >Si vous utilisez des règles de synchronisation de campagne personnalisées, [!DNL Marketo Measure] ne lira aucune mise à jour que vous avez effectuée à l’aide du bouton Date de point de contact de mise à jour en bloc.

1. Cliquez sur la coche, puis ajoutez des règles supplémentaires pour les campagnes supplémentaires si nécessaire.

   ![](assets/4-1.png)

   >[!NOTE]
   >
   >Maintenant que les règles sont définies en même temps que la synchronisation CRM, les règles indiquées commencent naturellement à entrer en conflit. Si vous choisissez de continuer à utiliser à la fois la synchronisation de campagne personnalisée _et_ le type de synchronisation CRM, il est essentiel de créer des règles afin que vos types de synchronisation CRM ne soient pas ignorés.

   ![](assets/5-1.png)

   >[!NOTE]
   >
   >Si vous envisagez d’arrêter l’utilisateur du [!UICONTROL Type de synchronisation CRM], l’idéal est de créer des règles qui ne font pas référence au &quot;Type de synchronisation&quot;, mais _toujours_ conservent les points de contact CRM actuels. Ainsi, les règles fonctionnent toujours si/quand cet interrupteur est effectué.

Voici un exemple de ce à quoi cela ressemblerait, de sorte qu’aucun point de contact CRM existant ne soit perdu :

## Validation {#validation}

Vous pouvez facilement vérifier les points de contact de l’acheteur et les enregistrements Buyer Attribution Touchpoint dans Campaign pour vous assurer que les règles fonctionnent correctement. Voici un BAT créé par [!DNL Marketo Measure] avec la date de point de contact dynamique appropriée, extraite de la campagne. Le champ Date de création se trouve dans l’image ci-dessous.

![](assets/6-1.png)

## Test {#testing}

1. La fonctionnalité Synchronisation des campagnes s’accompagne d’une fonctionnalité de test qui vous permet de vérifier si les règles que vous avez créées correspondent réellement aux critères de campagne. Commencez par cliquer sur le bouton [!UICONTROL Test] . Les règles doivent d’abord être enregistrées avant de pouvoir commencer le test.

   ![](assets/7-1.png)

   Une fenêtre contextuelle s’affiche, dans laquelle vous pouvez saisir un ID de campagne (15 ou 18 caractères du CRM) à tester. Il s’agit de saisir l’ID de campagne du CRM que vous tentiez de synchroniser pour vous assurer qu’il correspond à la règle que vous avez créée.

   ![](assets/8-1.png)

1. Après avoir cliqué sur [!UICONTROL Test], le nom de la campagne et le nombre de membres de la campagne éligibles pour les points de contact s’affichent. Un tableau ci-dessous présente toutes les règles correspondant à votre ID de campagne. Seules les correspondances s’affichent.

   ![](assets/9.png)

1. Vous pouvez également cliquer sur le nombre de membres pour voir la liste des Leads et contacts et leurs identifiants qui font partie de l&#39;éligibilité aux règles de Campaign. Il s’agit simplement d’un jeu d’exemples qui affichera jusqu’à 50 enregistrements afin que vous puissiez vous faire une idée des enregistrements à qualifier.

   ![](assets/10.png)
