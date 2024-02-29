---
description: "[!DNL Marketo Measure] Intégrations avec Adobe Analytics - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Intégrations avec [!DNL Adobe Analytics]"
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
feature: Integration
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 1%

---

# Intégrations [!DNL Marketo Measure] avec Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

L’intégration des attributs du client B2B permet aux utilisateurs mutuels de [!DNL Marketo Measure] et Adobe Analytics pour enrichir leurs [!DNL Adobe Analytics] profils utilisateur avec des métadonnées précieuses dérivées de [!DNL Marketo Measure] moteur d’attribution et par le biais de sa fonctionnalité de synchronisation avec les CRM ([!DNL Microsoft Dynamics] et [!DNL Salesforce]). Il est disponible gratuitement pour tous les clients qui utilisent [!DNL Adobe Analytics] et [!DNL Marketo Measure].

>[!PREREQUISITES]
>
>Vous devez disposer d’abonnements actifs aux [!DNL Marketo Measure] et [!DNL Adobe Analytics].

## Configuration de l’intégration {#configuring-the-integration}

1. Créez une source de données Attributs du client dans votre console d’Experience Cloud. Instructions détaillées [peut être consulté ici](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html).

   Prenez note des informations suivantes, nécessaires lors des étapes suivantes :

   * ID d’alias, qui peut être n’importe quelle valeur que vous souhaitez. Nous recommandons &quot;marketomeasure_id&quot;

   * Nom d’hôte et informations d’identification du serveur FTP (nom d’utilisateur et mot de passe)

1. Une fois la source de données Attributs du client créée, poursuivez le processus de configuration en accédant à la **[!UICONTROL Intégrations]** > **[!UICONTROL Connexions]** dans l’écran [!DNL Marketo Measure] menu admin.

1. Cliquez sur le bouton **[!UICONTROL Configurer une nouvelle connexion aux attributs du client]** et suivez les instructions pour configurer l’intégration des attributs du client. L’interface utilisateur vous invite à saisir l’ID d’alias et les informations de connexion FTP que vous avez acquises lors de la création de la source des attributs du client dans votre console des services principaux et à sélectionner l’ensemble des attributs de compte que vous souhaitez synchroniser avec votre [!DNL Adobe Analytics] compte .

   vous devrez également saisir votre ID d’organisation Adobe IMS. Cet identifiant s’affiche dans le coin inférieur droit de votre Admin Console Adobe Experience Cloud. Pour obtenir de l’aide sur la recherche de cet ID, consultez l’équipe du compte Adobe (votre gestionnaire de compte).

1. Une fois que vous avez créé la connexion dans votre [!DNL Marketo Measure] , vous devez revenir à la console de votre Experience Cloud pour [valider le schéma](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/validate-schema.html?lang=en). Vous n’avez pas à vous soucier du téléchargement du fichier FTP. [!DNL Marketo Measure] a automatisé cette partie pour vous. Tout ce que vous devez faire est d’accéder à l’écran de schéma &quot;Afficher/Modifier&quot; de la source d’attributs du client que vous avez créée à l’étape 1 et indiquer à Adobe quels sont les types de données pour chacun des attributs que vous avez créés. [!DNL Marketo Measure] a été chargé en votre nom. Vous pouvez également créer de nouveaux noms affichables pour les attributs chargés, le cas échéant.

   Si vous avez choisi de synchroniser les attributs de votre objet de compte CRM, il est vivement recommandé de leur attribuer de nouveaux noms d’affichage, comme [!DNL Marketo Measure] renseignera uniquement les noms au niveau de l’API pour ces attributs, qui ne sont généralement pas compatibles avec les rapports.

1. La dernière étape consiste à configurer les abonnements aux attributs pour les applications Experience Cloud dans lesquelles vous souhaitez utiliser les attributs. Vous pouvez configurer des abonnements pour [!DNL Adobe Analytics] ou [!DNL Adobe Target].  Informations supplémentaires sur la manière de procéder [peut être consulté ici](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/subscription.html).

## Descriptions des attributs {#attribute-descriptions}

Lorsque vous créez une connexion d’attributs du client B2B, [!DNL Marketo Measure] crée automatiquement un ensemble standard d’attributs du client B2B pour vous. Ces attributs sont décrits dans le tableau ci-dessous.

