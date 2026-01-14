---
description: Consignes  [!DNL Marketo Measure]  balisage AdWords pour les utilisateurs de Marketo Measure
title: 'Comprendre le balisage AdWords dans [!DNL Marketo Measure] '
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
feature: APIs, Integration, UTM Parameters
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 6%

---

# Comprendre [!DNL Marketo Measure] balisage AdWords {#understanding-marketo-measure-adwords-tagging}

Pour effectuer le suivi de vos publicités à un niveau très granulaire, les URL de destination de la publicité doivent être uniques. Pour ce faire, [!DNL Marketo Measure] balisage automatique ajoute automatiquement des paramètres de suivi aux URL de destination des annonces [!DNL AdWords]. Examinons un exemple ci-dessous.

L’URL suivante ne fournit aucune donnée granulaire :

* `http://example.com/landing-page?myParam=foo`

Cependant, la même URL fournira des données granulaires en raison des paramètres [!DNL Marketo Measure] :

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Fonctionnement [!DNL Marketo Measure] balisage automatique {#how-marketo-measure-auto-tagging-works}

**Si [!DNL Marketo Measure] trouve un modèle de tracking :**

* [!DNL Marketo Measure] ajoutera ses paramètres au modèle de suivi.
* Si une redirection tierce est trouvée dans un modèle de suivi tel que Kenshoo ou Marin, [!DNL Marketo Measure] n’entreprendra aucune action. Vous devez [ajouter [!DNL Marketo Measure] des paramètres à l’outil tiers dans votre compte](/help/api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

Cependant, si aucun modèle de suivi n’est trouvé, [!DNL Marketo Measure] :

* Analysez toutes les URL de destination publicitaire pour connaître nos paramètres [!DNL Marketo Measure].
* Si elle est trouvée, tout est prêt.
* S’il est introuvable, [!DNL Marketo Measure] ajoute ses paramètres à la fin des URL de destination de l’annonce. Pour les nouvelles publicités, [!DNL Marketo Measure] ajoutera ses paramètres à l’URL de destination de la publicité dans les deux heures suivant leur création.
* Il est important de mettre en place un modèle de suivi avant d’activer le balisage automatique afin que [!DNL Marketo Measure] puissiez le joindre et empêcher la réinitialisation de l’historique des publicités.

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne, ou du groupe de publicités, car cela permet d’ajouter et de soustraire des paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique des publicités.

## Modèles de tracking {#tracking-templates}

Comme expliqué par [!DNL Google AdWords], un modèle de tracking est l’URL utilisée pour atteindre une page de destination. Les informations de suivi collectées sont utilisées pour comprendre votre trafic publicitaire. [Cliquez ici](https://support.google.com/adwords/answer/7197008?hl=en){target="_blank"} pour plus d’informations à partir de Google.

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne ou du groupe publicitaire , car il permet d’ajouter et de soustraire des paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique publicitaire.

Il existe deux modèles de tracking que [!DNL Marketo Measure] recommande d’utiliser. Utilisez les éléments suivants pour déterminer la version qui vous convient :

* Si toutes les URL de vos publicités comportent un « ? » dans ces pages, utilisez cette URL :

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* Si aucune de vos URL d’annonces publicitaires ne comporte de « ? » dans ces pages, utilisez cette URL :

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Configuration d’un modèle de tracking au niveau du compte {#setting-up-a-tracking-template-at-the-account-level}

1. Connectez-vous à votre compte [!DNL Google AdWords].

1. Cliquez sur **[!UICONTROL Toutes les campagnes]** puis sur **[!UICONTROL Paramètres]** dans la fenêtre qui s’étend.

   ![1. Cliquez sur Toutes les campagnes , puis sur Paramètres dans l’extension](assets/utilizing-connections-13.png)

1. Cliquez sur **[!UICONTROL Paramètres du compte]** dans la partie supérieure, puis sur **[!UICONTROL Modèle de suivi]**. Saisissez le modèle de suivi [!DNL Marketo Measure].

   ![1. Cliquez sur Paramètres du compte en haut, puis sur Suivi](assets/bizible-guide-1.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**

## Configurer un modèle de tracking au niveau d&#39;une campagne {#setting-up-a-tracking-template-at-the-campaign-level}

1. Cliquez sur **[!UICONTROL Toutes les campagnes]** puis sur **[!UICONTROL Campagnes]** dans la fenêtre en expansion.

   ![1. Cliquez sur Toutes les campagnes , puis sur Campagnes dans l’extension](assets/utilizing-connections-12.png)

1. Sélectionnez toutes les campagnes applicables ou **[!UICONTROL Tout sélectionner]**, cliquez sur **[!UICONTROL Modifier]**, puis sur **[!UICONTROL Modifier les modèles de suivi]**.

   ![1. Sélectionnez toutes les campagnes applicables ou sélectionnez tout, cliquez sur Modifier ](../assets/marketo-engage-activities-05.png)

1. Saisissez le modèle de suivi [!DNL Marketo Measure] et cliquez sur **[!UICONTROL Appliquer]**.

## Configuration d’un modèle de suivi au niveau du groupe publicitaire : {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Cliquez sur **[!UICONTROL Toutes les campagnes]** puis sur **[!UICONTROL Groupes publicitaires]** dans la fenêtre qui s’étend.

   ![1. Cliquez sur Toutes les campagnes , puis sur Groupes publicitaires dans l’](assets/api-connections-01.png)

1. Sélectionnez tous les groupes publicitaires applicables ou sélectionnez tout, cliquez sur **[!UICONTROL Modifier]** puis sur **[!UICONTROL Modifier les modèles de suivi]**.

1. Saisissez le modèle de suivi [!DNL Marketo Measure] et cliquez sur **[!UICONTROL Appliquer]**.

   ![1. Saisissez le modèle de suivi Marketo Measure, puis cliquez sur Appliquer](../assets/marketo-engage-activities-01.png).

## Questions fréquentes {#faq}

**Q : De quelles autorisations l’utilisateur connecté a-t-il besoin ?**

A : userinfo.email

**Q : Combien de temps faut-il pour importer les données de dépenses ?**

A : 6 heures

**Q : Combien de temps faut-il pour importer les données publicitaires ?**

A : 4 heures

**Q : Pour les annonces de recherche dynamique, pouvons-nous suivre la combinaison de titre, description, etc., dans le contenu créatif diffusé ?**

R : Nous ne pouvons pas récupérer les détails créatifs individuels pour les annonces de recherche dynamique, mais si le balisage automatique est activé, nous pouvons toujours obtenir l’identifiant créatif et le chiffre d’affaires des attributs.

>[!NOTE]
>
>Une fois les modifications apportées, vous avez terminé. N’hésitez pas à contacter l’assistance technique de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour toute question lors de la configuration.

[Cliquez ici](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"} pour obtenir des instructions de Google sur la création de modèles de suivi au niveau du compte.
