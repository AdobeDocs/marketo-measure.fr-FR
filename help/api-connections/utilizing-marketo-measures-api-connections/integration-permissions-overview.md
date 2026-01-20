---
description: Présentation des autorisations d’intégration - [!DNL Marketo Measure]
title: Vue d’ensemble des autorisations d’intégration
feature: APIs, Integration
exl-id: c45598fe-0c33-459a-9fde-de7f6906bd0c
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 3%

---

# Vue d’ensemble des autorisations d’intégration {#integration-permissions-overview}

Ce guide décrit les autorisations nécessaires à une intégration transparente à Marketo Measure, en s’assurant que chaque intégration fonctionne efficacement et sans problème.

<table>
<thead>
  <tr>
    <th style="width:10%">Intégration</th>
    <th style="width:25%">Type de données
    <li>Données d’interaction web</li>
    <li>Données du système B2B</li>
    <li>Données de plateforme publicitaire</li></th>
    <th style="width:25%">Ce que nous suivons</th>
    <th style="width:40%">Exigences d’autorisation</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>Données du système B2B    
</td>
    <td>Marketo Measure effectue le suivi de :
    <p>
    <li>Compte</li>
    <li>Campagne</li>
    <li>Membre de la campagne</li>
    <li>Contact</li>
    <li>CurrencyConversionRange</li>
    <li>CurrencyStatus</li>
    <li>Événements</li>
    <li>FieldHistory (lead, contact et opportunité)</li>
    <li>Prospect</li>
    <li>Opportunité</li>
    <li>OpportunityContactRole</li>
    <li>Historique de l’opportunité</li>
    <li>Tâches</li>
<p>
Les points de contact créés et d’autres données sont écrits dans des champs Bizible personnalisés sur le compte, la campagne, le membre de la campagne, le dossier, le contact, le lead et l’opportunité.</td>
    <td><b>Autorisations d'utilisateur connecté Salesforce (requises)</b>
    <p>
    <b>Jeu d'autorisations d'administrateur Marketo Measure pour un utilisateur dédié :</b> Autoriser l'administrateur SFDC à effectuer des opérations CRUD sur des objets de mesure marketo.
    <br>
    <b>Afficher et modifier le jeu d’autorisations des prospects convertis :</b> permet à Marketo Measure d’agrémenter les prospects une fois qu’ils ont été convertis en contacts.
    <br>
    <b>Case à cocher Utilisateur marketing Salesforce :</b> la case Utilisateur marketing permet aux utilisateurs de créer des campagnes et d’utiliser les assistants d’importation de campagnes.
    <br>
    <b>Utilisateur Marketo Measure Standard :</b> permet à un utilisateur de lire des enregistrements à partir d’objets Marketo Measure.
    <p>
    <b>Autorisations des champs standard de Salesforce</b>
    <br>
    <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Objets et accès standard de Salesforce</a>
    <p>
    <b>Autorisations des champs personnalisés Salesforce</b>
    <br>
    Nous fournissons des paramètres de fonctionnalité pour contenir les champs SalesForce personnalisés que les clients peuvent utiliser. Si ces paramètres de fonctionnalité sont définis, nous avons besoin d’un accès en lecture à chacun des champs Salesforce enregistrés dans le paramètre de fonctionnalité (par exemple, si la valeur du paramètre CustomLeadSourceField est égale à « LeadSource__c », nous avons besoin d’un accès en lecture à ce champ).
    </td>
  </tr>
  <tr>
    <td>Dynamics </td>
    <td>Données du système B2B</td>
    <td>Marketo Measure effectue le suivi de :
    <p>
    <li>Compte
