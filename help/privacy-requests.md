---
description: Conseils sur les demandes d’accès à des informations personnelles pour les utilisateurs de Marketo Measure
title: Demandes d’accès à des informations personnelles
exl-id: 883e475f-9868-412a-b505-230556f38484
feature: APIs, Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 24%

---


# Demandes d’accès à des informations personnelles {#privacy-requests}

Ce document présente la gestion des demandes individuelles d’accès à des informations personnelles que vous pouvez envoyer à [!DNL Marketo Measure] par le biais de l’interface utilisateur de [!DNL Privacy Service] et de l’API **[!DNL Privacy Service]**.

Vous pouvez soumettre des requêtes individuelles pour accéder aux données des clients et les supprimer de [!DNL Marketo Measure] de deux manières :

* Via l’[[!DNL Privacy Service] IU](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html?lang=fr){target="_blank"}.
* Via l’API **[!DNL Privacy Service]**. Consultez la documentation [ici](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html?lang=fr){target="_blank"} et la référence de l’API [ici](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target="_blank"}.

[Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=fr){target="_blank"} prend en charge deux types de demandes : l&#39;accès aux données et la suppression des données.

Voyons comment créer des demandes d’accès et de suppression.

## Configuration requise pour envoyer des requêtes pour Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

Pour envoyer des demandes d’accès et de suppression de données pour [!DNL Marketo Measure], vous devez :

1. Identifier les éléments suivants :

   a. ID d’organisation IMS

   b. Adresse e-mail de la personne sur laquelle vous souhaitez agir

   Un identifiant de l’organisation IMS est une chaîne alphanumérique de 24 caractères à laquelle est ajouté @AdobeOrg. Si votre équipe marketing ou votre administrateur système Adobe interne ne connaît pas l’identifiant de l’organisation IMS de votre entreprise, contactez l’Assistance clientèle Adobe à l’adresse gdprsupport@adobe.com. Vous avez besoin de l’identifiant d’organisation IMS pour envoyer des requêtes à l’API Privacy.

1. Dans [!DNL Privacy Service], vous pouvez envoyer des demandes d’accès et de suppression à [!DNL Marketo Measure] et vérifier le statut des demandes existantes.

## Valeurs de champ requises dans les demandes JSON relatives aux [!DNL Marketo Measure] {#required-field-values-in-marketo-measure-json-requests}

« companyContexts » :

* « namespace » : **imsOrgID**
* « value » : `<Your IMS Org ID Value>`

&quot;users&quot; :

* « action » : [!UICONTROL accès] ou suppression
* « userIDs » :
   * « namespace » : email
   * « type » : standard
   * « value » : `<Data Subject's Email Address>`

« include » :

* **marketoMeasure** (qui est le produit Adobe qui s’applique à la requête)

« règlement » :

* **rgpd**, **ccpa**, **pdpa**, **lgpd_bra** ou **nzpa_nzl** (qui est le règlement sur la confidentialité qui s’applique à la demande)

## Exemple 1 : demande de suppression en vertu du RGPD {#gdpr-delete-request}

Requête JSON

```json
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

```json
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

## Exemple 2 : demande d’accès au CCPA {#ccpa-access-request}

Requête JSON

```json
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

```json
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
