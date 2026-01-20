---
description: Bonnes pratiques relatives aux canaux en ligne -  [!DNL Marketo Measure]
title: Bonnes pratiques pour les canaux en ligne
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
feature: Channels
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 100%

---

# Bonnes pratiques pour les canaux en ligne {#best-practices-for-online-channels}

## Vue d’ensemble {#overview}

Pour que la création de rapports [!DNL Marketo Measure] soit exacte, vos canaux marketing doivent être correctement configurés. Le champ Canal marketing affiche le groupe d’activités marketing du plus haut niveau auquel un point de contact peut appartenir (par exemple, Référencement payant, Direct, Social, etc.).

La configuration de vos canaux marketing comporte deux aspects : en ligne et hors ligne. Ce document est axé sur les recommandations des bonnes pratiques de [!DNL Marketo Measure] relatives à la configuration et la gestion de vos canaux en ligne.

Les règles de canal en ligne régissent la manière dont [!DNL Marketo Measure] mappe vos points de contact numériques, c’est-à-dire les points de contact qui sont suivis et créés par le biais du code JS [!DNL Marketo Measure] sur votre site. Si ces règles ne sont pas complètes ou ne sont pas classées correctement, les points de contact peuvent être attribués au mauvais canal, ce qui réduit l’exactitude de vos rapports. En veillant à ce que vos règles de canal en ligne soient exactes et à jour, vous avez la garantie que vos données numériques sont attribuées au bon canal et aux bons sous-canaux dans votre création de rapports [!DNL Marketo Measure].

## Bonne pratique {#best-practice}

Gardez à l’esprit les bonnes pratiques suivantes, que vous configuriez vos règles pour la première fois ou que vous les révisiez simplement pour en vérifier l’exactitude.

Prenez le temps de réfléchir à l’organisation de vos campagnes marketing et à la manière dont elles s’inscrivent dans le framework [!DNL Marketo Measure]. Déterminez les canaux et sous-canaux à représenter dans vos canaux en ligne, ainsi que les campagnes, les paramètres UTM ou les sites web de référence qui différencient ces canaux les uns des autres.

Points à retenir :

* Tous les canaux et sous-canaux numériques doivent être représentés par au moins une règle
   * Si le canal ne conduit pas les personnes vers votre site, il ne s’agit pas d’un canal en ligne
* Vous pouvez avoir plusieurs règles pour un canal/sous-canal
   * Avoir plusieurs règles peut être considéré comme un « filet plus large » pour s’assurer que chaque point de contact est correctement mappé. Il arrive souvent d’ajouter de manière incorrecte ou d’oublier d’ajouter des paramètres. Disposer de plusieurs règles pour capturer un canal/sous-canal est donc une bonne idée pour garantir l’exactitude du mappage.
* La logique [!DNL Marketo Measure] donne la priorité au mappage des points de contact dans l’ordre décroissant, en commençant par la ligne supérieure de la feuille de calcul et en allant vers le bas
   * [!DNL Marketo Measure] lit chaque règle (ligne), en recherchant les valeurs « true » et « first fit ». Le point de contact est ensuite mappé à ce canal/sous-canal
   * Ne triez pas votre feuille par ordre alphabétique, car cela interfère avec les règles de logique.
* Conservez les règles entre crochets, ne les modifiez pas et n’ajoutez rien aux règles entre crochets (exemple : [Référencement payant AdWords] ou [Référencement payant Facebook]).
   * Il s’agit de règles [!DNL Marketo Measure] prêtes à l’emploi ayant une logique intégrée, qui sont liées aux intégrations [!DNL Marketo Measure]. Accordez une priorité maximum à ces règles pour cette section de canal/sous-canal afin de garantir que les intégrations [!DNL Marketo Measure] puissent fonctionner normalement.
* Une fois le fichier chargé, vous ne pouvez plus modifier les règles pendant sept jours
   * [!DNL Marketo Measure] utilise ce délai pour traiter et mettre à jour les points de contact. Veillez donc à vérifier deux fois vos règles avant de les charger.

## Bonne pratique de maintenance {#best-practice-for-maintenace}

Une fois que les règles de canal en ligne sont enregistrées et traitées, elles effectuent le classement en continu de vos points de contact numériques. Toutefois, certains changements ou scénario peuvent vous inciter à revoir la configuration de votre canal en ligne. [!DNL Marketo Measure] recommande de consulter vos règles de canal en ligne tous les six mois. Cela vous permet de vous assurer que les données [!DNL Marketo Measure] sont alignées avec vos définitions internes des canaux/sous-canaux en ligne et avec votre utilisation des UTM.

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
