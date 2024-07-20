---
description: "[!DNL Salesforce] Consolidation des modules - [!DNL Marketo Measure]"
title: "[!DNL Salesforce] Consolidation des modules"
exl-id: ae559f5f-91bf-4504-9d5a-af47f95ca01f
feature: Salesforce
source-git-commit: 518a984b0d8d640290bd9b637221fcdc0948e5b9
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 5%

---

# Consolidation des packages [!DNL Salesforce] {#salesforce-package-consolidation}

Pour améliorer l’expérience utilisateur et simplifier l’utilisation, les modules existants sont compilés en un seul module complet.

## Retrait d’un paquet {#package-retirement}

En raison de cette consolidation, les modules V1, V2_EXT, V2_Security et tous les modules de reporting actuels seront abandonnés après août 2023. Si le package V2 est déjà installé, vous devez le mettre à jour vers la nouvelle version consolidée.

## Nouveau package consolidé {#new-consolidated-package}

Le nouveau package V2 consolidé intègre toutes les fonctionnalités des packages précédents, offrant ainsi une meilleure expérience utilisateur. Ce package mis à jour permet un suivi plus efficace des performances marketing et de vente et permet d’obtenir des informations plus détaillées sur le comportement des clients.

Deux nouveaux champs vous permettent d’améliorer vos fonctionnalités de reporting :

* form_name : désormais disponible dans les objets BT/BAT, ce champ permet aux utilisateurs et utilisatrices de créer des rapports en fonction des noms de formulaire.
* user_touchpoint_id : ce champ permet aux utilisateurs de créer des rapports avec des nombres de points de contact utilisateur uniques (`bizible2__User_Touchpoint_V2__c` dans Salesforce).

## Assistance et transition {#support-and-transition}

L’ [ équipe d’assistance](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} est disponible pour répondre à toutes les questions et vous aider à garantir une transition fluide vers le nouveau package consolidé.

## Actions requises {#retired-actions}

* Si le package V2 est déjà installé, vous devez le mettre à jour vers la nouvelle version consolidée.
* Si vous disposez de rapports ou de tableaux de bord provenant de n’importe quel package de reporting, vous pouvez facilement les recréer sans aucune modification requise, car tous les champs existent dans le package consolidé.
* Si des rapports utilisent des champs dans le package V2_EXT, vous pouvez les recréer dans le package consolidé en procédant comme suit :
   * Toutes les données des champs V2_EXT sont disponibles dans les champs de point de contact. Vous pouvez donc modifier vos rapports pour récupérer les données des champs de point de contact V2 correspondants en ajoutant un filtre sur la position du point de contact.
   * Exemple de rapport récupérant toutes les pistes avec le contenu publicitaire FT contenant le texte &quot;Attractivité&quot;.
      * Requête V2_EXT :
         * bizible2_ext__Ad_Content_FT__c contient le canal d’extension

![](assets/package-consolidation-1.png)

* Requête correspondante dans le package consolidé :
   * bizible2__Touchpoint_Position__c contient FT AND AND
   * bizible2__Ad_Content__c contient Outreach

![](assets/salesforce-package-consolidation-2.png)

## Questions fréquentes {#faq}

**Le package consolidé va-t-il avoir des conflits avec les champs de mon package existant ?**

Vous n’avez pas besoin de désinstaller votre package avant d’installer le package consolidé. Il n’y aura aucun conflit dans les champs, car ils se trouvent dans un autre espace de noms.

**Comment puis-je renvoyer les données de mes packages actuels ?**

Vous pouvez déposer un ticket [avec l’assistance](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour le renvoi et le retraitement des données BT/BAT afin de remplir les champs Identifiant du point de contact et Identifiant du formulaire.

**Les champs des packages V1 et V2_EXT seront-ils disponibles dans le package consolidé ?**

Oui. Le package consolidé contient les mêmes champs dans V1 avec d’autres ventilations par objets et des champs V2_EXT via les champs de point de contact.

**Les rapports qui utilisent des champs V2_EXT peuvent-ils être recréés dans le package consolidé ?**

Oui. Suivez les étapes de la section [Actions requises](#retired-actions) .
