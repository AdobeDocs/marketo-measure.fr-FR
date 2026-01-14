---
description: Conseils pour ne jamais supprimer de points de contact pour les utilisateurs de Marketo Measure
title: Pourquoi il ne faut jamais supprimer les points de contact
exl-id: e74c14ff-0399-4ee9-b732-6686823ff5c7
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 5%

---

# Pourquoi il ne faut jamais supprimer les points de contact {#why-you-should-never-delete-touchpoints}

Si vous constatez qu’il existe un point de contact sur une opportunité à laquelle le crédit d’attribution est attribué de manière incorrecte, contactez votre gestionnaire de compte pour déterminer les étapes suivantes. Dans ce cas, il est recommandé d’utiliser la fonctionnalité de suppression des points de contact de l’acheteur pour supprimer le point de contact de SFDC et du tableau de bord du retour sur investissement. Votre gestionnaire de compte peut vous aider à créer ces règles. Ne supprimez pas manuellement ces points de contact vous-même.

Le système de traitement des [!DNL Marketo Measure] n’enregistre pas qu’un point de contact a été supprimé manuellement de SFDC. À l&#39;heure actuelle, aucun déclencheur n&#39;indique à notre système d&#39;ajuster les données. [!DNL Marketo Measure] n’intégrera pas automatiquement un autre point de contact pour remplacer celui qui a été supprimé, et ne réaffectera pas la position ou l’attribution du point de contact au point de contact suivant.

Lorsqu’un point de contact est supprimé, il crée un trou dans les données d’attribution. En règle générale, cela se manifeste dans les points de contact d’attribution d’une opportunité. Dans l’image ci-dessous, le point de contact qui aurait reçu le contact de création d’opportunité a été supprimé. Par conséquent, le point de contact OC est manquant dans cette opportunité et le pourcentage d’attribution pour cette opportunité ne s’additionnera pas jusqu’à 100 %.

![Lorsqu’un point de contact est supprimé, il crée un trou dans l’attribution](assets/touchpoint-settings-10.png)

Si des points de contact ont été supprimés de votre SFDC, contactez l’assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour demander une réimportation de vos données.
