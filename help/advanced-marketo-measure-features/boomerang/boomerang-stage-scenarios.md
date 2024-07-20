---
unique-page-id: 18874692
description: Scénarios d’évaluation Boomerang - [!DNL Marketo Measure]
title: Scénarios d’étape de boomerang
exl-id: 150db070-eef5-4741-845c-775ab4034ead
feature: Boomerang
source-git-commit: ea113b02b910fbc894311200aff83286636d4b32
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---

# Scénarios d’étape de boomerang {#boomerang-stage-scenarios}

>[!AVAILABILITY]
>
>La fonction Boomerang n’est activée que pour les clients des niveaux 2 et 3. Pour demander un niveau de compte supérieur, contactez l’équipe Compte d’Adobe (votre gestionnaire de compte).

Vous trouverez ci-dessous quelques exemples de scénarios d’évaluation de Boomerang afin de vous expliquer comment [!DNL Marketo Measure] crée des points de contact dans chaque situation.

## Scénarios de piste uniques {#single-lead-scenarios}

**Scénario 1 : points de contact standard Boomerang pour une piste**

C&#39;est le scénario Boomerang le plus simple. La ligne supérieure (appelée &quot;piste 1&quot;) représente le parcours des pistes individuelles et la manière dont leurs points de contact apparaissent dans l’enregistrement de piste. La ligne de bas (désignée par le terme Opportunité) indique comment les points de contact des Pistes se traduisent par Opportunité. La progression des points de contact est expliquée dans l’occurrence chronologique, de gauche à droite.

Dans ce scénario, un client a choisi de faire suivre ses scènes **MQL** et **SQL** avec des robots. Chaque position de point de contact Boomerang est associée à l’étape et au nombre d’occurrences (MQL-01, SQL-01, MQL-02). Le dernier point de contact boomerang de cette scène a &quot;(Last)&quot; en position de point de contact.

Le prospect 1 est ensuite converti en contact avec une opportunité, qui est considéré comme la touche OC.

![](assets/1-1.png)

**Scénario 2 : points de contact Boomerang ET étapes personnalisées pour une piste**

Dans ce scénario, un client a choisi de suivre uniquement l’ **étape SQL** avec des points de contact boomerang. Les scènes MQL et SAL sont toujours suivies, mais avec la fonction [!DNL Marketo Measure] Custom Stage (Intermédiaire personnalisé).

![](assets/2-1.png)

Notez que la position du point de contact MQL n’est pas étiquetée avec un nombre. En effet, elle n’a pas été sélectionnée pour être suivie avec les points de contact Boomerang. Lors de la création de points de contact pour les scènes incluses dans le modèle personnalisé, mais qui ne sont pas suivies avec Boomerang, [!DNL Marketo Measure] prend la dernière occurrence de cette étape.

Pour l’étape SAL, [!DNL Marketo Measure] ignore les deux premières occurrences de cette étape. [!DNL Marketo Measure] crée uniquement un point de contact SAL pour l’occurrence _last_ . Dans l’exemple ci-dessus, cela se produit juste avant le point de contact OC.

La scène SQL est suivie avec les points de contact Boomerang, et trois points de contact ont été créés et étiquetés en conséquence.

Le prospect 1 est ensuite converti en contact avec une opportunité, qui est considéré comme la touche OC.

**Scénario 3 : lorsque les pistes n’atteignent/ne sautent pas une étape**

Ce scénario utilise les mêmes critères que le scénario 2. Un client a choisi de ne suivre que la scène SQL avec des points de contact boomerang. MQL et SAL font toujours l’objet d’un suivi, mais avec la fonction [!DNL Marketo Measure] d’évaluation personnalisée.

![](assets/3.png)

Dans ce scénario, le prospect ne passe jamais réellement à l’étape SAL. Il se convertit en Contact avant d’atteindre l’étape SAL, essentiellement &quot;sauter&quot; l’étape SAL. Dans ce cas, [!DNL Marketo Measure] suppose que la SAL se produit avec le point de contact OC, et que la position SAL et OC apparaîtront sur le même point de contact.

Le prospect 1 est ensuite converti en contact avec une opportunité, qui est considéré comme la touche OC.

## Scénarios avec plusieurs pistes {#scenarios-with-multiple-leads}

Les scénarios suivants sont là où les phases Boomerang peuvent devenir plus complexes, alors que nous étudions comment plusieurs pistes peuvent influencer le parcours d’opportunités.

