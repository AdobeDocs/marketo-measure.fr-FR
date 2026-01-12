---
description: Intégration des programmes [!DNL Marketo Engage] - [!DNL Marketo Measure]
title: Intégration des programmes [!DNL Marketo Engage]
exl-id: c26087e3-d821-4fe7-bacd-eeaa1530a4b0
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 1%

---


# Intégration des programmes [!DNL Marketo Engage] {#marketo-engage-programs-integration}

Grâce à l’intégration [!DNL Marketo Measure] aux programmes [!DNL Marketo Engage], nos clients peuvent commencer à créer des points de contact pour le suivi de l’attribution à partir des adhésions au programme Marketo. Cette fonctionnalité permet aux spécialistes marketing de commencer à effectuer le suivi des adhésions aux programmes à partir d’e-mails ou de programmes d’engagement qui ne sont pas visibles autrement par le javascript [!DNL Marketo Measure] et qui doivent être mesurés dans le parcours d’attribution.

## Disponibilité {#availability}

Tous les niveaux.

## Exigences {#requirements}

* Instance de Marketo de production
* Salesforce de production ou instance Microsoft Dynamics
* Tout abonnement [!DNL Marketo Measure] payant
* Synchronisation des personnes Marketo activée (paramètres [!DNL Marketo Measure])
* Programmes Marketo activés (paramètres [!DNL Marketo Measure])

## Configuration {#setup}

**Règles**

1. Pour commencer à configurer des règles sur les programmes Marketo, accédez à **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]** > **[!UICONTROL Programmes]**. Cliquez sur l’icône **+** pour commencer à créer votre première règle.

   ![Page des paramètres des programmes dans le compte Marketo Measure](assets/one.png)

   ![Boîte de dialogue Créer une règle avec le bouton Ajouter](assets/two.png)

1. Vous pouvez éventuellement définir un nom pour la règle si cela permet d’en effectuer le suivi. vous allez d’abord sélectionner le champ pour définir votre règle dans la liste des champs Programme et Appartenance au programme . Continuez à créer la règle en sélectionnant l’opérateur et la valeur attendue à vérifier.

   ![Créateur de règles avec menu déroulant de sélection de champ et options d’opérateur](assets/three.png)

1. Ajoutez une autre instruction dans la même zone pour configurer un critère « et » dans la règle ou cliquez sur l’icône + en dehors de la zone pour configurer une instruction « ou ».

   ![Créateur de règles présentant plusieurs conditions avec des options logiques et/ou ](assets/four.png)

1. Choisissez le champ de date ou de date/heure à utiliser pour mapper à la date du point de contact. Pour afficher la liste des valeurs disponibles à partir de Marketo, saisissez un crochet `{` et les champs disponibles s’affichent.

   ![Mappage des champs de date avec une liste déroulante de saisie automatique affichant les champs disponibles](assets/five.png)

   >[!NOTE]
   >Si votre règle souhaite capturer la date de l&#39;activité, ou la date à laquelle un membre du programme a atteint un statut particulier, vous devez utiliser l&#39;intégration des activités [!DNL Marketo Engage] et configurer une règle pour le type d&#39;activité « Changement de statut en cours ».

   ![Configuration de règle terminée affichant les mappages et conditions de champ](assets/six.png)

La règle terminée doit ressembler à ce qui suit :

## Test {#test}

Après avoir créé des règles, vous pouvez les tester pour vérifier que votre relevé correspond à vos programmes.

1. Pour exécuter un test, cliquez sur le bouton **[!UICONTROL TEST]** comme illustré ci-dessous.

   ![Bouton Tester dans l’interface des règles du programme](assets/seven.png)

