---
description: Méthodes de gestion des dépenses - [!DNL Marketo Measure]
title: Méthodes de gestion des dépenses
exl-id: 36478d8d-986c-4d4f-8854-3287d6c57a9d
feature: Spend Management
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---

# Méthodes de gestion des dépenses {#spend-management-methods}

Les données de dépense sont essentielles au succès de la création de rapports sur le retour sur investissement avec [!DNL Marketo Measure]. Pour disposer de rapports de retour sur investissement précis et complets sur l’ensemble de vos canaux et sous-canaux, vous devez vous assurer que les données de dépenses appropriées sont extraites vers [!DNL Marketo Measure].

Il existe trois façons de transférer des données dans [!DNL Marketo Measure]. Chaque méthode est conçue pour extraire des données de dépenses à partir d’entrées de données spécifiques.

**1 comptes connectés à l’API**

Tout compte publicitaire que vous avez connecté à [!DNL Marketo Measure] par le biais d’une API a ses dépenses automatiquement transférées dans [!DNL Marketo Measure] pour la création de rapports sur le retour sur investissement. Pour vérifier les comptes que vous avez connectés et par conséquent qui récupèrent dans les dépenses, accédez à votre application [!DNL Marketo Measure] et sélectionnez l’onglet [!UICONTROL Connexions] sous la section [!UICONTROL Intégrations] . Pour plus d’informations sur la configuration de vos connexions API, consultez la section [Plateformes d’annonces intégrées](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms).

**2 Synchronisation des coûts de campagne CRM**

Chaque compte [!DNL Marketo Measure] a accès à une fonctionnalité appelée [Synchroniser les coûts de campagne CRM](/help/marketing-spend/spend-management/crm-campaign-costs.md#availability). Par défaut, ce bit de fonctionnalité est défini sur &quot;Non&quot;, mais il peut être activé à tout moment.

![](assets/spend-management-methods-1.png)

Lorsqu’elle est activée, cette fonctionnalité extrait automatiquement les dépenses de n’importe quel programme/campagne CRM répondant aux critères suivants :

i. [!DNL Marketo Measure] commence par vérifier si la campagne/le programme crée des points de contact, soit à partir d’une [règle de synchronisation de campagne](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md) correspondante, soit à partir d’une [règle de synchronisation de programme](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md) correspondante, soit à partir de la [valeur Activer les points de contact d’achat](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md#how-to-create-a-campaign-and-sync-buyer-touchpoints) est &quot;Inclure tous les membres de campagne&quot; ou &quot;Inclure les membres de campagne &quot;réactifs&quot;.&quot;

ii. Une Date de début doit être renseignée sur la campagne/le programme.

iii. Une Date de fin doit être renseignée sur la campagne/le programme.

iv. Le coût réel (pour les campagnes dans SFDC) ou le coût de la période (pour les programmes dans Marketo) doit être spécifié.

**3 Chargement manuel des coûts**

Cette méthode vous permet de [&#x200B; télécharger manuellement les données de dépenses](/help/marketing-spend/spend-management/marketing-channel-costs.md#uploading-marketing-costs) pour ces canaux et sous-canaux qui ne sont pas couverts par les comptes connectés à l’API ou la synchronisation des coûts de campagne CRM. En accédant à la section Dépense marketing dans vos paramètres [!DNL Marketo Measure], vous pouvez télécharger des données de dépenses via un fichier CSV pour l’un de vos canaux.

Les clients peuvent utiliser une combinaison des trois méthodes pour gérer leurs dépenses, en fonction de la configuration spécifique de [!DNL Marketo Measure]. Comme il existe trois méthodes pour importer des dépenses dans [!DNL Marketo Measure], il est vivement recommandé d’utiliser le tableau des dépenses marketing situé dans Discover pour obtenir une vue d’ensemble complète de toutes les données relatives aux dépenses. Ce panorama est le seul endroit où vous pourrez voir tous vos canaux et leurs dépenses associées. Le panorama des dépenses marketing peut vous aider à identifier rapidement les lacunes dans vos données de dépenses et à déterminer comment améliorer vos rapports sur le retour sur investissement.
