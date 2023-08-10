---
unique-page-id: 18874590
description: « [!DNL Marketo Measure] Cookies - [!DNL Marketo Measure] - Documentation du produit »
title: « Cookies [!DNL Marketo Measure] »
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 100%

---

# Cookies Marketo Measure {#marketo-measure-cookies}

En savoir plus sur les différents cookies [!DNL Marketo Measure] chargés sur votre site lorsque vous appliquez le JavaScript [!DNL Marketo Measure] à vos pages de destination. Ces informations peuvent se révéler utiles à l’équipe de développement web lors de la mise en œuvre.

| **Nom du cookie** | **Type de cookie** | **But** |
|---|---|---|
| _BUID | Tiers, enregistré sur le domaine .bizible.com | Identifiant utilisateur universel permettant d’identifier la même personne utilisatrice sur plusieurs domaines clients. |
| _biz_uid | Premier niveau | Identifiant utilisateur sur le domaine actif. |
| _biz_sid | Premier niveau | ID de session de la personne utilisatrice. |
| _biz_flagsA | Premier niveau | Un seul cookie qui stocke plusieurs informations, notamment si la personne a envoyé ou non un formulaire, effectué une migration inter-domaines, envoyé un pixel View-Through, désactivé le suivi, etc. |
| _biz_nA | Premier niveau | Numéro de séquence que [!DNL Marketo Measure] inclut pour toutes les requêtes, à des fins de diagnostic interne |
| _biz_dfsA | Premier niveau | Stocke temporairement les données d’envoi de formulaire qui se produisent avant que [!DNL bizible.js] ne reçoive une configuration JS pour déterminer si le formulaire de suivi sur HTTPS est activé ou non. |
| _biz_pendingA | Premier niveau | Stocke temporairement les données d’analyse qui n’ont pas encore été envoyées avec succès au serveur [!DNL Marketo Measure]. |

Si un avertissement de pare-feu d’applications web (WAF) est déclenché lors de la configuration de JavaScript, les utilisateurs et utilisatrices peuvent désactiver cette règle de WAF ou placer les cookies sur la liste autorisée, comme dans l’exemple ci-dessous :

![](assets/marketo-measure-cookies-1.png)