La ligne supérieure (désignée sous le nom de piste 1, en bleu) représente le parcours des pistes individuelles et la manière dont leurs points de contact apparaissent dans l’enregistrement de piste. Il en va de même pour le Lead 2 (en rose) et le Lead 3 (en orange). La ligne de base (intitulée Opportunité) indique comment les points de contact de ces deux pistes se traduisent en opportunité. La progression des points de contact est expliquée dans l’occurrence chronologique, de gauche à droite.

**Scénario 1 : [!UICONTROL Trois pistes avec opportunité]**

Dans ce scénario, un client a choisi de suivre les **scènes MQL** et les **scènes SAL** avec des points de contact boomerang. L’étape SQL est suivie par les étapes personnalisées standard.

![](assets/4.png)

Les points de contact FT et LC sur l’opportunité proviennent de la piste 1 (bleue), car ils se sont produits avant le FT et la LC de la piste 2 (rose). Le point de contact LC pour l’piste 2 apparaît comme point de contact &quot;Formulaire&quot; sur l’opportunité.

Le MQL-01 (dernier) du prospect 2 sera le premier MQL sur l’opportunité. Le MQL-01 de la piste 1 n’apparaîtra pas comme point de contact sur l’opportunité, car le MQL de la piste 2 s’est produit en premier. Toutefois, les MQL-02 et MQL-03 de Lead 1 apparaissent dans l’opportunité.

La scène SQL est suivie avec des scènes personnalisées, et non des scènes boomerang. Même s’il existe trois occurrences de l’étape SQL entre la piste 1 et la piste 2, seule la dernière occurrence SQL sera incluse comme point de contact sur l’opportunité.

Le point de contact SAL-01 (dernier) de la piste 1 est transféré comme point de contact de l’opportunité. Le prospect 1 est ensuite converti en contact avec une opportunité, qui est considéré comme la touche OC. Le point de contact SAL-01 (dernier) de la piste 2 sera créé comme point de contact car cette transition d’étape s’est produite _après_ la touche OC.

Les points de contact FT, LC et MQL de Lead 3, SQL, SAL (orange) se sont tous produits après le point de contact OC sur l’opportunité. Ces points de contact sont inclus dans l’opportunité, mais sont considérés comme des &quot;touches intermédiaires&quot;.

Lorsque les pistes 2 et 3 sont converties en contacts, [!DNL Marketo Measure] ne crée pas un autre point de contact OC, car il ne peut y avoir qu’une seule étape de création d’opportunités.

**Scénario 2 - [!UICONTROL Trois pistes avec opportunité]**

Dans ce scénario, un client a choisi de suivre les étapes **MQL**, **SQL** et **SAL** avec des points de contact boomerang.

Tous les points de contact du prospect 1 sont inclus sur l’opportunité, de FT à SAL-01 (dernier). Le point de contact LC de l’piste 2 sera inclus comme point de contact Formulaire entre les points de contact LC et MQL-01 de l’opportunité.

![](assets/5.png)

Le MQL-01 (dernier) du prospect 2 correspond finalement au MQL-04 (dernier) point de contact de l’opportunité. Dans la mesure où ce scénario examine plusieurs parcours de pistes dans une seule opportunité, le positionnement et la numérotation des points de contact des pistes peuvent changer lorsqu’ils sont traduits comme points de contact sur l’opportunité. De même, le SQL-01 (Dernier) du prospect 2 devient le SQL-04 (Dernier) du formulaire Opp. La piste 2 SAL-01 (dernière) devient également la SAL-02 (dernière) de l’opportunité.

L’opportunité ne contient que 2 points de contact SAL. [!DNL Marketo Measure] n’essaiera pas de forcer/créer des points de contact pour les transitions intermédiaires si elles ne se sont pas produites.

Le parcours de point de contact du prospect 3 commence juste avant que la touche OC ne se produise, mais longtemps après que les points 1 et 2 aient eu leur touche FT et LC. Dans ce cas, le formulaire FT et le document LC de la piste 3 apparaissent comme un point de contact de formulaire sur l’opportunité. Le prospect 1 est ensuite converti en contact avec une opportunité, qui est considéré comme la touche OC.

Les touches MQL, SQL et SAL du prospect 3 se produisent toutes en même temps, après la touche OC. Puisqu’elles se sont produites après le point de contact OC, ce point de contact s’affiche sous la forme d’un formulaire/contact intermédiaire sur l’opportunité plutôt que sous la forme d’une transition d’étape Boomerang.

**Scénario 2a - Points de contact Boomerang des visites web**

Dans ce scénario, un client a choisi de suivre les étapes **MQL**, **SQL** et **SAL** avec des points de contact boomerang. Ce scénario est presque identique à celui ci-dessus, à quelques exceptions près.

![](assets/6.png)

