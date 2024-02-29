---
description: Méthodes de gestion des dépenses - [!DNL Marketo Measure]
title: Méthodes de gestion des dépenses
exl-id: 36478d8d-986c-4d4f-8854-3287d6c57a9d
feature: Spend Management
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---

# Méthodes de gestion des dépenses {#spend-management-methods}

Les données de dépense sont essentielles au succès de la création de rapports sur le retour sur investissement avec [!DNL Marketo Measure]. Afin de disposer de rapports précis et complets sur le ROI sur l’ensemble de vos canaux et sous-canaux, vous devez vous assurer que les données de dépense appropriées sont extraites dans [!DNL Marketo Measure].

Il existe trois façons de transférer des données dans [!DNL Marketo Measure]. Chaque méthode est conçue pour extraire des données de dépenses à partir d’entrées de données spécifiques.

**1) Comptes connectés à l’API**

Tout compte publicitaire auquel vous êtes connecté [!DNL Marketo Measure] via une API, ses dépenses seront automatiquement transférées dans [!DNL Marketo Measure] pour la création de rapports sur le retour sur investissement. Pour vérifier les comptes que vous avez connectés et donc qui génèrent des dépenses, accédez à votre [!DNL Marketo Measure] Application et sélectionnez [!UICONTROL Connexions] sous la balise [!UICONTROL Intégrations] . Pour plus d’informations sur la configuration de vos connexions API, consultez notre [Plateformes d’annonces intégrées](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) article.

**2) Synchronisation des coûts de la campagne CRM**

Chaque [!DNL Marketo Measure] a accès à une fonctionnalité appelée [Coûts de la campagne CRM de synchronisation](/help/marketing-spend/spend-management/crm-campaign-costs.md#availability). Par défaut, ce bit de fonctionnalité est défini sur &quot;Non&quot;, mais il peut être activé à tout moment.

![](assets/spend-management-methods-1.png)

Une fois activée, cette fonctionnalité extrait automatiquement les dépenses de n’importe quel programme/campagne CRM répondant aux critères suivants.

i. [!DNL Marketo Measure] vérifie d’abord si la campagne/le programme crée des points de contact, à partir d’une correspondance [Règle de synchronisation de campagne](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md) qui a été créé ou une correspondance [Règle de synchronisation du programme](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md) qui a été créé, ou la variable [Activer la valeur Points de contact d’achat](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md#how-to-create-a-campaign-and-sync-buyer-touchpoints) est &quot;Inclure tous les membres de campagne&quot; ou &quot;Inclure les membres de campagne &quot;réactifs&quot;.

ii. Une Date de début doit être renseignée sur la campagne/le programme.

iii. Une Date de fin doit également être renseignée sur la campagne/le programme.

iv. Enfin, un coût réel (pour les campagnes dans la collecte de données régionale) ou un coût de période (pour les programmes dans Marketo) doit être spécifié.

**3) Chargement manuel des coûts**

Cette méthode vous permet de [charger manuellement les données de dépenses](/help/marketing-spend/spend-management/marketing-channel-costs.md#uploading-marketing-costs) pour les canaux et sous-canaux qui ne sont pas couverts par les comptes connectés à l’API ou la synchronisation des coûts de la campagne CRM. En accédant à la section Dépense marketing de votre [!DNL Marketo Measure] , vous pouvez télécharger des données de dépenses via un fichier CSV pour l’un de vos canaux.

Les clients peuvent utiliser une combinaison de ces trois méthodes pour gérer leurs dépenses et dépendra de la configuration spécifique de la variable [!DNL Marketo Measure]. Parce qu’il existe trois méthodes pour importer des dépenses dans [!DNL Marketo Measure], nous vous recommandons vivement d’utiliser le panorama des dépenses marketing de Discover afin d’obtenir une vue d’ensemble complète de toutes les données relatives aux dépenses. Ce panorama est le seul endroit où vous pourrez voir tous vos canaux et leurs dépenses associées. Le panorama des dépenses marketing peut vous aider à identifier rapidement les lacunes dans vos données de dépenses et à déterminer comment améliorer vos rapports sur le retour sur investissement.
