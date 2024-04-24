---
description: Notes de mise à jour actuelles -  [!DNL Marketo Measure]
title: Notes de mise à jour actuelles
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: cbb2afd48c0e462768be0a7cfe56007ae285c492
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 71%

---

# Notes de mise à jour : 2024 {#release-notes-2024}

Vous trouverez ci-dessous toutes les nouvelles fonctionnalités ainsi que les fonctionnalités mises à jour pour nos versions de 2024.

## Version du 2e trimestre {#q2-release}

<p>

**Abandon de fonctionnalités Marketo Measure en réponse à l’élimination progressive des cookies tiers**

En réponse aux préoccupations croissantes concernant la confidentialité, les cookies tiers sont progressivement supprimés et la date limite du troisième trimestre 2024 établie par Google Chrome indique la fin de leur existence. Marketo Measure abandonnera certaines fonctionnalités qui dépendent de cookies tiers, en particulier le suivi inter-domaines et l’attribution après affichage (View-through), qui dépendent du cookie d’impression Google/DoubleClick. Cette modification n’aura aucune incidence sur les autres fonctionnalités de Marketo Measure ni sur l’utilisation de cookies propriétaires. D’après le calendrier de Google, ces fonctionnalités doivent être abandonnées d’ici le 1er juin, mais les clientes et les clients pourront toujours accéder aux données collectées avant cette date.

* [Adaptation à l’abandon des cookies tiers dans Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Cookies Marketo Measure](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Déploiement par phases de notre gestion améliorée des erreurs**

Nous introduisons un déploiement progressif de la gestion améliorée des erreurs pour les tâches d’exportation, en commençant par des notifications Push in-app immédiates pour les erreurs d’autorisation, et en passant à une nouvelle approche où les tâches d’exportation seront suspendues au point d’erreur. Ce changement vise à améliorer l’intégrité et la visibilité des données, en assurant des processus de gestion des données plus fluides et plus fiables pour nos utilisateurs et nos utilisatrices. Pour garantir une transition fluide et une perturbation minimale de vos opérations, nous effectuons l’implémentation de ces modifications en deux phases :

* Disponibilité immédiate des notifications lumineuses : vous recevrez des notifications lumineuses in-app pour les erreurs d’autorisation lors des traitements d’export. Celles-ci n’interrompent pas vos exports, mais vous aident à en savoir plus sur les erreurs sans affecter vos traitements actuels.
* Mise en oeuvre de la suspension de tâche le 25 avril : **POSTPONED** - Après avoir pris en compte les commentaires des utilisateurs de Marketo Measure, nous avons décidé de reporter la mise en oeuvre de la mise en pause des tâches d’exportation au point d’erreur, initialement planifiée pour le 25 avril. Nous reconnaissons que l&#39;arrêt des emplois n&#39;est peut-être pas l&#39;approche la plus efficace. Nous nous engageons à trouver une meilleure solution qui préserve l’intégrité des données et minimise les perturbations. Nous repousserons toute modification de notre système actuel jusqu’à ce que nous puissions garantir une solution qui s’aligne plus étroitement sur les besoins de nos utilisateurs.

_Pourquoi c’est important_

Amélioration de l’intégrité des données et anticipation des risques relatifs à votre intégration : nous arrêtons le traitement dès le premier signe de problème afin d’éviter les pertes de données et de garantir son exactitude. Cela permet de résoudre rapidement les problèmes, d’améliorer la qualité de l’export des données et la fiabilité du système.

Visibilité immédiate : la mise en place de notifications lumineuses permet de réagir rapidement aux erreurs d’autorisation, en évitant des impacts potentiels sur les opérations.

_Pour vous aider à faire la transition_

Pour vous aider à vous adapter à cette modification, [nous avons créé une documentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} avec des descriptions des erreurs claires et des étapes de résolution de problèmes exhaustives.

<br>

**Action requise pour l’intégration de LinkedIn**

LinkedIn a récemment publié une version mise à jour de son API de synchronisation des leads. Authentifiez à nouveau la connexion LinkedIn dans votre instance Marketo Measure d’ici le 20 mai pour éviter toute interruption.

