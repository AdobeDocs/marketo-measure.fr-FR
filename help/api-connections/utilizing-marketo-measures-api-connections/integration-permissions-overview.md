---
description: Présentation des autorisations d’intégration - [!DNL Marketo Measure] - Documentation du produit
title: Vue d’ensemble des autorisations d’intégration
hide: true
hidefromtoc: true
feature: APIs, Integration
source-git-commit: 3d4ee7c71ed241c8e3885b4db57168f753dcdf65
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 3%

---

# Vue d’ensemble des autorisations d’intégration {#integration-permissions-overview}

Ce guide décrit les autorisations nécessaires à une intégration transparente avec Marketo Measure, afin de garantir un fonctionnement efficace et sans problème de chaque intégration.

<table>
<thead>
  <tr>
    <th style="width:10%">Intégration</th>
    <th style="width:25%">Type de données
    <li>Données d’interaction web</li>
    <li>Données système B2B</li>
    <li>Données de la plateforme publicitaire</li></th>
    <th style="width:25%">Ce que nous suivons</th>
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
    <li>Lead</li>
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
    <br>
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
<li>Lead
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
<br>
Nous vous recommandons de créer un utilisateur Marketo Measure dédié dans Dynamics afin que nous puissions exporter et importer des données via afin d’éviter tout problème avec d’autres utilisateurs de votre CRM. Prenez note du nom d’utilisateur et du mot de passe, ainsi que de l’URL du point de terminaison, qui sera utilisé lors de la création du compte Marketo Measure.
<p>
<b>Rôles de sécurité</b>
<br>
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
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/ads_management/">ads_management</a>
<br>
<li>Créez des campagnes, gérez des publicités et récupérez des mesures par programmation.</li>
<li>Créez des outils de gestion des publicités qui offrent des solutions innovantes et une valeur différenciée aux annonceurs.</li>
<br>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/email">email</a>
<br>
<li>Communiquer avec les personnes et leur permettre de se connecter à votre application avec l’adresse électronique associée à leur profil Facebook.</li></td>
  </tr>
  <tr>
    <td>LinkedIn</td>
    <td>Données de la plateforme publicitaire
    <p>
    Données système B2B (données de formulaire de génération de piste, y compris les formulaires et les envois, qui sont classés comme activité CRM).</td>
    <td>Marketo Measure effectue le suivi des campagnes LinkedIn Ads, des créatifs et des données de coûts, ainsi que des Forms et réponses de Lead Gen. En fonction des données importées, nous pouvons générer des points de contact LinkedIn et associer des réponses de formulaire de piste aux pistes pour les clients.</td>
    <td><li>Le rôle de gestionnaire de campagne ou de gestionnaire de compte est requis pour que Marketo Measure télécharge les données de coût. (Ligne de portée 1)</li>
    <br>
    <li>Un super administrateur (rôle d’administrateur de page, portée 2) ou un gestionnaire Forms de prospect (rôle d’administrateur de média payant, portée 3) est nécessaire pour que Marketo Measure accède aux données de formulaires de génération de piste</li>
    <br>
    <li>Un super administrateur (rôle d’administrateur de page, portée 2) ou une affiche de contenu sponsorisé (rôle d’administrateur de médias payants, portée 3) est requis pour que Marketo Measure puisse manipuler le balisage automatique.</li>
    <p>
    <b>Portées</b>
    <br>
    <a href="https://www.linkedin.com/campaignmanager/accounts">Configuration d’un rôle utilisateur dans le portail (nécessite une connexion au compte LinkedIn)</a> - <a href="https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager">Présentation des rôles utilisateur</a>: rôle de l’utilisateur, affichage et gestion des autorisations utilisateur, affectation de rôles tels que gestionnaire de compte ou responsable de campagne
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Configuration du rôle d’administrateur de page - <a href="https://www.linkedin.com/help/linkedin/answer/a541981/linkedin-page-admin-roles-overview">Définitions de rôle d’administrateur de page</a>: rôle d’administrateur de page, sur la page d’administration souhaitée.
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Configuration du rôle d’administrateur des médias payants (recherchez l’administrateur des médias payants) - <a href="https://www.linkedin.com/help/linkedin/answer/a554540">Définitions d’administrateur des médias payants</a>: rôles d’administrateur des médias payants</td>
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
