---
description: Explication des positions et de la génération de points de contact entre les BT et les AT - [!DNL Marketo Measure]
title: Explication des positions et de la génération de points de contact entre les BT et les  [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
feature: Touchpoints
source-git-commit: cd5597a681f388a5b5c743dadd38bf3127811bff
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 3%

---

# Explication des positions et de la génération de points de contact entre les BT et [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Génération de positions de points de contact et flux via le Parcours des acheteurs**

Il est essentiel de comprendre les positions du point de contact de l’acheteur et la manière dont elles sont déclenchées pour réussir à créer des rapports avec [!DNL Marketo Measure] data. Vous voulez avoir une bonne compréhension de ce que vos prospects ont fait lorsqu&#39;ils ont traversé le parcours de l&#39;acheteur et à son tour de ce que cela ressemblera dans les données de points de contact. Pour plus d’informations sur ce sujet, nous vous recommandons de consulter la section [[!UICONTROL Génération et mappage des points de contact]](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-generation-and-mapping.md) article.

[!DNL Marketo Measure] dispose d’une variété de positions de points de contact qui sont déclenchées par diverses étapes du parcours de l’acheteur. Lors de la création de rapports sur [!DNL Marketo Measure] Il existe deux ensembles de données de point de contact, Points de contact d’achat (BAT) et Points de contact d’attribution d’achat (BAT). Vous remarquerez peut-être que ces jeux de données ont des positions légèrement différentes en ce qui concerne différents objets. Pour plus d’informations sur ce sujet, nous vous recommandons de consulter la section [Différence entre les points de contact d’achat et les points de contact d’attribution d’achat](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md) article.

**Points de contact d’achat (BT)**: il s’agit des points de contact associés à une personne et à son parcours et qui lui sont propres. Les rapports prêts à l’emploi suivants sont construits à partir des données du point de contact de l’acheteur.

* [!DNL Marketo Measure] 101 : Passe par ID
* [!DNL Marketo Measure] 101 : Pistes par canal
* [!DNL Marketo Measure] 101 : ID de prospect/contact
* [!DNL Marketo Measure] 101 : Piste/Contact par canal

Le tableau suivant présente les positions de point de contact de l’acheteur qui décrivent où se trouve une personne dans son parcours et les actions qu’elle a entreprises pour obtenir cette position.

<table> 
 <tbody>
  <tr>
   <th>Position du point de contact de l’acheteur</th> 
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
   <td>Form Fill <strong>OU</strong> Inclusion de campagne/programme</td> 
   <td>Le premier formulaire remplit une personne (généralement un envoi de formulaire, mais peut également être une inclusion de campagne/programme).</td> 
  </tr>
  <tr>
   <td>Post LC</td> 
   <td>Form Fill <strong>OU</strong> Inclusion de campagne/programme</td> 
   <td>Tout formulaire qu’un individu a rempli après son LC (ou une inclusion Campaign/Program ultérieure)</td> 
  </tr>
 </tbody>
</table>

**Points de contact d’attribution des acheteurs (BATS)**: points de contact associés à une opportunité et à son parcours. Ces points de contact sont liés aux recettes, car ils sont connectés à l’opportunité et à ses contacts. Les rapports prêts à l’emploi suivants sont construits à partir des données du point de contact d’attribution de l’achat.

* [!DNL Marketo Measure] 101 : Opportunités par ID
* [!DNL Marketo Measure] 101 : Opportunités par canal d’identification

<table> 
 <tbody>
  <tr>
   <th>Position du point de contact d’attribution de l’achat</th> 
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
   <td>Form Fill <strong>OU</strong> Inclusion de campagne/programme</td> 
   <td>Le premier formulaire rempli par un contact (généralement un envoi de formulaire, mais peut également être une inclusion de campagne/programme)</td> 
  </tr>
  <tr>
   <td>Création d’opportunités</td> 
   <td>Form Fill <strong>OU</strong> Visite web <strong>OU</strong> Inclusion de campagne/programme</td> 
   <td>Interaction marketing la plus proche du moment de création de l’Opp</td> 
  </tr> 
  <tr>
   <td>Perte/gain fermé</td> 
   <td>Form Fill <strong>OU</strong> Visite web <strong>OU</strong> Inclusion de campagne/programme</td> 
   <td>Interaction marketing la plus proche du moment où l’Opp est fermée (Gagnant ou perdu)</td> 
  </tr>
  <tr>
   <td>Contacts intermédiaires</td> 
   <td>Form Fill <strong>OU</strong> Inclusion de campagne/programme</td> 
   <td>Lorsqu’un contact remplit un formulaire en ligne et qu’il ne correspond pas au point de contact de jalon</td> 
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] dispose de ces deux ensembles de données de points de contact afin de créer une compréhension claire du parcours d’une personne et des opportunités. Ces deux jeux de données de points de contact vous donnent une carte claire de ce qui s’est passé du haut de l’entonnoir au bas de l’entonnoir.

L’exemple suivant illustre le flux de données entre les points de contact d’achat et les points de contact d’attribution d’achat. Dans cet exemple, la personne A et la personne B font toutes deux partie de la même opportunité qui a une Date de création de 3/7/2020 et une Date de fermeture de 5/6/2020.

**Personne A** Jeu de données de points de contact d’achat

* Première touche (FT) - Recherche payante.AdWords - 9/1/2019
* Création de piste (LC) - Recherche organique.Google - 11/20/2019
* Post LC (remplissage de formulaire) - Webinaire - 3/4/2020

**Personne B** Jeu de données de points de contact d’achat

* Première touche (FT) - Social payant.Facebook - 8/26/2019
* Création de piste (LC) - Recherche organique.Yahoo - 2/20/2020
* Post LC (remplissage de formulaire) - Email - 5/1/2020

**Opportunités** Les données du point de contact d’attribution de l’achat se liraient comme suit...

* Première touche (FT) - Social payant.Facebook - 8/26/2019
   * (de **Personne B** parce qu&#39;ils ont le vrai _Première touche_ pour le compte/l’Opp)
* Création de piste (LC) - Recherche organique.Google - 11/20/2019
   * (de **Personne A** parce qu&#39;ils ont le vrai _Création de piste_ pour le compte/l’Opp)
* Création d’opportunités (OC) - Webinaire - 3/4/2020
   * (point de contact Post LC depuis **Personne A** serait _Point de contact OC_ car il s’agit de l’interaction la plus récente que nous ayons avec l’opportunité créée le 3/7/2020)
* Closed Won - Email - 5/1/2020
   * (point de contact Post LC depuis **Personne B** serait _Point de contact Won Fermé_ car il s’agit de l’interaction la plus récente que nous avons avec l’opportunité fermée le 5/6/2020)
