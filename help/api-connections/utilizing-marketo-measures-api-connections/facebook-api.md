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

# [!DNL Facebook] API {#facebook-api}

## Introduction {#introduction}

Semblable à nos AdWords et [!DNL Bing Ads] intégrations, nos [!DNL Facebook] l’intégration effectue deux actions fondamentales :

* Balisage automatique de toutes les [!DNL Facebook] Publicités avec un [!DNL Marketo Measure] parameter (_bf)
* Téléchargement des informations de coût de la publicité sur toutes les publicités Facebook actives

## Comment configurer le [!DNL Facebook] Intégration {#how-to-configure-the-facebook-integration}

En ce qui concerne la configuration, sept étapes doivent être exécutées dans la [!DNL Marketo Measure] application.

1. Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et se connecter.
1. Sous Mon compte, sélectionnez **[!UICONTROL Paramètres]**.
1. Sous Intégrations , sélectionnez **[!UICONTROL Connexions]**.
1. Sélectionner **[!UICONTROL Configurer une nouvelle connexion aux publicités]** et une fenêtre contextuelle s’affiche. Sélectionner **[!UICONTROL Facebook]** et connectez-vous à l’aide de vos informations d’identification Facebook.

   >[!NOTE]
   >
   >La personne qui connecte la variable [!DNL Facebook Ads] doit être un administrateur dans la variable [!DNL Facebook Ads] compte .

1. Une fois [!DNL Marketo Measure] est connecté à votre compte Facebook, cliquez sur l’icône en forme de crayon en regard du compte.
1. Dans cette vue, déplacez le &quot;balisage automatique ?&quot; basculez sur &quot;Oui&quot;. Cochez ensuite la case située dans la variable [!UICONTROL En savoir plus] pour accepter les conditions générales. Assurez-vous que la variable [!UICONTROL Balisage automatique] Le bouton bascule est toujours défini sur &quot;[!UICONTROL Oui]&#39;.

## Connexion au compte {#connecting-the-account}

![](assets/1.gif)

## Activation de l’authentification {#enabling-autotagging}

>[!NOTE]
>
>Si vous activez le balisage automatique, l’historique de conversion et le BAT social de toutes les publicités que nous marquons seront réinitialisés. Nous vous recommandons vivement [exportation de ces données au format CSV](https://www.facebook.com/business/help/205067636197240) avant d’activer le balisage automatique.

![](assets/2-2.png)

Une fois que vous avez activé l’intégration, [!DNL Marketo Measure] commence à télécharger le coût au niveau de l’annonce dans la variable [!DNL Marketo Measure Marketing ROI] Tableau de bord.

Pour que l’intégration fonctionne correctement, vous devez activer le balisage automatique sur votre [!DNL Facebook] compte . Cela permettra à notre système d’ajouter un paramètre _bf à tous les liens publicitaires. Ce processus ajoute le nouveau paramètre en plus des autres paramètres de suivi que vous avez déjà ajoutés à votre [!DNL Facebook] publicités.

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
   <td><p>[[!DNL Facebook] Nom de la campagne], ou [utm_campaign], si fourni</p></td> 
  </tr> 
  <tr> 
   <td><p>Identifiant du groupe publicitaire</p></td> 
   <td><p>[[!DNL Facebook] Identifiant De Visionneuse De Publicités]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom de groupe publicitaire</p></td> 
   <td><p>[[!DNL Facebook] Nom de la visionneuse de publicités]</p></td> 
  </tr> 
  <tr> 
   <td><p>Source du point de contact</p></td> 
   <td><p>"[!DNL Facebook]", ou [utm_source] si fourni</p></td> 
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
   <td><p>[[!DNL Facebook] Identifiant de publicité]</p></td> 
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
   <td><p>[[!DNL Facebook] N° de compte</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom_compte (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Nom du compte]</p></td> 
  </tr> 
 </tbody> 
</table>

## Questions fréquentes {#faq}

**Q : Quels éléments ? [!DNL Facebook] Les publicités sont prises en charge par [!DNL Marketo Measure]?**

R : Carrousel, Une seule image. Pas vidéo, diaporama ou collection pour l’instant.

**Q : Qu&#39;est-ce que la preuve sociale ?**

R : Un BAT social est un engagement visible comme des mentions J’aime, des clics, des commentaires et des partages.

**Q : Ce qui se passe lorsque [!DNL Marketo Measure] balise la publicité ?**

A : [!DNL Facebook] n’autorise pas la modification des publicités. [!DNL Marketo Measure] doit supprimer le contenu créatif, qui contient l’URL de destination, puis recréer la publicité avec les nouveaux paramètres.

**Q : Pourquoi [!DNL Marketo Measure] mettre à jour tout [!DNL Facebook] Publicités ?**

R : Le [!DNL Marketo Measure] Le processus consiste à baliser toutes les publicités au cas où elles seraient réactivées.

**Q : De quelle autorisation l’utilisateur connecté a-t-il besoin ?**

A : ads_management, e-mail

**Q. : Combien de temps peut-on mettre pour importer des données de dépenses ?**

A : 1 heure

**Q. : Combien de temps peut-il s’écouler avant l’importation des données publicitaires ?**

A : 4 heures
