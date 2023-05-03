---
description: "[!DNL Salesforce] Consolidation des modules - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Salesforce] Consolidation des modules"
hide: true
hidefromtoc: true
source-git-commit: 502a08b9a670c0b9a997a0fbb238a4db865f79d2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Salesforce] Consolidation des modules {#salesforce-package-consolidation}

Nous sommes ravis d’annoncer les modifications à venir des packages Marketo Measure Salesforce. Afin d’améliorer l’expérience utilisateur et de simplifier l’utilisation, nous consolidons tous les modules existants en un seul module complet.

## Retrait d’un paquet {#package-retirement}

En raison de cette consolidation, les modules V1, V2_EXT, V2_Security et tous les modules de reporting actuels seront abandonnés après août 2023. Si le package V2 est déjà installé, vous devez le mettre à jour vers la nouvelle version consolidée.

## Nouveau package consolidé {#new-consolidated-package}

Le nouveau package V2 consolidé intègre toutes les fonctionnalités des packages précédents, offrant ainsi une meilleure expérience utilisateur. Ce module mis à jour permet un suivi plus efficace des performances marketing et commerciales et permet d’obtenir des informations plus précises sur le comportement des clients.

## Assistance et transition {#support-and-transition}

Nous comprenons que ce changement peut nécessiter des ajustements, et nous nous engageons à vous soutenir tout au long du processus. Notre [Équipe d’assistance](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} est facilement disponible pour répondre à toutes les questions et faciliter la transition vers le nouveau module consolidé.

## Actions requises {#retired-actions}

* Si le package V2 est déjà installé, vous devez le mettre à jour vers la nouvelle version consolidée.
* Si vous disposez de rapports ou de tableaux de bord provenant de n’importe quel package de reporting, vous pouvez facilement les recréer sans aucune modification requise, car tous les champs utilisés existent dans le package consolidé.
* Si des rapports utilisent des champs dans le package V2_EXT, vous pouvez les recréer dans le package consolidé en procédant comme suit :
   * Toutes les données des champs V2_EXT sont disponibles dans les champs de point de contact. Vous pouvez donc modifier vos rapports pour récupérer les données des champs de point de contact V2 correspondants en ajoutant un filtre sur la position du point de contact.
   * Exemple de rapport récupérant toutes les pistes avec le contenu publicitaire FT contenant le texte &quot;Attractivité&quot;.
      * Requête V2_EXT :
         * bizible2_ext__Ad_Content_FT__c contient le canal d’extension

![](assets/salesforce-package-consolidation-1.png)

* Requête correspondante dans le package consolidé :
   * bizible2__Touchpoint_Position__c contient FT AND AND
   * bizible2__Ad_Content__c contient Outreach

![](assets/salesforce-package-consolidation-2.png)

## Questions fréquentes {#faq}

**Le package consolidé sera-t-il en conflit avec les champs de mon package existant ?**

Vous n’avez pas besoin de désinstaller votre package avant d’installer le package consolidé. Il n’y aura aucun conflit dans les champs, car ils seront dans un autre espace de noms.

**Comment puis-je renvoyer les données de mes packages actuels ?**

Vous pouvez déposer un ticket [avec assistance](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour renvoyer et retraiter les données BT/BAT afin de renseigner les champs Identifiant du point de contact et Identifiant du formulaire.

**Les champs des packages V1 et V2_EXT seront-ils disponibles dans le package consolidé ?**

Oui. Le package consolidé contient les mêmes champs dans la version V1 avec d’autres ventilations par objets et les champs V2_EXT via les champs de point de contact.

**Les rapports qui utilisent des champs V2_EXT peuvent-ils être recréés dans le package consolidé ?**

Oui. Suivez les étapes de la section [Actions requises](#retired-actions) ci-dessus.
