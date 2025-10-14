---
unique-page-id: 18874696
description: ' [!DNL Salesforce] Autorisations recommandées pour [!DNL Marketo Measure] Utilisateur connecté - [!DNL Marketo Measure]'
title: Autorisations [!DNL Salesforce] recommandées pour l’utilisateur [!DNL Marketo Measure] connecté
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 23%

---

# Autorisations [!DNL Salesforce] recommandées pour l’utilisateur connecté [!DNL Marketo Measure] {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] envoie et reçoit des données par l’intermédiaire d’un utilisateur [!DNL Salesforce] connecté à l’application [!DNL Marketo Measure].

Pour transmettre des données de point de contact à votre instance [!DNL Salesforce], l’utilisateur connecté doit avoir accès à [!DNL Marketo Measure] objets personnalisés (c’est-à-dire Buyer Touchpoint et Buyer Attribution Touchpoint) ainsi qu’à des objets [!DNL Salesforce] standard tels que Leads et Contacts. Voir [[!DNL Marketo Measure] dans Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Les licences d’utilisateur administrateur peuvent servir d’utilisateur connecté, car elles disposent souvent par défaut des privilèges de données nécessaires. Cependant, votre équipe peut préférer utiliser un utilisateur d’intégration ou une licence d’utilisateur [!DNL Salesforce] dédiée pour suivre l’impact de [!DNL Marketo Measure] sur votre instance.

Nous recommandons les autorisations suivantes pour nous assurer que les données [!DNL Marketo Measure] circulent correctement :

* [!DNL Marketo Measure] Jeu D’Autorisations Administrateur Pour Un Utilisateur Dédié

Ce jeu d’autorisations géré permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements depuis les objets [!DNL Marketo Measure].

* Afficher et modifier le jeu d’autorisations de pistes converties

Ces autorisations permettent à [!DNL Marketo Measure] de décorer les prospects après leur conversion en contacts. Si ce jeu d’autorisations n’est pas activé, il peut y avoir d’importants écarts de suivi des données. Vous trouverez plus d&#39;informations dans [[!DNL Salesforce Trailblazer] community](https://help.salesforce.com/s/articleView?language=en_US&id=leads_view_edit_converted.htm&type=5).

* [!DNL Salesforce] Case à cocher des utilisateurs marketing

La case à cocher [!UICONTROL Utilisateur marketing] permet à l’utilisateur de créer des campagnes, mais aussi d’utiliser les assistants d’importation de campagne. Si cette case n’est pas cochée, l’utilisateur ou l’utilisatrice peut uniquement afficher les campagnes et leur configuration avancée, modifier leur historique pour un seul prospect ou contact et générer des rapports de campagne. [!DNL Marketo Measure] doit pouvoir lire et écrire vers l’objet de campagne.

**Dépannage supplémentaire**

Si [!DNL Marketo Measure] rencontre toujours des problèmes lors de la lecture ou de l’écriture de données, il peut s’avérer utile d’étudier les points suivants :

* Accès aux files d’attente [!DNL Salesforce]

Si l’utilisateur dédié n’a pas accès aux pistes dans les files d’attente, il ne peut pas modifier les pistes avec des données [!DNL Marketo Measure]. Pour ce faire, vous pouvez avoir un rôle dans la hiérarchie qui permet l’accès aux files d’attente ou qui accorde individuellement l’accès aux utilisateurs.

* Sécurité et accessibilité au niveau du champ

La sécurité au niveau du champ et l’accessibilité des champs sont liées, mais présentent des différences clés. La sécurité au niveau du champ définit la visibilité des champs pour un profil donné, tandis que l’accessibilité des champs détermine si un champ est modifiable en fonction de la sécurité au niveau du champ et de la configuration de la mise en page. À l’aide des jeux d’autorisations du package [!DNL Marketo Measure], vous recevez les paramètres de sécurité d’objet de champ nécessaires. Parfois, pour garantir une bonne accessibilité des champs, l’utilisateur connecté doit disposer des champs [!DNL Marketo Measure] sur les mises en page. Les champs [!DNL Marketo Measure] de la mise en page permettent aux données [!DNL Marketo Measure] de correspondre à [!DNL Salesforce]. Cela dépend de votre environnement [!DNL Salesforce] particulier.

Le [!DNL Salesforce] de chaque organisation a des besoins individuels, mais nous vous fournissons nos besoins pour équilibrer les besoins d’accès [!DNL Marketo Measure] avec vos protocoles de sécurité. N’hésitez pas à contacter [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
