---
description: Intégrations [!DNL Marketo Measure] à Adobe Analytics - [!DNL Marketo Measure]
title: '[!DNL Marketo Measure] Intégrations à  [!DNL Adobe Analytics]'
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
feature: Integration
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 1%

---

# Intégrations [!DNL Marketo Measure] avec Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

L’intégration Attributs du client B2B permet aux utilisateurs mutuels d’[!DNL Marketo Measure] et d’Adobe Analytics d’enrichir leurs profils d’utilisateurs [!DNL Adobe Analytics] avec des métadonnées précieuses dérivées du moteur d’attribution [!DNL Marketo Measure] et grâce à sa fonctionnalité de synchronisation avec les CRM ([!DNL Microsoft Dynamics] et [!DNL Salesforce]). Il est disponible gratuitement pour tous les clients qui utilisent [!DNL Adobe Analytics] et [!DNL Marketo Measure].

>[!PREREQUISITES]
>
>Vous devez disposer d’abonnements actifs à [!DNL Marketo Measure] et [!DNL Adobe Analytics].

## Configuration de l’intégration {#configuring-the-integration}

1. Créez une nouvelle Source de données d’attributs du client dans votre console Experience Cloud. Des instructions détaillées [voir ici](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html?lang=fr).

   Tenez compte des informations suivantes, nécessaires lors des étapes suivantes :

   * L’ID d’alias, qui peut être n’importe quelle valeur que vous souhaitez. Nous vous recommandons d’utiliser « marketomeasure_id »

   * Nom d’hôte et informations d’identification du serveur FTP (nom d’utilisateur et mot de passe)

1. Une fois la Source de données d’attributs du client créée, poursuivez le processus de configuration en accédant à l’écran **[!UICONTROL Intégrations]** > **[!UICONTROL Connexions]** dans le menu d’administration [!DNL Marketo Measure].

1. Cliquez sur le bouton **[!UICONTROL Configurer une nouvelle connexion aux attributs du client]** et suivez les instructions pour configurer l’intégration des attributs du client. L’interface utilisateur vous invite à saisir l’ID d’alias et les informations de connexion FTP que vous avez acquises lors de la création du Source Attributs du client dans la console des services principaux. Sélectionnez l’ensemble des attributs de compte que vous souhaitez synchroniser avec votre compte [!DNL Adobe Analytics].

   Saisissez votre identifiant d’organisation Adobe IMS. Cet identifiant s’affiche dans le coin inférieur droit de votre Admin Console Adobe Experience Cloud. Pour plus d’informations sur la recherche de cet identifiant, contactez l’équipe chargée du compte Adobe (votre gestionnaire de compte).

1. Une fois la création de la connexion dans votre compte [!DNL Marketo Measure] terminée, vous devez revenir à votre console Experience Cloud pour [valider le schéma](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/validate-schema.html?lang=fr). Vous n’avez pas à vous soucier du chargement du fichier FTP, [!DNL Marketo Measure] a automatisé cette partie pour vous. Accédez à l’écran « Afficher/Modifier » le schéma du Source d’attributs du client que vous avez créé à l’étape 1 et indiquez à Adobe quels sont les types de données pour chacun des attributs que [!DNL Marketo Measure] a chargés en votre nom. Si vous le souhaitez, vous pouvez également créer des noms conviviaux pour l’affichage des attributs chargés.

   Si vous avez choisi de synchroniser les attributs de votre objet de compte CRM, il est vivement recommandé de choisir de nouveaux noms d’affichage pour ces attributs, car [!DNL Marketo Measure] renseigne uniquement les noms au niveau de l’API pour ces attributs, qui ne sont généralement pas conviviaux pour la création de rapports.

1. La dernière étape consiste à configurer les abonnements aux attributs pour les applications Experience Cloud dans lesquelles vous souhaitez utiliser les attributs. Vous pouvez configurer des abonnements pour [!DNL Adobe Analytics] ou [!DNL Adobe Target].  Vous trouverez plus d’informations sur la façon de procéder [ici](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/subscription.html?lang=fr).

## Descriptions des attributs {#attribute-descriptions}

Lorsque vous créez une connexion d’attributs du client B2B, [!DNL Marketo Measure] crée automatiquement un ensemble standard d’attributs du client B2B pour vous. Ces attributs sont décrits dans le tableau ci-dessous.

