---
description: Bonnes pratiques pour les canaux hors ligne - [!DNL Marketo Measure]
title: Bonnes pratiques pour les canaux hors ligne
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
feature: Channels
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 4%

---

# Bonnes pratiques pour les canaux hors ligne {#best-practices-for-offline-channels}

## Vue d’ensemble {#overview}

Pour disposer de rapports [!DNL Marketo Measure] précis, vos canaux marketing doivent être correctement configurés. Le champ &#39;[!UICONTROL Canal marketing]&#39; affiche le groupe de tactiques marketing de niveau supérieur auquel un point de contact peut appartenir (par exemple, Événements, Webinaires, Syndication de contenu, etc.).

La configuration de vos canaux marketing comporte deux aspects : en ligne et hors ligne. Ce document se concentre sur les recommandations de bonnes pratiques [!DNL Marketo Measure] pour configurer et gérer vos canaux hors ligne et sur la manière dont ils sont synchronisés avec [!DNL Marketo Measure] via les campagnes CRM.

Les canaux hors ligne ont deux aspects clés :

1. Mappage des canaux hors ligne qui est la structure qui indique à [!DNL Marketo Measure] à quel canal et sous-canal le point de contact hors ligne appartient
1. Synchronisation des campagnes hors ligne qui est la création des points de contact hors ligne

Les points de contact hors ligne sont créés à partir d&#39;une campagne CRM et ont pour but de suivre toute interaction marketing qui ne peut pas être suivie numériquement via le JavaScript [!DNL Marketo Measure] implémenté sur les pages de votre site web. Lorsqu’une campagne CRM est synchronisée avec [!DNL Marketo Measure], des points de contact sont créés pour les membres de campagne définis dans la campagne.

La valeur &quot;Canal marketing&quot; de ces points de contact est basée sur le champ &quot;Type&quot; de la campagne. Le mappage de &quot;Type de campagne CRM&quot; à &quot;Canal marketing&quot; et &quot;Sous-canal&quot; est géré dans l’onglet &quot;Canaux hors ligne&quot; de vos paramètres de compte [!DNL Marketo Measure]. En veillant à ce que le mappage de votre canal hors ligne soit précis et à jour, vous garantissez que vos données de point de contact hors ligne sont attribuées aux canaux marketing et aux sous-canaux appropriés dans vos rapports [!DNL Marketo Measure].

## Bonne pratique | Mappage de canal hors ligne {#best-practice-offline-channel-mapping}

Gardez à l’esprit les bonnes pratiques suivantes, que vous mappiez vos canaux hors ligne pour la première fois ou que vous les examiniez simplement pour vérifier leur précision.

* Création d’une structure délibérée pour vos canaux hors ligne
   * Prenez le temps de réfléchir à l’organisation de vos campagnes marketing et à la manière dont elles s’inscrivent dans le framework [!DNL Marketo Measure]. Déterminer quels canaux et sous-canaux doivent être représentés dans vos canaux hors ligne et quels types de campagne CRM différencient ces canaux les uns des autres
* Commencez par utiliser vos valeurs &quot;Type&quot; de campagne CRM actuelles.
   * Les canaux hors ligne sont définis par le &quot;Type&quot; de la campagne CRM. Toutefois, il se peut que la valeur &quot;Type&quot; de la campagne CRM personnalisée doive être créée pour s’adapter aux valeurs idéales Canal hors ligne et Sous-canal. Les valeurs &quot;Type&quot; de campagne CRM personnalisée doivent porter la convention d’affectation de nom illustrée ci-dessous :
      * CANAL - SUBCANAL
      * Exemple : Événement - Tradeshow
      * Cela permet de s’assurer que le mappage au niveau du sous-canal est aussi simple et propre que possible.
* Un sous-canal ne peut être mappé qu’à un type de campagne CRM
   * Plusieurs types de campagne CRM peuvent être mappés à un seul canal, mais un seul type de campagne CRM peut être mappé à chaque sous-canal de chaque canal.
* Seuls les &quot;types&quot; de campagne CRM hors ligne doivent être mappés aux canaux hors ligne, car seules les campagnes hors ligne doivent être synchronisées avec [!DNL Marketo Measure] pour créer des points de contact :
   * Les &quot;types&quot; de la campagne CRM ONLINE doivent être mappés à un [!UICONTROL canal marketing] = &quot;NULL&quot;. Cette valeur est recommandée, car elle agit comme un &quot;indicateur rouge&quot; qui indique que vos canaux hors ligne ont été vérifiés et que tout &quot;type&quot; de campagne CRM mappé sur &quot;NULL&quot; est un &quot;type&quot; EN LIGNE et ne doit pas être synchronisé avec [!DNL Marketo Measure]. Les points de contact liés aux &quot;types&quot; de la campagne CRM en ligne seraient déjà suivis via les fonctionnalités et canaux en ligne [!DNL Marketo Measure]. La synchronisation de ces campagnes risque de &quot;dupliquer&quot; les points de contact/double comptage.

