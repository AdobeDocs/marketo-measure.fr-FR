---
description: Scénarios d’étape de boomerang - [!DNL Marketo Measure]
title: Scénarios d’étape de boomerang
exl-id: 150db070-eef5-4741-845c-775ab4034ead
feature: Boomerang
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 0%

---


# Scénarios d’étape de boomerang {#boomerang-stage-scenarios}

>[!AVAILABILITY]
>La fonction Boomerang est uniquement activée pour les clients de niveau 2 et 3. Pour demander un niveau de compte supérieur, contactez l’équipe du compte Adobe (votre gestionnaire de compte).

Vous trouverez ci-dessous quelques exemples de scénarios de Boomerang Stage pour comprendre comment [!DNL Marketo Measure] crée des points de contact dans chaque situation.

## Scénarios de lead unique {#single-lead-scenarios}

**Scénario 1 : points de contact Boomerang standard pour un prospect**

Il s’agit du scénario Boomerang le plus simple. La ligne supérieure (intitulée Lead 1) représente le parcours de chaque lead et la façon dont ses points de contact apparaissent dans l’enregistrement du lead. Les résultats (appelés Opportunité) indiquent la manière dont les points de contact des prospects sont traduits dans l’opportunité. La progression des points de contact est expliquée par occurrence chronologique, de gauche à droite.

Dans ce scénario, un client a choisi de suivre ses étapes **MQL** et **SQL** avec des boomerangs. Chaque position de point de contact Boomerang est étiquetée avec l’étape et le numéro dans lequel elle se produit (MQL-01, SQL-01, MQL-02). Le dernier point de contact de boomerang de cette étape comporte « (Dernier) » en position de point de contact.

Le lead 1 est ensuite converti en contact avec une opportunité, ce qui est considéré comme le contact OC.

![Diagramme de parcours de lead montrant les points de contact MQL et SQL avec progression chronologique vers l’opportunité](assets/1-1.png)

**Scénario 2 : points de contact de boomerang ET étapes personnalisées pour un prospect**

Dans ce scénario, un client a choisi de suivre uniquement l’étape **SQL** avec des points de contact de boomerang. Les étapes MQL et SAL font toujours l’objet d’un suivi, mais avec la fonctionnalité d’évaluation personnalisée [!DNL Marketo Measure].

![parcours de lead présentant les points de contact SQL boomerang avec MQL et SAL suivis comme étapes personnalisées](assets/2-1.png)

Notez que la position du point de contact MQL n’est pas marquée par un nombre. Cela est dû au fait qu’il n’a pas été sélectionné pour être suivi avec les points de contact Boomerang. Lors de la création de points de contact pour les étapes incluses dans le modèle personnalisé, mais qui ne sont pas suivies par Boomerang, [!DNL Marketo Measure] prend la dernière occurrence de cette étape.

Pour l’étape AL, [!DNL Marketo Measure] ignore les deux premières occurrences de cette étape. [!DNL Marketo Measure] crée uniquement un point de contact SSL pour la _dernière_ occurrence. Dans l’exemple ci-dessus, cela se produit juste avant le point de contact OC.

L’étape SQL est suivie avec les points de contact Boomerang, et trois points de contact ont été créés et étiquetés en conséquence.

Le lead 1 est ensuite converti en contact avec une opportunité, ce qui est considéré comme le contact OC.

**Scénario 3 : lorsque les prospects n’atteignent pas/ignorent une étape**

Ce scénario utilise les mêmes critères que le scénario 2. Un client a choisi de ne suivre que l’étape SQL avec les points de contact de boomerang. MQL et SAL font toujours l’objet d’un suivi, mais avec la fonctionnalité d’évaluation personnalisée [!DNL Marketo Measure].

![parcours de prospect montrant l’étape SAL ignorée avec les positions SAL et OC combinées au même point de contact](assets/3.png)

Dans ce scénario, le prospect ne passe jamais réellement à l’étape de l’accord commercial. Il se transforme en contact avant d’atteindre l’étape SAL, en « ignorant » essentiellement l’étape SAL. Dans ce cas, [!DNL Marketo Measure] suppose que le SAL se produit avec le point de contact OC, et les positions SAL et OC apparaîtront toutes deux sur le même point de contact.

Le lead 1 est ensuite converti en contact avec une opportunité, ce qui est considéré comme le contact OC.

## Scénarios avec plusieurs prospects {#scenarios-with-multiple-leads}

Dans les scénarios suivants, les étapes de boomerang peuvent devenir plus complexes, car nous examinons comment plusieurs prospects peuvent influencer le parcours d’opportunité.

La ligne supérieure (intitulée Lead 1, en bleu) représente le parcours de chaque lead et la façon dont ses points de contact apparaissent dans l’enregistrement du lead. Il en va de même pour le plomb 2 (en rose) et le plomb 3 (en orange). Le résultat (appelé Opportunité) indique comment les points de contact de ces deux prospects se traduisent par l’opportunité. La progression des points de contact est expliquée par occurrence chronologique, de gauche à droite.