En plus de ceux répertoriés ci-dessous, vous pouvez également charger les attributs associés à l’objet de compte dans votre CRM. Si plusieurs comptes sont liés à l’utilisateur donné, [!DNL Marketo Measure] renseigne toutes les valeurs d’attribut de compte correspondantes dans une liste délimitée par des points-virgules.

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><b>Nom de l’attribut</b></td> 
   <td><b>Description</b></td>
  </tr> 
  <tr> 
   <td>Account.Name</td> 
   <td>Noms de compte associés au visiteur web donné. Si plusieurs comptes sont liés à l’utilisateur donné, [!DNL Marketo Measure] renseigne tous les noms de compte correspondants dans une liste délimitée par des points-virgules.<br/>
   <strong>Remarque :</strong> account.name est le nom au niveau de l’API Salesforce pour l’attribut name sur l’objet account. Vous pouvez choisir un meilleur nom d’affichage (par exemple, « Société ») pour cet attribut au cours de l’étape Validation du schéma de la configuration d’intégration (étape 4).</td>
  </tr>
  <tr> 
   <td>Chiffre d’affaires attribué - ‹MODÈLE›</td> 
   <td>Chiffre d’affaires attribué à ce client en raison de son association avec des opportunités closes et confirmées dans votre CRM, tel que calculé par le moteur d’attribution [!DNL Marketo Measure].<br/>
   Il existe un de ces attributs pour chaque modèle d’attribution que vos abonnements [!DNL Marketo Measure] autorisent (par exemple, « Revenu attribué - Chemin complet »).</td>
  </tr>
  <tr> 
   <td>Étape Funnel la plus profonde</td> 
   <td>Étape funnel la plus profonde de toute opportunité ouverte associée à l’utilisateur donné.</td>
  </tr>
  <tr> 
   <td>Opportunités ouvertes</td> 
   <td>Liste des identifiants d’opportunité auxquels l’utilisateur donné est lié en fonction de vos données CRM, délimités par des points-virgules.</td>
  </tr> 
 </tbody> 
</table>

**Remarque sur les limites d’attributs**

Les attributs affichés via cette intégration sont comptabilisés par rapport à vos limites d’attributs contractuelles dans [!DNL Adobe Analytics] et [!DNL Adobe Target]. Seuls les attributs affichés par le biais d’un abonnement aux attributs (étape 5 de [Configuration de l’intégration](#configuring-the-integration)) sont comptabilisés par rapport à votre limite pour l’application à laquelle vous êtes abonné.

## Questions fréquentes {#faqs}

**Comment modifier l’ensemble des attributs que je souhaite partager via cette intégration ?**

Pour qu’un attribut partagé par [!DNL Marketo Measure] à votre organisation Adobe IMS via cette intégration soit visible et utilisé dans [!DNL Adobe Analytics], il doit être surfacé via un abonnement aux attributs configuré dans la console des services principaux. Par conséquent, si vous souhaitez supprimer un attribut afin qu’il n’apparaisse plus dans [!DNL Adobe Analytics], vous pouvez le faire simplement en supprimant l’abonnement aux attributs.

Vous pouvez également supprimer la connexion Attribut du client B2B dans [!DNL Marketo Measure] et la recréer avec l’attribut que vous ne souhaitez plus partager, exclu de la configuration de connexion. De même, pour ajouter des attributs à l’intégration, vous devez supprimer la connexion existante et en créer une nouvelle avec les attributs souhaités ajoutés à la configuration.

Compte tenu de ce qui précède, il est vivement recommandé, lors de la configuration initiale de la connexion d’attribut, d’être aussi inclusif que possible lors de la sélection d’attributs.

**Quels sont des exemples de cas d’utilisation pour cette intégration ?**

1. Mesures de trafic basé sur les comptes : à l’aide de l’attribut nom du compte, vous pouvez créer des segments d’un ou de plusieurs comptes cibles dans Adobe Analytics et analyser les mesures de trafic du site pour le sous-ensemble du trafic provenant des comptes cibles.
1. Content Analytics : utilisez la mesure du chiffre d’affaires pour analyser le contenu du site le plus attrayant pour les clients qui achètent finalement votre produit ou service, ou pour ceux qui atteignent une étape spécifique de funnel.
1. Assistance en direct : équipez votre équipe des ventes d’insight exploitable en analysant le comportement du site pour les utilisateurs associés à une opportunité ouverte spécifique dans votre CRM.