Tous les points de contact du prospect 1 seront inclus sur l’opportunité, de FT à SAL-01 (dernier). Le point de contact LC de l’piste 2 sera inclus comme point de contact Formulaire entre les points de contact LC et MQL-01 de l’opportunité.

Le MQL-01 (Dernière) de la piste 2 (Visite Web) ne sera pas créé comme point de contact sur l’Opp. Cela est dû au fait que ce point de contact était une visite web qui se produit après la dernière occurrence de l’étape SQL et n’aide pas à faire avancer l’opportunité.

L’étape du prospect 1 passe à SAL, puis est convertie en Contact avec une opportunité ; dans ce cas, les positions SAL-01 (dernier) et OC sont combinées dans le même point de contact.

Le formulaire FT de Lead 3, LC touch est créé en tant que point de contact de formulaire dans l’Opp. Seules les actions de remplissage de formulaire seront créées en tant que points de contact après la touche OC. Pour cette raison, les transitions d’étape SQL-01 (dernier) et SAL-01 (dernier) de la piste 2 ne seront pas créées en tant que points de contact, car ces points de contact étaient des visites web.

Les touches MQL, SQL et SAL de Lead 3 sont incluses comme point de contact, car il s’agissait d’une action de remplissage de formulaire.

**Scénario 3 - Pondération d’attribution Boomerang**

Dans ce scénario, un client a choisi de suivre les étapes **MQL**, **SQL** et **SAL** avec des points de contact boomerang.

![](assets/7.png)

Les points de contact FT et LC sur l’opportunité proviennent de la piste 1 (bleue), car ils se sont produits avant le FT et la LC de la piste 2 (rose). Le point de contact LC de l’piste 2 apparaît comme point de contact &quot;Formulaire&quot; sur l’opportunité.

Le MQL-01 (dernier) du prospect 2 est le premier MQL sur l’opportunité. Le MQL-01 de la piste 1 n’apparaîtra pas comme point de contact sur l’opportunité, car le MQL de la piste 2 s’est produit en premier.

Le SQL-01 (dernier) du prospect 2 devient SQL-01 sur l&#39;opportunité. Le code SQL-01 sur le prospect 1 n’apparaîtra pas comme point de contact sur l’opportunité, car SQL-01 sur le prospect 2 s’est produit en premier.

Notez que les boomerangs Lead 1 entre MQL et SQL plusieurs fois avant d’atteindre enfin l’étape SAL. SQL-01, MQL-02, SQL-02, MQL-03, SQL-0}ne sera pas _inclus comme points de contact sur l’opportunité, car ces transitions intermédiaires ne contribuent pas à faire avancer l’opportunité dans le parcours._

Le point de contact SAL-01 (dernier) de la piste 1 est le prochain point de contact à inclure dans l’Opp. La piste 1 se convertit ensuite en contact avec une opportunité, créant ainsi le point de contact OC.

Les points de contact FT et LC de Lead 3, ainsi que les points de contact MQL, SQL et SAL apparaissent sous la forme d’un formulaire permettant d’accéder à l’opportunité.

Le point de contact SQL-01 (dernier) de la piste 2 ne sera pas inclus comme point de contact dans l’Opp, car il s’est produit après le point de contact OC. En outre, la transition de l’étape SQL du prospect 2 s’est produite _après la transition finale de l’étape SAL_ et ne contribue pas à faire avancer le parcours d’opportunités.

## Scénarios d’opportunité {#opportunity-scenarios}

**Scénario 1 - Contacts avec suivi des opportunités et du boomerang{1**

Dans ce scénario, un client a choisi de suivre les **transitions de l&#39;étape de démonstration et de négociation** sur le **contact**. Chaque étape de boomerang peut recevoir jusqu’à deux points de contact. La différence entre les transitions d’étape sur un contact et les transitions d’étape sur un prospect est que les transitions d’étape Contact peuvent apparaître sous forme de points de contact Boomerang sur l’ _opportunité suivant_ le point de contact OC. Ce n’est pas le cas pour les transitions d’étape qui se produisent sur l’piste, car elles apparaissent comme un point de contact de formulaire.

![](assets/8.png)

Dans cet exemple, les transitions d’étape de démonstration et de négociation de Contact 1 sont incluses en tant que points de contact Demo-01 et Négociation-01 sur l’opportunité. La transition de l’étape de démonstration de Contact 2 se produit _après_ Contact 1’s et s’affiche comme point de contact Demo-02 (Dernier) sur l’opportunité.

Notez qu’il n’y a pas de deuxième transition vers l’étape de négociation ; l’opportunité passe immédiatement de Demo-02 (Dernier) à Fermer Won. Dans ce cas, [!DNL Marketo Measure] inclura la transition de négociation avec le point de contact Won fermé .
