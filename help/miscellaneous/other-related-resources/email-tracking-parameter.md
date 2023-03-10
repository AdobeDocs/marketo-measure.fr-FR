---
unique-page-id: 37356030
description: Paramètre de suivi des emails - [!DNL Marketo Measure] - Documentation du produit
title: Paramètre de suivi des e-mails
exl-id: e2cfd59e-ce4a-4cbb-b64a-828d1db7410f
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 3%

---

# Paramètre de suivi des e-mails {#email-tracking-parameter}

Le [!DNL Marketo Measure] Le paramètre de suivi des courriers électroniques permet aux marketeurs de traiter les clics par courrier électronique comme des envois de formulaire, de sorte que des points de contact soient générés pour ces actions. Sans utiliser de paramètre de suivi d’email, les clics publicitaires provenant d’un email ne sont traités comme des &quot;visites web&quot; que lorsque l’utilisateur interagit réellement avec le site par le biais d’un envoi de formulaire ou d’une discussion web.

## Cas d’utilisation  {#use-cases}

**Enregistrement de webinaire**: L’équipe marketing envoie une invitation par courrier électronique avec un seul bouton pour s’inscrire à un webinaire. Comme le courrier électronique contient déjà les informations de la personne, un seul clic l’enregistre automatiquement. La page d’entrée contient le paramètre de suivi des emails. Ainsi, lorsqu’ils cliquent et arrivent sur la page de confirmation, [!DNL Marketo Measure] peut capturer l’adresse électronique et traiter le clic publicitaire comme un remplissage de formulaire, ce qui génère un point de contact.

**Téléchargement de contenu**: L’équipe marketing du contenu souhaite promouvoir un livre électronique récent qu’elle a publié à l’aide d’un lien de téléchargement direct à partir d’un e-mail. Lors de la création du modèle d&#39;email, la page de confirmation des téléchargements contiendra le paramètre de suivi email de sorte que lorsqu&#39;ils cliquent, [!DNL Marketo Measure] peut capturer l’adresse électronique. Sans avoir à remplir un formulaire sur le site, [!DNL Marketo Measure] peut générer un point de contact pour le téléchargement de contenu qui s’est produit via l’e-mail, car il les a placés sur la page de confirmation avec le paramètre de suivi de l’e-mail.

## Fonctionnement {#how-it-works}

Lorsqu’un visiteur arrive sur votre site, [!DNL Marketo Measure] s’attend à trouver une page d’entrée avec une adresse électronique ou [!DNL Salesforce] Identifiant permettant d’associer cette visite à un &quot;envoi de formulaire&quot; et de générer un point de contact pour cette activité.

En tant que client, vous allez créer un modèle d’email comme vous le feriez normalement. Une fois qu’il est temps d’ajouter dans la page d’entrée l’action dont vous souhaitez effectuer le suivi, vous devez déterminer le jeton, la balise de variable ou la macro que votre plateforme d’automatisation marketing accepte pour afficher dynamiquement la valeur de chaque individu.

Marketo Measure accepte les valeurs suivantes : Adresse électronique, ID de piste Salesforce ou ID de contact Salesforce.

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
   <th><p>Jeton/Balise/Macro </p></th> 
   <th><p>Exemple</p></th> 
   <th><p>Matériel de support</p></th> 
  </tr> 
  <tr> 
   <td><p>Marketo</p></td> 
   <td><p>{{lead.Email Address} </p></td> 
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId={{lead.EmailAddress}}</p></td> 
   <td><p>https://docs.marketo.com/display/public/DOCS/Tokens+Overview#TokensOverview-PersonTokens</p></td> 
  </tr> 
  <tr> 
   <td><p>Pardot</p></td> 
   <td><p>%%E-mail%% </p><p>ou</p><p>%%user_crm_id%%</p></td> 
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId=%%email%%</p></td> 
   <td><p>https://help.salesforce.com/articleView?id=pardot_variable_tags_reference.htm&amp;type=5</p></td> 
  </tr> 
  <tr> 
   <td><p>Hubspot</p></td> 
   <td><p>(inséré via l’éditeur)</p></td> 
   <td><p>s/o</p></td> 
   <td><p>https://knowledge.hubspot.com/cos-general/how-to-use-personalization-with-your-content</p></td> 
  </tr> 
  <tr> 
   <td><p>Activation</p></td> 
   <td><p>(inséré via le compositeur de message)</p></td> 
   <td><p>s/o</p></td> 
   <td><p>https://connect.act-on.com/hc/en-us/articles/360033436074-How-to-Personalize-Email-Content-with-CRM-Data</p></td> 
  </tr> 
 </tbody> 
</table>

Et enfin, à l&#39;intérieur [!DNL Marketo Measure], vous devez spécifier le paramètre de suivi pour que [!DNL Marketo Measure] peut localiser la valeur d’adresse électronique ou d’identifiant. La valeur par défaut est &quot;mailId&quot;, comme illustré dans les exemples ci-dessus et dans la capture d’écran ci-dessous. Saisissez la valeur dans vos Paramètres dans [!DNL Marketo Measure], puis cliquez sur **[!UICONTROL Enregistrer]**.

![](assets/one.png)