## Bonne pratique | Synchronisation des campagnes hors ligne {#best-practice-offline-campaign-sync}

* Assurez-vous que le champ &#39;Type&#39; est précis sur chaque campagne CRM
   * &quot;Type&quot; détermine Canal marketing et Sous-canal pour tous les points de contact provenant de la campagne une fois synchronisés.
* Que vous utilisiez la méthode de synchronisation de campagne basée sur la gestion de la relation client (Activer les points de contact de l’acheteur) ou la méthode de synchronisation basée sur l’application [!DNL Marketo Measure] (Synchronisation de campagne personnalisée dans l’onglet &#39;[!UICONTROL Campagnes]&#39; de vos paramètres de compte [!UICONTROL Marketo Measure]), les points de contact hors ligne ne doivent être créés que si le membre de campagne a un engagement hors ligne réel avec Campaign et votre marque :
   * Pour les canaux hors ligne tels que les événements ou les webinaires : les &quot;inscriptions&quot; sont généralement suivies via les envois de formulaire sur votre site web et la fonctionnalité en ligne [!DNL Marketo Measure]. Par conséquent, les membres de la campagne dont le statut est &quot;enregistrés&quot; ne doivent pas recevoir de point de contact hors ligne de la campagne pour éviter un double comptage. Les points de contact hors ligne doivent être représentatifs de la &quot;participation&quot; à l’événement ou au webinaire uniquement.
   * Certains canaux hors ligne, tels que la syndication de contenu, sont plus simples dans la mesure où chaque membre de campagne a le même état de &quot;réponse&quot; qui indique qu’il a effectivement répondu à la campagne. Dans ce cas, il télécharge du contenu sur un site tiers et doit donc recevoir un point de contact hors ligne.
* Lors de l’utilisation de la méthode de synchronisation de campagne personnalisée dans l’application [!DNL Marketo Measure], assurez-vous que le champ &quot;Date du point de contact&quot; est basé sur le champ de date de la campagne ou du membre de la campagne qui est le plus indicateur du moment où l’interaction du point de contact s’est réellement produite.
* Utilisez le bouton &quot;Date de point de contact de mise à jour en bloc&quot; si vous devez remplacer la &quot;Date de point de contact&quot; pour l’un des points de contact hors ligne provenant d’une campagne CRM. La &quot;Date du point de contact&quot; doit être aussi précise que possible pour s’assurer que le point de contact contient la &quot;position du point de contact&quot; la plus précise possible et, par conséquent, le crédit d’attribution approprié.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Une fois la configuration initiale effectuée, votre configuration de canal hors ligne continue à créer des points de contact hors ligne en conséquence. Il est recommandé de passer en revue votre configuration hors ligne au moins deux fois par an. Cela garantit des données de point de contact Acheteur claires et précises.

En outre, si vous apportez des modifications à la gestion ou aux processus de Campaign, vous devez vous assurer que vous mettez à jour votre processus de synchronisation et/ou mappage de canal hors ligne [!DNL Marketo Measure].

Les modifications susceptibles de déclencher votre équipe à mettre à jour la configuration du canal hors ligne dans [!DNL Marketo Measure] peuvent inclure :

* Types de campagne CRM créés ou modifiés
* Statut du membre de la campagne créé ou modifié
* Si vous utilisez la méthode de synchronisation des campagnes CRM via le champ &quot;Activer les points de contact des acheteurs&quot;, assurez-vous que ce champ est révisé et mis à jour pour chaque campagne CRM créée. Si ce champ est négligé, il n’y aura aucune donnée de point de contact hors ligne associée.
* Si vous rencontrez des points de contact hors ligne d’une campagne CRM qui semblent être des points de contact en ligne (Canal marketing = NULL), vérifiez que la campagne CRM associée est passée en revue et que la synchronisation est désactivée.

Si votre équipe a récemment fait l&#39;expérience de l&#39;une des expériences ci-dessus, [!DNL Marketo Measure] vous recommande de passer en revue le mappage des canaux hors ligne et les campagnes hors ligne afin d&#39;apporter les modifications appropriées et de vous assurer qu&#39;elles sont correctement synchronisées.

>[!MORELIKETHIS]
>
>* [Configuration de canal hors ligne](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Synchronisation de campagne personnalisée - Synchronisation de l’application](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Synchronisation des campagnes hors ligne - Synchronisation CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
>* [Campagne hors ligne et membres de campagne - Synchronisation CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaigns-and-campaign-members.md)
>* [Dates de synchronisation de campagne - Synchronisation CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaign-sync-dates.md)
>* [Configurations pour plusieurs types d’enregistrements Campaign](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md)
>* [Création d’une vue de liste de campagnes](/help/channel-tracking-and-setup/offline-channels/legacy-processes/creating-a-campaign-list-view-for-salesforce-campaigns.md)
>* [Synchronisation des données historiques](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-historical-data.md)
