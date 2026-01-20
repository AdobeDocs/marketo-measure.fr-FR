---
description: Données collectées par JavaScript - [!DNL Marketo Measure]
title: Données collectées par JavaScript
feature: Tracking
exl-id: 83814168-9d3e-45ac-b514-df58f0b2e90b
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 98%

---

# Données collectées par JavaScript {#data-collected-by-javascript}

Découvrez les données collectées par le JavaScript Marketo Measure lors du déploiement.

**Exemple de requête :**

```
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure collecte les données communes suivantes pour tous les types de requêtes :

<table>
<thead>
  <tr>
    <th>Origine</th>
    <th>Nom</th>
    <th>Type de données</th>
    <th>But</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>En-tête de requête</td>
    <td>Adresse IP</td>
    <td>Chaîne</td>
    <td>L’emplacement de l’utilisateur ou de l’utilisatrice est déduit de la recherche GeoIP. Ces données sont temporaires et ne sont pas stockées de manière permanente.</td>
  </tr>
  <tr>
    <td>En-tête de requête</td>
    <td>Chaîne agent utilisateur</td>
    <td>Chaîne</td>
    <td>Détermine l’appareil utilisé par l’utilisateur ou l’utilisatrice.</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_u</td>
    <td>Chaîne</td>
    <td>ID du cookie Bizible.</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_l</td>
    <td>Chaîne</td>
    <td>URL de la page active.</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_t</td>
    <td>long</td>
    <td>Date et heure de l’activité.</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_i</td>
    <td>Chaîne</td>
    <td>Titre de la page active.</td>
  </tr>
</tbody>
</table>

Outre les données communes ci-dessus, bizible.js ajoute également des données supplémentaires en fonction des types de requêtes, comme indiqué ci-dessous :

<table>
<thead>
  <tr>
    <th>Type de requête</th>
    <th>Chemin de la requête</th>
    <th>Paramètre de requête supplémentaire</th>
    <th>Type de données</th>
    <th>But</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Pageview</td>
    <td>/ipv</td>
    <td>_biz_r</td>
    <td>Chaîne</td>
    <td>URL de la page référente.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_h</td>
    <td>Chaîne</td>
    <td>Résolution d’écran client hachée.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_c</td>
    <td>Chaîne</td>
    <td>Paramètre facultatif. Si ce paramètre est présent, il indique que le client configure bizible.js pour attendre le consentement de l’utilisateur ou de l’utilisatrice avant de procéder au suivi, puis que bizible.js reçoit le consentement.</td>
  </tr>
  <tr>
    <td>Envois du formulaire</td>
    <td>/frm</td>
    <td>E-Mail</td>
    <td>Chaîne</td>
    <td>Adresse e-mail en texte brut.</td>
  </tr>
  <tr>
    <td>Mappage des identifiants de l’utilisateur ou de l’utilisatrice</td>
    <td>/u</td>
    <td>mapType</td>
    <td>enum</td>
    <td>Quel type de mappage d’ID de l’utilisateur ou de l’utilisatrice bizible.js a-t-il détecté ? (ID Munchkin Marketo et Adobe ECID)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>mapValue</td>
    <td>Chaîne</td>
    <td>Valeur réelle de l’ID de cookie tiers de l’intégration ci-dessus.</td>
  </tr>
</tbody>
</table>

>[!NOTE]
>
>Bizible est l’ancien nom de Marketo Measure.
