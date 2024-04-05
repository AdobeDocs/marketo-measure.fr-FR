---
description: Notes de mise à jour actuelles - [!DNL Marketo Measure]
title: Notes de mise à jour actuelles
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: 81ce4ead229e461eeb9e6e3b1e951108b627a4e8
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Notes de mise à jour : 2024 {#release-notes-2024}

Voir ci-dessous pour connaître toutes les nouvelles fonctionnalités et les fonctionnalités mises à jour pour nos versions 2024.

## Version du 2e trimestre {#q2-release}

<p>

**Abandon des fonctionnalités Marketo Measure en réponse à l’élimination progressive des cookies tiers**

En réponse aux préoccupations croissantes concernant la confidentialité, les cookies tiers sont progressivement supprimés, la date limite du troisième trimestre 2024 de Google Chrome indiquant leur fin. Marketo Measure abandonnera certaines fonctionnalités qui dépendent de cookies tiers, en particulier le suivi inter-domaines et l’attribution d’affichage publicitaire, qui dépendent du cookie d’impression Google/DoubleClick. Cette modification n’aura aucune incidence sur les autres fonctionnalités de Marketo Measure ni sur l’utilisation de cookies propriétaires. Une fois le calendrier de Google, ces fonctionnalités devraient être abandonnées d’ici le 1er juin, bien que les données collectées avant cette date soient toujours accessibles aux clients.

* [Adaptation à l’obsolescence des cookies tiers dans Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Cookies Marketo Measure](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Déploiement par phases de notre gestion améliorée des erreurs**

Nous introduisons un déploiement progressif de la gestion améliorée des erreurs pour les tâches d’exportation, en commençant par des notifications Push in-app immédiates pour les erreurs d’autorisation, et en passant le 25 avril à une nouvelle approche où les tâches d’exportation seront suspendues au point d’erreur. Ce changement vise à améliorer l’intégrité et la visibilité des données, en assurant des processus de gestion des données plus fluides et plus fiables pour nos utilisateurs. Pour garantir une transition fluide et une perturbation minimale de vos opérations, nous mettons en oeuvre ces modifications en deux phases :

* Disponibilité immédiate des notifications Pulse : vous recevrez des notifications Push in-app pour les erreurs d’autorisation lors des tâches d’exportation. Cela n’interrompra pas vos exportations, mais vous aidera à en savoir plus sur les erreurs sans affecter vos traitements actuels.
* Mise en oeuvre de la tâche en pause le 25 avril : à compter du 25 avril, si notre système rencontre une erreur d’autorisation lors d’une tâche d’exportation, il la met en pause pour s’assurer qu’aucune donnée n’est ignorée. Vous serez averti de tout problème. Une fois les autorisations corrigées, la tâche d’exportation reprendra en toute transparence à partir de l’endroit où elle s’est arrêtée.

_Pourquoi cela est important_

Amélioration de l’intégrité des données et de l’anti-futur de votre intégration : nous arrêtons la tâche dès le premier signe de difficulté à empêcher les pertes de données et à garantir la précision. Cela permet de résoudre rapidement les problèmes, d’améliorer la qualité de l’exportation des données et la fiabilité du système.

Visibilité immédiate : l’introduction des notifications Push permet de réagir rapidement aux erreurs d’autorisation, en évitant les impacts potentiels sur les opérations.

_Support de votre transition_

Pour vous aider à vous adapter à cette modification, [nous avons créé la documentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} avec des descriptions d’erreur claires et des étapes de dépannage complètes.

**Action requise pour l’intégration LinkedIn**

LinkedIn a récemment publié une version mise à jour de son API de synchronisation des pistes. Veuillez réauthentifier la connexion LinkedIn dans votre instance Marketo Measure d’ici le 20 mai pour éviter toute interruption.

