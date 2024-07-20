---
unique-page-id: 42762729
description: "[!DNL Marketo Engage] Programmes Integration - [!DNL Marketo Measure]"
title: "[!DNL Marketo Engage] Programmes Integration"
exl-id: c26087e3-d821-4fe7-bacd-eeaa1530a4b0
feature: Integration
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '1261'
ht-degree: 1%

---

# [!DNL Marketo Engage] Intégration de programmes {#marketo-engage-programs-integration}

Grâce à l’intégration de [!DNL Marketo Measure] aux programmes [!DNL Marketo Engage], nos clients peuvent commencer à créer des points de contact pour le suivi de l’attribution à partir des adhésions au programme Marketo. Cette fonctionnalité permet aux marketeurs de commencer le suivi des abonnements aux programmes à partir de programmes de messagerie ou d’engagement qui ne sont pas visibles par le javascript [!DNL Marketo Measure] et qui doivent être mesurés dans le parcours d’attribution.

## Disponibilité {#availability}

Tous les niveaux.

## Exigences {#requirements}

* Instance Marketo de production
* Production Salesforce ou instance Microsoft Dynamics
* Tout abonnement [!DNL Marketo Measure] payant
* Synchronisation des personnes Marketo activée ([!DNL Marketo Measure] paramètres)
* Programmes Marketo activés ([!DNL Marketo Measure] Paramètres)

## Configuration {#setup}

**Règles**

1. Pour commencer à configurer des règles sur les programmes Marketo, accédez à **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]** > **[!UICONTROL Programmes]**. Cliquez sur l’icône **+** pour commencer à créer votre première règle.

   ![](assets/one.png)

   ![](assets/two.png)

1. Vous pouvez éventuellement définir un nom pour la règle si cela permet d’en effectuer le suivi. vous devez d’abord sélectionner le champ à définir dans la liste des champs Programme et Adhésion au programme . Continuez à créer la règle en sélectionnant l’opérateur et la valeur attendue à vérifier.

   ![](assets/three.png)

1. Ajoutez une autre instruction dans la même zone pour configurer un critère &quot;et&quot; dans la règle ou cliquez sur l’icône + en dehors de la zone pour configurer une instruction &quot;ou&quot;.

   ![](assets/four.png)

1. Sélectionnez le champ Date ou Date/Heure à utiliser pour le mappage à la Date du point de contact. Pour afficher la liste des valeurs disponibles à partir de Marketo, saisissez un accolade `{` et nous afficherons les champs disponibles.

   ![](assets/five.png)

   >[!NOTE]
   >
   >Si votre règle souhaite capturer la date d’activité, ou la date à laquelle un membre de programme a atteint un état particulier, vous souhaiterez utiliser l’ intégration des activités [!DNL Marketo Engage] et configurer une règle pour le type d’activité &quot;Changement d’état en progression&quot;.

   ![](assets/six.png)

La règle terminée doit ressembler à ceci :

## Test {#test}

Après avoir créé certaines règles, vous pouvez le tester afin de vérifier que votre instruction correspond à vos programmes.

1. Pour exécuter un test, cliquez sur le bouton **[!UICONTROL TEST]** comme illustré ci-dessous.

   ![](assets/seven.png)

1. Un modal s’affiche, où vous pouvez saisir l’ID de programme à partir de Marketo.

   ![](assets/eight.png)

   Une fois que vous avez saisi l’identifiant et cliqué sur le bouton [!UICONTROL Test] , notre moteur de règles passe en revue chaque règle et détermine si le programme correspond ou non à l’une des règles. Dans l’exemple ci-dessous, vous pouvez constater que le programme 1002, appelé [!DNL Marketo Measure] Ebook, comporte 5 membres de programme et est éligible en raison de la règle affichée.

   Les règles sont exécutées sur une taille d’échantillon de 5 000 membres. Si votre programme contient plus de 5 000 membres, il est possible que nous ne vérifiions pas la compatibilité de tous les membres. Cet outil sert simplement à vérifier que les règles sont correctement construites.

   ![](assets/nine.png)

   Vous pouvez cliquer sur Nombre de membres pour afficher la liste des ID de personnes Marketo éligibles dans le programme.

   ![](assets/ten.png)

## Mappage de canaux {#channel-mapping}

Dans la liste des canaux de programme Marketo, vous souhaitez mapper les valeurs aux canaux marketing personnalisés [!DNL Marketo Measure] que vous avez créés dans Paramètres. Tous les points de contact générés par ces programmes hériteront des noms de canal et de sous-canal que vous sélectionnez ici.

1. Commencez par accéder à **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]** > **[!UICONTROL Canaux hors ligne]**.

1. Dans la partie supérieure, vous aurez la possibilité de mapper les types de campagne CRM. Ensuite, dans la partie inférieure, vous verrez les options de vos canaux de programme Marketo.

1. Sélectionnez tout d’abord le canal qui doit correspondre à la valeur, puis sélectionnez éventuellement le sous-canal. Une fois que vous avez terminé, cliquez sur **[!UICONTROL Enregistrer]** en bas de la page.

   ![](assets/eleven.png)

## Coûts du programme {#program-costs}

Grâce à l’importation des données des programmes Marketo, les coûts sont automatiquement téléchargés à partir des Coûts de la période et le coût reporté dans Marketo est distribué tout au long du mois affecté. Si, par exemple, 1 000 $ est signalé pour janvier 2021, les 1 000 $ sont répartis sur 31 jours. Les coûts sont disponibles dans [!DNL Marketo Measure Discover].