**Scénario 1 : [!UICONTROL trois prospects avec opportunité]**

Dans ce scénario, un client a choisi de suivre les étapes **MQL** et **SAL** avec des points de contact de boomerang. L’étape SQL est suivie par les étapes personnalisées standard.

![Diagramme de parcours de trois prospects montrant les points de contact de boomerang MQL et SAL traduisant en opportunité](assets/4.png)

Les points de contact FT et LC sur l’opportunité proviennent du lead 1 (bleu), car ils se sont produits avant le FT et le LC du lead 2 (rose). Le point de contact LC pour le lead 2 s’affichera comme point de contact de « formulaire » sur l’opportunité.

Le MQL-01 (dernier) du lead 2 deviendra le premier MQL de l’opportunité. Le MQL-01 du lead 1 n’apparaîtra pas comme point de contact sur l’opportunité, car le MQL du lead 2 est apparu en premier. Toutefois, les MQL-02 et MQL-03 du lead 1 s’affichent dans l’opportunité.

L’étape SQL est suivie avec des étapes personnalisées, et non des étapes de boomerang. Même s’il existe trois occurrences de l’étape SQL entre le lead 1 et le lead 2, seule la dernière occurrence SQL sera incluse comme point de contact sur l’opportunité.

Le point de contact SAL-01 (dernier) du lead 1 est conservé comme point de contact sur l’opportunité. Le lead 1 est ensuite converti en contact avec une opportunité, ce qui est considéré comme le contact OC. Le point de contact SAL-01 (dernier) du lead 2 ne sera pas créé comme point de contact, car cette transition d’étape s’est produite _après_ le contact OC.

Les points de contact FT, LC et MQL, SQL et SAL du lead 3 (orange) se sont tous produits après le point de contact OC sur l’opportunité. Ces points de contact sont inclus dans l’opportunité, mais sont considérés comme des « contacts intermédiaires ».

Lorsque les leads 2 et 3 sont convertis en contacts, [!DNL Marketo Measure] ne créerez pas d’autre point de contact OC, car il ne peut y avoir qu’une seule étape de création d’opportunité.

**Scénario 2 - [!UICONTROL Trois prospects avec opportunité]**

Dans ce scénario, un client a choisi de suivre les étapes **MQL**, **SQL** et **SAL** avec des points de contact de boomerang.

Tous les points de contact du lead 1 sont inclus dans l’opportunité, de FT à SAL-01 (dernier). Le point de contact LC du lead 2 sera inclus comme point de contact de formulaire entre les points de contact LC et MQL-01 sur l’opportunité.

![Trois parcours de prospect présentant les points de contact de boomerang MQL, SQL et SAL avec numérotation de position sur l’opportunité](assets/5.png)

Le MQL-01 (dernier) du lead 2 finit par être le point de contact MQL-04 (dernier) sur l’opportunité. Comme ce scénario s’intéresse à plusieurs parcours de leads dans une opportunité, le positionnement et la numérotation des points de contact des leads peuvent changer lorsqu’ils sont traduits en tant que points de contact sur l’opportunité. De même, le code SQL-01 (Last) du lead 2 devient le code SQL-04 (Last) de l’opportunité. Le SAL-01 (dernier) du lead 2 devient également le SAL-02 (dernier) de l’opportunité.

Seuls 2 points de contact SSL sont inclus dans l’opportunité. [!DNL Marketo Measure] n’essaiera pas de forcer/créer des points de contact pour les transitions d’étape si elles ne se sont pas produites.

Le parcours du point de contact du lead 3 commence juste avant le contact OC, mais longtemps après que le lead 1 et le lead 2 ont eu leur contact FT et LC. Dans ce cas, le FT et le LC du lead 3 apparaissent comme un point de contact de formulaire sur l’opportunité. Le lead 1 est ensuite converti en contact avec une opportunité, ce qui est considéré comme le contact OC.

Les contacts MQL, SQL et SAL du lead 3 se produisent tous en même temps, après le contact OC. Puisqu’ils se sont produits après le point de contact OC, ce point de contact s’affichera sous la forme d’un formulaire/contact intermédiaire sur l’opportunité plutôt que sous la forme d’une transition d’étape Boomerang.

**Scénario 2a - Points de contact de boomerang de visite web**

Dans ce scénario, un client a choisi de suivre les étapes **MQL**, **SQL** et **SAL** avec des points de contact de boomerang. Ce scénario est presque identique à celui ci-dessus, à quelques exceptions près.

![Trois parcours de prospect présentant les points de contact de boomerang des visites web exclus de l’opportunité après l’étape SQL](assets/6.png)

