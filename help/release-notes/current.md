---
description: Notes de mise à jour actuelles - [!DNL Marketo Measure]
title: Notes de mise à jour actuelles
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: db71cbfaf7deb5b724ac4babc38e835c04fadac7
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Notes de mise à jour : 2024 {#release-notes-2024}

Consultez ci-dessous toutes les fonctionnalités nouvelles et mises à jour de nos versions 2024.

## Version du 2e trimestre {#q2-release}

<p>

**Obsolescence des fonctionnalités de Marketo Measure en réponse à l’élimination progressive des cookies tiers**

En réponse aux préoccupations croissantes en matière de confidentialité, les cookies tiers sont progressivement supprimés, l’échéance du 3e trimestre 2024 de Google Chrome annonçant leur fin. Marketo Measure va rendre obsolète certaines fonctionnalités qui dépendent des cookies tiers, en particulier le suivi inter-domaines et l’attribution de vue publicitaire, qui reposent sur le cookie d’impression Google/DoubleClick. Cette modification n’aura aucune incidence sur les autres fonctionnalités de Marketo Measure ou sur l’utilisation de cookies propriétaires. Selon le calendrier de Google, ces fonctionnalités devraient être abandonnées d’ici le 1er juin, bien que les données collectées avant cette date soient toujours accessibles aux clients.

* [Adaptation à l’obsolescence des cookies tiers dans Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Cookies Marketo Measure](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Déploiement échelonné de notre gestion améliorée des erreurs**

Nous introduisons un déploiement échelonné de la gestion améliorée des erreurs pour les tâches d’exportation, en commençant par des notifications Push in-app immédiates pour les erreurs d’autorisation, et en passant le 25 avril à une nouvelle approche où les tâches d’exportation s’arrêteront au point d’erreur. Ce changement vise à améliorer l’intégrité et la visibilité des données, assurant ainsi des processus de gestion des données plus fluides et plus fiables pour nos utilisateurs. Pour garantir une transition en douceur et une perturbation minimale de vos activités, nous mettons en œuvre ces modifications en deux phases :

* Disponibilité immédiate des notifications Pulse : vous recevrez des notifications Pulse in-app pour les erreurs d’autorisation lors des tâches d’exportation. Cela n’interrompra pas vos exportations, mais vous aidera à en savoir plus sur les erreurs sans affecter vos tâches actuelles.
* Mise en œuvre de la tâche en pause le 25 avril : à compter du 25 avril, si notre système rencontre une erreur d’autorisation lors d’une tâche d’exportation, il suspend la tâche pour s’assurer qu’aucune donnée n’est ignorée. Vous serez informé de tout problème et, une fois les autorisations corrigées, la tâche d’exportation reprendra de manière transparente là où elle s’est arrêtée.

_Pourquoi C’Est Important_

Intégrité des données améliorée et pérennisation de votre intégration : nous arrêtons le travail dès les premiers signes de problème afin d’éviter la perte de données et d’assurer la précision. Cela permet de résoudre rapidement les problèmes, d’améliorer la qualité de l’exportation des données et la fiabilité du système.

Visibilité immédiate : l’introduction des notifications Push permet de répondre rapidement aux erreurs d’autorisation, ce qui évite les impacts potentiels sur les opérations.

_Prise en charge de votre transition_

Pour vous aider à vous adapter à ce changement, [nous avons créé la documentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} avec des descriptions d’erreur claires et des étapes de dépannage complètes.

<br>
**Action requise pour l’intégration de LinkedIn**

LinkedIn a récemment publié une version mise à jour de son API de synchronisation des leads. Veuillez réauthentifier la connexion LinkedIn dans votre instance Marketo Measure d’ici le 20 mai afin d’éviter toute interruption.

