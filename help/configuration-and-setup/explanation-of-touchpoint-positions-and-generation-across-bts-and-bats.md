---
description: Explication des positions des points de contact et de la génération sur les BT et conseils  [!DNL BATs]  les utilisateurs de Marketo Measure
title: Explication des positions et de la génération de points de contact entre les BT et les  [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 3%

---


# Explication des positions des points de contact et de la génération parmi les BT et les [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Génération de positions de point de contact et flux via le Parcours des acheteurs**

Il est essentiel de comprendre les positions du Buyer Touchpoint et leur déclenchement pour réussir à créer des rapports avec des données [!DNL Marketo Measure]. Vous souhaitez avoir une compréhension claire de ce que vos prospects ont fait lorsqu’ils ont traversé le parcours de l’acheteur et, par conséquent, de ce à quoi cela ressemblera dans les données de point de contact. Pour plus d’informations sur ce sujet, nous vous recommandons de lire l’article [[!UICONTROL Génération et mappage des points de contact]](/help/configuration-and-setup/touchpoint-generation-and-mapping.md).

[!DNL Marketo Measure] dispose de différentes positions de point de contact qui sont déclenchées par différentes étapes du parcours de l’acheteur. Lors de la création de rapports sur les données [!DNL Marketo Measure], il existe deux ensembles de données de point de contact, les points de contact d’acheteur (BT) et les points de contact d’attribution d’acheteur (BAT). Vous remarquerez peut-être que ces ensembles de données ont des positions légèrement différentes car ils se rapportent à différents objets. Pour plus d’informations sur ce sujet, nous vous recommandons de lire l’article [Différence entre les points de contact d’achat (BT) et les points de contact d’attribution d’acheteur (BAT)](/help/configuration-and-setup/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md).

**Points de contact de l’acheteur (BT)** : il s’agit des points de contact associés à une personne et à son parcours et qui sont propres à cette personne. Les rapports prêts à l’emploi suivants sont créés à partir de données Buyer Touchpoint.

* [!DNL Marketo Measure] 101 : Leads par ID
* [!DNL Marketo Measure] 101 : Leads Par Canal
* [!DNL Marketo Measure] 101 : Lead/Contact par ID
* [!DNL Marketo Measure] 101 : Lead/Contact Par Canal

Vous trouverez ci-dessous un aperçu des postes Buyer Touchpoint qui décrivent où se trouve une personne dans son parcours et les mesures prises pour obtenir ce poste.

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
   <td>Première interaction marketing d’un individu avec votre marque</td>
  </tr>
  <tr>
   <td>Création de prospects (LC pour « Lead Creation »)</td>
   <td>Remplissage de formulaire <strong>OU</strong> Campagne/inclusion de programme</td>
   <td>Le premier formulaire rempli par une personne (généralement un envoi de formulaire, mais il peut également s’agir d’une inclusion de campagne/programme)</td>
  </tr>
  <tr>
   <td>Publier LC</td>
   <td>Remplissage de formulaire <strong>OU</strong> Campagne/inclusion de programme</td>
   <td>Tout formulaire qu’un individu remplit après sa LC (ou une inclusion ultérieure de campagne/programme)</td>
  </tr>
 </tbody>
</table>

**BATS (Buyer Attribution Touchpoints)** : il s’agit des points de contact associés à une opportunité et à son parcours. Ces points de contact sont liés au chiffre d’affaires comme ils sont liés à l’opportunité et à ses contacts. Les rapports prêts à l’emploi suivants sont créés à partir de données Buyer Attribution Touchpoint.

* [!DNL Marketo Measure] 101 : opportunités par ID
* [!DNL Marketo Measure] 101 : Opportunités par canal d’ID

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
   <td>Remplissage de formulaire <strong>OU</strong> Campagne/inclusion de programme</td>
   <td>Le premier formulaire rempli par un contact (généralement un envoi de formulaire, mais il peut également s’agir d’une inclusion de campagne/programme)</td>
  </tr>
  <tr>
   <td>Création de l’opportunité</td>
   <td>Remplissage de formulaire <strong>OU</strong> visite web <strong>OU</strong> campagne/inclusion de programme</td>
   <td>Interaction marketing la plus proche du moment où l’opportunité est créée</td>
  </tr>
  <tr>
   <td>Clôturé - Gagné/Perdu</td>
   <td>Remplissage de formulaire <strong>OU</strong> visite web <strong>OU</strong> campagne/inclusion de programme</td>
   <td>Interaction marketing la plus proche du moment où l’opportunité est fermée (confirmée ou perdue)</td>
  </tr>
  <tr>
   <td>Contacts intermédiaires</td>
   <td>Remplissage de formulaire <strong>OU</strong> Campagne/inclusion de programme</td>
   <td>Lorsqu’un contact remplit un formulaire en ligne et qu’il ne correspond pas à un point de contact jalonné</td>
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] dispose de ces deux ensembles de données de point de contact afin de bien comprendre le parcours d’une personne et les opportunités. Ces deux jeux de données de point de contact vous donnent une carte claire de ce qui s’est passé du haut de funnel au bas de funnel.

L’exemple suivant illustre le flux de données des points de contact d’acheteur (BT) vers les points de contact d’attribution d’acheteur (BAT). Dans cet exemple, la personne A et la personne B font toutes deux partie de la même opportunité qui a une date de création le 3/7/2020 et une date de fermeture le 5/6/2020.

**Jeu de données Buyer Touchpoint Personne A**

* Première touche (FT) - Référencement payant.AdWords - 9/1/2019
* Création de lead (LC) - Organic Search.Google - 11/20/2019
* Publier un LC (formulaire rempli) - Webinaire - 3/4/2020

**Personne B** Jeu de données Buyer Touchpoint

* Premier contact (FT) - Paid Social.Facebook - 8/26/2019
* Création de leads (LC) - Organic Search.Yahoo - 2/20/2020
* Publier LC (formulaire rempli) - Email - 5/1/2020

**Opportunités** les données Buyer Attribution Touchpoint se liraient comme suit...

* Premier contact (FT) - Paid Social.Facebook - 8/26/2019
   * (de **Personne B** car elle possède la véritable _Première touche_ pour le compte/l’opportunité)
* Création de lead (LC) - Organic Search.Google - 11/20/2019
   * (de **Personne A** car elle possède la véritable _Création de lead_ pour le compte/l’opportunité)
* Création d’une opportunité (OC) - Webinaire - 3/4/2020
   * (le point de contact Post LC de **Personne A** serait le point de contact _OC_ car il s’agissait de l’interaction la plus récente que nous ayons avec l’opportunité créée le 3/7/2020)
* Clôturé et confirmé - E-mail - 5/1/2020
   * (le point de contact Post LC de **Personne B** serait le _Point de contact Fermé et confirmé_ car il s’agissait de l’interaction la plus récente que nous ayons avec l’opportunité en cours de fermeture le 5/6/2020)
