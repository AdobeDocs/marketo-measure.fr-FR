---
unique-page-id: 35586105
description: Chemin de l’engagement - [!DNL Marketo Measure]
title: Parcours d’engagement
exl-id: 104d803f-9f40-4ab6-872d-6432f8c087e9
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 4%

---

# Parcours d’engagement {#engagement-path}

Chemin d’accès de l’engagement vous permet d’afficher une vue complète des engagements de prospect, de contact, de compte et d’opportunité à partir de la première touche jusqu’à la fin.

![](assets/one-2.png)

## Description du titre {#tile-description}

**Type d’événement :** Type de point de contact (Session, Campaign CRM, Événement CRM, Tâche CRM, Impression)

**Position du point de contact de l’utilisateur :** Position du point de contact du prospect/contact

**Position du point de contact de l’attribution de l’achat :** Position du point de contact d’attribution de l’achat de l’opportunité

**Date du point de contact :** Pour les sources en ligne : date et heure de l’engagement. Pour les événements hors ligne : date et heure définies dans la campagne Salesforce. Pour le point de contact des activités : champ de date du point de contact référencé dans la configuration des activités

**Email :** Adresse électronique associée à l’engagement

**Type de contact marketing :** Type d’engagement (Visite Web, Formulaire Web, Chat Web, CRM, Types d’activité)

**Canal :** Canal marketing qui a conduit l’engagement

**Moyen :** Moyen d’engagement

* Si l&#39;engagement provient d&#39;une plateforme connectée à une API (Adwords/BingAds), le CPC sera
* Si la page d’entrée de l’engagement contient utm_medium, nous allons analyser
* Si l&#39;engagement provient d&#39;une campagne CRM, le support provient du champ &quot;Type&quot; de la campagne CRM.

**Source Web :** Cette colonne affiche la source de l’engagement.

* Si l’engagement provient d’une plateforme connectée à une API, la source web affichera le nom de la plateforme publicitaire.
* Si le point de contact provient de la recherche organique, ce champ affiche le nom du moteur de recherche.
* Si elle n’est pas #1 ou #2 et que la valeur utm_source est présente dans l’URL de la page d’entrée pour le point de contact, cette valeur est affichée ici.
* Si vous ne trouvez pas #1 ou #2 et qu’aucune valeur utm_source n’est présente, le domaine racine de l’URL de référence s’affiche ici.
* Si aucune des options ci-dessus n’est affichée, Web direct ou Web

**Première interaction avec la personne :** Cette colonne affiche Oui ou Non si ce point de contact était la première interaction des individus.

**Recettes affectées :** Cette colonne affiche les recettes attribuées à ce point de contact en fonction du modèle d’attribution sélectionné.

