---
description: Cookies [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Cookies [!DNL Marketo Measure]
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
hidefromtoc: 'yes'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 86%
---
# Cookies Marketo Measure {#marketo-measure-cookies}

En savoir plus sur les différents cookies [!DNL Marketo Measure] chargés sur votre site lorsque vous appliquez le JavaScript [!DNL Marketo Measure] à vos pages de destination. Ces informations peuvent se révéler utiles à l’équipe de développement web lors de la mise en œuvre.

>[!IMPORTANT]
>
>En raison de problèmes de confidentialité, des cookies tiers sont en cours d’élimination. L’abandon des cookies tiers annoncé par Google Chrome au troisième trimestre 2024 marque effectivement la fin de cette forme de suivi. Par conséquent, Adobe abandonnera les fonctions Marketo Measure qui reposent sur des cookies tiers, en particulier le suivi inter-domaines et l’attribution après affichage (View-through), qui utilisent le cookie d’impression Google/DoubleClick. Aucune autre fonction de Marketo Measure ne sera affectée. L’utilisation des cookies propriétaires ne sera pas non plus affectée. Compte tenu du planning de Google, la date d’obsolescence attendue des deux fonctions ci-dessus est le 01/06/2024. Les données connexes collectées avant cette date restent disponibles pour les clientes et clients Adobe.

| Nom du cookie | Type de cookie | But | Expiration | L’indicateur Sécurisé est-il défini ? | L’indicateur HTTP uniquement est-il défini ? | Créateur de cookie |
| --- | --- | --- | --- | --- | --- | --- |
| `_biz_uid` | Premier niveau | Identifier de manière unique un utilisateur sur le domaine actuel. | 1 an | Non | Non | `bizible.js` |
| `_biz_nA` | Premier niveau | Numéro de séquence que Marketo Measure inclut pour toutes les requêtes, à des fins de diagnostic interne. | 1 an | Non | Non | `bizible.js` |
| `_biz_flagsA` | Premier niveau | Cookie qui stocke diverses informations sur l’utilisateur, telles que l’envoi de formulaire, la migration interdomaine, le pixel de taux de visionnage, le statut de désactivation du suivi, etc. | 1 an | Non | Non | `bizible.js` |
| `_biz_pendingA` | Premier niveau | Stocke temporairement les données d’analyse jusqu’à ce qu’elles aient été envoyées au serveur Marketo Measure. | 1 an | Non | Non | `bizible.js` |
| `_biz_ABTestA` | Premier niveau | Liste des sommes de contrôle provenant des tests AB d&#39;Optimizely et de Visual Web Optimizer qui ont déjà été signalées, empêchant `bizible.js` de renvoyer les données collectées. | 1 an | Non | Non | `bizible.js` |
| `_biz_EventA` | Premier niveau | Liste des sommes de contrôle signalées par les événements Bizible pour empêcher les `bizible.js` de renvoyer les données collectées. | 1 an | Non | Non | `bizible.js` |
| `_biz_su` | Premier niveau | Identifiant d’utilisateur ou d’utilisatrice universel permettant d’identifier une personne sur plusieurs domaines, applicable uniquement aux clientes et clients avec une intégration qui outrepasse les limites ITP. | 1 an | Oui | Non | Edgecast |
| `_BUID` | Tiers, domaine=.bizible.com | Identifiant d’utilisateur ou d’utilisatrice universel permettant d’identifier une personne sur plusieurs domaines. | 1 an | Oui | Non | Edgecast |
| `_BUID` | Tiers, domaine=.bizibly.com | Mappage entre l’ID de cookie Marketo Measure sur le domaine du client ou de la cliente et son ID de cookie d’impression Doubleclick. | 1 an | Oui | Non | Edgecast |

Si un avertissement de pare-feu d’application web (WAF) est déclenché lors de la configuration JavaScript, les utilisateurs peuvent soit désactiver cette règle WAF, soit placer les cookies sur une liste autorisée, comme dans l’exemple ci-dessous :

![Si un avertissement de pare-feu d’application web (WAF) est déclenché pendant le JavaScript](assets/adding-script-1.png)
