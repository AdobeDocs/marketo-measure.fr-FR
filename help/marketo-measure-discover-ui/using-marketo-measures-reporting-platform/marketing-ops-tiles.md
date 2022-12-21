---
unique-page-id: 34406495
description: Mosaïques des opérations marketing - [!DNL Marketo Measure] - Documentation du produit
title: Mosaïques des opérations marketing
exl-id: e7978a79-6f6e-4bfd-9962-b35b7d46a9ac
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 10%

---

# Mosaïques des opérations marketing {#marketing-ops-tiles}

Les opérations marketing vous permettent de valider et de diagnostiquer [!DNL Marketo Measure] données avec une visibilité complète sur les points de contact individuels par Leads, Contacts, Comptes, Campagnes et Opportunités.

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><br></td> 
   <td><p><strong>ID de compte</strong></p></td> 
   <td><p><strong>Nom du compte</strong></p></td> 
   <td><p><strong>Identifiant Opp</strong></p></td> 
   <td><p><strong>Nom Opp</strong></p></td> 
   <td><p><strong>ID de lead ou de contact</strong></p></td> 
   <td><p><strong>E-mail du lead ou du contact</strong></p></td> 
   <td><p><strong>ID de la campagne</strong></p></td> 
   <td><p><strong>Opportunité confirmée</strong></p></td> 
   <td><p><strong>Date de création de l’Opp</strong></p></td> 
   <td><p><strong>Date de fermeture d’Opp</strong></p></td> 
   <td><p><strong>Date du Touchpoint</strong></p></td> 
   <td><p><strong>Modèle d’attribution</strong></p></td> 
  </tr> 
  <tr> 
   <td><p><strong>Comptes</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Opportunité</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Contacts</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Prospects</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Campagnes</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
 </tbody> 
</table>

## Mosaïque Compte {#account-tile}

![](assets/one-1.png)

Affiche les données suivantes relatives au(x) compte(s) spécifié(s).

**Les comptes doivent comporter des données de point de contact (applicable uniquement si la fonctionnalité ABM est activée).**

-Identifiant de compte : Identifiant de compte dans le CRM

-Nom du compte : Nom du compte dans le CRM

Date de création : Date de création du compte dans le CRM

* Zoom avant : Voir Date de création par heure, minute, heure

-Site Web : Valeur trouvée dans le champ Site Web du compte

-Évaluation de l’engagement : Score d’engagement prédictif (PES) renseigné par [!DNL Marketo Measure]^1

-Opportunités : Nombre d’opportunités connectées au compte

* Zoom avant : Voir les détails de la ou des opportunités associées

-Contacts : Nombre de contacts répertoriés sur ce compte

* Zoom avant : Voir les détails des contacts associés.

-Leads : Nombre de pistes mappées à ce compte par mappage de pistes à des comptes^1

* Zoom avant : Afficher les détails des pistes qui ont été mappées au compte

-Points de contact d’attribution : Nombre de points de contact d’attribution de l’achat pour le compte

* Zoom avant : Reportez-vous aux détails du point de contact d’attribution de l’achat (ID, courrier électronique, date de point de contact, nom du compte, campagne, canal, sous-canal, type de contact marketing, modèle d’attribution).

-Points de contact : Nombre de points de contact que les contacts de ce compte ont^2

* Zoom avant : Voir Points de contact dans les détails du point de contact du compte (ID, E-mail, Date de point de contact, Nom du compte, Campagne, Canal, Sous-canal, Type de contact marketing).

>[!NOTE]
>
>Si vous disposez d’ABM, il affiche les points de contact associés aux pistes qui ont été mappées par le biais du mappage de pistes à comptes.

## Mosaïque Opportunité {#opportunity-tile}

![](assets/two-1.png)

Affiche les données suivantes liées aux opportunités spécifiées.

-Identifiant d’opportunité : Identifiant d’opportunité dans le CRM

