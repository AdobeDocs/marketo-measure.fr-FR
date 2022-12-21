---
description: Bonnes pratiques pour les canaux en ligne - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques pour les canaux en ligne
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Bonnes pratiques pour les canaux en ligne {#best-practices-for-online-channels}

## APERÇU {#overview}

Pour avoir la précision [!DNL Marketo Measure] création de rapports, vos canaux marketing doivent être correctement configurés. Le champ Canal marketing affiche le groupe d’activités marketing de niveau supérieur auquel un point de contact peut appartenir (par exemple, Recherche payante, Direct, Social, etc.).

La configuration de vos canaux marketing comporte deux aspects : en ligne et hors ligne. Ce document sera axé sur la [!DNL Marketo Measure] recommandations de bonnes pratiques pour configurer et gérer vos canaux en ligne.

Les règles de canal en ligne constituent les directives relatives à la manière dont : [!DNL Marketo Measure] mappe vos points de contact numériques, c’est-à-dire les points de contact qui sont suivis et créés au moyen de la variable [!DNL Marketo Measure] JS sur votre site. Si ces règles ne sont pas complètes ou ne sont pas classées correctement, les points de contact peuvent être attribués à un canal incorrect, ce qui réduit la précision de vos rapports. En veillant à ce que vos règles de canal en ligne soient exactes et à jour, vous avez la garantie que vos données numériques sont attribuées au canal et aux sous-canaux appropriés dans votre [!DNL Marketo Measure] Création de rapports.

## Bonne pratique {#best-practice}

Gardez à l’esprit les bonnes pratiques suivantes, que vous configuriez vos règles pour la première fois ou que vous les examiniez simplement pour vérifier leur exactitude.

Prenez le temps de réfléchir à l’organisation de vos campagnes marketing et à leur place dans la variable [!DNL Marketo Measure] framework. Déterminez les canaux et sous-canaux à représenter dans vos canaux en ligne, ainsi que les campagnes, les paramètres UTM ou les sites web de référence qui différencient ces canaux les uns des autres.

À retenir :

* Tous les canaux et sous-canaux numériques doivent être représentés par au moins une règle.
   * Si le canal ne conduit pas les visiteurs vers votre site, il ne s’agit pas d’un canal en ligne.
* Vous pouvez avoir plusieurs règles pour un canal/sous-canal.
   * Plusieurs règles peuvent être considérées comme un &quot;filet plus large&quot; pour s’assurer que chaque point de contact est correctement mappé. Il est souvent possible d’ajouter ou de ne pas complètement ajouter des paramètres, de sorte que disposer de plusieurs règles pour capturer un canal/sous-canal est une bonne idée pour garantir la précision du mappage.
* [!DNL Marketo Measure] la logique donne la priorité au mappage des points de contact dans l’ordre décroissant en commençant par la ligne supérieure de la feuille de calcul et en descendant.
   * [!DNL Marketo Measure] lit chaque règle (ligne), en recherchant la valeur &quot;true&quot; et &quot;first fit&quot;. Le point de contact est ensuite mappé à ce canal/sous-canal.
   * Ne triez pas votre feuille dans l’ordre alphabétique, car cela interférera avec les règles logiques.
* Conserver les règles entre crochets, ne pas les modifier ni les ajouter aux règles entre crochets (exemple : [AdWords Paid Search] ou [Facebook payante] )
   * Ils sont prêts à l&#39;emploi. [!DNL Marketo Measure] règles ayant une logique intégrée, qui sont liées à la variable [!DNL Marketo Measure] intégrations. Donnez la priorité à ces règles pour cette section de canal/sous-canal afin de garantir que [!DNL Marketo Measure] les intégrations peuvent fonctionner comme prévu.
* Une fois le fichier téléchargé, vous ne pouvez pas modifier les règles pendant sept jours.
   * [!DNL Marketo Measure] utilise ce temps pour traiter et mettre à jour les points de contact. Veillez donc à vérifier deux fois vos règles avant de les transférer.

## Bonne pratique pour la maintenance {#best-practice-for-maintenace}

Une fois enregistrées et traitées, les règles de canal en ligne fonctionnent en continu pour regrouper vos points de contact numériques. Toutefois, certains changements ou scénarios entraînent la révision de votre configuration de canal en ligne. [!DNL Marketo Measure] recommande de consulter vos règles de canal en ligne une fois tous les six mois. Cela vous permettra de vous assurer que la variable [!DNL Marketo Measure] Les données sont alignées avec vos définitions internes des canaux/sous-canaux en ligne et votre utilisation des UTM.

Voici d’autres éléments susceptibles de déclencher votre équipe pour la maintenance du canal en ligne....

* Nouveau canal/sous-canal numérique lancé
* Mise à jour ou modification des paramètres UTM
* Modifications apportées à l’organisation des canaux ou aux conventions de dénomination
* Chiffre d’affaires de votre équipe marketing

Si votre équipe a récemment fait l’expérience de l’une des expériences ci-dessus [!DNL Marketo Measure] vous recommande de consulter vos règles de canaux en ligne et d’apporter les modifications appropriées.

>[!MORELIKETHIS]
>
>* [Configuration des canaux en ligne](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Paramètres UTM](/help/channel-tracking-and-setup/online-channels/utm-parameters.md)
>* [Canal marketing et sous-canal](/help/channel-tracking-and-setup/online-channels/marketing-channels-and-subchannels.md)
>* [Bonnes pratiques UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md)

