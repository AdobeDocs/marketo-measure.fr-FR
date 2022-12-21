---
unique-page-id: 18874732
description: Bonnes pratiques pour la configuration des paramètres UTM - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques pour la configuration des paramètres UTM
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Bonnes pratiques pour la configuration des paramètres UTM {#best-practices-for-setting-up-utm-parameters}

Les paramètres de la gestion dynamique des balises sont un excellent moyen de découper et de découper vos données marketing. [!DNL Marketo Measure] utilise et capture tous les paramètres UTM pour renseigner les champs dans Salesforce et dans la variable [!DNL Marketo Measure] application. Grâce à ces informations, vous serez en mesure d’obtenir une compréhension granulaire de l’origine de vos prospects, opportunités et offres clôturées/gagnées.

Vous pouvez utiliser la variable [Créateur d’URL Google](https://support.google.com/analytics/answer/1033867?hl=en){target=&quot;_blank&quot;} pour configurer vos paramètres UTM et les ajouter à vos liens dans le cadre de vos efforts marketing. Utilisez cette [Feuille de calcul Google](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target=&quot;_blank&quot;} si vous souhaitez une méthode plus simple de suivi de tous vos liens UTM.

## Valeurs de haut niveau pour chaque paramètre {#high-level-values-for-each-parameter}

**utm_medium**: Ce champ est mappé sur le champ Support . Utilisez utm_medium pour représenter le canal de haut niveau.

par exemple : [!UICONTROL Social], CPC, e-mail, web, organique

N’utilisez pas ce champ pour appeler le sous-canal.

**utm_source**: Ce champ est mappé sur le champ Source du point de contact. Utilisez utm_source pour définir le sous-canal à partir duquel provient la piste.

par exemple : Facebook, Twitter, Linkedin, Drip_email, Email_blast, newsletter.

Restez simple. N’utilisez pas ce paramètre pour indiquer le type d’annonce, comme le reciblage, le parrainage, etc. N’ajoutez pas de utm_source = page d’accueil, webdirect, site web. [!DNL Marketo Measure] renseignera automatiquement ces informations.

**utm_campaign**: Ce champ correspond au nom de la campagne publicitaire. Utilisez utm_campaign pour indiquer le titre de la campagne tel qu’il existe dans la plateforme publicitaire ou tel qu’il est référencé en interne.

Il s’agit également d’un bon paramètre pour indiquer la géolocalisation, le type de réseau publicitaire (affichage v. recherche), etc.

Il est recommandé d’utiliser des traits de soulignement plutôt que des espaces et d’éviter d’utiliser la ponctuation. Cela réduit les risques d’erreurs de codage par les navigateurs lors de la lecture de vos paramètres.

par exemple : AU_Idea_for_an_App_50k

**utm_content**: Cela correspond au contenu de la publicité. Utilisez le titre de la publicité dans le paramètre utm_content . S’il s’agit d’une publicité avec image, utilisez le titre de la publicité et incluez les dimensions de la publicité.

par exemple : [titre publicitaire] 200 x 400 px

**utm_term**: Cette option correspond à Texte du mot-clé. Utilisez ce paramètre pour indiquer le mot-clé associé au déclenchement de la publicité.

Si aucun mot-clé n’est associé à la publicité, laissez ce paramètre vide.

par exemple : Idées de l’application iPhone

**Soyez simple et succinct. Ne dupliquez pas les efforts, les termes et les canaux.**

Nous imaginons la hiérarchie UTM comme suit :

Moyen > [!UICONTROL Source] > [!UICONTROL Campagne] > [!UICONTROL Contenu/Terme]

par exemple : Si une [!UICONTROL display] est placée sur Facebook. Nous vous recommandons ce qui suit :

fakewebsite.com/

?utm_medium=social

&amp;utm_source=facebook

&amp;utm_campaign=Display_campaign_ID

&amp;utm_content=content_of_campaign

Notez que les termes/canaux ne sont pas dupliqués et que utm_term n’est pas utilisé dans ce cas.

Si vous avez des questions, contactez votre responsable du succès client ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.
