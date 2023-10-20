---
unique-page-id: 18874590
description: « [!DNL Marketo Measure] Cookies - [!DNL Marketo Measure] - Documentation du produit »
title: « Cookies [!DNL Marketo Measure] »
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: 69304dddf3569cd92c95a50e9a2e346acdad0f43
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 42%

---

# Cookies Marketo Measure {#marketo-measure-cookies}

En savoir plus sur les différents cookies [!DNL Marketo Measure] chargés sur votre site lorsque vous appliquez le JavaScript [!DNL Marketo Measure] à vos pages de destination. Ces informations peuvent se révéler utiles à l’équipe de développement web lors de la mise en œuvre.

<table>
<thead>
  <tr>
    <th>Nom du cookie</th>
    <th>Type de cookie</th>
    <th>But</th>
    <th>Expiration</th>
    <th>L’indicateur sécurisé a-t-il été défini ?<br></th>
    <th>L’indicateur HTTP uniquement est-il défini ?</th>
    <th>Cookie Setter</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>_biz_uid</td>
    <td>Premier niveau</td>
    <td>Identifier de manière unique un utilisateur sur le domaine actuel.</td>
    <td>1 an</td>
    <td>Non</td>
    <td>Non</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_nA</td>
    <td>Premier niveau</td>
    <td>Numéro de séquence que Marketo Measure inclut pour toutes les requêtes de diagnostic interne.</td>
    <td>1 an</td>
    <td>Non</td>
    <td>Non</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_flagsA</td>
    <td>Premier niveau</td>
    <td>Un cookie qui stocke diverses informations sur l’utilisateur, telles que l’envoi de formulaire, la migration interdomaines, le pixel d’affichage publicitaire, l’état d’exclusion du suivi, etc.</td>
    <td>1 an</td>
    <td>Non</td>
    <td>Non</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_pendingA</td>
    <td>Premier niveau</td>
    <td>Stocke temporairement les données d’analyse jusqu’à ce qu’elles aient été envoyées au serveur Marketo Measure.</td>
    <td>1 an</td>
    <td>Non</td>
    <td>Non</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_ABTestA</td>
    <td>Premier niveau</td>
    <td>Liste des sommes de contrôle provenant des données ABTests Optimizely et Visual Web Optimizer qui ont déjà été signalées, ce qui empêche bizible.js de renvoyer les données collectées.</td>
    <td>1 an</td>
    <td>Non</td>
    <td>Non</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_EventA</td>
    <td>Premier niveau</td>
    <td>Liste des sommes de contrôle signalées par les événements Bizible pour empêcher bizible.js d’envoyer à nouveau les données collectées.</td>
    <td>1 an</td>
    <td>Non</td>
    <td>Non</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_su</td>
    <td>Premier niveau</td>
    <td>Identifiant utilisateur universel permettant d’identifier un utilisateur sur plusieurs domaines, applicable uniquement aux clients avec une intégration qui outrepasse les limites ITP.</td>
    <td>1 an</td>
    <td>Oui</td>
    <td>Non</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Tiers, domaine=.<a href="http://bizible.com/">bizible.com</a></td>
    <td>Identifiant utilisateur universel pour identifier un utilisateur sur plusieurs domaines.</td>
    <td>1 an</td>
    <td>Oui</td>
    <td>Non</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Tiers, domaine=.<a href="http://bizibly.com/">bizibly.com</a></td>
    <td>Mappage entre l’ID de cookie Marketo Measure sur le domaine du client et son ID de cookie d’impression Doubleclick.</td>
    <td>1 an</td>
    <td>Oui</td>
    <td>Non</td>
    <td>Edgecast</td>
  </tr>
</tbody>
</table>

Si un avertissement de pare-feu d’applications web (WAF) est déclenché lors de la configuration de JavaScript, les utilisateurs et utilisatrices peuvent désactiver cette règle de WAF ou placer les cookies sur la liste autorisée, comme dans l’exemple ci-dessous :

![](assets/marketo-measure-cookies-1.png)