Outre ceux répertoriés ci-dessous, vous pouvez également charger tous les attributs associés à l’objet de compte dans votre système de gestion de la relation client. Si plusieurs comptes sont liés à un utilisateur donné, [!DNL Marketo Measure] renseigne toutes les valeurs d’attribut de compte correspondantes dans une liste délimitée par des points-virgules.

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><b>Nom attribut</b></td> 
   <td><b>Description</b></td>
  </tr> 
  <tr> 
   <td>Account.Name</td> 
   <td>Noms de compte associés au visiteur web donné. Si plusieurs comptes sont liés à un utilisateur donné, [!DNL Marketo Measure] renseigne tous les noms de compte correspondants dans une liste délimitée par des points-virgules.<br/>
   <strong>Remarque :</strong> account.name est le nom de niveau Salesforce-API de l’attribut name sur l’objet de compte. Vous pouvez choisir un meilleur nom d’affichage (par exemple, "Société") pour cet attribut lors de l’étape Validation du schéma de la configuration de l’intégration (étape 4).</td>
  </tr>
  <tr> 
   <td>Recettes affectées - MODEL’</td> 
   <td>Le chiffre d’affaires attribué à ce client en raison de son association avec des opportunités non validées dans votre CRM, comme calculé par la variable [!DNL Marketo Measure] moteur d’attribution.<br/>
   Il existe un de ces attributs pour chaque modèle d’attribution que votre [!DNL Marketo Measure] abonnements autorise (par exemple, "Recettes affectées - Chemin complet").</td>
  </tr>
  <tr> 
   <td>Etape Entonnoir le plus profond</td> 
   <td>L’étape d’entonnoir la plus profonde de toute opportunité ouverte associée à l’utilisateur donné.</td>
  </tr>
  <tr> 
   <td>Opportunités ouvertes</td> 
   <td>Liste, délimitée par des points-virgules, des identifiants d’opportunité auxquels l’utilisateur donné est lié en fonction de vos données CRM.</td>
  </tr> 
 </tbody> 
</table>

**Remarque sur les limites d’attribut**

Les attributs affichés via cette intégration seront toujours pris en compte par rapport à vos limites d’attributs contractuelles dans [!DNL Adobe Analytics] et [!DNL Adobe Target]. Uniquement les attributs qui apparaissent via un abonnement aux attributs (étape 5 de la section [Configuration de l’intégration](#configuring-the-integration)) comptera sur votre limite pour l’application abonnée.

## FAQ {#faqs}

**Comment modifier l’ensemble d’attributs que je souhaite partager via cette intégration ?**

Pour un attribut partagé par [!DNL Marketo Measure] à votre organisation Adobe IMS via cette intégration à afficher et à utiliser dans [!DNL Adobe Analytics], il doit être affiché via un abonnement aux attributs configuré dans la console des services principaux. Par conséquent, si vous souhaitez supprimer un attribut afin qu’il n’apparaisse plus dans [!DNL Adobe Analytics], vous pouvez y parvenir en supprimant simplement l’abonnement à l’attribut .

Vous pouvez également supprimer la connexion Attribut client B2B dans [!DNL Marketo Measure] et recréez-le avec l’attribut que vous ne souhaitez plus partager exclu de la configuration de la connexion. De même, pour ajouter des attributs à l’intégration, vous devez supprimer la connexion existante et en créer une nouvelle avec les attributs souhaités ajoutés à la configuration.

Compte tenu de ce qui précède, il est vivement recommandé, lors de la configuration de la connexion d’attributs pour la première fois, d’être aussi inclusif que possible lors de la sélection des attributs.

**Quels sont les exemples d’utilisation de cette intégration ?**

1. Mesures de trafic basées sur un compte : à l’aide de l’attribut nom du compte, vous pouvez créer des segments d’un ou de plusieurs comptes cibles dans Adobe Analytics et analyser les mesures de trafic du site pour seulement le sous-ensemble du trafic provenant des comptes cibles.
1. Analyses de contenu : utilisez la mesure des recettes pour analyser le contenu du site le plus attrayant pour les clients qui achètent votre produit ou service, ou ceux qui atteignent un stade d’entonnoir spécifique.
1. Assistance en direct : apportez à votre équipe commerciale des informations exploitables en analysant le comportement du site des utilisateurs associés à une opportunité d’ouverture spécifique dans votre CRM.
