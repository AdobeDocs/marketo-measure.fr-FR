---
unique-page-id: 18874732
description: Bonnes pratiques pour la configuration des paramètres UTM - [!DNL Marketo Measure] - Documentation produit
title: Bonnes pratiques pour la configuration des paramètres UTM
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
feature: UTM Parameters
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: ht
source-wordcount: '463'
ht-degree: 100%

---

# Bonnes pratiques pour la configuration des paramètres UTM {#best-practices-for-setting-up-utm-parameters}

Les paramètres UTM sont un excellent moyen de découper vos données marketing. [!DNL Marketo Measure] utilise et capture tous les paramètres UTM pour renseigner les champs dans Salesforce et dans l’application [!DNL Marketo Measure]. Grâce à ces informations, vous serez en mesure de comprendre en détail l’origine de vos prospects, opportunités et offres clôturées/gagnées.

Vous pouvez utiliser le [Créateur d’URL Google](https://support.google.com/analytics/answer/1033867?hl=fr){target="_blank"} to set up your UTM parameters and add them to your links within your marketing efforts. Use this [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"} si vous souhaitez un moyen plus simple de suivre tous vos liens UTM.

## Valeurs de haut niveau pour chaque paramètre {#high-level-values-for-each-parameter}

**utm_medium** : ce champ est mappé sur le champ Medium. Utilisez utm_medium pour représenter le canal de haut niveau.

Par exemple, [!UICONTROL Social], coît par clic (CPC), e-mail, web, organique

N’utilisez pas ce champ pour appeler le sous-canal.

**utm_source** : ce champ est mappé sur le champ Touchpoint Source. Utilisez utm_source pour définir le sous-canal duquel provient le prospect.

Par exemple, Facebook, Twitter, Linkedin, Drip_email, Email_blast, newsletter.

Restez simple. N’utilisez pas ce paramètre pour indiquer le type d’annonce, comme le reciblage, le parrainage, etc. N’ajoutez pas d’utm_source = homepage, webdirect, website. [!DNL Marketo Measure] renseigne automatiquement ces informations.

**utm_campaign** : ce champ est mappé sur le nom de la campagne publicitaire. Utilisez utm_campaign pour indiquer le titre de la campagne tel qu’il existe dans la plateforme publicitaire ou tel qu’il est référencé en interne.

Il s’agit également d’un bon paramètre pour indiquer la géolocalisation, le type de réseau publicitaire (affichage vs recherche), etc.

Nous recommandons d’utiliser des traits de soulignement plutôt que des espaces et d’éviter d’utiliser la ponctuation. Cela réduit les risques d’erreurs de codage par les navigateurs lors de la lecture de vos paramètres.

Par exemple, AU_Idea_for_an_App_50k

**utm_content**: ce champ est mappé au contenu publicitaire. Utilisez le titre de l’annonce publicitaire dans le paramètre utm_content. S’il s’agit d’une annonce publicitaire avec image, utilisez le titre de l’annonce publicitaire et incluez les dimensions de l’annonce.

Par exemple, [titre de l’annonce publicitaire] 200 x 400 px

**utm_term** : ce champ est mappé au texte du mot-clé. Utilisez ce paramètre pour indiquer le mot-clé associé au déclenchement de l’annonce publicitaire.

Si aucun mot-clé n’est associé à l’annonce publicitaire, laissez ce paramètre vide.

Par exemple, Idées d’applications iPhone

**Soyez simple et concis. Ne dupliquez pas les efforts, les termes et les canaux.**

Nous imaginons la hiérarchie UTM comme suit :

Medium > [!UICONTROL Source] > [!UICONTROL Campagne] > [!UICONTROL Contenu/Terme]

Par exemple, si une annonce publicitaire d’[!UICONTROL affichage] est mise sur Facebook, nous vous recommandons ce qui suit :

fakewebsite.com/

?utm_medium=social

&amp;utm_source=facebook

&amp;utm_campaign=Display_campaign_ID

&amp;utm_content=content_of_campaign

Notez que les termes/canaux ne sont pas dupliqués et que utm_term n’est pas utilisé dans ce cas.

Si vous avez des questions, contactez l’équipe Adobe en charge des comptes (votre gestionnaire de compte) ou le [service d’assistance de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
