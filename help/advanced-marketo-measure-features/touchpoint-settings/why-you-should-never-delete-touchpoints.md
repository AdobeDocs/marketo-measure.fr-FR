---
unique-page-id: 18874560
description: Pourquoi ne jamais supprimer les points de contact - [!DNL Marketo Measure] - Documentation du produit
title: Pourquoi il ne faut jamais supprimer les points de contact
exl-id: e74c14ff-0399-4ee9-b732-6686823ff5c7
feature: Touchpoints
source-git-commit: cc786cb3af08fa36af91ef22f4dba3072c9617eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 5%

---

# Pourquoi il ne faut jamais supprimer les points de contact {#why-you-should-never-delete-touchpoints}

Si vous constatez qu’un point de contact d’une opportunité se voit attribuer incorrectement un crédit d’attribution, contactez votre gestionnaire de compte pour déterminer les prochaines étapes. Dans ce cas, nous vous recommandons d’utiliser la fonction de suppression du point de contact de l’utilisateur pour supprimer le point de contact de la collecte de données régionale et du tableau de bord du retour sur investissement. Votre gestionnaire de compte peut vous aider à créer ces règles. Veuillez ne pas supprimer manuellement ces points de contact.

La variable [!DNL Marketo Measure] Le système de traitement n’enregistre pas la suppression manuelle d’un point de contact de la collecte de données régionale. À ce jour, aucun déclencheur n’indique à notre système d’ajuster les données. [!DNL Marketo Measure] ne poussera pas automatiquement un autre point de contact pour remplacer celui qui a été supprimé, ni ne réaffectera la position ou l’attribution du point de contact au point de contact suivant.

Lorsqu’un point de contact est supprimé, cela crée un trou dans les données d’attribution. En règle générale, cela se manifeste dans les points de contact d’attribution sur une opportunité. Dans l’image ci-dessous, le point de contact qui aurait reçu la touche Création d’opportunité a été supprimé. Par conséquent, le point de contact OC est manquant pour cette opportunité et le pourcentage d’attribution pour cette Opp ne totalisera pas 100 %.

![](assets/1.png)

Si des points de contact ont été supprimés de votre SFDC, contactez [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour demander une réimportation de vos données.
