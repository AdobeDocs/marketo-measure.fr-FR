---
description: Méthodes de gestion des dépenses - [!DNL Marketo Measure]
title: Méthodes de gestion des dépenses
exl-id: 36478d8d-986c-4d4f-8854-3287d6c57a9d
feature: Spend Management
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---

# Méthodes de gestion des dépenses {#spend-management-methods}

Les données sur les dépenses sont essentielles à la réussite des rapports sur le retour sur investissement avec [!DNL Marketo Measure]. Pour générer des rapports sur le RSI précis et complets sur tous vos canaux et sous-canaux, vous devez vous assurer que les données de dépenses appropriées sont extraites dans [!DNL Marketo Measure].

Il existe trois façons d’importer des données sur les dépenses dans [!DNL Marketo Measure]. Chaque méthode est conçue pour extraire des données de dépenses à partir d’entrées de données spécifiques.

Comptes connectés de l’API **1**

Les dépenses de tout compte publicitaire que vous avez connecté à [!DNL Marketo Measure] via une API sont automatiquement extraites dans [!DNL Marketo Measure] pour la création de rapports sur le retour sur investissement. Pour vérifier quels comptes vous avez connectés et donc extrayant des dépenses, accédez à votre application [!DNL Marketo Measure] et sélectionnez l’onglet [!UICONTROL Connexions] sous la section [!UICONTROL Intégrations]. Pour plus d’informations sur la configuration des connexions d’API, consultez [Plateformes publicitaires intégrées](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms).

Synchronisation des coûts de la campagne CRM **2**

Chaque compte [!DNL Marketo Measure] a accès à une fonctionnalité appelée [ Synchroniser les coûts de campagne CRM ](/help/marketing-spend/spend-management/crm-campaign-costs.md#availability). Par défaut, ce bit caractéristique est défini sur « Non », mais peut être activé à tout moment.

![](assets/spend-management-methods-1.png)

Lorsqu’elle est activée, cette fonctionnalité extrait automatiquement les dépenses de toute campagne/programme CRM qui répond aux critères suivants :

i. [!DNL Marketo Measure] commence par vérifier si la campagne/le programme crée des points de contact, à partir d’une [règle de synchronisation de la campagne](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md) correspondante qui a été créée ou d’une [règle de synchronisation du programme](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md) correspondante qui a été créée ou si la valeur [Activer les points de contact de l’acheteur](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md#how-to-create-a-campaign-and-sync-buyer-touchpoints) est « Inclure tous les membres de la campagne » ou « Inclure les membres de la campagne « Répondus ».

ii. Une date de début doit être renseignée sur la campagne/le programme

iii. Une date de fin doit être renseignée sur la campagne/le programme

iv. Le coût réel (pour les campagnes dans SFDC) ou le coût périodique (pour les programmes dans Marketo) doit être spécifié.

Chargement manuel des coûts **3**

Cette méthode vous permet de [charger manuellement les données de dépenses](/help/marketing-spend/spend-management/marketing-channel-costs.md#uploading-marketing-costs) pour les canaux et sous-canaux qui ne sont pas couverts par les comptes connectés d’API ou la synchronisation des coûts de campagne CRM. En accédant à la section Dépenses marketing dans vos paramètres de [!DNL Marketo Measure], vous pouvez charger des données de dépenses via un fichier CSV pour l’un de vos canaux.

Les clients peuvent utiliser une combinaison de ces trois méthodes pour gérer leurs dépenses, selon la configuration spécifique du [!DNL Marketo Measure]. Comme il existe trois méthodes d’importation des dépenses dans [!DNL Marketo Measure], nous vous recommandons vivement d’utiliser votre tableau Dépenses marketing situé dans Discover pour obtenir une vue complète de toutes les données relatives aux dépenses. Ce tableau est le seul endroit où vous pourrez voir tous vos canaux et leurs dépenses associées. Le tableau des dépenses marketing peut vous aider à identifier rapidement les lacunes éventuelles dans vos données de dépenses et la manière dont vous pouvez améliorer vos rapports sur le retour sur investissement.
