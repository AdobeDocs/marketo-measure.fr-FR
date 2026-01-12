---
description: Paramètre de suivi des e-mails - [!DNL Marketo Measure]
title: Paramètre de suivi des e-mails
exl-id: e2cfd59e-ce4a-4cbb-b64a-828d1db7410f
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 5%

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

<table>
 <colgroup>
  <col>
  <col>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <th><p>Automatisation du marketing</p></th>
   <th><p>Jeton / Balise / Macro </p></th>
   <th><p>Exemple</p></th>
   <th><p>Matériel De Support</p></th>
  </tr>
  <tr>
   <td><p>Marketo</p></td>
   <td><p>{{lead.adresse électronique}} </p></td>
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId={{lead.EmailAddress}}</p></td>
   <td><p>https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/personalizing-landing-pages/tokens-overview.html</p></td>
  </tr>
  <tr>
   <td><p>Pardot</p></td>
   <td><p>%%email%% </p><p>ou</p><p>%%user_crm_id%%</p></td>
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId=%%email%%</p></td>
   <td><p>https://help.salesforce.com/s/articleView?language=en_US&amp;id=pardot_variable_tags_reference.htm&amp;type=5</p></td>
  </tr>
  <tr>
   <td><p>Point De Raccordement</p></td>
   <td><p>(inséré via l’éditeur)</p></td>
   <td><p>s/o</p></td>
   <td><p>https://knowledge.hubspot.com/website-pages/personalize-your-content</p></td>
  </tr>
  <tr>
   <td><p>Action</p></td>
   <td><p>(inséré via le compositeur de messages)</p></td>
   <td><p>s/o</p></td>
   <td><p>https://connect.act-on.com/hc/en-us/articles/360033436074-How-to-Personalize-Email-Content-with-CRM-Data</p></td>
  </tr>
 </tbody>
</table>

Enfin, dans [!DNL Marketo Measure], vous devez spécifier le paramètre de tracking afin que [!DNL Marketo Measure] puissiez localiser la valeur de l’e-mail ou de l’ID. La valeur par défaut est « mailId », comme illustré dans les exemples ci-dessus et dans la capture d’écran ci-dessous. Saisissez la valeur dans vos Paramètres dans [!DNL Marketo Measure], puis cliquez sur **[!UICONTROL Enregistrer]**.

![Option Suivi des e-mails](assets/one.png)
