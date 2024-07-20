---
unique-page-id: 18874678
description: Comprendre [!DNL Marketo Measure] Balisage AdWords - [!DNL Marketo Measure]
title: Comprendre le balisage AdWords dans [!DNL Marketo Measure]
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
feature: APIs, Integration, UTM Parameters
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 6%

---

# Comprendre le balisage des [!DNL Marketo Measure] AdWords {#understanding-marketo-measure-adwords-tagging}

Pour effectuer le suivi de vos publicités à un niveau très granulaire, les URL de destination de l’annonce doivent être uniques. Pour ce faire, le balisage automatique [!DNL Marketo Measure] ajoute automatiquement des paramètres de suivi aux URL de destination de l’annonce de vos [!DNL AdWords] publicités. Regardons un exemple ci-dessous.

L’URL suivante ne fournit aucune donnée granulaire :

* `http://example.com/landing-page?myParam=foo`

Cependant, la même URL fournit des données granulaires en raison des paramètres [!DNL Marketo Measure] :

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Fonctionnement du balisage automatique [!DNL Marketo Measure] {#how-marketo-measure-auto-tagging-works}

**Si [!DNL Marketo Measure] trouve un modèle de suivi :**

* [!DNL Marketo Measure] ajoutera ses paramètres au modèle de suivi.
* Si une redirection tierce se trouve dans un modèle de suivi tel que Kenshoo ou Marin, [!DNL Marketo Measure] n’effectue aucune action. À la place, vous devez [ajouter [!DNL Marketo Measure] des paramètres à l’outil tiers dans votre compte](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

Cependant, si aucun modèle de suivi n’est trouvé, [!DNL Marketo Measure] :

* Analysez toutes les URL de destination de l’annonce pour nos paramètres [!DNL Marketo Measure].
* Si on le trouve, tu es bon d&#39;y aller.
* Si elle est introuvable, [!DNL Marketo Measure] ajoute ses paramètres à la fin des URL de destination de l’annonce. Pour les nouvelles publicités, [!DNL Marketo Measure] ajoute ses paramètres à l’URL de destination de l’annonce dans les deux heures suivant la création.
* Il est important de mettre en place un modèle de suivi avant d’activer le balisage automatique afin que [!DNL Marketo Measure] puisse y être associé et empêcher la réinitialisation de l’historique des publicités.

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne, ou du groupe de publicités, car cela permet d’ajouter et de soustraire des paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique des publicités.

## Modèles de suivi {#tracking-templates}

Comme expliqué par [!DNL Google AdWords], un modèle de suivi est l’URL utilisée pour atteindre une page d’entrée. Les informations de suivi collectées sont utilisées pour comprendre le trafic de vos publicités. [Cliquez ici](https://support.google.com/adwords/answer/7197008?hl=en){target="_blank"} pour plus d’informations sur Google.

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne ou du groupe publicitaire, car il permet l’ajout et la soustraction de paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique des publicités.

Il existe deux modèles de suivi [!DNL Marketo Measure] que vous pouvez utiliser. Utilisez les éléments suivants pour déterminer la version qui vous convient :

* Si toutes les URL de vos publicités comportent un &quot;?&quot; dans , utilisez cette URL :

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* Si aucune de vos URL de publicité n’a de &quot;?&quot; dans , utilisez cette URL :

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Configuration d’un modèle de suivi au niveau du compte {#setting-up-a-tracking-template-at-the-account-level}

1. Connectez-vous à votre compte [!DNL Google AdWords].

1. Cliquez sur **[!UICONTROL Toutes les campagnes]**, puis sur **[!UICONTROL Paramètres]** dans la fenêtre de développement.

   ![](assets/1.png)

1. Cliquez sur **[!UICONTROL Paramètres du compte]** en haut, puis sur **[!UICONTROL Modèle de suivi]**. Saisissez le modèle de suivi [!DNL Marketo Measure].

   ![](assets/2-1.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Configuration d’un modèle de suivi au niveau de la campagne {#setting-up-a-tracking-template-at-the-campaign-level}

1. Cliquez sur **[!UICONTROL Toutes les campagnes]**, puis sur **[!UICONTROL Campagnes]** dans la fenêtre de développement.

   ![](assets/3.png)

1. Sélectionnez toutes les campagnes applicables ou **[!UICONTROL Sélectionner tout]**, cliquez sur **[!UICONTROL Modifier]**, puis sur **[!UICONTROL Modifier les modèles de suivi]**.

   ![](assets/4-1.png)

1. Saisissez le modèle de suivi [!DNL Marketo Measure] et cliquez sur **[!UICONTROL Apply]**.

## Configuration d’un modèle de suivi au niveau du groupe d’annonces : {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Cliquez sur **[!UICONTROL Toutes les campagnes]**, puis sur **[!UICONTROL Groupes publicitaires]** dans la fenêtre de développement.

   ![](assets/5-1.png)

1. Sélectionnez tous les groupes publicitaires applicables ou sélectionnez tout, cliquez sur **[!UICONTROL Modifier]**, puis sur **[!UICONTROL Modifier les modèles de suivi]**.

1. Saisissez le modèle de suivi [!DNL Marketo Measure] et cliquez sur **[!UICONTROL Apply]**.

   ![](assets/6-1.png)

## Questions fréquentes {#faq}

**Q : De quelles autorisations l’utilisateur connecté a-t-il besoin ?**

A : userinfo.email

**Q : Combien de temps faut-il pour importer des données de dépenses ?**

A : 6 heures

**Q : Combien de temps faut-il pour importer des données de publicité ?**

A : 4 heures

**Q : Pour les annonces de recherche dynamique, pouvons-nous suivre la combinaison du titre, de la description, etc., dans le créatif qui a été diffusé ?**

R : Nous ne pouvons pas récupérer les détails créatifs individuels pour les annonces de recherche dynamique, mais si le balisage automatique est activé, nous pouvons toujours obtenir l’identifiant créatif et les recettes d’attributs.

>[!NOTE]
>
>Une fois les modifications effectuées, vous avez terminé. N’hésitez pas à contacter le [support Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} si vous avez des questions pendant la configuration.

[Cliquez ici](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"} pour obtenir des instructions de Google sur la création de modèles de suivi au niveau du compte.
