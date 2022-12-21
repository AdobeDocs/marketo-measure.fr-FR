---
unique-page-id: 18874554
description: Génération et mappage des points de contact - [!DNL Marketo Measure] - Documentation du produit
title: Génération et mappage des points de contact
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Génération et mappage des points de contact {#touchpoint-generation-and-mapping}

[!DNL Marketo Measure] les articles d’attribution dépendent de deux processus :

* Génération de points de contact qui crée des points de contact qui représentent les interactions d’une personne avec vos efforts marketing et de vente
* Mappage des points de contact, qui crédite les points de contact sur le canal et le sous-canal appropriés

Pour que vous tiriez le meilleur parti de [!DNL Marketo Measure], vous devez travailler avec votre [!DNL Marketo Measure] Rep pour personnaliser les deux processus en fonction des besoins de votre entreprise.

Méthodes de génération de points de contact

Le processus de génération du point de contact répond à la question &quot;Comment se passe-t-il ? [!DNL Marketo Measure] vous savez que c&#39;est arrivé ?&quot; Selon votre jeu de fonctionnalités et les types d’interactions que vos clients potentiels peuvent avoir, il existe jusqu’à trois façons [!DNL Marketo Measure] peut relever une interaction et créer un point de contact pour la représenter.

| **Type d&#39;interaction** | **Exemple** | **Méthode de génération de point de contact** |
|---|---|---|
| En ligne, sur votre ou vos sites | Form fill | [!DNL Marketo Measure] JavaScript |
| Hors ligne ; En ligne et non sur votre ou vos sites | les dépannages; Le partenaire de syndication de contenu fournit une liste de responsables qui ont interagi avec votre contenu. | Appartenance à Campaign CRM synchronisée avec [!DNL Marketo Measure], soit en définissant le type de synchronisation de campagne directement dans la campagne, soit en définissant des règles sur la page Campagnes dans [!DNL Marketo Measure] |
| Activité de vente | Appel sortant par SDR | Enregistrement d’activité CRM (tâche ou événement) synchronisé avec [!DNL Marketo Measure], par le biais de la logique sur la variable [!UICONTROL Activités] page [!DNL Marketo Measure] |

Méthodes de mappage des points de contact

Le processus de mappage des points de contact répond à la question : &quot;Une fois ce point de contact créé, comment [!DNL Marketo Measure] vous allez savoir à quel canal et sous-canal il appartient ?&quot; Chaque méthode de génération de point de contact possède sa propre méthode de mappage des points de contact.

| **Type d&#39;interaction** | **Méthode de génération** | **Méthode de mappage** |
|---|---|---|
| En ligne, sur votre ou vos sites | [!DNL Marketo Measure] JavaScript | Par le biais de la [!DNL Online Channels] page [!DNL Marketo Measure], en référençant les valeurs UTM, la page d’entrée et les informations de page de référence |
| Hors ligne ; En ligne, et non sur votre ou vos sites | Synchronisation de l’appartenance CRM Campaign | Par le biais de la [!UICONTROL Canaux hors ligne] page [!DNL Marketo Measure], en référençant Type de campagne |
| Activité de vente | Synchronisation de l’activité CRM | Par le biais de la [!UICONTROL Canaux en ligne] page [!DNL Marketo Measure], en référençant le nom de la campagne affecté à la variable [!UICONTROL Activités] page |

>[!MORELIKETHIS]
>
>* [Mappage des points de contact en ligne à [!DNL Marketo Measure] Canaux/Sous-canaux](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Synchronisation des campagnes CRM depuis SFDC](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)
>* [Synchronisation des campagnes CRM dans [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Mappage des campagnes CRM à [!DNL Marketo Measure] Canaux/Sous-canaux](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Création de points de contact à partir des activités de vente](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [FAQ sur les activités et mappage des points de contact des activités sur les canaux/sous-canaux](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)