<li>ActivityParty
<li>ActivityPointer
<li>Campagne
<li>CampaignItem (CampaignList dans notre système)
<li>CampaignResponse (Membre de la campagne dans notre système)
<li>Contact
<li>Lead
<li>Liste (MarketingList dans notre système)
<li>ListMember (MarketingListMember dans notre système)
<li>Opportunité
<li>Organisation
<li>TransactionCurrency (CurrencyConversionRange et CurrencyStatus dans notre système)
<li>Rendez-vous, CampaignActivity, E-mail, Fax, Résolution d'incident, Lettre, Appel téléphonique, RécurrentAppointmentMaster, ServiceAppointment, Tâche
<li>bizible2_bizible_abtest
<li>bizible2_bizible_attribution_touchpoint
<li>bizible2_bizible_event
<li>bizible2_bizible_history
<li>bizible2_bizible_touchpoint
<p>
Les points de contact créés et d’autres données sont écrits dans des champs Bizible personnalisés sur Compte, Campagne, Réponse de campagne, Contact, Lead, Liste, Opportunité et Appel téléphonique</td>
    <td><b>Autorisations utilisateur Marketo Measure</b>
<br>
Nous vous recommandons de créer un utilisateur Marketo Measure dédié dans Dynamics pour que nous puissions exporter et importer des données par le biais de afin d’éviter tout problème avec d’autres utilisateurs dans votre CRM. Notez le nom d’utilisateur et le mot de passe, ainsi que l’URL du point d’entrée, car ils seront utilisés lors de la création du compte Marketo Measure.
<p>
<b> Rôles de sécurité </b>
<br>
Si votre organisation utilise des rôles de sécurité Dynamics, assurez-vous que l’utilisateur connecté ou l’utilisateur Marketo Measure dédié dispose d’autorisations suffisantes en lecture/écriture sur les entités requises.
<br>
Pour accéder aux rôles de sécurité, sélectionnez Paramètres &gt; Sécurité &gt; Rôles de sécurité .
<br>
Pour les entités personnalisées de Marketo Measure, nous aurons besoin d’autorisations complètes sur toutes nos entités.
<p>
<b>Autorisations des champs standard de Dynamics</b>
<br>
<a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Schéma Marketo Measure Dynamics</a>
<p>
<b>Autorisations des champs personnalisés Dynamics</b>
<br>
Nous avons besoin d’un accès en LECTURE pour tout champ de l’entité de prospect ou de contact que le client souhaite utiliser pour les règles personnalisées de suppression/suppression des paramètres de point de contact.
<br>
Nous avons besoin d’un accès en LECTURE pour tout champ de l’entité Lead ou Opportunité que le client souhaite utiliser pour les règles de segmentation ou le mappage d’étape.
<br>
Nous avons besoin d’un accès en LECTURE pour tout champ des entités Campaign, CampaignResponse et List que le client souhaite utiliser pour synchroniser les membres de Campaign/MarketingList.
</td>
  </tr>
  <tr>
    <td>Facebook</td>
    <td>Données de plateforme publicitaire</td>
    <td>Nous intégrons à Facebook pour :
<p>
<li>Importer les données des publicités client</li>
<li>Importer les données de coût des publicités client</li>
<li>Mettre à jour les publicités du client en ajoutant des paramètres d’URL</li>
<p>
Marketo Measure effectue le suivi des comptes, des campagnes, des groupes publicitaires, des publicités, des identifiants de filtre et des URL.</td>
    <td><li>L’autorisation ads_management est requise pour créer des campagnes, gérer des annonces ou récupérer des mesures publicitaires.</li>
