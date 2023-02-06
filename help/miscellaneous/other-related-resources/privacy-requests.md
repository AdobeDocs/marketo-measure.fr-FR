---
description: Demandes d’accès à des informations personnelles - [!DNL Marketo Measure] - Documentation du produit
title: Demandes d’accès à des informations personnelles
exl-id: 883e475f-9868-412a-b505-230556f38484
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 1%

---

# Demandes d’accès à des informations personnelles {#privacy-requests}

Ce document présente la gestion des demandes de confidentialité des données individuelles que vous pouvez envoyer à [!DNL Marketo Measure] via la [!DNL Privacy Service] l’interface utilisateur et la fonction **[!DNL Privacy Service]API**.

Vous pouvez envoyer des requêtes individuelles pour accéder aux données des consommateurs et les supprimer de [!DNL Marketo Measure] de deux manières :

* Par le biais de la [[!DNL Privacy Service] Interface utilisateur](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html){target="_blank"}.
* Par le biais de la **[!DNL Privacy Service]API**. Consultez la documentation [here](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html){target="_blank"} and the API reference [here](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target="_blank"}.

Le [Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html){target="_blank"} prend en charge deux types de requêtes : accès aux données et suppression des données.

Découvrez comment créer des demandes d’accès et de suppression.

## Configuration requise pour envoyer des requêtes pour Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

Pour envoyer des requêtes d’accès et de suppression de données pour [!DNL Marketo Measure], vous devez :

1. Identifiez les éléments suivants :

   a. Identifiant de l’organisation IMS

   b. Adresse électronique de la personne sur laquelle vous souhaitez agir

   Un identifiant de l’organisation IMS est une chaîne alphanumérique de 24 caractères annexée avec @AdobeOrg. Si votre équipe marketing ou votre administrateur système d’Adobes interne ne connaît pas l’identifiant de l’organisation IMS de votre entreprise, contactez l’assistance clientèle d’Adobe à l’adresse gdprsupport@adobe.com. Vous avez besoin de l’identifiant de l’organisation IMS pour envoyer des requêtes à l’API de confidentialité.

1. Dans [!DNL Privacy Service], vous pouvez envoyer des demandes d’accès et de suppression à [!DNL Marketo Measure]et vérifiez l’état des requêtes existantes.

## Valeurs de champ requises dans [!DNL Marketo Measure] Requêtes JSON {#required-field-values-in-marketo-measure-json-requests}

&quot;companyContexts&quot;:

* &quot;namespace&quot; : **imsOrgID**
* &quot;Valeur&quot;: `<Your IMS Org ID Value>`

&quot;utilisateurs&quot;:

* &quot;action&quot; : both [!UICONTROL access] ou supprimer
* &quot;userIDs&quot; :
   * &quot;namespace&quot; : email
   * &quot;type&quot;: standard
   * &quot;Valeur&quot;: `<Data Subject's Email Address>`

&quot;include&quot; :

* **marketoMeasurement** (qui est le produit Adobe qui s’applique à la requête)

&quot;regulation&quot; :

* **gdpr**, **ccpa**, **pdpa**, **lgpd_bra** ou **nzpa_nzl** (qui est la réglementation sur la confidentialité qui s’applique à la demande)

## Exemple 1 : Demande de suppression RGPD {#gdpr-delete-request}

Requête JSON

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "delete"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "gdpr",
}
```

Réponse JSON

```text
{
  "requestId": "16331241037112570RX-245",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "997b01e3-9568-402c-904b-b4e60a437875",
      "customer": {
        "user": {
          "action": [
            "delete"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```

## Exemple 2 : Demande d’accès au CCPA {#ccpa-access-request}

Requête JSON

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "access"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "ccpa",
}
```

Réponse JSON

```text
{
  "requestId": "16329573462631890RX-207",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "3115e42d-011b-47ab-a2b0-ed4356af4d3e",
      "customer": {
        "user": {
          "action": [
            "access"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```
