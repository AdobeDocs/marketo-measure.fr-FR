---
description: Explication des positions et de la génération des points de contact sur BT et BAT - [!DNL Marketo Measure]
title: Explication des positions et de la génération de points de contact entre les BT et les  [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
feature: Touchpoints
source-git-commit: cd5597a681f388a5b5c743dadd38bf3127811bff
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 3%

---

# Explication des positions et de la génération des points de contact sur BT et [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Génération de positions de points de contact et flux via le Parcours des acheteurs**

Pour réussir à créer des rapports avec des données [!DNL Marketo Measure], il est essentiel de connaître les positions de Buyer Touchpoint et la manière dont elles sont déclenchées. Vous voulez avoir une bonne compréhension de ce que vos prospects ont fait lorsqu&#39;ils ont traversé le parcours de l&#39;acheteur et à son tour de ce que cela ressemblera dans les données de points de contact. Pour plus d’informations sur cette rubrique, nous vous recommandons de consulter l’article [[!UICONTROL Génération et mappage de points de contact]](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-generation-and-mapping.md) .

[!DNL Marketo Measure] possède une variété de positions de points de contact qui sont déclenchées par diverses étapes dans le parcours de l’acheteur. Lors de la création de rapports sur les données [!DNL Marketo Measure], il existe deux ensembles de données de point de contact, Points de contact d’achat (BT) et Points de contact d’attribution d’achat (BAT). Vous remarquerez peut-être que ces jeux de données ont des positions légèrement différentes en ce qui concerne différents objets. Pour plus d’informations sur cette rubrique, nous vous recommandons de consulter l’article [Différence entre les points de contact d’achat (BT) et les points de contact d’attribution d’achat (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md) .

**Points de contact de l’utilisateur (BT)** : il s’agit des points de contact associés à une personne et à son parcours. Ils seront propres à cette personne. Les rapports prêts à l’emploi suivants sont construits à partir de données Buyer Touchpoint.

* [!DNL Marketo Measure] 101 : Passe Par Identifiant
* [!DNL Marketo Measure] 101 : Pistes Par Canal
* [!DNL Marketo Measure] 101 : Prospérité/Contact par identifiant
* [!DNL Marketo Measure] 101 : Piste/Contact par canal

Le tableau suivant présente les positions de Buyer Touchpoint qui décrivent où se trouve un individu dans son parcours et les actions qu’il a entreprises pour obtenir ce poste.

<table> 
 <tbody>
  <tr>
   <th>Position de Buyer Touchpoint (BT)</th> 
   <th>Type de point de contact (action pouvant déclencher un point de contact)</th> 
   <th>Description du point de contact</th> 
  </tr>
  <tr>
   <td>Premier contact (FT pour « First Touch »)</td> 
   <td>Visite Web</td> 
   <td>Première interaction marketing qu’un individu a avec votre marque</td> 
  </tr>
  <tr>
   <td>Création de prospects (LC pour « Lead Creation »)</td> 
   <td>Form Fill <strong>OR</strong> Inclusion de campagne/programme</td> 
   <td>Le premier formulaire remplit une personne (généralement un envoi de formulaire, mais peut également être une inclusion de campagne/programme).</td> 
  </tr>
  <tr>
   <td>Post LC</td> 
   <td>Form Fill <strong>OR</strong> Inclusion de campagne/programme</td> 
   <td>Tout formulaire qu’un individu a rempli après son LC (ou une inclusion Campaign/Program ultérieure)</td> 
  </tr>
 </tbody>
</table>

**Points de contact d’attribution de l’achat (BAT)** : il s’agit des points de contact associés à une opportunité et à son parcours. Ces points de contact sont liés aux recettes, car ils sont connectés à l’opportunité et à ses contacts. Les rapports prêts à l’emploi suivants sont construits à partir de données Buyer Attribution Touchpoint.

* [!DNL Marketo Measure] 101 : Opportunités par identifiant
* [!DNL Marketo Measure] 101 : Opportunités Par Canal D’Identifiant

<table> 
 <tbody>
  <tr>
   <th>Position de Buyer Attribution Touchpoint (BAT)</th> 
   <th>Type de point de contact (action pouvant déclencher un point de contact)</th> 
   <th>Description du point de contact</th> 
  </tr>
  <tr>
   <td>Premier contact (FT pour « First Touch »)</td> 
   <td>Visite Web</td> 
   <td>Première interaction marketing qu’un contact a eue avec votre marque</td> 
  </tr>
  <tr>
   <td>Création de prospects (LC pour « Lead Creation »)</td> 
   <td>Form Fill <strong>OR</strong> Inclusion de campagne/programme</td> 
   <td>Le premier formulaire rempli par un contact (généralement un envoi de formulaire, mais peut également être une inclusion de campagne/programme)</td> 
  </tr>
  <tr>
   <td>Création d’opportunités</td> 
   <td>Renseignez Le Formulaire <strong>OU</strong> Visite Web <strong>OU</strong> Inclusion De Campagne/Programme</td> 
   <td>Interaction marketing la plus proche du moment de création de l’Opp</td> 
  </tr> 
  <tr>
   <td>Perte/gain fermé</td> 
   <td>Renseignez Le Formulaire <strong>OU</strong> Visite Web <strong>OU</strong> Inclusion De Campagne/Programme</td> 
   <td>Interaction marketing la plus proche du moment où l’Opp est fermée (Gagnant ou perdu)</td> 
  </tr>
  <tr>
   <td>Contacts intermédiaires</td> 
   <td>Form Fill <strong>OR</strong> Inclusion de campagne/programme</td> 
   <td>Lorsqu’un contact remplit un formulaire en ligne et qu’il ne correspond pas au point de contact de jalon</td> 
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] possède ces deux ensembles de données de points de contact pour créer une compréhension claire de l’parcours d’une personne et des opportunités. Ces deux jeux de données de points de contact vous donnent une carte claire de ce qui s’est passé du haut de l’entonnoir au bas de l’entonnoir.

L’exemple suivant illustre le flux de données entre les points de contact d’achat (BT) et les points de contact d’attribution d’achat (BAT). Dans cet exemple, la personne A et la personne B font toutes deux partie de la même opportunité qui a une Date de création de 3/7/2020 et une Date de fermeture de 5/6/2020.

**Personne A** Jeu de données Buyer Touchpoint

* Première touche (FT) - Recherche payante.AdWords - 9/1/2019
* Création de piste (LC) - Recherche organique.Google - 11/20/2019
* Post LC (remplissage de formulaire) - Webinaire - 3/4/2020

**Personne B** Jeu de données Buyer Touchpoint

* Première touche (FT) - Social payant.Facebook - 8/26/2019
* Création de piste (LC) - Recherche organique.Yahoo - 2/20/2020
* Post LC (remplissage de formulaire) - Email - 5/1/2020

**Opportunités** Les données Buyer Attribution Touchpoint se liraient comme suit...

* Première touche (FT) - Social payant.Facebook - 8/26/2019
   * (de **la personne B**, car elle dispose de la _Première touche_ vraie pour le compte/l’option)
* Création de piste (LC) - Recherche organique.Google - 11/20/2019
   * (de la **personne A**, car elle possède la _création de piste_ vraie pour le compte/l’Opp)
* Création d’opportunités (OC) - Webinaire - 3/4/2020
   * (Le point de contact Post LC de la **Personne A** serait le point de contact _OC Touchpoint_, car il s’agit de l’interaction la plus récente que nous avons avec l’opportunité créée le 3/7/2020)
* Closed Won - Email - 5/1/2020
   * (Le point de contact Post LC de la **personne B** serait le point de contact _Won Won fermé_, car il s’agit de l’interaction la plus récente que nous avons avec l’opportunité fermée le 5/6/2020)
