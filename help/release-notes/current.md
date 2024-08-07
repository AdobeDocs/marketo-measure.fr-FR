---
description: Notes de mise à jour actuelles -  [!DNL Marketo Measure]
title: Notes de mise à jour actuelles
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: 9f374537dd3690b5c904e2ac1933ff460dc66282
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 100%

---

# Notes de mise à jour : 2024 {#release-notes-2024}

Vous trouverez ci-dessous toutes les nouvelles fonctionnalités ainsi que les fonctionnalités mises à jour pour nos versions de 2024.

## Version du 3e trimestre {#q3-release}

<p>

**Rappel : obsolescence des champs Salesforce : 14 juin**

Comme annoncé l’année dernière, nous [supprimerons progressivement nos traitements d’export pour les objets Lead/Contact](https://nation.marketo.com/t5/employee-blogs/marketo-measure-salesforce-lead-and-contact-field-deprecation-06/ba-p/350179){target="_blank"} afin de simplifier notre intégration et d’éliminer la nécessité d’exporter vers des objets standard Salesforce. Vous pouvez obtenir les mêmes données de vos objets de point de contact en suivant les étapes [documentées ici](/help/release-notes/previous-releases/2023.md#deprecations){target="_blank"}. Nous partagerons également la documentation sur la création de workflows pour ajouter ces données à l’objet Lead/Contact. L’obsolescence prendra effet le 14 juin 2024.

Ce changement aura les deux avantages clés suivants :

* **Réduction des coûts de l’API Salesforce** : la clientèle peut s’attendre à une réduction des coûts de leur API Salesforce d’environ 10 %.
* **Intégration rationalisée** : la majorité des erreurs des traitements d’export est liée à ces traitements. Leur suppression permettra de rationaliser considérablement notre intégration.

**Tableau de bord Opportunités attribuées**

Nous avons le plaisir de vous présenter le nouveau [Tableau de bord Opportunités attribuées](/help/marketo-measure-discover-ui/dashboards/attributed-opportunity-dashboard.md){target="_blank"}, conçu pour vous donner une vue d’ensemble exhaustive de la manière dont vos efforts marketing contribuent aux opportunités de pipeline naissantes et matures. Ce tableau de bord vous permet de vous plonger dans les détails de chaque opportunité ouverte et fermée pouvant être attribuée à vos stratégies, avec la possibilité de filtrer par étape d’opportunité. Il fournit des informations sur les canaux, sous-canaux ou campagnes qui se classent le plus haut en termes de montant des opportunités attribuées. Il affiche le montant total des opportunités attribuées, ainsi que le nombre d’opportunités ouvertes et fermées attribuées.

**Synchronisation des cookies de Marketo Engage pour Marketo Measure Ultimate**

La synchronisation des cookies de Marketo Engage est désormais disponible pour Marketo Measure Ultimate. Pour utiliser cette fonctionnalité, procédez comme suit :

1. Sur la page Schémas AEP, modifiez le schéma de personne B2B et ajoutez le groupe de champs « Détails des personnes Marketo Engage ».
1. Lors de l’ingestion des données à MMU, mappez le champ ID de cookie du groupe de champs au champ Cookies de Marketo Engage.

**Étapes Boomerang activées pour la clientèle de niveau 2**

Auparavant réservée à la clientèle de niveau 3, la fonction Étapes Boomerang est également disponible pour la clientèle de niveau 2 à compter du 13 juin 2024. Pour plus d’informations sur cette fonctionnalité, consultez la documentation ci-dessous.

* [Étapes et points de contact Boomerang](/help/advanced-marketo-measure-features/boomerang/boomerang-stages-and-touchpoints.md){target="_blank"}
* [Configurer des étapes Boomerang](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md){target="_blank"}
* [Scénarios d’étape Boomerang](/help/advanced-marketo-measure-features/boomerang/boomerang-stage-scenarios.md){target="_blank"}

<p>

## Version du 2e trimestre {#q2-release}

<p>

**Abandon de fonctionnalités Marketo Measure en réponse à l’élimination progressive des cookies tiers**

En réponse aux préoccupations croissantes concernant la confidentialité, les cookies tiers sont progressivement supprimés et la date limite du troisième trimestre 2024 établie par Google Chrome indique la fin de leur existence. Marketo Measure abandonnera certaines fonctionnalités qui dépendent de cookies tiers, en particulier le suivi inter-domaines et l’attribution après affichage (View-through), qui dépendent du cookie d’impression Google/DoubleClick. Cette modification n’aura aucune incidence sur les autres fonctionnalités de Marketo Measure ni sur l’utilisation de cookies propriétaires. D’après le calendrier de Google, ces fonctionnalités doivent être abandonnées d’ici le 1er juin, mais les clientes et les clients pourront toujours accéder aux données collectées avant cette date.

* [Adaptation à l’abandon des cookies tiers dans Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Cookies Marketo Measure](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Déploiement par phases de notre gestion améliorée des erreurs**

Nous mettons en place un déploiement progressif de la gestion améliorée des erreurs pour les traitements d’export, en commençant par des notifications lumineuses in-app immédiates pour les erreurs d’autorisation, puis en instaurant une nouvelle approche consistant à interrompre les traitements d’export au moment de l’erreur. Ce changement vise à améliorer l’intégrité et la visibilité des données, en assurant des processus de gestion des données plus fluides et plus fiables pour nos utilisateurs et nos utilisatrices. Pour garantir une transition fluide et une perturbation minimale de vos opérations, nous effectuons l’implémentation de ces modifications en deux phases :

* Disponibilité immédiate des notifications lumineuses : vous recevrez des notifications lumineuses in-app pour les erreurs d’autorisation lors des traitements d’export. Celles-ci n’interrompent pas vos exports, mais vous aident à en savoir plus sur les erreurs sans affecter vos traitements actuels.
* Implémentation des pauses de traitement le 25 avril : **REPORTÉ** - Après avoir pris en compte les commentaires des utilisateurs et utilisatrices de Marketo Measure, nous avons décidé de reporter l’implémentation des pauses de traitement d’export au moment de l’erreur, initialement planifiée pour le 25 avril. Nous avons conscience que l’arrêt des traitements n’est peut-être pas l’approche la plus efficace. Nous nous engageons à trouver une meilleure solution qui préserve l’intégrité des données et minimise les perturbations. Nous mettons en pause toute modification de notre système actuel jusqu’à ce que nous puissions garantir une solution qui s’aligne plus étroitement sur les besoins de nos utilisateurs et utilisatrices.

_Pourquoi c’est important_

Amélioration de l’intégrité des données et anticipation des risques relatifs à votre intégration : nous arrêtons le traitement dès le premier signe de problème afin d’éviter les pertes de données et de garantir son exactitude. Cela permet de résoudre rapidement les problèmes, d’améliorer la qualité de l’export des données et la fiabilité du système.

Visibilité immédiate : la mise en place de notifications lumineuses permet de réagir rapidement aux erreurs d’autorisation, en évitant des impacts potentiels sur les opérations.

_Pour vous aider à faire la transition_

Pour vous aider à vous adapter à cette modification, [nous avons créé une documentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} avec des descriptions des erreurs claires et des étapes de résolution de problèmes exhaustives.

<br>

**Action requise pour l’intégration de LinkedIn**

LinkedIn a récemment publié une version mise à jour de son API de synchronisation des leads. Authentifiez à nouveau la connexion LinkedIn dans votre instance Marketo Measure d’ici le 20 mai pour éviter toute interruption.

