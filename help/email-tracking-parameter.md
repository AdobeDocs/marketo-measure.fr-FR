---
description: Conseils sur les paramètres de suivi des e-mails pour les utilisateurs de Marketo Measure
title: Paramètre de suivi des e-mails
exl-id: e2cfd59e-ce4a-4cbb-b64a-828d1db7410f
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 4%

---

# Paramètre de suivi des e-mails {#email-tracking-parameter}

Le paramètre de suivi des e-mails [!DNL Marketo Measure] permet aux spécialistes marketing de traiter les clics sur les e-mails comme des envois de formulaire afin que les points de contact soient générés pour ces actions. Sans utiliser de paramètre de suivi des e-mails, les clics publicitaires d’un e-mail ne sont traités que comme des « visites web » jusqu’à ce que l’utilisateur interagisse réellement avec le site par le biais d’un envoi de formulaire ou d’une discussion web.

## Cas d’utilisation  {#use-cases}

**Enregistrement au webinaire** : l’équipe marketing envoie une invitation par e-mail avec un seul bouton pour s’inscrire à un webinaire. Comme l’e-mail contient déjà les informations de la personne, le simple clic permet de les enregistrer automatiquement. La page de destination contient le paramètre de suivi des e-mails. Ainsi, lorsqu’ils cliquent sur la page de confirmation et y accèdent, [!DNL Marketo Measure] pouvez capturer l’adresse e-mail et traiter le clic publicitaire comme un remplissage de formulaire, ce qui génère un point de contact.

**Téléchargement de contenu** : l’équipe de marketing de contenu souhaite promouvoir un livre électronique récent qu’elle a publié avec un lien de téléchargement direct à partir d’un e-mail. Lorsque le modèle d’e-mail est créé, la page de confirmation de téléchargement contient le paramètre de suivi des e-mails. Ainsi, lorsque les [!DNL Marketo Measure] cliquent dessus, ils peuvent capturer l’adresse e-mail. Sans avoir à remplir un formulaire sur le site, [!DNL Marketo Measure] pouvez générer un point de contact pour le téléchargement de contenu. En effet, l’e-mail les a envoyées sur la page de confirmation avec le paramètre de tracking d’e-mail.

## Fonctionnement {#how-it-works}

Lorsqu’un visiteur arrive sur votre site, [!DNL Marketo Measure] s’attend à trouver une page de destination avec une adresse e-mail ou un ID de [!DNL Salesforce] afin que nous puissions associer cette visite à un « envoi de formulaire » et générer un point de contact pour cette activité.

En tant que client, vous créez un modèle d’e-mail comme vous le feriez normalement. Une fois qu’il est temps d’ajouter dans la page de destination l’action que vous souhaitez suivre, vous devez déterminer le jeton, la balise de variable ou la macro que votre plateforme d’automatisation du marketing accepte pour afficher dynamiquement la valeur de chaque individu.

Marketo Measure accepte les valeurs suivantes : adresse e-mail, ID de lead Salesforce ou ID de contact Salesforce.

## Exemples de balises {#tag-examples}

| Automatisation du marketing | Jeton / Balise / Macro | Exemple | Matériel De Support |
| --- | --- | --- | --- |
| Marketo | {{lead.Email Address}} | <https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId={{lead.EmailAddress}}> | [Présentation des jetons](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/personalizing-landing-pages/tokens-overview.html) |
| Pardot | %%email%% ou %%user_crm_id%% | <https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId=%%email%%> | [Référence des balises de variables Pardot](https://help.salesforce.com/s/articleView?language=en_US&id=pardot_variable_tags_reference.htm&type=5) |
| Point De Raccordement | (inséré via l’éditeur) | s/o | [Personnalisation du contenu HubSpot](https://knowledge.hubspot.com/website-pages/personalize-your-content) |
| Action | (inséré via le compositeur de messages) | s/o | [Action pour personnaliser le contenu des e-mails](https://connect.act-on.com/hc/en-us/articles/360033436074-How-to-Personalize-Email-Content-with-CRM-Data) |

Enfin, dans [!DNL Marketo Measure], vous devez spécifier le paramètre de tracking afin que [!DNL Marketo Measure] puissiez localiser la valeur de l’e-mail ou de l’ID. La valeur par défaut est « mailId », comme illustré dans les exemples ci-dessus et dans la capture d’écran ci-dessous. Saisissez la valeur dans vos Paramètres dans [!DNL Marketo Measure], puis cliquez sur **[!UICONTROL Enregistrer]**.

![Enfin, dans Marketo Measure, vous devez spécifier le paramètre de tracking](assets/marketo-engage-activities-01.png)