## Description du filtre {#filter-description}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>Nom de filtre</th> 
   <th>Description</th> 
  </tr> 
  <tr> 
   <td><p>Nom/ID du compte</p></td> 
   <td><p>Permet l’utilisation de plusieurs valeurs en ajoutant des filtres par le signe plus "+" à droite. Plusieurs valeurs de filtre auront une relation "ou", ce qui signifie que la mosaïque affichera les résultats des deux valeurs de filtre. Si l’une des valeurs de filtre n’est pas valide, le tableau de bord ne produit pas de résultats pour la valeur non valide, mais continue à filtrer selon les valeurs de filtre valides. Non sensible à la casse.</p></td> 
  </tr> 
  <tr> 
   <td><p>Nom/ID de l’opportunité</p></td> 
   <td><p>Permet l’utilisation de plusieurs valeurs en ajoutant des filtres par le signe plus "+" à droite. Plusieurs valeurs de filtre auront une relation "ou", ce qui signifie que la mosaïque affichera les résultats des deux valeurs de filtre. Si l’une des valeurs de filtre n’est pas valide, le tableau de bord ne produit pas de résultats pour la valeur non valide, mais continue à filtrer selon les valeurs de filtre valides. Non sensible à la casse.</p></td> 
  </tr> 
  <tr> 
   <td><p>E-mail/ID du lead</p></td> 
   <td><p>Permet l’utilisation de plusieurs valeurs en ajoutant des filtres par le signe plus "+" à droite. Plusieurs valeurs de filtre auront une relation "ou", ce qui signifie que la mosaïque affichera les résultats des deux valeurs de filtre. Si l’une des valeurs de filtre n’est pas valide, le tableau de bord ne produit pas de résultats pour la valeur non valide, mais continue à filtrer selon les valeurs de filtre valides. Non sensible à la casse.</p></td> 
  </tr> 
  <tr> 
   <td><p>E-mail/ID du contact</p></td> 
   <td><p>Permet l’utilisation de plusieurs valeurs en ajoutant des filtres par le signe plus "+" à droite. Plusieurs valeurs de filtre auront une relation "ou", ce qui signifie que la mosaïque affichera les résultats des deux valeurs de filtre. Si l’une des valeurs de filtre n’est pas valide, le tableau de bord ne produit pas de résultats pour la valeur non valide, mais continue à filtrer selon les valeurs de filtre valides. Non sensible à la casse.</p><p>Nom/ID de compte, ID de piste/adresse électronique, ID de contact/filtre d’adresse électronique sont des relations "ou", ce qui signifie que si le filtre de piste et le filtre de contact ont une valeur, tous les enregistrements de l’un ou l’autre des ID s’afficheront.</p></td> 
  </tr> 
  <tr> 
   <td><p>Modèle d’attribution</p></td> 
   <td><p>Indiquez à quel modèle les recettes attribuées doivent être calculées. Valeurs autorisées : "Attribution de chemin complet", "Attribution Première touche", "Attribution de modèle personnalisé", "Attribution de création de piste", "Attribution en forme de U", "Attribution en forme de W".</p></td> 
  </tr> 
  <tr> 
   <td><p>Type d’événement</p></td> 
   <td><p>Filtrez le parcours par type d’événement sur lequel repose le point de contact de l’utilisateur. Permet l’utilisation de plusieurs valeurs en ajoutant des filtres par le signe plus "+" à droite. Valeurs autorisées : "Session", "Campagne CRM", "Événement CRM", "Tâche CRM", "Impression".</p></td> 
  </tr> 
  <tr> 
   <td><p>Étapes de lead</p></td> 
   <td><p>Filtrage du parcours par étape de piste sur laquelle repose le point de contact de l’utilisateur. Permet l’utilisation de plusieurs valeurs en ajoutant des filtres par le signe plus "+" à droite. Le filtre par défaut "est égal à" affiche des suggestions parmi lesquelles choisir, mais recommande d’utiliser "contient" comme critère de filtrage pour plusieurs filtres sur les scènes.</p></td> 
  </tr> 
  <tr> 
   <td><p>Étapes opportunité</p></td> 
   <td><p>Filtrez le parcours par étape d’opportunité sur laquelle repose le point de contact de l’utilisateur. Permet l’utilisation de plusieurs valeurs en ajoutant des filtres par le signe plus "+" à droite. Le filtre par défaut "est égal à" affiche des suggestions parmi lesquelles choisir, mais recommande d’utiliser "contient" comme critère de filtrage pour plusieurs filtres sur les scènes.</p></td> 
  </tr> 
  <tr> 
   <td><p>Date du Touchpoint</p></td> 
   <td><p>Filtrez le parcours par date/heure du point de contact.</p></td> 
  </tr> 
  <tr> 
   <td><p>E-mail de Touchpoint de l’utilisateur</p></td> 
   <td><p>Filtrez le parcours par courrier électronique sur le point de contact de l’utilisateur. Cela permet de filtrer les emails qui ne sont pas associés à un prospect/contact/compte.</p></td> 
  </tr> 
  <tr> 
   <td><p>Type de contact marketing</p></td> 
   <td><p>Filtrez le parcours par type de contact marketing.</p></td> 
  </tr> 
  <tr> 
   <td><p>Canal</p></td> 
   <td><p>Filtrez le parcours par canal.</p></td> 
  </tr> 
  <tr> 
   <td><p>Support</p></td> 
   <td><p>Filtrez le parcours par support.</p></td> 
  </tr> 
  <tr> 
   <td><p>Source Internet</p></td> 
   <td><p>Filtrage du parcours par source web.</p></td> 
  </tr> 
  <tr> 
   <td><p>Première interaction avec la personne</p></td> 
   <td><p>Filtrez le parcours par la colonne "Is First Touch" dans le tableau des points de contact utilisateur.</p></td> 
  </tr> 
  <tr> 
   <td><p>Revenu attribué</p></td> 
   <td><p>Filtrez le parcours par valeur de recettes attribuée.</p></td> 
  </tr> 
 </tbody> 
</table>
