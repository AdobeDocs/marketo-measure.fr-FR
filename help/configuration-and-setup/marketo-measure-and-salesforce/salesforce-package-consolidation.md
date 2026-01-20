---
description: Consolidation de packages [!DNL Salesforce] - [!DNL Marketo Measure]
title: Consolidation des packages [!DNL Salesforce]
exl-id: ae559f5f-91bf-4504-9d5a-af47f95ca01f
feature: Salesforce
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 6%

---

# Consolidation des packages [!DNL Salesforce] {#salesforce-package-consolidation}

Pour améliorer l’expérience utilisateur et simplifier l’utilisation, les packages existants sont compilés dans un package unique et complet.

## Retrait de package {#package-retirement}

Suite à cette consolidation, les packages V1, V2_EXT, V2_Security actuels et tous les packages de création de rapports seront supprimés après août 2023. Si le package V2 est déjà installé, vous devez le mettre à jour vers la nouvelle version consolidée.

## Nouveau Package Consolidé {#new-consolidated-package}

Le nouveau package V2 consolidé intègre toutes les fonctionnalités des packages précédents, offrant ainsi une expérience utilisateur améliorée. Ce package mis à jour permet un suivi plus efficace des performances marketing et des ventes, ainsi que des informations plus précises sur le comportement des clients.

Il existe deux nouveaux champs pour améliorer vos fonctionnalités de création de rapports :

* form_name : désormais disponible dans les objets BT/BAT, ce champ permet aux utilisateurs et utilisatrices de créer des rapports en fonction des noms de formulaire.
* user_touchpoint_id : ce champ permet aux utilisateurs de créer des rapports avec un nombre de points de contact d’utilisateur unique (`bizible2__User_Touchpoint_V2__c` dans Salesforce).

## Soutien et transition {#support-and-transition}

L’équipe d’assistance [Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} est disponible pour répondre à toutes vos questions et vous aider à assurer une transition en douceur vers le nouveau package consolidé.

## Actions requises {#retired-actions}

* Si le package V2 est déjà installé, vous devez le mettre à jour vers la nouvelle version consolidée.
* Si vous disposez de rapports ou de tableaux de bord provenant de n’importe quel package de création de rapports, vous pouvez facilement les recréer sans avoir à apporter de modifications, puisque tous les champs existent dans le package consolidé.
* Si vous disposez de rapports utilisant des champs dans le package V2_EXT, vous pouvez les recréer dans le package consolidé en procédant comme suit :
   * Toutes les données des champs V2_EXT sont disponibles dans les champs de point de contact. Vous pouvez donc modifier vos rapports pour récupérer les données des champs de point de contact V2 correspondants en ajoutant un filtre sur la position du point de contact.
   * Exemple de rapport récupérant tous les prospects avec un FT de contenu publicitaire contenant du texte « Portée ».
      * Requête V2_EXT :
         * bizible2_ext__Ad_Content_FT__c contient la portée

![](assets/package-consolidation-1.png)

* Requête correspondante dans le package consolidé :
   * bizible2__Touchpoint_Position__c contient FT ET
   * Bizible2__Ad_Content__c contient l’extension

![](assets/salesforce-package-consolidation-2.png)

## Questions fréquentes {#faq}

**Le package consolidé aura-t-il des conflits avec les champs de mon package existant ?**

Il n’est pas nécessaire de désinstaller le package avant de l’installer. Il n’y aura pas de conflits dans les champs puisqu’ils se trouvent dans un espace de noms différent.

**Comment puis-je renvoyer les données de mes packages actuels ?**

Vous pouvez déposer un ticket [auprès de l’assistance](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour le renvoi et le retraitement des données BT/BAT afin de renseigner les champs ID de point de contact et ID de formulaire .

**Les champs des packages V1 et V2_EXT seront-ils disponibles dans le package consolidé ?**

Oui. Le package consolidé contient les mêmes champs dans la version 1 avec d’autres répartitions par objets et par champs V2_EXT via les champs de point de contact.

**Les rapports qui utilisent des champs V2_EXT peuvent-ils être recréés dans le package consolidé ?**

Oui. Suivez les étapes de la section [Actions requises](#retired-actions).