## Fonctionnement {#how-it-works}

**Mappages de champ**

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
   <td>id</td> 
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

| biz_campaign_members | Marketo |
|---|---|
| ID | &quot;MarketoProgramMembership&quot;_ProgramId_Lead Id |
| MODIFIED_DATE | updatedAt |
| CREATED_DATE | membershipDate |
| LEAD_ID | Id (appartenance à une liste) |
| LEAD_EMAIL | Email (abonnement à une liste) |
| STATUS | progressStatus |
| HAS_RESPONDED | reachStatus |
| CAMPAIGN_NAME | programName |
| CAMPAIGN_ID | programId |
| CAMPAIGN_TYPE | marketing |

## Mappage des cookies {#cookie-mapping}

Suite à l’intégration de [!DNL Marketo Measure] avec Marketo, l’ID de cookie [!DNL Marketo Measure] est également mappé et synchronisé avec [!DNL Marketo Munchkin Id]. Cela permet de réduire l’écart pour attribuer la première touche anonyme à une session web plutôt que d’attribuer les touches FT et LC à une activité Marketo. Imaginez ce scénario :

Mark clique sur une publicité [!DNL Facebook] et accède à wayneenterprises.com où il est cookie avec les [!DNL Marketo Measure] Id 123 et [!DNL Marketo Munchkin Id] 456. Aucun remplissage de formulaire n’a lieu.

L’équipe marketing Wayne Entreprises envoie un message électronique à des pistes ciblées spécifiques, dont l’une est `mark@email.com`.

`mark@email.com` reçoit le courrier électronique et les clics publicitaires et accède à wayneenterprises.com. Cela devient `mark@email.com's` seconde visite à `wayneenterprise.com` avec les mêmes ID de cookie, mais il n’y a pas eu de remplissage de formulaire. Par conséquent, pour [!DNL Marketo Measure], il s’agit toujours d’un visiteur anonyme.

L’équipe marketing Wayne Entreprises crée une règle Activité Marketo afin de générer des points de contact pour un type d’activité &quot;Clic e-mail&quot;.

La mise en oeuvre d’aujourd’hui créerait un point de contact FT et LC unique pour `mark@email.com` à partir de l’activité Marketo à partir du type d’activité &quot;Clic sur email&quot;.

Avec cette amélioration du mappage de cookies, le FT revient et est crédité à la publicité [!DNL Facebook] et le LC est crédité au courrier électronique.

>[!NOTE]
>
>Avec le comportement du mappage de cookies, vous pouvez trouver certains points de contact LC provenant d’une visite web. Il est possible qu’une piste apparaisse dans Marketo sans aucune activité associée, puis que [!DNL Marketo Measure] ait téléchargé cette piste, corresponde aux cookies associés, puis soit remontée vers la session web la plus récente, même si aucune activité de formulaire n’a créé la piste.

## Questions fréquentes {#faq}

**Comment définir la date du point de contact comme date de progression ou date à laquelle le changement d’état est arrivé à mon membre de programme ?**

Si votre règle souhaite capturer la date d’activité, ou la date à laquelle un membre de programme a atteint un état particulier, vous souhaiterez utiliser l’ intégration des activités [!DNL Marketo Engage] et configurer une règle pour le type d’activité &quot;Changement d’état en progression&quot;. Dans le cas contraire, l’intégration de programmes [!DNL Marketo Engage] rend disponible uniquement la date d’adhésion, qui est la première date à avoir introduit la personne Marketo dans le programme, même s’il existe plusieurs états.

**Puis-je obtenir une liste de sélection des options de date pour la date du point de contact ?**

Pour déclencher la saisie automatique, commencez par saisir un accolades `{` dans le champ de texte, puis les champs disponibles s’affichent.

**Si je crée des règles de programme Marketo et que je dispose également de règles de campagne CRM, seront-elles comptabilisées deux fois ?**

Cela dépend de votre définition de règle, mais peut-être, oui. vous souhaitez évaluer votre jeu de règles afin que vous ne disposiez pas de règles couvrant un programme et une campagne, car nous ne dédupliquerons ni ne détecterons les appartenances similaires. Une solution possible consiste à copier vos règles Campaign dans Programmes si vous souhaitez que Marketo soit votre source unique de vérité, puis à supprimer les règles Campaign. Une autre option consiste à ajouter un critère &quot;CreatedOn&quot; ou &quot;CreatedDate&quot; dans vos règles, de sorte que les règles antérieures à une certaine date utilisent les règles et règles de Campaign après qu’une certaine date utilisera les règles de programme. Il y a beaucoup de solutions possibles, mais cela demandera un peu de planification et de coordination.

**Les champs personnalisés de l’appartenance au programme Marketo sont-ils disponibles pour définir ?**

En raison de limitations techniques, nous ne pouvons pas prendre en charge pour l’instant les champs personnalisés d’appartenance à un programme. Une fois ces champs disponibles via des API Marketo supplémentaires, ils nous seront exposés et visibles pour que vous puissiez les utiliser.

**Comment savoir si je dois utiliser des programmes ou des activités ?**

L’ [!DNL Marketo Engage] intégration de programmes est un moyen simple de générer des points de contact selon qu’une personne est ou non membre d’un programme. Si vous souhaitez définir une règle en fonction du moment où une personne passe à un état de programme spécifique, l’ intégration des activités [!DNL Marketo Engage] sera la configuration souhaitée, en particulier le type d’activité &quot;Modifier l’état de progression&quot;.
