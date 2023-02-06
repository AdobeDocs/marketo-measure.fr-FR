---
unique-page-id: 18874590
description: "[!DNL Marketo Measure] Cookies - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] Cookies"
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
source-git-commit: 3a13ab3e497652d1975e69280a3d224ac95504aa
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cookies Marketo Measure {#marketo-measure-cookies}

En savoir plus sur les différentes [!DNL Marketo Measure] Cookies chargés sur votre site lorsque vous appliquez la variable [!DNL Marketo Measure] JavaScript vers vos landing pages. Ces informations peuvent s’avérer utiles à l’équipe de développement web lors de la mise en oeuvre.

| **Nom du cookie** | **Type de cookie** | **But** |
|---|---|---|
| _BUID | Tiers, enregistrés sur le domaine .bizible.com | Identifiant utilisateur universel pour identifier le même utilisateur sur plusieurs domaines de clients. |
| _biz_uid | Premier niveau | Identifiant utilisateur sur le domaine actif. |
| _biz_sid | Premier niveau | ID de session de l’utilisateur. |
| _biz_flagsA | Premier niveau | Un seul cookie qui stocke plusieurs informations, telles que si l’utilisateur a envoyé ou non un formulaire, effectué une migration inter-domaines, envoyé un pixel de vue, désactivé le suivi, etc. |
| _biz_nA | Premier niveau | Numéro de séquence qui [!DNL Marketo Measure] inclut toutes les requêtes, à des fins de diagnostic interne ; |
| _biz_dfsA | Premier niveau | Stocke temporairement les données d’envoi de formulaire qui se produisent avant [!DNL bizible.js] reçoit une configuration JS pour déterminer si le formulaire de suivi sur HTTPS est activé ou non. |
| _biz_pendingA | Premier niveau | Stocke temporairement les données d’analyse qui n’ont pas été envoyées avec succès à [!DNL Marketo Measure] du serveur. |

Si un avertissement de pare-feu d’applications web (WAF) est déclenché lors de la configuration de JavaScript, les utilisateurs peuvent désactiver cette règle de WAF ou placer sur la liste autorisée les cookies, comme dans l’exemple ci-dessous :

![](assets/marketo-measure-cookies-1.png)
