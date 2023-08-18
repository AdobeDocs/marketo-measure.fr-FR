---
description: Tableau de bord du ROI - [!DNL Marketo Measure] - Produit
title: Tableau de bord du retour sur investissement
feature: Reporting
source-git-commit: 436e30c2a4138d780232d6ba9e64456d6277ac9b
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 18%

---

# Tableau de bord du retour sur investissement {#roi-dashboard}

Le tableau de bord du ROI offre aux marketeurs une vue granulaire des retours sur investissement sur les canaux, sous-canaux et campagnes. Il ventile méticuleusement les schémas de coûts et de recettes, tout en mettant en avant des mesures telles que le coût par prospect, l’offre et les opportunités, afin d’assurer une compréhension complète de l’attribution marketing.

Questions sur le panorama :

* Quelles étaient les valeurs de ROI pour chaque canal, sous-canal et campagne ?
* Comment les coûts et les revenus ont-ils été répartis sur chaque canal, sous-canal et campagne ?
* Quel était le coût par piste, le coût par transaction et le coût par opportunité ?

<table style="table-layout:auto"> 
<tbody>
 <tr> 
   <th>Composant</th> 
   <th>Description</th>
   <th>Type de date</th>
   <th>Champs d’exploration</th>
   <th>Filtres</th>
  </tr>
  <tr>
    <td>Mosaïque Coût</td>
    <td>Coût total</td>
    <td>Date d’entrée du coût</td>
    <td><li>ID de Campagne</li>
<li>Nom de campagne</li>
<li>Canal</li>
<li>Sous-canal</li>
<li>Date</li>
<li>Dépenses</li></td>
    <td rowspan="15"><li>Date</li>
<li>Modèle d’attribution (paramètre)</li>
<li>Canal</li>
<li>Sous-canal</li>
<li>Campagne</li></td>
  </tr>
  <tr>
    <td>Mosaïque Recettes affectées</td>
    <td>Chiffre d’affaires total attribué</td>
    <td>Jour complet</td>
    <td><li>ID de l’opportunité</li>
<li>Nom de l'opportunité</li>
<li>Date de création d'opportunité</li>
<li>Date de fermeture de l'opportunité</li>
<li>Est fermé (O/N)</li>
<li>Est gagnant (O/N)</li>
<li>Modèle d’attribution</li>
<li>Revenu attribué</li>
<li>Recettes réalisées</li></td>
  </tr>
  <tr>
    <td>Mosaïque ROI simple</td>
    <td>RSI hérité : recettes divisées par les coûts sur une période donnée. 
    <li>Coût : coût engendré dans la période filtrée.</li>
    <li>Recettes : Recettes provenant des opportunités de "victoire close" au cours de cette période.</li></td>
    <td>Jour complet</td>
    <td>S/O</td>
  </tr>
  <tr>
    <td>Mosaïque ROI réalisée</td>
    <td>ROI réalisé : représente les résultats tangibles des points de contact générés par les campagnes au cours d’une période donnée.
    <li>Coût : coût engendré dans la période filtrée.</li>
    <li>Chiffre d’affaires : chiffre d’affaires réalisé à partir de tous les contrats "Closed Won", en particulier ceux qui dépendent de points de contact dans le délai imparti.</li>
    <br/><img src="assets/roi-dashboard-1.png" width="600"></td>
    <td>Date d’entrée du coût</td>
    <td>S/O</td>
  </tr>
  <tr>
    <td>Mosaïque Total des nouvelles pistes</td>
    <td>Nombre total de nouvelles pistes (nombre entier) générées au cours d’une période donnée, y compris les pistes touchées et non touchées.</td>
    <td>Date créée</td>
    <td rowspan="2">
    <li>ID du lead</li>
    <li>E-mail du lead</li>
    <li>Date LC</li></td>
  </tr>
  <tr>
    <td>Mosaïque Coût par nouveau prospect</td>
    <td>Nombre total de nouvelles pistes (nombre entier) divisé par les coûts.</td>
    <td>Date créée</td>
  </tr>
  <tr>
    <td>Mosaïque Total nouvelles opportunités</td>
    <td>Nombre total de nouvelles opportunités (nombre entier) générées au cours d’une période donnée, y compris les pistes touchées et non touchées.</td>
    <td>Date créée</td>
    <td rowspan="2">
    <li>ID de l’opportunité</li>
    <li>Nom de l'opportunité</li>
    <li>Date de création d'opportunité</li>
    <li>Date de fermeture de l'opportunité</li>
    <li>Est fermé (O/N)</li>
    <li>Est gagnant (O/N)</li>
    <li>Étape actuelle</li></td>
  </tr>
  <tr>
    <td>Mosaïque Coût par nouvelle opportunité</td>
    <td>Nombre total de nouvelles opportunités (nombre entier) divisé par les coûts.</td>
    <td>Date créée</td>
  </tr>
  <tr>
    <td>Mosaïque Total des affaires</td>
    <td>Nombre total d’offres clôturées au cours d’une période spécifiée, y compris celles qui n’ont pas de points de contact associés.</td>
    <td>Jour complet</td>
    <td><li>ID de l’opportunité</li>
