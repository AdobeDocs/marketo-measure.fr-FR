---
description: Présentation des autorisations d’intégration - [!DNL Marketo Measure] - Documentation du produit
title: Présentation des autorisations d’intégration
hide: true
hidefromtoc: true
feature: APIs, Integration
source-git-commit: d7ded9075f7f5831314d59294327f1e4928baf8a
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 4%

---

# Présentation des autorisations d’intégration {#integration-permissions-overview}

Ce guide décrit les autorisations nécessaires à une intégration transparente avec Marketo Measure, afin de garantir un fonctionnement efficace et sans problème de chaque intégration.

<table>
<thead>
  <tr>
    <th style="width:10%">Intégration</th>
    <th style="width:20%">Type de données
    <li>Données d’interaction web</li>
    <li>Données système B2B</li>
    <li>Données de la plateforme publicitaire</li></th>
    <th style="width:30%">Ce que nous suivons</th>
    <th style="width:40%">Exigences d’autorisation</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>Données système B2B    
</td>
    <td>Marketo Measure effectue le suivi :
    <p>
    <li>Compte</li>
    <li>Campagne</li>
    <li>CampaignMember</li>
    <li>Contact</li>
    <li>CurrencyConversionRange</li>
    <li>CurrencyStatus</li>
    <li>Événements</li>
    <li>FieldHistory (prospect, contact et opportunité)</li>
    <li>Prospect</li>
    <li>Opportunité</li>
    <li>OpportunityContactRole</li>
    <li>OpportunityHistory</li>
    <li>Tâches</li>
<p>
Les points de contact créés et d’autres données sont écrits dans des champs bizibles personnalisés sur Compte, Campaign, CampaignMember, Case, Contact, Lead et Opportunity.</td>
    <td><b>Autorisations des utilisateurs connectés à Salesforce (obligatoire)</b>
    <p>
    <b>Jeu d’autorisations d’administrateur Marketo Measure pour un utilisateur dédié :</b> Permet à l’administrateur SFDC d’effectuer des opérations CRUD sur le marketing pour mesurer des objets.
    <br>
    <b>Afficher et modifier le jeu d’autorisations de pistes converties :</b> Marketo Measure peut ainsi décorer les pistes après leur conversion en contacts.
    <br>
    <b>Case à cocher des utilisateurs marketing Salesforce :</b> La case à cocher Utilisateur marketing permet aux utilisateurs de créer des campagnes et d’utiliser les assistants d’importation de campagne.
    <br>
    <b>Utilisateur Marketo Measure Standard :</b> Permet à l’utilisateur de lire des enregistrements à partir d’objets Marketo Measure.
    <p>
    <b>Autorisations de champ Salesforce Standard</b>
    <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Objets standard Salesforce et accès</a>
    <p>
    <b>Autorisations de champ personnalisé Salesforce</b>
    <br>
    Nous fournissons des paramètres de fonctionnalité permettant de contenir des champs Salesforce personnalisés que les clients peuvent utiliser. Si ces paramètres de fonctionnalité sont définis, nous avons besoin d’un accès en LECTURE à chacun des champs Salesforce enregistrés dans le paramètre de fonctionnalité (par exemple, si la valeur du paramètre CustomLeadSourceField est égale à "LeadSource__c", nous avons besoin d’un accès en LECTURE à ce champ).
    </td>
  </tr>
  <tr>
    <td>Dynamics </td>
    <td>Données système B2B</td>
    <td>Marketo Measure effectue le suivi :
    <p>
    <li>Compte
