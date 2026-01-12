---
description: Bonnes pratiques relatives aux canaux hors ligne - [!DNL Marketo Measure]
title: Bonnes pratiques pour les canaux hors ligne
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
feature: Channels
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 4%

---


# Bonnes pratiques pour les canaux hors ligne {#best-practices-for-offline-channels}

## Vue d’ensemble {#overview}

Pour obtenir des rapports [!DNL Marketo Measure] précis, vos canaux marketing doivent être correctement configurés. Le champ « [!UICONTROL Canal marketing] » affiche le groupe de plus haut niveau de tactiques marketing auquel un point de contact peut appartenir (par exemple, Événements, Webinaires, Syndication de contenu, etc.).

La configuration de vos canaux marketing comporte deux aspects : en ligne et hors ligne. Ce document est axé sur les [!DNL Marketo Measure] recommandations de bonnes pratiques relatives à la configuration et à la maintenance de vos canaux hors ligne et à leur synchronisation avec les [!DNL Marketo Measure] via des campagnes CRM.

Les canaux hors ligne présentent deux aspects clés :

1. Mappage de canal hors ligne qui est le framework qui indique [!DNL Marketo Measure] canal et le sous-canal auxquels appartient le point de contact hors ligne
1. La synchronisation de la campagne hors ligne qui correspond à la création des points de contact hors ligne

Les points de contact hors ligne sont créés à partir d’une campagne CRM et sont destinés à suivre toute interaction marketing qui ne peut pas être suivie numériquement via le JavaScript [!DNL Marketo Measure] implémenté sur les pages de votre site web. Lorsqu’une campagne CRM est synchronisée avec [!DNL Marketo Measure], des points de contact sont créés pour les membres de campagne définis dans la campagne.

La valeur « Canal marketing » pour ces points de contact est basée sur le champ « Type » de la campagne. Le mappage de « Type de campagne CRM » à « Canal marketing » et « Sous-canal » est géré dans l’onglet « Canaux hors ligne » des paramètres de votre compte [!DNL Marketo Measure]. En vous assurant que votre mappage de canal hors ligne est exact et à jour, vous garantirez que vos données de point de contact hors ligne sont attribuées aux canaux et sous-canaux marketing corrects dans vos rapports [!DNL Marketo Measure].

## Bonne pratique | Mappage de canal hors ligne {#best-practice-offline-channel-mapping}

Que vous mappiez vos canaux hors ligne pour la première fois ou que vous les examiniez simplement pour vérifier leur précision, gardez à l’esprit les bonnes pratiques suivantes.

* Créer un cadre délibéré pour vos canaux hors ligne
   * Prenez le temps de réfléchir à l’organisation de vos campagnes marketing et à la manière dont elles s’inscrivent dans le framework [!DNL Marketo Measure]. Déterminez quels canaux et sous-canaux doivent être représentés dans vos canaux hors ligne et quels types de campagnes CRM différencient ces canaux les uns des autres
* Tâchez d’utiliser d’abord vos valeurs « Type » de campagne CRM actuelle.
   * Les canaux hors ligne sont définis par le « type » de campagne CRM, mais il se peut que la valeur « type » de campagne CRM personnalisée doive être créée pour s’adapter aux valeurs idéales de canal et de sous-canal hors ligne. Dans l’idéal, les valeurs « Type » de campagne CRM personnalisée doivent respecter la convention de nommage présentée ci-dessous :
      * CANAL - SOUS-CANAL
      * Exemple : Événement - Salon professionnel
      * Cela permet de s’assurer que le mappage au niveau du sous-canal est aussi facile et propre que possible
* Un seul sous-canal ne peut être mappé qu’à un seul « type » de campagne CRM
   * Plusieurs « types » de campagne CRM peuvent être mappés à un seul canal, mais un seul « type » de campagne CRM peut être mappé à chaque sous-canal dans chaque canal
* Seuls les « types » de campagne CRM HORS LIGNE doivent être mappés aux canaux hors ligne, car seules les campagnes hors ligne doivent être synchronisées avec [!DNL Marketo Measure] pour créer des points de contact :
   * Les « types » de campagne CRM EN LIGNE doivent être mappés à un [!UICONTROL canal marketing] = « NULL ». Cette valeur est recommandée, car elle agit comme un « indicateur rouge » qui indique que vos canaux hors ligne ont été examinés et qu’un « Type » de campagne CRM mappé à « NULL » est un « Type » ONLINE et ne doit pas être synchronisé avec [!DNL Marketo Measure]. Les points de contact liés aux « types » de campagnes CRM en ligne seraient déjà suivis via [!DNL Marketo Measure] fonctionnalité et les canaux en ligne. La synchronisation de ces campagnes risque de générer des points de contact « dupliqués » ou un double comptage