<li>L’autorisation par e-mail est requise pour permettre aux utilisateurs et utilisatrices de se connecter à leur e-mail Facebook.</li>
<p>
<b>Portées</b>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/ads_management/">ads_management</a>
<br>
<li>Créez des campagnes par programmation, gérez des annonces et récupérez des mesures.</li>
<li>Créer des outils de gestion des publicités qui offrent des solutions innovantes et une valeur différenciée aux annonceurs.</li>
<br>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/email">email</a>
<br>
<li>Communiquer avec les personnes et leur permettre de se connecter à votre application avec l’adresse e-mail associée à leur profil Facebook.</li></td>
  </tr>
  <tr>
    <td>LinkedIn</td>
    <td>Données de plateforme publicitaire
    <p>
    Données du système B2B (données de formulaire de génération de leads, y compris les formulaires et les envois, qui ont été classés comme activité CRM).</td>
    <td>Marketo Measure effectue le suivi des campagnes LinkedIn Ads, des contenus publicitaires, des données sur les coûts, ainsi que des Forms et réponses de génération de leads. Sur la base des données importées, nous pouvons générer des points de contact LinkedIn et associer des réponses de formulaire de prospect aux prospects pour les clients.</td>
    <td><li>Le rôle de gestionnaire de campagne ou de gestionnaire de compte est requis pour que Marketo Measure télécharge les données de coût. (Portée ligne 1)</li>
    <br>
    <li>Super administrateur (rôle d’administrateur de page, étendue 2) ou gestionnaire Forms de génération de leads (rôle d’administrateur de médias payants, étendue 3) est requis pour que Marketo Measure accède aux données de formulaires de génération de leads</li>
    <br>
    <li>Un super administrateur (rôle d’administrateur de page, étendue 2) ou une affiche de contenu sponsorisé (rôle d’administrateur de médias payants, étendue 3) est nécessaire pour que Marketo Measure puisse manipuler le balisage automatique</li>
    <p>
    <b>Portées</b>
    <br>
    <a href="https://www.linkedin.com/campaignmanager/accounts">Configuration du rôle d'utilisateur dans le portail (nécessite une connexion au compte LinkedIn)</a> - <a href="https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager">Présentation des rôles d'utilisateur</a> : rôle d'utilisateur, affichage et gestion des autorisations d'utilisateur, affectation de rôles tels que gestionnaire de compte ou responsable de campagne
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Configurer le rôle d’administrateur de page - <a href="https://www.linkedin.com/help/linkedin/answer/a541981/linkedin-page-admin-roles-overview">Définitions de rôle d’administrateur de page</a> : rôle d’administrateur de page, sur la page d’administration souhaitée
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Configuration du rôle d’administrateur de médias payants (recherchez « Paid Media Admin ») - <a href="https://www.linkedin.com/help/linkedin/answer/a554540">Définitions d’administrateur de médias payants</a> : rôles d’administrateur de médias payants</td>
  </tr>
  <tr>
    <td>DoubleClick</td>
    <td>Données de plateforme publicitaire</td>
    <td>Marketo Measure effectue le suivi des comptes, des annonceurs, des campagnes, des pages de destination (personnalisées), des publicités, des contenus publicitaires, des emplacements et des sites.</td>
    <td><li>L’adresse e-mail principale du compte Google de l’utilisateur est requise.</li>
<li>Autorisations Campaign Manager requises pour accéder au compte Campaign Manager 360</li>
<ul>
<li>Afficher et gérer les rapports DoubleClick Advertisers</li>
<li>Afficher et gérer les campagnes publicitaires des gestionnaires de campagnes DoubleClick</li>
<p>
    <b>Portées</b>
    <br>
    <a href="https://www.googleapis.com/auth/userinfo.email">https://www.googleapis.com/auth/userinfo.email</a> : consultez l’adresse e-mail principale de votre compte Google.
    <p>
     <a href="https://www.googleapis.com/auth/dfareporting">https://www.googleapis.com/auth/dfareporting</a> : Afficher et gérer les rapports DoubleClick for Advertisers
    <p>
     <a href="https://www.googleapis.com/auth/dfatrafficking">https://www.googleapis.com/auth/dfatrafficking</a> : affichez et gérez vos campagnes publicitaires Display DoubleClick Campaign Manager (DCM)</td>
  </tr>
  <tr>
    <td>AdWords</td>
    <td>Données de plateforme publicitaire</td>
    <td>Nous intégrons à AdWords pour :
<p>
<li>Importer les données des publicités client</li>
<li>Importer les données de coût des publicités client</li>
<li>Mettre à jour les publicités du client en ajoutant des paramètres d’URL/mettant à jour les modèles de suivi d’URL</li>
<p>
Marketo Measure effectue le suivi des campagnes, des groupes publicitaires, des contenus publicitaires, des liens de site et des mots-clés.</td>
    <td><li>L’adresse e-mail principale du compte Google de l’utilisateur est requise.</li>