1. Une boîte de dialogue modale s’affiche, dans laquelle vous pouvez saisir l’ID de programme à partir de Marketo.

   ![Boîte de dialogue modale de test avec le champ d’entrée ID de programme](assets/eight.png)

   Une fois que vous avez saisi l&#39;ID et cliqué sur le bouton [!UICONTROL Test], notre moteur de règles passe en revue chaque règle et détermine si le Programme correspond ou non à l&#39;une des règles. Dans l&#39;exemple ci-dessous, vous pouvez voir que le Programme 1002, appelé Ebook [!DNL Marketo Measure], compte 5 Membres de programme et est éligible en raison de la règle affichée.

   Les règles sont exécutées sur un échantillon de 5 000 membres. Si votre programme compte plus de 5000 membres, il est possible que nous ne contrôlions pas la compatibilité de tous les membres. Cet outil sert simplement à vérifier que les règles sont correctement construites.

   ![Résultats du test affichant le programme correspondant avec le nombre de membres](assets/nine.png)

   Vous pouvez cliquer sur le Nombre de membres pour afficher la liste des ID de personnes Marketo éligibles dans le programme.

   ![Liste des ID de personnes Marketo éligibles à partir des résultats du test](assets/ten.png)

## Mappage de canal {#channel-mapping}

Dans la liste des canaux de programme Marketo, vous souhaiterez mapper les valeurs aux canaux marketing personnalisés [!DNL Marketo Measure] que vous avez créés dans les paramètres. Tous les points de contact générés par ces programmes hériteront des noms de canal et de sous-canal que vous sélectionnez ici.

1. Commencez par accéder à **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]** > **[!UICONTROL Canaux hors ligne]**.

1. Dans la partie supérieure, vous avez la possibilité de mapper les types de campagnes CRM, puis dans la partie inférieure, vous verrez les options relatives à vos canaux de programme Marketo.

1. Sélectionnez d’abord le canal à mapper à la valeur, puis éventuellement le sous-canal. Lorsque vous avez terminé, cliquez sur **[!UICONTROL Enregistrer]** en bas de la page.

   ![Paramètres des canaux hors ligne affichant les options de mappage des canaux de programme Marketo](assets/eleven.png)

## Coûts du programme {#program-costs}

Grâce à l’importation des données des programmes Marketo, les coûts sont automatiquement téléchargés à partir des coûts de la période et le coût déclaré dans Marketo est distribué tout au long du mois attribué. Par exemple, si 1 000 $ sont déclarés pour janvier 2021, les 1 000 $ sont répartis sur 31 jours. Les coûts se trouvent à [!DNL Marketo Measure Discover].

>[!NOTE]
>
>Marketo Measure ne prend en charge qu&#39;une seule entrée de coût de période par mois. Pour vous assurer que tous les coûts sont importés, agrégez le coût mensuel total en une seule entrée. Plusieurs postes de coût pour le même mois ne sont pas pris en charge.

## Fonctionnement {#how-it-works}

**Mappages de champs**

<table>
 <colgroup>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <th>biz_ad_campaigns</th>
   <th>Marketo</th>
  </tr>
  <tr>
   <td>ID</td>
   <td>identifiant</td>
  </tr>
  <tr>
   <td>IS_DELETED</td>
   <td>(vérifier si le programme existe toujours via l’API)</td>
  </tr>
  <tr>
   <td><p>NAME</p></td>
   <td>name</td>
  </tr>
 </tbody>
</table>

| membres_campaign_de_l’entreprise | Marketo |
|---|---|
| ID | « MarketoProgramMembership »_ProgramId_Lead Id |
| MODIFIED_DATE | updatedAt |
| CREATED_DATE | membershipDate |
| LEAD_ID | Id (appartenance à une liste) |
| LEAD_EMAIL | E-mail (liste des membres) |
| STATUS | progressionStatus |
| HAS_RESPONDED | reachStatus |
| CAMPAIGN_NAME | programName |
| CAMPAIGN_ID | programId |
| CAMPAIGN_TYPE | marketing |

## Mappage des cookies {#cookie-mapping}

Suite à l’intégration d’[!DNL Marketo Measure] à Marketo, l’ID de cookie [!DNL Marketo Measure] est désormais également mappé et synchronisé avec le [!DNL Marketo Munchkin Id]. Cela permet de combler l’écart afin d’attribuer le premier contact anonyme à une session web plutôt que d’attribuer les contacts FT et LC à une activité Marketo. Imaginez ce scénario :

Mark clique sur une annonce [!DNL Facebook] et arrive sur wayneenterprises.com où il est cuisiné avec les [!DNL Marketo Measure] ID 123 et [!DNL Marketo Munchkin Id] 456. Aucun remplissage de formulaire n’a lieu.