<li>Nom de l'opportunité</li>
<li>Date de création d'opportunité</li>
<li>Date de fermeture de l'opportunité</li>
<li>Est fermé (O/N)</li>
<li>Est gagnant (O/N)</li>
<li>Étape actuelle</li>
<li>Devise</li>
<li>Modèle d’attribution</li>
<li>Revenu attribué</li>
<li>Recettes réalisées</li></td>
  </tr>
  <tr>
    <td>Coût et recettes par graphique de canal</td>
    <td>Graphique à barres illustrant à la fois les coûts et les recettes, conçu pour offrir une perspective comparative de leur ampleur par rapport à divers canaux, sous-canaux et campagnes.
    <br/><img src="assets/roi-dashboard-2.png" width="600"></td>
    <td>Jour complet</td>
    <td>Coût:
<br/>
<li>ID de Campagne</li>
<li>Nom de campagne</li>
<li>Canal</li>
<li>Sous-canal</li>
<li>Date d’entrée du coût</li>
<li>Devise</li>
<li>Dépenses</li>
<p>
Recettes:
<br/>
<li>ID de l’opportunité</li>
<li>Nom de l'opportunité</li>
<li>Date de création d'opportunité</li>
<li>Date de fermeture de l'opportunité</li>
<li>Est fermé (O/N)</li>
<li>Est gagnant (O/N)</li>
<li>Revenu attribué</li>
<li>Modèle d’attribution</li>
<li>Revenu attribué</li>
<li>Recettes réalisées</li></td>
  </tr>
  <tr>
    <td>RSI réel ou simple au fil du temps</td>
    <td>Graphique en courbes de série temporelle présentant la comparaison entre le retour sur investissement réel et simple, en suivant leur progression au fil du temps.
    <br/><img src="assets/roi-dashboard-3.png" width="600"></td>
    <td>ROI simple : date d’entrée et date de fermeture du coût
    <p>RSI réalisé : Date d’entrée en coût et Date de point de contact</td>
    <td>S/O</td>
  </tr>
  <tr>
    <td>Graphique du coût au fil du temps</td>
    <td>Graphique à barres empilées présentant les coûts totaux trimestriels/mensuels, segmentés par canaux individuels pour une ventilation détaillée.
    <br/><img src="assets/roi-dashboard-4.png" width="600"></td>
    <td>Date d’entrée du coût</td>
    <td rowspan="2"><li>ID de Campagne</li>
<li>Nom de campagne</li>
<li>Canal</li>
<li>Sous-canal</li>
<li>Date d’entrée du coût</li>
<li>Devise</li>
<li>Dépenses</li></td>
  </tr>
  <tr>
    <td>Coût par graphique de canal</td>
    <td>Graphique à barres affichant les dépenses marketing segmentées par canaux.
    <br/><img src="assets/roi-dashboard-5.png" width="600"></td>
    <td>Date d’entrée du coût</td>
  </tr>
  <tr>
    <td>Tableau récapitulatif du ROI</td>
    <td>Tableau présentant les recettes attribuées, les coûts et le retour sur investissement segmentés par canaux individuels pour une ventilation détaillée.
<p>
<b>Colonnes:</b>
<p>
<li>Canal/Subchannel/Campaign</li>
<li>Coût</li>
<li>Revenu attribué</li>
<li>ROI simple</li>
<li>ROI réalisé</li>
<li>Pipeline non réalisé</li>
<ul style="padding-left: 30px;"><li>Pipeline à partir des points de contact (opportunités ouvertes) associés aux campagnes dans une période donnée</li></ul></td>
    <td>ROI simple : date d’entrée et date de fermeture du coût
    <p>RSI réalisé : Date d’entrée en coût et Date de point de contact</td>
    <td>S/O</td>
  </tr>
  <tr>
    <td>Tableau des dépenses marketing</td>
    <td>Tableau présentant les coûts, les nouveaux prospects, les opportunités et les offres clôturées par des canaux individuels pour une ventilation détaillée.
<p>
<b>Colonnes:</b>
<p>
<li>Canal/Subchannel/Campaign</li>
<li>Coût</li>
<li>Nouveaux leads</li>
<li>Coût par nouvelle piste</li>
<li>Nouvelles opportunités</li>
<li>Coût par nouvelle opportunité</li>
<li>Offres fermées</li>
<li>Coût par opération clôturée</li></td>
    <td><li>Coût : date d'encaissement</li>
<li>Nouvelles pistes : date de création</li>
<li>Nouvelles opportunités : date de création</li>
<li>Offres fermées : Date de fermeture</li></td>
    <td>S/O</td>
  </tr>
</tbody>
</table>

>[!MORELIKETHIS]
>
>[Découvrir les bases d’un tableau de bord](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