Tous les points de contact du lead 1 seront inclus dans l’opportunité, de FT à SAL-01 (dernier). Le point de contact LC du lead 2 sera inclus comme point de contact de formulaire entre les points de contact LC et MQL-01 sur l’opportunité.

Le MQL-01 (dernière) (visite web) du lead 2 ne sera pas créé comme point de contact sur l’opportunité. En effet, ce point de contact était une visite web qui se produit après la dernière occurrence de l’étape SQL et ne contribue pas à faire avancer l’opportunité.

L’étape du lead 1 passe à SAL, puis est convertie en contact avec une opportunité ; dans ce cas, les positions SAL-01 (dernier) et OC sont combinées au même point de contact.

Le contact FT, LC du lead 3 est créé comme point de contact de formulaire sur l’opportunité. Seules les actions de remplissage de formulaire seront créées comme points de contact après le contact OC. Pour cette raison, les transitions d’étape SQL-01 (dernier) et SAL-01 (dernier) pour le prospect 2 ne seront pas créées en tant que points de contact, car ces points de contact étaient des visites web.

Les contacts MQL, SQL et SAL du lead 3 sont inclus comme point de contact, car il s’agissait d’une action de remplissage de formulaire.

**Scénario 3 - Pondération D’Attribution Boomerang**

Dans ce scénario, un client a choisi de suivre les étapes **MQL**, **SQL** et **SAL** avec des points de contact de boomerang.

![Trois parcours de prospect présentant une pondération d’attribution boomerang avec plusieurs transitions d’étape](assets/7.png)

Les points de contact FT et LC sur l’opportunité proviennent du lead 1 (bleu), car ils se sont produits avant le FT et le LC du lead 2 (rose). Le point de contact LC pour le lead 2 apparaît comme point de contact de « formulaire » sur l’opportunité.

Le MQL-01 (dernier) du lead 2 devient le premier MQL de l’opportunité. Le MQL-01 du lead 1 n’apparaîtra pas comme point de contact sur l’opportunité, car le MQL du lead 2 est apparu en premier.

Le SQL-01 (dernier) du lead 2 devient SQL-01 sur l’opportunité. Le SQL-01 sur le lead 1 n’apparaîtra pas comme point de contact sur l’opportunité, car le SQL-01 sur le lead 2 s’est produit en premier.

Notez que le boomerang de lead 1 entre MQL et SQL plusieurs fois avant d’atteindre finalement l’étape SAL. SQL-01, MQL-02, SQL-02, MQL-03, SQL-03 _ne seront pas_ inclus en tant que points de contact sur l’opportunité, car ces transitions d’étape ne contribuent pas à faire avancer l’opportunité dans le parcours.

Le point de contact SAL-01 (dernier) du lead 1 est le prochain point de contact à inclure dans l’opportunité. Le lead 1 se convertit ensuite en contact avec une opportunité, créant ainsi le point de contact OC.

Le FT et le LC du lead 3, ainsi que les points de contact MQL, SQL et SAL, apparaissent sous la forme de contacts de formulaire sur l’opportunité.

Le point de contact SQL-01 (dernier) du lead 2 ne sera pas inclus comme point de contact dans l’opportunité, car il s’est produit après le point de contact OC. En outre, la transition d’étape SQL du lead 2 s’est produite _après la transition d’étape finale du SQL_ et ne contribue pas à faire avancer le parcours d’opportunité.

## Scénarios d’opportunités {#opportunity-scenarios}

**Scénario 1 - Contacts avec suivi des opportunités et des boomerangs**

Dans ce scénario, un client a choisi de suivre les transitions d’étape **Démonstration et Négociation** sur le **Contact**. Chaque étape de boomerang peut recevoir jusqu’à deux points de contact. La différence entre les transitions d’étape sur un contact et les transitions d’étape sur un prospect est que les transitions d’étape de contact peuvent apparaître comme des points de contact Boomerang sur l’opportunité _après_ le point de contact OC. Ce n’est pas le cas pour les transitions d’étape qui se produisent sur le prospect, car elles apparaissent comme un point de contact de formulaire.

![parcours de contact présentant les points de contact de boomerang de démonstration et de négociation apparaissant après le point de contact OC sur l’opportunité](assets/8.png)

Dans cet exemple, les transitions de l’étape de démonstration et de négociation du contact 1 sont incluses en tant que points de contact Demo-01 et Négociation-01 sur l’opportunité. La transition d’étape de démonstration du contact 2 se produit _après_ celle du contact 1 et apparaît comme le point de contact de démonstration 02 (dernier) sur l’opportunité.

Notez qu’il n’y a pas de seconde transition vers l’étape Négociation ; l’opportunité passe immédiatement de Démo-02 (Dernier) mouvements à Fermer gagné. Dans ce cas, [!DNL Marketo Measure] inclura la transition de négociation avec le point de contact Fermé et confirmé.