<p>
    <b>Portées</b>
    <br>
    <a href="https://www.googleapis.com/auth/userinfo.email">https://www.googleapis.com/auth/userinfo.email</a> : consultez l’adresse e-mail principale de votre compte Google.</td>
  </tr>
  <tr>
    <td>Bing</td>
    <td>Données de plateforme publicitaire</td>
    <td>Marketo Measure effectue le suivi des comptes, campagnes, groupes publicitaires, contenus publicitaires et mots-clés.</td>
    <td><li>L’utilisateur doit accorder un « accès hors ligne » via son compte Microsoft (qui accorde à Marketo Measure l’accès aux UserInfo de l’utilisateur final même s’il n’est pas connecté). Voir la page de Microsoft <a href="https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access"></a> pour savoir comment procéder.</li>
<p>
    <b>Portées</b>
    <br>
    <a href="https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access">https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access</a> : conservez l’accès aux données pour lesquelles vous avez autorisé l’accès.</td>
  </tr>
  <tr>
    <td>Marketo Engage</td>
    <td>Données du système B2B</td>
    <td>L’intégration de Marketo permet à Marketo Measure de collecter les activités, les personnes, les programmes et les appartenances aux programmes Marketo. En outre, Marketo Measure effectue le suivi des cookies Marketo (identifiants Munchkin) à des fins de liaison des activités web Marketo aux points de contact du prospect Marketo Measure, <a href="/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#cookie-mapping">comme décrit ici</a> :
    <p>
    <i>Suite à l’intégration de Marketo Measure à Marketo, l’ID de cookie Marketo Measure est désormais également mappé et synchronisé avec l’ID de Munchkin Marketo. Cela permet de combler l’écart afin d’attribuer le premier contact anonyme à une session web plutôt que d’attribuer les contacts FT et LC à une activité Marketo.</i>
    </td>
    <td>Le client doit créer un utilisateur d’API Marketo Engage dédié et fournir les informations d’identification à Marketo Measure. Aucune configuration d’autorisation supplémentaire n’est requise. <a href="/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/set-up-marketo-connection.md#configuring-the-integration">En savoir plus</a>.</td>
  </tr>
  <tr>
    <td>Adobe Analytics</td>
    <td>Données du système B2B</td>
    <td>L’intégration des attributs du client B2B permet aux utilisateurs mutuels de Marketo Measure et d’Adobe Analytics d’enrichir leurs profils utilisateur Adobe Analytics avec des métadonnées précieuses dérivées du moteur d’attribution de Marketo Measure et grâce à sa fonctionnalité de synchronisation avec les systèmes de gestion de la relation client (Microsoft Dynamics et Salesforce). <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">En savoir plus</a>.</td>
    <td>Le client doit fournir à Marketo Measure un ID d’alias et des informations d’identification de serveur FTP à un emplacement où les données seront chargées vers son instance Analytics.
    <p>
    Notez les informations suivantes, car vous en aurez besoin pour certaines des étapes suivantes du processus :
    <p>
    <li>L’ID d’alias, qui peut être n’importe quelle valeur que vous souhaitez. Nous vous recommandons d’utiliser « marketomeasure_id »</li>
    <li>Nom d’hôte et informations d’identification du serveur FTP (nom d’utilisateur et mot de passe)</li>
    <p>
    <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md#configuring-the-integration">En savoir plus</a></td>
  </tr>
  <tr>
    <td>Javascript Bizible</td>
    <td></td>
    <td><a href="/help/marketo-measure-tracking/setting-up-tracking/data-collected-by-javascript.md">Quelles données bizible.js collecte-t-il </a>.</td>
    <td></td>
  </tr>
</tbody>
</table>

>[!MORELIKETHIS]
>
>[Notifications d’erreur](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
