---
description: Conseils sur les données collectées par JavaScript pour les utilisateurs de Marketo Measure
title: Données collectées par JavaScript
feature: Tracking
exl-id: 83814168-9d3e-45ac-b514-df58f0b2e90b
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 77%

---

# Données collectées par JavaScript {#data-collected-by-javascript}

Découvrez les données collectées par le JavaScript Marketo Measure lors du déploiement.

**Exemple de requête :**

```text
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure collecte les données communes suivantes pour tous les types de requêtes :

| Origine | Nom | Type de données | But |
| --- | --- | --- | --- |
| En-tête de requête | Adresse IP | Chaîne | L’emplacement de l’utilisateur ou de l’utilisatrice est déduit de la recherche GeoIP. Ces données sont temporaires et ne sont pas stockées de manière permanente. |
| En-tête de requête | Chaîne agent utilisateur | Chaîne | Détermine l’appareil utilisé par l’utilisateur ou l’utilisatrice. |
| Paramètre de requête | `_biz_u` | Chaîne | ID du cookie Bizible. |
| Paramètre de requête | `_biz_l` | Chaîne | URL de la page active. |
| Paramètre de requête | `_biz_t` | long | Date et heure de l’activité. |
| Paramètre de requête | `_biz_i` | Chaîne | Titre de la page active. |

Outre les données communes ci-dessus, bizible.js ajoute également des données supplémentaires en fonction des types de requêtes, comme indiqué ci-dessous :

| Type de requête | Chemin de la requête | Paramètre de requête supplémentaire | Type de données | But |
| --- | --- | --- | --- | --- |
| Pageview | `/ipv` | `_biz_r` | Chaîne | URL de la page référente. |
|  |  | `_biz_h` | Chaîne | Résolution d’écran client hachée. |
|  |  | `_biz_c` | Chaîne | Paramètre facultatif. Si ce paramètre est présent, il indique que le client configure `bizible.js` pour qu’il attende le consentement de l’utilisateur avant d’effectuer le suivi et qu’`bizible.js` a reçu le consentement de l’utilisateur pour faire l’objet d’un suivi. |
| Envois du formulaire | `/frm` | `eMail` | Chaîne | Adresse e-mail en texte brut. |
| Mappage des identifiants de l’utilisateur ou de l’utilisatrice | `/u` | `mapType` | enum | Quel type de mappage d’ID utilisateur `bizible.js` détecté (ID Marketo Munchkin et ECID Adobe) ? |
|  |  | `mapValue` | Chaîne | Valeur réelle de l’ID de cookie tiers de l’intégration ci-dessus. |

>[!NOTE]
>
>Bizible est l’ancien nom de Marketo Measure.
