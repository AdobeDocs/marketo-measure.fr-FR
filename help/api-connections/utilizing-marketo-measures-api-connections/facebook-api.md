---
unique-page-id: 18874680
description: "[!DNL Facebook] API - [!DNL Marketo Measure]"
title: "[!DNL Facebook] API"
exl-id: d6d18545-baae-4103-b0a6-c3de681ec833
feature: APIs, Integration, UTM Parameters
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---

# API [!DNL Facebook] {#facebook-api}

## Introduction {#introduction}

Tout comme nos intégrations AdWords et [!DNL Bing Ads] , notre intégration [!DNL Facebook] effectue deux actions fondamentales :

* Balisez automatiquement toutes les [!DNL Facebook] publicités avec un paramètre [!DNL Marketo Measure] (_bf)
* Téléchargement des informations de coût de la publicité sur toutes les publicités Facebook actives

## Configuration de l’intégration [!DNL Facebook] {#how-to-configure-the-facebook-integration}

Pour ce qui est de la configuration, sept étapes doivent être effectuées dans l’application [!DNL Marketo Measure].

1. Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous.
1. Sous Mon compte, sélectionnez **[!UICONTROL Paramètres]**.
1. Sous Intégrations, sélectionnez **[!UICONTROL Connexions]**.
1. Sélectionnez **[!UICONTROL Configurer une nouvelle connexion aux publicités]** et une fenêtre contextuelle s’affiche. Sélectionnez **[!UICONTROL Facebook]** et connectez-vous à l’aide de vos informations d’identification Facebook.

   >[!NOTE]
   >
   >La personne qui se connecte au compte [!DNL Facebook Ads] doit être un administrateur dans le compte [!DNL Facebook Ads].

1. Une fois [!DNL Marketo Measure] connecté à votre compte Facebook, cliquez sur l’icône en forme de crayon en regard du compte.
1. Dans cette vue, déplacez le &quot;balisage automatique ?&quot; basculez sur &quot;Oui&quot;. Cochez ensuite la case située dans la section [!UICONTROL En savoir plus] pour accepter les conditions générales. Assurez-vous que le bouton [!UICONTROL Balisage automatique] est toujours défini sur &quot;[!UICONTROL Oui]&quot;.

## Connexion au compte {#connecting-the-account}

![](assets/1.gif)

## Activation de l’authentification {#enabling-autotagging}

>[!NOTE]
>
>Si vous activez le balisage automatique, l’historique de conversion et le BAT social de toutes les publicités que nous marquons seront réinitialisés. Nous vous recommandons vivement d’exporter ces données au format CSV](https://www.facebook.com/business/help/205067636197240) avant d’activer le balisage automatique.[

![](assets/2-2.png)

Une fois que vous avez activé l’intégration, [!DNL Marketo Measure] commence à télécharger le coût au niveau de l’annonce dans le tableau de bord [!DNL Marketo Measure Marketing ROI].

Pour que l’intégration fonctionne correctement, vous devez activer le balisage automatique sur votre compte [!DNL Facebook]. Cela permettra à notre système d’ajouter un paramètre _bf à tous les liens publicitaires. Ce processus ajoute le nouveau paramètre en plus des autres paramètres de suivi que vous avez déjà ajoutés à vos publicités [!DNL Facebook].

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
   <td><p>Identifiant de campagne publicitaire</p></td> 
   <td><p>[[!DNL Facebook] ID de campagne]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom de la campagne publicitaire </p></td> 
   <td><p>[[!DNL Facebook] Nom de la campagne] ou [utm_campaign] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Identifiant du groupe publicitaire</p></td> 
   <td><p>[[!DNL Facebook] Id De Visionneuse De Publicités]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom de groupe publicitaire</p></td> 
   <td><p>[[!DNL Facebook] Nom de la visionneuse de publicités]</p></td> 
  </tr> 
  <tr> 
   <td><p>Source du point de contact</p></td> 
   <td><p>"[!DNL Facebook]" ou [utm_source], le cas échéant</p></td> 
  </tr> 
  <tr> 
   <td><p>Support</p></td> 
   <td><p>"Social" ou [utm_medium] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Identifiant de publicité ou Creative_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[ID personnalisé généré à partir de utm_content]</p></td> 
  </tr> 
  <tr> 
   <td><p>Contenu de la publicité ou nom_créatif (Data Warehouse)</p></td> 
   <td><p>[utm_content] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Texte du mot-clé ou Nom_mot-clé (Data Warehouse)</p></td> 
   <td><p>[utm_term] si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] ID De Publicité]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Name (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Nom de la publicité]</p></td> 
  </tr> 
  <tr> 
   <td><p>Keyword_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[ID personnalisé généré à partir de utm_term]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Provider (Data Warehouse)</p></td> 
   <td><p>"[!DNL Facebook]"</p></td> 
  </tr> 
  <tr> 
   <td><p>Account_Unique_ID (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] N° de compte]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom_compte (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Nom du compte]</p></td> 
  </tr> 
 </tbody> 
</table>

## Questions fréquentes {#faq}

**Q : Quelles [!DNL Facebook] publicités sont prises en charge par [!DNL Marketo Measure] ?**

R : Carrousel, Une seule image. Pas vidéo, diaporama ou collection pour l’instant.

**Q : Qu’est-ce que le BAT social ?**

R : Un BAT social est un engagement visible comme des mentions J’aime, des clics, des commentaires et des partages.

**Q : Que se passe-t-il lorsque [!DNL Marketo Measure] balise la publicité ?**

R : [!DNL Facebook] n’autorise pas la modification des publicités. [!DNL Marketo Measure] doit donc supprimer le créatif, qui contient l’URL de destination, puis recréer la publicité avec les nouveaux paramètres.

**Q : Pourquoi [!DNL Marketo Measure] met-il à jour toutes les [!DNL Facebook] publicités ?**

R : Le processus [!DNL Marketo Measure] consiste à baliser toutes les publicités au cas où elles seraient réactivées.

**Q : De quelle autorisation l’utilisateur connecté a-t-il besoin ?**

A : ads_management, e-mail

**Q : Combien de temps faut-il pour importer des données de dépenses ?**

A : 1 heure

**Q : Combien de temps faut-il pour importer des données de publicité ?**

A : 4 heures
