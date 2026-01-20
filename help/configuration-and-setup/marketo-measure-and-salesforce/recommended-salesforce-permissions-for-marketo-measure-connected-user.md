---
unique-page-id: 18874696
description: Autorisations  [!DNL Salesforce]  recommandées pour  [!DNL Marketo Measure]  utilisateur connecté -  [!DNL Marketo Measure]
title: Autorisations [!DNL Salesforce] recommandées pour l’utilisateur [!DNL Marketo Measure] connecté
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
feature: Salesforce
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 23%

---

# Autorisations [!DNL Salesforce] recommandées pour [!DNL Marketo Measure] utilisateur connecté {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] envoie et reçoit des données par l’intermédiaire d’un utilisateur [!DNL Salesforce] connecté à l’application [!DNL Marketo Measure].

Pour transmettre les données de point de contact à votre instance [!DNL Salesforce], l’utilisateur connecté doit avoir accès à [!DNL Marketo Measure] objets personnalisés (c’est-à-dire, Buyer Touchpoint et Buyer Attribution Touchpoint) ainsi qu’aux objets [!DNL Salesforce] standard tels que les prospects et les contacts. Voir [[!DNL Marketo Measure] dans Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

Les licences d’utilisateur de l’administrateur [!DNL Salesforce] peuvent servir d’utilisateur connecté, car elles disposent souvent des privilèges de données nécessaires par défaut. Cependant, votre équipe peut préférer utiliser un utilisateur de l’intégration ou une licence d’utilisateur [!DNL Salesforce] dédiée pour suivre l’impact de la [!DNL Marketo Measure] sur votre instance.

Nous vous recommandons d’utiliser les autorisations suivantes pour vous assurer que [!DNL Marketo Measure] données circulent correctement :

* Ensemble D’Autorisations D’Administrateur [!DNL Marketo Measure] Pour Un Utilisateur Dédié

Ce jeu d’autorisations géré permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements depuis les objets [!DNL Marketo Measure].

* Afficher et modifier le jeu d’autorisations pour les leads convertis

Ces autorisations permettent à [!DNL Marketo Measure] de décorer les prospects après leur conversion en contacts. Si ce jeu d’autorisations n’est pas activé, il peut y avoir des lacunes importantes dans le suivi des données. Vous trouverez plus d’informations dans [[!DNL Salesforce Trailblazer] communauté](https://help.salesforce.com/s/articleView?language=en_US&id=leads_view_edit_converted.htm&type=5).

* [!DNL Salesforce] la case à cocher Utilisateur marketing

La case à cocher [!UICONTROL Utilisateur marketing] permet à l’utilisateur de créer des campagnes, mais aussi d’utiliser les assistants d’importation de campagne. Si cette case n’est pas cochée, l’utilisateur ou l’utilisatrice peut uniquement afficher les campagnes et leur configuration avancée, modifier leur historique pour un seul prospect ou contact et générer des rapports de campagne. [!DNL Marketo Measure] doit pouvoir lire et écrire vers l’objet de campagne.

**Dépannage supplémentaire**

Si [!DNL Marketo Measure] rencontrez toujours des problèmes lors de la lecture ou de l’écriture des données, il peut être utile d’examiner les points suivants :

* Accès aux files d’attente [!DNL Salesforce]

Si l’utilisateur dédié n’a pas accès aux prospects des files d’attente, il ne peut pas modifier les prospects avec les données [!DNL Marketo Measure]. Pour ce faire, vous devez disposer d’un rôle dans la hiérarchie qui permet d’accéder aux files d’attente ou accorder individuellement l’accès aux utilisateurs.

* Sécurité et accessibilité au niveau du champ

La sécurité au niveau du champ et l’accessibilité des champs sont liées, mais présentent quelques différences importantes. La sécurité au niveau du champ définit la visibilité du champ pour un profil donné, tandis que l’accessibilité du champ détermine si un champ est modifiable en fonction de la sécurité au niveau du champ et de la configuration de la mise en page. En utilisant les jeux d’autorisations du package [!DNL Marketo Measure], vous recevez les paramètres de sécurité d’objet de champ nécessaires. Parfois, pour bénéficier d’une accessibilité correcte des champs, l’utilisateur connecté doit disposer des champs [!DNL Marketo Measure] dans les mises en page. [!DNL Marketo Measure] champs de la mise en page permettent aux données [!DNL Marketo Measure] de se mapper en [!DNL Salesforce]. Cela dépend de votre environnement [!DNL Salesforce].

Les [!DNL Salesforce] de chaque organisation ont des besoins individuels, mais nous vous fournissons nos exigences pour équilibrer les besoins d&#39;accès [!DNL Marketo Measure] avec vos protocoles de sécurité. N&#39;hésitez pas à contacter [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
