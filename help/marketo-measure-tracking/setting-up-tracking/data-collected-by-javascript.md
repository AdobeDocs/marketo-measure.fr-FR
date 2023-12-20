---
description: Données collectées par JavaScript - [!DNL Marketo Measure] - Documentation du produit
title: Données collectées par JavaScript
feature: Tracking
source-git-commit: 2be08b96fb9f6d027e80751db64f16a7f2893764
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 8%

---

# Données collectées par JavaScript {#data-collected-by-javascript}

Découvrez les données collectées par Marketo Measure JavaScript lors du déploiement.

**Exemple de requête :**

```
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure collecte les données communes suivantes pour tous les types de requêtes :

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
    <td>Adresse IP</td>
    <td>Chaîne</td>
    <td>L’emplacement de l’utilisateur est déduit par le biais de la recherche GeoIP. Ces données sont temporaires et ne sont pas stockées de manière permanente.</td>
  </tr>
  <tr>
    <td>En-tête de requête</td>
    <td>Chaîne de l’agent utilisateur</td>
    <td>Chaîne</td>
    <td>Détermine l’appareil utilisé par l’utilisateur.</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_u</td>
    <td>Chaîne</td>
    <td>Identifiant de cookie Bizible</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_l</td>
    <td>Chaîne</td>
    <td>URL de la page actuelle</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_t</td>
    <td>long</td>
    <td>Horodatage de l’activité</td>
  </tr>
  <tr>
    <td>Paramètre de requête</td>
    <td>_biz_i</td>
    <td>Chaîne</td>
    <td>Titre de la page actuelle</td>
  </tr>
</tbody>
</table>

Outre les données communes ci-dessus, bizible.js ajoute également des données supplémentaires en fonction des types de requêtes, comme indiqué ci-dessous :

<table>
<thead>
  <tr>
    <th>Type de demande</th>
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
    <td>URL de la page du référent.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_h</td>
    <td>Chaîne</td>
    <td>Résolution d’écran du client hachée.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_c</td>
    <td>Chaîne</td>
    <td>Paramètre facultatif. Si ce paramètre est présent, il indique que le client configure bizible.js pour attendre le consentement des utilisateurs avant le suivi, et que bizible.js a reçu le consentement de l’utilisateur à suivre.</td>
  </tr>
  <tr>
    <td>Envoi de formulaire</td>
    <td>/form</td>
    <td>eMail</td>
    <td>Chaîne</td>
    <td>Adresse électronique en texte brut.</td>
  </tr>
  <tr>
    <td>Mappage des identifiants utilisateur</td>
    <td>/u</td>
    <td>mapType</td>
    <td>enum</td>
    <td>Quel type de mappage d’ID utilisateur bizible.js a détecté (ID de correspondance Marketo et ECID d’Adobe) ?</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>mapValue</td>
    <td>Chaîne</td>
    <td>La valeur réelle de l’ID de cookie tiers de l’intégration ci-dessus.</td>
  </tr>
</tbody>
</table>

>[!NOTE]
>
>Bizible est l&#39;ancien nom de Marketo Measure.