-Nom de l’opportunité : Nom de l&#39;opportunité dans le CRM

-Nom du compte : Nom du compte associé à l’opportunité

Date de création : Date de création de l&#39;opportunité dans le CRM

Zoom avant : Voir Date de création par heure, minute, heure

Date de fermeture : Date de clôture de l&#39;opportunité dans le CRM

Zoom avant : Voir Date de fermeture par heure, minute, heure

-Amount : Montant total de l’opportunité

-Contacts : Nombre de contacts associés à l&#39;opportunité

Zoom avant : Voir les détails des contacts associés.

-Points de contact d’attribution : Nombre de points de contact d’attribution d’achat associés

Zoom avant : Reportez-vous aux détails du point de contact d’attribution de l’achat (ID, courrier électronique, date de point de contact, nom du compte, campagne, canal, sous-canal, type de contact marketing, modèle d’attribution).

## Mosaïque Contacts {#contacts-tile}

![](assets/three-1.png)

Affiche les données suivantes relatives au ou aux contacts spécifiés.

-Contact ID : Identifiant de contact dans le CRM

-Email: Adresse électronique de l’enregistrement de contact

Date de création : Date de création du contact dans le CRM

* Zoom avant : Voir Date de création par heure, minute, heure

-Nom du compte : Nom du compte associé au contact

-Points de contact d’attribution : Nombre de points de contact d’attribution de l’achat pour le contact

* Zoom avant : Reportez-vous aux détails du point de contact d’attribution de l’achat (ID, courrier électronique, date de point de contact, nom du compte, campagne, canal, sous-canal, type de contact marketing, modèle d’attribution).

-Points de contact : Nombre de points de contact d’achat pour le contact

* Zoom avant : Voir Contacts sur les détails du point de contact du compte (ID, E-mail, Date de point de contact, Nom du compte, Campagne, Canal, Sous-canal, Type de contact marketing).

## Mosaïque Leads {#leads-tile}

![](assets/four-1.png)

Affiche les données suivantes relatives aux pistes spécifiées.

-Identifiant de piste : Identifiant de piste dans le CRM

-Email: Adresse électronique de l’enregistrement de piste

Date de création : Lorsque le prospect a été créé dans le CRM

* Zoom avant : Voir Date de création par heure, minute, heure

- Société (à partir du prospect) : Entreprise répertoriée dans l’enregistrement dans le CRM renseigné par le client

-Nom du compte : Nom du compte [!DNL Marketo Measure] renseigne en fonction de notre mappage de piste vers compte.

-Points de contact : Nombre de points de contact associés au(x) prospect(s).

* Zoom avant : Voir Contacts sur les détails du point de contact du compte (ID, E-mail, Date de point de contact, Nom du compte, Campagne, Canal, Sous-canal, Type de contact marketing).

## Mosaïque Campagnes {#campaigns-tile}

![](assets/five-1.png)

Affiche les données suivantes relatives à la ou aux campagnes spécifiées.

-Identifiant de campagne : Identifiant de campagne dans le CRM

-Nom de la campagne : Nom de la campagne dans le CRM

- Dépense de campagne : Les dépenses [!DNL Marketo Measure] a été enregistré associé à la campagne

-Modèle d’attribution : L’attribution appropriée s’affiche alors en fonction du modèle sélectionné.

-Points de contact d’attribution : Nombre de points de contact d’attribution d’achat associés à la ou aux campagnes.

* Zoom avant : Reportez-vous aux détails du point de contact d’attribution de l’achat (ID, courrier électronique, date de point de contact, nom du compte, campagne, canal, sous-canal, type de contact marketing, modèle d’attribution).

-Points de contact : Le nombre de points de contact associés à la ou aux campagnes.

* Zoom avant : Voir Contacts sur les détails du point de contact du compte (ID, E-mail, Date de point de contact, Nom du compte, Campagne, Canal, Sous-canal, Type de contact marketing).