## Bonne pratique | Synchronisation de la campagne hors ligne {#best-practice-offline-campaign-sync}

* Vérifiez que le champ &#39;Type&#39; est correct sur chaque campagne CRM
   * « Type » détermine le canal et le sous-canal marketing pour tous les points de contact provenant de la campagne une fois synchronisés
* Que vous utilisiez la méthode de synchronisation de la campagne basée sur le CRM (activer les points de contact de l’acheteur) ou la méthode de synchronisation basée sur l’application [!DNL Marketo Measure] (synchronisation de la campagne personnalisée dans l’onglet « [!UICONTROL Campagnes] » de vos paramètres de compte [!UICONTROL Marketo Measure]), les points de contact hors ligne ne doivent être créés que si le membre de la campagne a eu un engagement hors ligne réel avec la campagne et votre marque :
   * Pour les canaux hors ligne tels que les événements ou les webinaires : le suivi des « enregistrements » s’effectue généralement par le biais d’envois de formulaires sur votre site web et de [!DNL Marketo Measure] fonctionnalité en ligne. Par conséquent, les membres de la campagne dont le statut est « Enregistré » ne doivent pas recevoir de point de contact hors ligne de la campagne pour éviter le double comptage. Les points de contact hors ligne doivent être représentatifs de la « participation » à l’événement ou au webinaire uniquement.
   * Certains canaux hors ligne, tels que la syndication de contenu, sont plus simples. En effet, chaque membre de la campagne possède le même statut « répondu » qui indique qu’il a bien répondu à la campagne, dans ce cas, il télécharge le contenu d’un site tiers et doit donc recevoir un point de contact hors ligne
* Lors de l’utilisation de la méthode de synchronisation de la campagne personnalisée dans l’application [!DNL Marketo Measure], assurez-vous que le champ « Date du point de contact » est basé sur le champ de date de la campagne ou du membre de la campagne qui est le plus indicatif de la date à laquelle l’interaction du point de contact s’est réellement produite
* Utilisez le bouton « Date du point de contact de mise à jour en bloc » si vous devez remplacer la « Date du point de contact » pour l’un des points de contact hors ligne provenant d’une campagne CRM. La « Date du point de contact » doit être aussi précise que possible pour s’assurer que le point de contact possède la « Position du point de contact » la plus précise possible et, par conséquent, le montant approprié du crédit d’attribution

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Une fois la configuration initiale effectuée, votre configuration de canal hors ligne continue à créer des points de contact hors ligne en conséquence. En règle générale, nous vous recommandons de passer en revue votre configuration hors ligne au moins deux fois par an. Cela garantit la clarté et la précision des données de point de contact de l’acheteur.

En outre, si vous apportez des modifications à la gestion ou aux processus de Campaign, vous devez vous assurer que vous mettez à jour le mappage de canal hors ligne [!DNL Marketo Measure] et/ou le processus de synchronisation.

Les modifications qui peuvent inciter votre équipe à effectuer des mises à jour sur la configuration du canal hors ligne dans [!DNL Marketo Measure] peuvent inclure :

* &#39;Types&#39; de campagnes CRM créés ou modifiés
* « Statut » du membre de la campagne créé ou modifié
* Si vous utilisez la méthode de synchronisation de la campagne CRM via le champ « Activer les points de contact de l’acheteur », assurez-vous que ce champ est révisé et mis à jour pour chaque campagne CRM créée. Si ce champ est négligé, il n’y aura aucune donnée de point de contact hors ligne associée
* Si vous rencontrez des points de contact hors ligne d’une campagne CRM qui semblent être des points de contact en ligne (Canal marketing = NULL), assurez-vous que la campagne CRM associée est examinée et que la synchronisation est désactivée

Si votre équipe a récemment rencontré l’un des problèmes ci-dessus, [!DNL Marketo Measure] vous recommande de passer en revue votre mappage de canal hors ligne et vos campagnes hors ligne afin d’apporter les modifications appropriées et de vous assurer qu’elles sont correctement synchronisées.

>[!MORELIKETHIS]
> [Configuration du canal hors ligne](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
> [Synchronisation de campagne personnalisée - Synchronisation de l’application](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
> [Synchronisation des campagnes hors ligne - Synchronisation CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
> [Campagne hors ligne et membres de campagne - Synchronisation CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaigns-and-campaign-members.md)
> [Dates de synchronisation de la campagne - Synchronisation CRM &#x200B;](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaign-sync-dates.md)
> [Configurations pour plusieurs types d’enregistrements Campaign](/help/channel-tracking-and-setup/offline-channels/configurations-record-types.md)
> [Création d&#39;une vue Liste de campagnes](/help/channel-tracking-and-setup/offline-channels/legacy-processes/creating-a-campaign-list-view-for-salesforce-campaigns.md)
> [Synchronisation des données historiques](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-historical-data.md)