L’équipe marketing de Wayne Enterprises envoie une grosse quantité d’e-mails à des prospects ciblés spécifiques, dont l’un est `mark@email.com`.

`mark@email.com` reçoit l’e-mail et clique sur et accède à wayneenterprises.com. Cela devient `mark@email.com's` deuxième visite pour `wayneenterprise.com` avec les mêmes ID de cookie, mais il n’y avait pas de remplissage de formulaire, donc pour [!DNL Marketo Measure], ils sont toujours un visiteur anonyme.

L’équipe marketing Wayne Enterprises crée une règle d’activité Marketo pour générer des points de contact pour un type d’activité « Cliquer sur l’e-mail ».

L’implémentation d’aujourd’hui créerait un seul point de contact FT et LC pour les `mark@email.com` de l’activité Marketo à partir du type d’activité « Cliquer sur l’e-mail ».

Grâce à cette amélioration du mappage des cookies, le FT retournerait en arrière et serait crédité à l’annonce [!DNL Facebook] et le LC serait crédité à l’e-mail.

>[!NOTE]
>Avec le comportement de mappage des cookies, vous pouvez trouver certains points de contact LC qui proviennent d’une visite web. Il est possible qu’un prospect se soit affiché dans Marketo sans activité associée, puis [!DNL Marketo Measure] téléchargé ce prospect, qu’il corresponde aux cookies associés, puis qu’il soit tracé jusqu’à la session web la plus récente, même s’il n’y avait aucune activité de formulaire à l’origine du prospect.

## Questions fréquentes {#faq}

**Comment puis-je définir la date du point de contact sur la date de progression ou la date à laquelle le changement de statut est arrivé au membre de mon programme ?**

Si votre règle souhaite capturer la date de l&#39;activité, ou la date à laquelle un membre du programme a atteint un statut particulier, vous devez utiliser l&#39;intégration des activités [!DNL Marketo Engage] et configurer une règle pour le type d&#39;activité « Changement de statut en cours ». Dans le cas contraire, l’intégration des programmes [!DNL Marketo Engage] rend uniquement disponible la date d’abonnement, qui est la première date à laquelle la personne Marketo a été intégrée au programme, même s’il existe plusieurs statuts.

**Puis-je obtenir une liste de sélection des options de date pour la date du point de contact ?**

Pour déclencher la saisie automatique, commencez par saisir un crochet `{` dans le champ de texte, puis les champs disponibles s’affichent.

**Si je crée des règles de programme Marketo et que j’ai également des règles de campagne CRM, seront-elles comptabilisées deux fois ?**

Cela dépend de la définition de votre règle, mais peut-être, oui. vous souhaiterez évaluer votre ensemble de règles afin de ne pas avoir de règles qui couvrent un programme et une campagne, car nous ne dédupliquerons pas ou ne détecterons pas d’appartenances similaires. Une solution possible consiste à copier vos règles Campaign dans Programmes si vous souhaitez que Marketo soit votre seule source de vérité, puis à supprimer les règles Campaign. Une autre option consiste à ajouter un critère « CreatedOn » ou « CreatedDate » à vos règles afin que les règles antérieures à une certaine date utilisent les règles de Campaign et que les règles postérieures à une certaine date utilisent les règles de Programme. Il existe de nombreuses solutions de rechange, mais il faudra un peu de planification et de coordination.

**Les champs personnalisés d’appartenance au programme Marketo sont-ils disponibles pour définition ?**

En raison de limitations techniques, nous ne pouvons pas prendre en charge les champs personnalisés d’appartenance à un programme pour l’instant. Une fois que ces champs sont disponibles par le biais d’API Marketo supplémentaires, ils nous sont exposés et vous pouvez les utiliser.

**Comment savoir si je dois utiliser les programmes ou les activités ?**

L’intégration des programmes [!DNL Marketo Engage] est un moyen simple de générer des points de contact selon qu’une personne est membre ou non d’un programme. Si vous souhaitez définir une règle basée sur le moment où une personne passe à un statut de programme particulier, l&#39;intégration des activités [!DNL Marketo Engage] sera la configuration souhaitée, en particulier le type d&#39;activité « Changement de statut en cours ».
