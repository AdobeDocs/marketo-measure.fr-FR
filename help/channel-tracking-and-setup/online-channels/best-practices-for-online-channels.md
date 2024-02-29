---
description: Bonnes pratiques pour les canaux en ligne - [!DNL Marketo Measure]
title: Bonnes pratiques pour les canaux en ligne
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
feature: Channels
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 67%

---

# Bonnes pratiques pour les canaux en ligne {#best-practices-for-online-channels}

## Vue d’ensemble {#overview}

Pour avoir la précision [!DNL Marketo Measure] création de rapports, vos canaux marketing doivent être correctement configurés. Le champ Canal marketing affiche le groupe d’activités marketing de niveau supérieur auquel un point de contact peut appartenir (par exemple, Recherche payante, Direct, Social, etc.).

La configuration de vos canaux marketing comporte deux aspects : en ligne et hors ligne. Ce document est axé sur la [!DNL Marketo Measure] recommandations de bonnes pratiques pour configurer et gérer vos canaux en ligne.

Les règles de canal en ligne constituent les directives relatives à la manière dont : [!DNL Marketo Measure] mappe vos points de contact numériques, c’est-à-dire tout point de contact qui est suivi et créé au moyen de la fonction [!DNL Marketo Measure] JS sur votre site. Si ces règles ne sont pas complètes ou ne sont pas classées correctement, les points de contact peuvent être attribués au mauvais canal, ce qui réduit l’exactitude de vos rapports. En veillant à ce que vos règles de canal en ligne soient exactes et à jour, vous avez la garantie que vos données numériques sont attribuées au bon canal et aux bons sous-canaux dans votre création de rapports [!DNL Marketo Measure].

## Bonne pratique {#best-practice}

Gardez à l’esprit les bonnes pratiques suivantes, que vous configuriez vos règles pour la première fois ou que vous les révisiez simplement pour en vérifier l’exactitude.

Prenez le temps de réfléchir à l’organisation de vos campagnes marketing et à la manière dont elle s’inscrivent dans le framework [!DNL Marketo Measure]. Déterminez les canaux et les sous-canaux à représenter dans vos canaux en ligne et les campagnes, paramètres UTM ou sites web de référence qui différencient ces canaux les uns des autres.

Points à retenir :

* Tous les canaux et sous-canaux numériques doivent être représentés par au moins une règle
   * Si le canal ne conduit pas les personnes vers votre site, il ne s’agit pas d’un canal en ligne
* Vous pouvez avoir plusieurs règles pour un canal/sous-canal
   * Avoir plusieurs règles peut être considéré comme un « filet plus large » pour s’assurer que chaque point de contact est correctement mappé. Il arrive souvent d’ajouter de manière incorrecte ou d’oublier d’ajouter des paramètres. Disposer de plusieurs règles pour capturer un canal/sous-canal est donc une bonne idée pour garantir l’exactitude du mappage.
* La logique [!DNL Marketo Measure] donne la priorité au mappage des points de contact dans l’ordre décroissant, en commençant par la ligne supérieure de la feuille de calcul et en allant vers le bas
   * [!DNL Marketo Measure] lit chaque règle (ligne), en recherchant les valeurs « true » et « first fit ». Le point de contact est ensuite mappé à ce canal/sous-canal
   * Ne triez pas votre feuille dans l’ordre alphabétique, car cela interfère avec les règles logiques.
* Conservez les règles entre crochets, ne les modifiez pas et ne les ajoutez pas aux règles entre crochets (exemple : [Référencement payant AdWords] ou [Référencement Facebook])
   * Ils sont prêts à l&#39;emploi. [!DNL Marketo Measure] règles ayant une logique intégrée, qui sont liées à la variable [!DNL Marketo Measure] intégrations. Attribuez la priorité absolue à ces règles pour cette section de canal/sous-canal. [!DNL Marketo Measure] les intégrations peuvent fonctionner comme prévu.
* Une fois le fichier chargé, vous ne pouvez plus modifier les règles pendant sept jours
   * [!DNL Marketo Measure] utilise ce délai pour traiter et mettre à jour les points de contact. Veillez donc à vérifier deux fois vos règles avant de les charger.

## Bonne pratique de maintenance {#best-practice-for-maintenace}

Une fois les règles de canal en ligne enregistrées et traitées, elles fonctionnent en permanence pour regrouper vos points de contact numériques. Toutefois, certains changements ou scénario peuvent vous inciter à revoir la configuration de votre canal en ligne. [!DNL Marketo Measure] recommande de consulter vos règles de canal en ligne tous les six mois. Cela permet de [!DNL Marketo Measure] Les données sont alignées avec vos définitions internes des canaux/sous-canaux en ligne et votre utilisation des UTM.

Voici d’autres éléments qui pourraient inciter votre équipe à effectuer la maintenance du canal en ligne...

* Nouveau canal/sous-canal numérique lancé
* Mise à jour ou modification des paramètres UTM
* Modifications apportées à l’organisation des canaux ou aux conventions de nommage
* Changements au sein de votre équipe marketing

Si votre équipe a récemment été confrontée à l’une des situations ci-dessus, [!DNL Marketo Measure] vous recommande d’examiner les règles de vos canaux en ligne et d’apporter les modifications appropriées.

>[!MORELIKETHIS]
>
>* [Configuration des canaux en ligne](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Paramètres UTM](/help/channel-tracking-and-setup/online-channels/utm-parameters.md)
>* [Canal et sous-canal marketing](/help/channel-tracking-and-setup/online-channels/marketing-channels-and-subchannels.md)
>* [Bonnes pratiques UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md)
