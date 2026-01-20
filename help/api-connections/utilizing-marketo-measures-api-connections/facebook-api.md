---
unique-page-id: 18874680
description: API [!DNL Facebook] - [!DNL Marketo Measure]
title: '[!DNL Facebook] API'
exl-id: d6d18545-baae-4103-b0a6-c3de681ec833
feature: APIs, Integration, UTM Parameters
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---

# [!DNL Facebook] API {#facebook-api}

## Introduction {#introduction}

Tout comme nos intégrations AdWords et [!DNL Bing Ads], notre intégration [!DNL Facebook] effectue deux actions fondamentales :

* Balisage automatique de toutes les publicités [!DNL Facebook] avec un paramètre [!DNL Marketo Measure] (_bf)
* Télécharger les informations sur les coûts des publicités sur toutes les publicités Facebook actives

## Configuration de l’intégration [!DNL Facebook] {#how-to-configure-the-facebook-integration}

En ce qui concerne la configuration, l’application [!DNL Marketo Measure] comporte sept étapes.

1. Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous.
1. Sous Mon compte, sélectionnez **[!UICONTROL Paramètres]**.
1. Sous Intégrations, sélectionnez **[!UICONTROL Connexions]**.
1. Sélectionnez **[!UICONTROL Configurer une nouvelle connexion publicitaire]** et un pop-up s’affiche. Sélectionnez **[!UICONTROL Facebook]** et connectez-vous à l’aide de vos identifiants Facebook.

   >[!NOTE]
   >
   >La personne qui connecte le compte [!DNL Facebook Ads] doit être un administrateur au sein du compte [!DNL Facebook Ads].

1. Une fois [!DNL Marketo Measure] connecté à votre compte Facebook, cliquez sur l’icône en forme de crayon en regard du compte.
1. Dans cette vue, déplacez le « Balisage automatique ? » Basculez sur « Oui ». Cochez ensuite la case située dans la section [!UICONTROL &#x200B; En savoir plus &#x200B;] pour accepter les conditions générales. Assurez-vous que le bouton (bascule) [!UICONTROL Balisage automatique] est toujours défini sur « [!UICONTROL Oui] ».

## Connexion au compte {#connecting-the-account}

![](assets/1.gif)

## Activation du balisage automatique {#enabling-autotagging}

>[!NOTE]
>
>Si vous activez le balisage automatique, nous réinitialiserons l’historique des conversions et le BAT des réseaux sociaux de toutes les publicités que nous balisons. Nous vous recommandons vivement d’[exporter ces données au format CSV](https://www.facebook.com/business/help/205067636197240) avant d’activer le balisage automatique.

![](assets/2-2.png)

Une fois que vous avez activé l’intégration, [!DNL Marketo Measure] commencerez à télécharger le coût au niveau des annonces dans le tableau de bord [!DNL Marketo Measure Marketing ROI].

Pour que l’intégration fonctionne correctement, vous devez activer le balisage automatique sur votre compte [!DNL Facebook]. Cela permettra à notre système d’ajouter un paramètre _bf à tous les liens publicitaires. Ce processus ajoute le nouveau paramètre en plus de tous les autres paramètres de suivi que vous avez déjà ajoutés à vos publicités [!DNL Facebook].

![](assets/3.gif)

## Appariement des champs {#field-mapping}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p><strong>Champ de point de contact</strong></p></th> 
   <th><p><strong>Valeur</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>ID de campagne publicitaire</p></td> 
   <td><p>[Identifiant De Campagne [!DNL Facebook]]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom de la campagne publicitaire </p></td> 
   <td><p>[Nom de la campagne [!DNL Facebook]] ou [utm_campaign] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>ID de groupe publicitaire</p></td> 
   <td><p>[[!DNL Facebook] Id De Visionneuse D’Annonces]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom de groupe publicitaire</p></td> 
   <td><p>[Nom de la visionneuse d’annonces [!DNL Facebook]]</p></td> 
  </tr> 
  <tr> 
   <td><p>Source du point de contact</p></td> 
   <td><p> »[!DNL Facebook] » ou [utm_source] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Support</p></td> 
   <td><p>« Social » ou [utm_medium] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad Id ou Creative_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[ID personnalisé généré à partir de utm_content]</p></td> 
  </tr> 
  <tr> 
   <td><p>Contenu publicitaire ou nom_Creative (Data Warehouse)</p></td> 
   <td><p>[utm_content] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Texte du mot-clé ou Nom_mot-clé (Data Warehouse)</p></td> 
   <td><p>[utm_term] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[ID d’annonce publicitaire [!DNL Facebook]]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Name (Data Warehouse)</p></td> 
   <td><p>[Nom de publicité [!DNL Facebook]]</p></td> 
  </tr> 
  <tr> 
   <td><p>Keyword_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[ID personnalisé généré à partir de utm_term]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Provider (Data Warehouse)</p></td> 
   <td><p> »[!DNL Facebook] »</p></td> 
  </tr> 
  <tr> 
   <td><p>Account_Unique_ID (Data Warehouse)</p></td> 
   <td><p>[N° de compte [!DNL Facebook]]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom_Compte (Data Warehouse)</p></td> 
   <td><p>[Nom de compte [!DNL Facebook]]</p></td> 
  </tr> 
 </tbody> 
</table>

## Questions fréquentes {#faq}

**Q : Quelles publicités [!DNL Facebook] sont prises en charge par [!DNL Marketo Measure] ?**

A : carrousel, image unique. Pas de vidéo, diaporama ou collection pour le moment.

**Q : Qu&#39;est-ce qu&#39;une preuve sociale ?**

R : La preuve sociale est un engagement visible tel que des likes, des clics, des commentaires et des partages.

**Q : Que se passe-t-il lorsque [!DNL Marketo Measure] balises de l’annonce publicitaire ?**

R : [!DNL Facebook] ne permet pas la modification des publicités. [!DNL Marketo Measure] devez donc supprimer le contenu créatif, qui contient l’URL de destination, puis recréer la publicité avec les nouveaux paramètres.

**Q : Pourquoi met-[!DNL Marketo Measure] à jour toutes [!DNL Facebook] publicités ?**

R : Le processus [!DNL Marketo Measure] consiste à baliser toutes les publicités au cas où elles seraient réactivées.

**Q : De quelle autorisation l’utilisateur connecté a-t-il besoin ?**

A : ads_management, e-mail

**Q : Combien de temps faut-il pour importer les données de dépenses ?**

A : 1 heure

**Q : Combien de temps faut-il pour importer les données publicitaires ?**

A : 4 heures
