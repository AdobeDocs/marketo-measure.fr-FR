---
description: Conseils de génération et de mappage des points de contact pour les utilisateurs de Marketo Measure
title: Génération et mappage des points de contact
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 97%

---

# Génération et mappage des points de contact {#touchpoint-generation-and-mapping}

L’attribution [!DNL Marketo Measure] s’articule autour de deux processus :

* La génération de points de contact crée des points de contact qui représentent les interactions d’une personne avec vos actions marketing et de vente
* Le mappage des points de contact attribue les points de contact au canal et au sous-canal appropriés

Pour tirer le meilleur parti de [!DNL Marketo Measure], vous devez travailler avec votre représentant ou représentante [!DNL Marketo Measure] pour adapter les deux processus aux besoins de votre organisation.

Méthodes de génération de points de contact

Le processus de génération de points de contact répond à la question « Comment [!DNL Marketo Measure] va-t-il savoir que cela s’est produit ? » Selon votre jeu de fonctionnalités et les types d’interactions que vos clients potentiels peuvent avoir, [!DNL Marketo Measure] peut détecter une interaction et créer un point de contact pour la représenter de trois manières différentes.

>[!IMPORTANT]
>
>[!DNL Marketo Measure] génère un seul point de contact par session. Si plusieurs formulaires ont été remplis, seul le premier est capturé.

| **Type d’interaction** | **Exemple** | **Méthode de génération de point de contact** |
|---|---|---|
| En ligne, sur vos sites | Remplissage de formulaire | Code JavaScript [!DNL Marketo Measure] |
| Hors ligne ; en ligne, mais pas sur vos sites | Salons ; le partenaire de syndication de contenu fournit une liste de prospects qui ont interagi avec votre contenu. | Abonnement à une campagne CRM synchronisée avec [!DNL Marketo Measure], soit en définissant le type de synchronisation de campagne directement dans la campagne, soit en définissant des règles sur la page Campagnes dans [!DNL Marketo Measure] |
| Activité de vente | Appel sortant par SDR | Enregistrement d’activité CRM (tâche ou événement) synchronisé avec [!DNL Marketo Measure], par le biais de la logique sur la page [!UICONTROL Activités] dans [!DNL Marketo Measure] |

Méthodes de mappage des points de contact

Le processus de mappage des points de contact répond à la question : « Une fois ce point de contact créé, comment [!DNL Marketo Measure] va-t-il savoir à quel canal et sous-canal il appartient ? » Chaque méthode de génération de point de contact possède sa propre méthode de mappage des points de contact.

| **Type d’interaction** | **Méthode de génération** | **Méthode de mappage** |
|---|---|---|
| En ligne, sur vos sites | Code JavaScript [!DNL Marketo Measure] | Sur la page [!DNL Online Channels] dans [!DNL Marketo Measure], en référençant les valeurs UTM, la page de destination et les informations de page de référence |
| Hors ligne ; en ligne, mais pas sur vos sites | Synchronisation de l’abonnement à une campagne CRM | Sur la page [!UICONTROL Canaux hors ligne] dans [!DNL Marketo Measure], en référençant le type de campagne |
| Activité de vente | Synchronisation de l’activité CRM | Sur la page [!UICONTROL Canaux en ligne] dans [!DNL Marketo Measure], en référençant le nom de la campagne attribué sur la page [!UICONTROL Activités] |

>[!MORELIKETHIS]
>
>* [Mappage des points de contact en ligne à des canaux/sous-canaux  [!DNL Marketo Measure] ](/help/channel-tracking-and-setup/online-custom-channel-setup.md)
>* [Synchronisation des campagnes CRM à partir de SFDC](/help/channel-tracking-and-setup/syncing-offline-campaigns.md)
>* [Synchronisation des campagnes CRM à partir de  [!DNL Marketo Measure]](/help/channel-tracking-and-setup/custom-campaign-sync.md)
>* [Mappage des campagnes CRM à des canaux/sous-canaux  [!DNL Marketo Measure] ](/help/channel-tracking-and-setup/offline-custom-channel-setup.md)
>* [Création de points de contact à partir des activités de vente](/help/channel-tracking-and-setup/salesforce-activities-attribution.md)
>* [Questions fréquentes sur les activités et mappage des points de contact des activités à des canaux/sous-canaux](/help/channel-tracking-and-setup/activities-attribution-faq.md)

