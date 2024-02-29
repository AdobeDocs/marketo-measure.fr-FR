---
unique-page-id: 18874696
description: Recommandé [!DNL Salesforce] Autorisations pour [!DNL Marketo Measure] Utilisateur connecté - [!DNL Marketo Measure]
title: Autorisations [!DNL Salesforce] recommandées pour l’utilisateur [!DNL Marketo Measure] connecté
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 14%

---

# Recommandé [!DNL Salesforce] Autorisations pour [!DNL Marketo Measure] Utilisateur connecté {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] envoie et reçoit des données par l’intermédiaire d’un utilisateur [!DNL Salesforce] connecté à l’application [!DNL Marketo Measure].

Pour envoyer des données de point de contact vers vos [!DNL Salesforce] , l’utilisateur connecté doit avoir accès à [!DNL Marketo Measure] des objets personnalisés (point de contact de l’achat et point de contact d’attribution de l’achat), ainsi que des objets standard ; [!DNL Salesforce] des objets tels que Leads et Contacts. Voir [[!DNL Marketo Measure] dans Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Les licences d’utilisateur administrateur peuvent servir d’utilisateur connecté, car elles disposent souvent par défaut des privilèges de données nécessaires. Cependant, votre équipe peut préférer utiliser un utilisateur d’intégration ou un [!DNL Salesforce] licence utilisateur pour suivre l’impact de [!DNL Marketo Measure] sur votre instance.

Nous vous recommandons les autorisations suivantes pour vous assurer que [!DNL Marketo Measure] les données circulent de manière précise :

* [!DNL Marketo Measure] Jeu D’Autorisations Administrateur Pour L’Utilisateur Dédié

Ce jeu d’autorisations géré permet à un administrateur SFDC de créer, lire, écrire et supprimer des enregistrements depuis les objets [!DNL Marketo Measure].

* Afficher et modifier le jeu d’autorisations de pistes converties

Ces autorisations permettent à [!DNL Marketo Measure] de décorer les prospects après leur conversion en contacts. Si ce jeu d’autorisations n’est pas activé, il peut y avoir d’importants écarts de suivi des données. Vous trouverez plus d’informations dans la section [[!DNL Salesforce Trailblazer] communauté](https://help.salesforce.com/s/articleView?language=en_US&amp;id=leads_view_edit_converted.htm&amp;type=5).

* [!DNL Salesforce] Case à cocher des utilisateurs marketing

La case à cocher [!UICONTROL Utilisateur marketing] permet à l’utilisateur de créer des campagnes, mais aussi d’utiliser les assistants d’importation de campagne. Si cette option n’est pas sélectionnée, l’utilisateur peut uniquement afficher les campagnes et la configuration avancée de la campagne, modifier l’historique des campagnes pour un seul prospect ou contact et exécuter des rapports de campagne. [!DNL Marketo Measure] doit être capable de lire et d’écrire dans l’objet campaign.

**Dépannage supplémentaire**

If [!DNL Marketo Measure] rencontre toujours des problèmes lors de la lecture ou de l’écriture de données. Il peut s’avérer utile d’étudier les points suivants :

* Accès à [!DNL Salesforce] Files d’attente

Si l’utilisateur dédié n’a pas accès aux pistes dans les files d’attente, il ne peut pas modifier les pistes avec [!DNL Marketo Measure] data. Pour ce faire, vous pouvez avoir un rôle dans la hiérarchie qui permet l’accès aux files d’attente ou qui accorde individuellement l’accès aux utilisateurs.

* Sécurité et accessibilité au niveau du champ

La sécurité au niveau du champ et l’accessibilité des champs sont liées, mais présentent des différences clés. La sécurité au niveau du champ définit la visibilité des champs pour un profil donné, tandis que l’accessibilité des champs détermine si un champ est modifiable en fonction de la sécurité au niveau du champ et de la configuration de la mise en page. En utilisant la variable [!DNL Marketo Measure] les jeux d’autorisations du module vous permettent de recevoir les paramètres de sécurité d’objet de champ nécessaires. Parfois, pour que le champ soit accessible correctement, l’utilisateur connecté doit disposer de la variable [!DNL Marketo Measure] sur les mises en page. [!DNL Marketo Measure] les champs de la mise en page permettent d’utiliser la variable [!DNL Marketo Measure] données à mapper dans [!DNL Salesforce]. Cela dépend de votre [!DNL Salesforce] environnement.

Toutes les organisations [!DNL Salesforce] a des besoins individuels, mais nous vous fournissons nos besoins pour équilibrer la [!DNL Marketo Measure] besoins d’accès avec vos protocoles de sécurité. N&#39;hésitez pas à tendre la main vers [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
