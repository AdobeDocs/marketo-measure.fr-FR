---
description: Présentation des autorisations d’intégration - [!DNL Marketo Measure] - Documentation du produit
title: Présentation des autorisations d’intégration
hide: true
hidefromtoc: true
feature: APIs, Integration
source-git-commit: 1c3cd5ac9999550003765a9e1ed8d538224fe8a9
workflow-type: tm+mt
source-wordcount: '239'
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
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
