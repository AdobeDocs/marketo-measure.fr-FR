---
unique-page-id: 18874678
description: Compréhension [!DNL Marketo Measure] Balisage AdWords - [!DNL Marketo Measure]
title: Comprendre le balisage AdWords dans [!DNL Marketo Measure]
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
feature: APIs, Integration, UTM Parameters
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 1%

---

# Compréhension [!DNL Marketo Measure] Balisage AdWords {#understanding-marketo-measure-adwords-tagging}

Pour effectuer le suivi de vos publicités à un niveau très granulaire, les URL de destination de l’annonce doivent être uniques. Pour ce faire, procédez comme suit : [!DNL Marketo Measure] Le balisage automatique ajoute automatiquement des paramètres de suivi aux URL de destination de l’annonce de votre [!DNL AdWords] publicités. Regardons un exemple ci-dessous.

L’URL suivante ne fournit aucune donnée granulaire :

* `http://example.com/landing-page?myParam=foo`

Cependant, la même URL fournit des données granulaires en raison de la variable [!DNL Marketo Measure] parameters:

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Comment [!DNL Marketo Measure] Fonctions de balisage automatique {#how-marketo-measure-auto-tagging-works}

**If [!DNL Marketo Measure] trouve un modèle de suivi :**

* [!DNL Marketo Measure] ajoute ses paramètres au modèle de suivi.
* Si une redirection tierce se trouve dans un modèle de suivi tel que Kenshoo ou Marin, [!DNL Marketo Measure] ne prendront aucune mesure. Au lieu de cela, vous devez [add [!DNL Marketo Measure] paramètres de l’outil tiers dans votre compte](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

Cependant, si aucun modèle de suivi n’est trouvé, [!DNL Marketo Measure] Will :

* Analysez toutes les URL de destination de l’annonce pour notre [!DNL Marketo Measure] Paramètres.
* Si on le trouve, tu es bon d&#39;y aller.
* Si elle est introuvable, [!DNL Marketo Measure] ajoute ses paramètres à la fin des URL de destination de l’annonce. Pour les nouvelles publicités, [!DNL Marketo Measure] ajoute ses paramètres à l’URL de destination de l’annonce dans les deux heures suivant sa création.
* Il est important de mettre en place un modèle de suivi avant d’activer le balisage automatique afin que [!DNL Marketo Measure] peut s’y joindre et empêcher la réinitialisation de l’historique des publicités.

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne ou du groupe publicitaire, car il permet l’ajout et la soustraction de paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique des publicités.

## Modèles de suivi {#tracking-templates}

Comme expliqué par [!DNL Google AdWords], un modèle de suivi est l’URL utilisée pour atteindre une landing page. Les informations de suivi collectées sont utilisées pour comprendre le trafic de vos publicités. [Cliquez ici](https://support.google.com/adwords/answer/7197008?hl=en){target="_blank"} pour plus d’informations à partir de Google.

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne ou du groupe publicitaire, car il permet l’ajout et la soustraction de paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique des publicités.

Il existe deux modèles de suivi [!DNL Marketo Measure] recommande d’utiliser . Utilisez les éléments suivants pour déterminer la version qui vous convient :

* Si toutes les URL de vos publicités comportent un &quot;?&quot; dans , utilisez cette URL :

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* Si aucune de vos URL de publicité n’a de &quot;?&quot; dans , utilisez cette URL :

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Configuration d’un modèle de suivi au niveau du compte {#setting-up-a-tracking-template-at-the-account-level}

1. Connectez-vous à [!DNL Google AdWords] Compte.

1. Cliquez sur **[!UICONTROL Toutes les campagnes]** puis **[!UICONTROL Paramètres]** dans la fenêtre d’extension.

   ![](assets/1.png)

1. Cliquez sur **[!UICONTROL Paramètres du compte]** en haut, puis **[!UICONTROL Modèle de suivi]**. Saisissez le [!DNL Marketo Measure] Modèle de suivi.

   ![](assets/2-1.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Configuration d’un modèle de suivi au niveau de la campagne {#setting-up-a-tracking-template-at-the-campaign-level}

1. Cliquez sur **[!UICONTROL Toutes les campagnes]** puis **[!UICONTROL Campagnes]** dans la fenêtre d’extension.

   ![](assets/3.png)

1. Sélectionnez toutes les campagnes applicables ou **[!UICONTROL Tout sélectionner]**, cliquez sur **[!UICONTROL Modifier]**, puis cliquez sur **[!UICONTROL Modifier les modèles de suivi]**.

   ![](assets/4-1.png)

1. Saisissez le [!DNL Marketo Measure] Modèle de suivi et cliquez sur **[!UICONTROL Appliquer]**.

## Configuration d’un modèle de suivi au niveau du groupe d’annonces : {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Cliquez sur **[!UICONTROL Toutes les campagnes]** puis **[!UICONTROL Groupes publicitaires]** dans la fenêtre d’extension.

   ![](assets/5-1.png)

1. Sélectionnez tous les groupes publicitaires applicables ou Tout sélectionner, cliquez sur **[!UICONTROL Modifier]** puis cliquez sur **[!UICONTROL Modifier les modèles de suivi]**.

1. Saisissez le [!DNL Marketo Measure] Modèle de suivi et cliquez sur **[!UICONTROL Appliquer]**.

   ![](assets/6-1.png)

## Questions fréquentes {#faq}

**Q : De quelles autorisations l’utilisateur connecté a-t-il besoin ?**

A : userinfo.email

**Q. : Combien de temps peut-on mettre pour importer des données de dépenses ?**

A : 6 heures

**Q. : Combien de temps peut-il s’écouler avant l’importation des données publicitaires ?**

A : 4 heures

**Q : Pour les annonces de recherche dynamique, pouvons-nous suivre la combinaison du titre, de la description, etc., dans le créatif qui a été diffusé ?**

R : Nous ne pouvons pas récupérer les détails créatifs individuels pour les annonces de recherche dynamique, mais si le balisage automatique est activé, nous pouvons toujours obtenir l’identifiant créatif et les recettes d’attributs.

>[!NOTE]
>
>Une fois les modifications effectuées, vous avez terminé. N&#39;hésitez pas à contacter [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} s’il y a des questions lors de la configuration.

[Cliquez ici](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"} pour obtenir des instructions de Google sur la création de modèles de suivi au niveau du compte.