<li>ActivityParty
<li>ActivityPointer
<li>Campagne
<li>CampaignItem (CampaignList dans notre système)
<li>CampaignResponse (CampaignMember dans notre système)
<li>Contact
<li>Prospect
<li>Liste (MarketingList dans notre système)
<li>ListMember (MarketingListMember dans notre système)
<li>Opportunité
<li>Organisation
<li>TransactionCurrency (CurrencyConversionRange et CurrencyStatus dans notre système)
<li>Rendez-vous, CampaignActivity, Email, Fax, IncidentResolution, Lettre, PhoneCall, RecurringNommentMaster, ServiceRendez-vous, Tâche
<li>bizible2_bizible_abtest
<li>bizible2_bizible_attribution_point_de_contact
<li>bizible2_bizible_event
<li>bizible2_bizible_history
<li>bizible2_bizible_touchpoint
<p>
Les points de contact créés et d’autres données sont écrits dans des champs bizibles personnalisés sur Compte, Campaign, CampaignResponse, Contact, Lead, List, Opportunity et PhoneCall.</td>
    <td><b>Autorisations utilisateur Marketo Measure</b>
<p>
Nous vous recommandons de créer un utilisateur Marketo Measure dédié dans Dynamics afin que nous puissions exporter et importer des données via afin d’éviter tout problème avec d’autres utilisateurs de votre CRM. Prenez note du nom d’utilisateur et du mot de passe, ainsi que de l’URL du point de terminaison, qui sera utilisé lors de la création du compte Marketo Measure.
<p>
<b>Rôles de sécurité</b>
<p>
Si votre organisation utilise les rôles de sécurité Dynamics, veillez à ce que l’utilisateur connecté ou l’utilisateur Marketo Measure dédié dispose des autorisations de lecture/écriture suffisantes pour les entités requises.
<br>
Les rôles de sécurité se trouvent ici : Paramètres &gt; Sécurité &gt; Rôles de sécurité
<br>
Pour les entités personnalisées Marketo Measure, nous aurons besoin d’autorisations complètes sur l’ensemble de nos entités.
<p>
<b>Autorisations de champ Dynamics Standard</b>
<br>
<a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Schéma Marketo Measure Dynamics</a>
<p>
<b>Autorisations de champ personnalisé Dynamics</b>
<br>
Nous avons besoin d’un accès en LECTURE pour tout champ de l’entité de piste ou de contact que le client souhaite utiliser pour les règles personnalisées Supprimer/Supprimer les paramètres de point de contact .
<br>
Nous avons besoin d’un accès en LECTURE pour tout champ de l’entité de piste ou d’opportunité que le client souhaite utiliser pour les règles de segment ou le mappage d’évaluation.
<br>
Nous avons besoin d’un accès en LECTURE pour tout champ de Campaign, CampaignResponse et les entités de liste que le client souhaite utiliser pour synchroniser les membres de Campaign/MarketingList.
</td>
  </tr>
  <tr>
    <td>Facebook</td>
    <td>Données de la plateforme publicitaire</td>
    <td>Nous nous intégrons à Facebook pour :
<p>
<li>Importation des données de publicités client</li>
<li>Importation des données de coût des publicités client</li>
<li>Mise à jour des publicités du client en ajoutant des paramètres d’URL</li>
<p>
Marketo Measure effectue le suivi des comptes, campagnes, groupes publicitaires, publicités, identifiants de filtre et URL.</td>
    <td><li>L’autorisation ads_management est nécessaire pour créer des campagnes, gérer des publicités ou récupérer des mesures publicitaires.</li>
<li>L’autorisation par courrier électronique est requise pour permettre aux utilisateurs de se connecter à leur adresse électronique Facebook.</li>
<p>
<b>Portées</b>
<p>
<a href="https://developers.facebook.com/docs/permissions/reference/ads_management/">ads_management</a>
<br>
<li>Créez des campagnes, gérez des publicités et récupérez des mesures par programmation.</li>
<li>Créez des outils de gestion des publicités qui offrent des solutions innovantes et une valeur différenciée aux annonceurs.</li>
<p>
<a href="https://developers.facebook.com/docs/permissions/reference/email">email</a>
<br>
<li>Communiquer avec les personnes et leur permettre de se connecter à votre application avec l’adresse électronique associée à leur profil Facebook.</li></td>
  </tr>
  <tr>
    <td>LinkedIn</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DoubleClick</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>AdWords</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bing</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Marketo Engage</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Analytics</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bizible Javascript</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
