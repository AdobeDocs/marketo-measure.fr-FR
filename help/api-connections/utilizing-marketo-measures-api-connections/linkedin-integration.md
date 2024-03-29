---
unique-page-id: 35586080
description: Intégration linkedIn - [!DNL Marketo Measure]
title: Intégration linkedIn
exl-id: 705209ef-1ece-496c-ac2f-6a31055bd993
feature: APIs, Integration
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '2653'
ht-degree: 1%

---

# Intégration linkedIn {#linkedin-integration}

## Vue d’ensemble {#overview}

La variable [!DNL Marketo Measure] l’intégration à LinkedIn se fait en deux parties :

Contenu sponsorisé : l’intégration de contenu sponsorisé permet [!DNL Marketo Measure] pour baliser les URL de destination sur [!DNL LinkedIn] publicités, qui permettent [!DNL Marketo Measure] pour suivre un utilisateur tout au long de son parcours de point de contact et mapper l’activité à [!DNL LinkedIn] Campaign et Creative. Cela fournit aux clients des informations sur le retour sur investissement de leur [!DNL LinkedIn] activité.

Forms Lead Gen : grâce à l’intégration à LinkedIn Lead Gen Forms, Marketo Measure obtient des informations sur les formulaires qui ont été envoyés par le biais de la plateforme LinkedIn. Ces champs de formulaire correspondent aux pistes de votre CRM ou [!DNL Marketo Engage] afin qu’ils soient éligibles à l’attribution. Grâce aux informations sur les formulaires, les créatifs et les campagnes qui ont contribué à générer les formulaires, les équipes peuvent désormais optimiser davantage leur marketing LinkedIn et leurs dépenses publicitaires.

## Disponibilité {#availability}

Disponible pour tous les utilisateurs.

## Exigences {#requirements}

**Rôles de Campaign Manager**

Pour [!DNL Marketo Measure] Pour pouvoir télécharger les données de coût des publicités et publicités, vous devez disposer de l’un des rôles suivants dans le Gestionnaire de campagnes :

* Administrateur de facturation
* Responsable des comptes
* Gestionnaire de campagnes

En savoir plus : [Rôles et fonctions utilisateur dans Campaign Manager](https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager).

**Rôles d’administration des médias payants**

Pour [!DNL Marketo Measure] pour pouvoir créer/mettre à jour des créatifs sponsorisés, vous devez disposer de l’un des rôles d’administrateur de médias payants suivants :

* Affiche de contenu sponsorisé
* Gestionnaire Forms de génération de pistes

En savoir plus : [Rôles d’administration des pages linkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

Il y a d&#39;autres [!DNL LinkedIn] rôles que nous faisons **not** nécessite pour notre intégration. Ces rôles sont souvent confondus avec les rôles requis. Notez donc qu’il y a une différence.

**Rôles d’administrateur de page**

Pour [!DNL Marketo Measure] pour pouvoir télécharger/intégrer des pistes à partir de formulaires de génération de piste, vous devez disposer du rôle d’administrateur de page suivant :

* Super administrateur

En savoir plus : [Rôles d’administration des pages linkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

## Types de publicité linkedIn {#linkedin-ad-types}

[!DNL Marketo Measure] prend en charge :

**Contenu sponsorisé :** Le contenu sponsorisé vous permet de diffuser du contenu au [!DNL LinkedIn] flux de membres au-delà de ceux qui suivent votre société. Le contenu sponsorisé peut être ciblé vers une audience spécifique et peut aider les annonceurs à atteindre [!DNL LinkedIn] membres quel que soit l’endroit et le moment où ils s’engagent sur la page [!DNL LinkedIn] plateforme sur ordinateur de bureau, mobile et tablette. Le contenu sponsorisé avec Lead Gen Forms est pris en charge.

Types de formats d’annonces de contenu sponsorisé pris en charge par [!DNL Marketo Measure] sont des publicités avec image unique et des publicités vidéo (via Lead Gen Forms). En raison de la complexité du schéma, nous ne prenons pas en charge les annonces carrousel.

[!DNL Marketo Measure] ne prend pas en charge la messagerie sponsorisée, les publicités textuelles ou les publicités dynamiques.

![](assets/one.png)

>[!TIP]
>
>Pour toutes vos campagnes/dépenses provenant d’une source de contenu non sponsorisé (par exemple, Type de campagne de &quot;publicité texte&quot; ou &quot;sponsorisée dans un courrier électronique&quot;), [!DNL Marketo Measure] does _not_ prennent en charge de manière inhérente le suivi de ces types de campagne. Si vous souhaitez effectuer le suivi des dépenses pour des campagnes comme celles-ci avec votre dépense de &quot;contenu sponsorisé&quot;, veillez à utiliser notre fichier CSV de dépenses marketing pour consigner manuellement ces dépenses.

## Fonctionnement : Contenu sponsorisé {#how-it-works-sponsored-content}

>[!NOTE]
>
>Avant la première utilisation, ce paramètre de fonctionnalité doit être activé en accédant à [!DNL Marketo Measure] [!UICONTROL Paramètres] > [!UICONTROL Intégrations] > [!UICONTROL Publicités] > [!UICONTROL Activer LinkedIn Lead Gen Forms].

**[!DNL LinkedIn's]Exigences uniques en matière de balisage automatique**

[!DNL Marketo Measure] peut vous aider à suivre vos [!DNL LinkedIn] performances de campagne en balisant automatiquement vos landing pages.

[!DNL Marketo Measure] rechercheront des créatifs avec un partage LinkedIn unique et ajouteront une `?_bl={creativeId}` à la fin de celle-ci.

**Copie de partages**

Avec ceci [!DNL Marketo Measure/LinkedIn] Intégration, nous demandons aux clients de ne pas copier/cloner/dupliquer des créatifs existants. Si des partages sont détectés et ne sont utilisés que sur un seul élément créatif, [!DNL Marketo Measure] Vous pouvez baliser le partage en l’état sans avoir à recréer de Creative ou de Partages, et l’historique de toutes les publicités (impressions, clics, partages) restera inchangé.

Dès qu’un partage est trouvé partagé entre plusieurs créatifs, [!DNL Marketo Measure] doit passer par un processus de mise en pause, de copie et de rebalisage pour créer un ensemble unique. [!DNL Marketo Measure] arrêtera et archivera les créatifs en direct et effacera donc l’historique des publicités, y compris les impressions, les clics et les partages sur les réseaux sociaux, afin de tout baliser automatiquement correctement.

aller de l&#39;avant, [!DNL Marketo Measure] recommande de ne pas dupliquer les [!DNL LinkedIn] Partage et conserve toutes les créations et tous les partages aussi uniques que possible afin que nous puissions simplement ajouter notre suivi sans avoir à effacer l’historique des publicités.

**URL raccourcies**

La raison de l’étape supplémentaire est que LinkedIn permet aux URL de destination d’être une URL abrégée (bit.ly, goog.le, etc.), ce qui signifie : [!DNL Marketo Measure] ne voit pas l’URL longue et résolue et [!DNL Marketo Measure] doit ajouter des paramètres de suivi à une URL résolue. Pour contourner ce problème, [!DNL Marketo Measure] recherche des URL raccourcies avant de recréer une publicité, développe l’URL, puis crée la nouvelle publicité avec l’URL résolue et tous ses paramètres, ce qui permet d’ [!DNL Marketo Measure] pour ajouter des balises. La création d’une nouvelle publicité effacera l’historique des publicités (impressions, clics, partages), d’où la nécessité d’autoriser le balisage des URL raccourcies.

Si vous utilisez massivement des URL raccourcies, cela peut fortement impacter vos créatifs. Nous vous recommandons de ne plus utiliser d’URL raccourcies afin que [!DNL Marketo Measure] Vous pouvez baliser les pages d’entrée sans avoir à créer de nouvelles publicités et effacer l’historique des publicités.

**Le processus**

Commençons par quelques exemples. Disons que nous avons....

Creative A : Partager 123\
Creative B : Partager 234\
Creative C : Partager 234\
Creative D : Partager 234

![](assets/two.png)

`1)` [!DNL Marketo Measure] recherche d’abord toutes les campagnes, tous les créatifs et tous les partages avec un état &quot;actif&quot;. [!DNL Marketo Measure] ne marquera pas les publicités suspendues, archivées ou annulées. Si une publicité a été suspendue, définissez sur [!UICONTROL active], nous le marquerons une fois qu’il sera à nouveau actif. Si nous pouvons trouver un partage unique, ce qui signifie qu’il n’est pas utilisé sur plusieurs créatifs ou campagnes (par exemple, Creative A : Partager 123), [!DNL Marketo Measure] ajoutera notre paramètre personnalisé `>> ?_bl={creativeId}` à l’URL de partage.

`2)` Désormais, si le partage a été partagé et qu’il a perdu son unicité (par exemple, Creative B : Partager 234 et Creative C : Partager 234 et Creative D : Partager 234), [!DNL Marketo Measure] arrêtera et archivera tous les créatifs similaires (qui seraient Creative B, Creative C et Creative D).

`3)` [!DNL Marketo Measure] crée 3 nouveaux créatifs, Creative E, Creative F et Creative G, qui copient le contenu de Creative B, qui est archivé.

`4)` [!DNL Marketo Measure] crée également 3 nouveaux partages, Partager 345, Partager 456 et Partager 567, qui copie le contenu de Partager 234, mais qui aura son propre fichier unique. `?_bl` balisage.

`5)` [!DNL Marketo Measure] Vous devrez vérifier régulièrement que les partages ne sont pas partagés et, dans ce cas, nous redémarrerons le processus à l’étape 2 ci-dessus.

>[!NOTE]
>
>La mise en oeuvre de cela signifie que nos clients perdront l’historique des publicités de Creative B : Share 234, Creative C : Share 234 et Creative D : Share 234, car il est désormais recréé avec Creative E : Share 345, Share F : Share 456 et Creative G : Share 567 respectivement.

![](assets/three.png)

## Fonctionnement : Lead Gen Forms {#how-it-works-lead-gen-forms}

**[!DNL LinkedIn's]Exigences uniques en matière de balisage automatique**

[!DNL Marketo Measure] peut vous aider à suivre vos [!DNL LinkedIn] performances de campagne en balisant automatiquement vos landing pages.

[!DNL Marketo Measure] rechercheront des créatifs avec un partage LinkedIn unique et ajouteront une `?_bl={creativeId}` à la fin de celle-ci.

**Le processus**

Via [!DNL LinkedIn's] API de formulaire d’annonce et API de réponse de formulaire d’annonce, nous pouvons rassembler les données d’envoi de formulaire pour un compte d’annonce et associer l’adresse électronique à un prospect depuis le CRM ou Marketo.

Les formulaires linkedIn peuvent contenir plusieurs adresses électroniques. Lorsque nous téléchargeons les réponses de formulaire, nous recherchons les adresses électroniques avec la priorité suivante : Adresse électronique professionnelle, Adresse électronique (champ de formulaire principal) ou champs personnalisés avec une valeur de courrier électronique valide.

Quel que soit l’état Campaign ou Creative, toutes les réponses au formulaire auront un point de contact. [!DNL Marketo Measure] comporte une restriction de recherche en amont de 90 jours ; [!DNL Marketo Measure] ne peut pas accéder aux réponses de formulaire datant de plus de 90 jours, mais plus la variable [!DNL Marketo Measure] et [!DNL LinkedIn] l’intégration est activée, plus les points de contact du formulaire de génération de piste sont visibles par le biais de [!DNL Marketo Measure].

>[!NOTE]
>
>Les coûts linkedIn sont toujours téléchargés dans le cadre des campagnes de contenu sponsorisé.

**Suivi de Lead Gen Forms dans CRM ou Marketo**

Avant le [!DNL Marketo Measure] et l’intégration Forms LinkedIn Lead Gen existait. Il était courant pour les clients de transmettre leurs envois de formulaire à un programme Marketo et/ou à une campagne CRM afin de suivre les formulaires et de recevoir l’attribution sur ces activités. Une fois que le paramètre Lead Gen Forms est activé, nous voulons nous assurer que ces envois de formulaire ne sont pas comptabilisés deux fois. Vérifiez les éléments suivants :

* Le champ &quot;Activer les points de contact de l’acheteur&quot; sur l’objet CRM est défini sur &quot;Aucun&quot; ou &quot;Exclure tous les membres de campagne&quot;.
* Mettre à jour tout programme Marketo ou règle d’activité Marketo associé
* Mettre à jour les règles de Campaign CRM associées

>[!NOTE]
>
>L’API LinkedIn présente une limite de recherche en amont de 90 jours. Par conséquent, si vous utilisez des règles Marketo ou CRM, il est recommandé de définir la date de fin de la règle sur 90 jours avant la date à laquelle vous avez activé l’intégration dans [!DNL Marketo Measure].

## Détails du Touchpoint {#touchpoint-details}

Après [!DNL Marketo Measure] a balisé correctement votre page d’entrée sur l’élément créatif LinkedIn. Vous pouvez afficher les données des publicités résolues sur le point de contact. Voici le mappage des valeurs de données que vous devriez voir :

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th style="width:30%">Champ de point de contact</th> 
   <th>Valeur échantillon</th> 
  </tr> 
  <tr> 
   <td>Identifiant de publicité</td>
   <td>84186224</td>
  </tr> 
  <tr> 
   <td>Contenu publicitaire</td>
   <td>copy-1-image-2-man 95% des spécialistes du marketing #B2B considèrent que la stratégie de création de demande est une réussite. En savoir plus : [!DNL https]://lnkd.in/jgdi50vKrgv</td>
  </tr> 
  <tr> 
   <td>Identifiant du groupe publicitaire</td>
   <td>(vide)</td>
  </tr> 
  <tr> 
   <td>Nom de groupe publicitaire</td>
   <td>(vide)</td>
  </tr> 
  <tr> 
   <td>Identifiant de campagne publicitaire</td>
   <td>138949954</td>
  </tr> 
  <tr> 
   <td>Nom de la campagne publicitaire</td>
   <td>SU - Comptes COM - Compétences à la demande</td>
  </tr> 
  <tr> 
   <td>URL de destination de l’annonce <b>*</b></td>
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217</td> 
  </tr> 
  <tr> 
   <td>URL du formulaire</td> 
   <td>info.bizible.com/demo</td> 
  </tr> 
  <tr> 
   <td>URL du formulaire - Brut</td> 
   <td>info.bizible.com/demo</td> 
  </tr> 
  <tr> 
   <td>Identifiant du mot-clé</td> 
   <td>(vide)</td> 
  </tr> 
  <tr> 
   <td>Type de correspondance de mot-clé</td> 
   <td>(vide)</td> 
  </tr> 
  <tr> 
   <td>Page de destination</td> 
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders</td> 
  </tr> 
  <tr> 
   <td>Page d’entrée - Raw</td> 
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217</td> 
  </tr> 
  <tr> 
   <td>Canal marketing</td> 
   <td>Référencement social payant</td> 
  </tr> 
  <tr> 
   <td>Canal marketing - Chemin</td> 
   <td>Social payant.LinkedIn</td> 
  </tr> 
  <tr> 
   <td>Support</td> 
   <td>"cpc" ou "Lead Gen Form"</td> 
  </tr> 
  <tr> 
   <td>Page du référent</td> 
   <td>www.linkedin.com/</td> 
  </tr> 
  <tr> 
   <td>Page du référent - Brut</td> 
   <td>www.linkedin.com/</td> 
  </tr> 
  <tr> 
   <td>Expression de recherche</td> 
   <td>(vide)</td> 
  </tr> 
  <tr> 
   <td>Type de point de contact</td> 
   <td>Formulaire web</td>
  </tr> 
  <tr> 
   <td>Source du point de contact</td>
   <td>LinkedIn</td>
  </tr> 
 </tbody> 
</table>

**&#42;** _Le champ &quot;URL de destination de l’annonce&quot; n’est renseigné que pour le contenu sponsorisé. Il n’est pas renseigné pour le Forms de génération de pistes._

<br>

## Coûts {#costs}

Parce que [!DNL Marketo Measure] dispose d’une intégration directe avec [!DNL LinkedIn], nous téléchargeons les dépenses enregistrées pour chaque campagne et chaque créatif chaque jour. Il n’est pas nécessaire qu’un client effectue un rapport sur [!DNL LinkedIn] dépensez dans la variable [!DNL Marketo Measure] de l’application.

Comme pour les autres intégrations d’annonces, [!DNL Marketo Measure] a défini une règle de canal marketing pour placer tout [!DNL LinkedIn] campagnes, créatifs et coûts. Pour utiliser la règle, le client souhaite insérer une nouvelle ligne pour sa payante [!DNL LinkedIn] les efforts. Il peut s’agir d’un canal nouveau ou existant. Dans la colonne Référent , utilisez la définition &quot;[[!DNL LinkedIn] Payée]&quot; [!DNL Marketo Measure] a été défini comme tout point de contact avec une [!DNL Marketo Measure] balise .

![](assets/four.png)

## [!DNL Marketo Measure] Discover {#marketo-measure-discover}

Certaines améliorations ont été apportées à la fonction [!DNL Marketo Measure] Découvrez comment prendre en charge la création de rapports Forms de Lead Gen.

**Payant Media Board**

Mosaïque Forms de génération de pistes : nouvelle mosaïque qui comprend le nombre de remplissages de formulaires LinkedIn. L’exploration de ce nombre affichera l’ID d’activité, la date du formulaire, le nom du formulaire et l’adresse électronique.

**Panneau Chemin d’accès de l’engagement**

Parcours des événements : inclut le type d’événement &quot;Activité&quot; et le &quot;formulaire de génération de piste&quot; moyen pour les formulaires issus de l’intégration. La vue d’exploration comprend les détails sur les campagnes, les créatifs et les formulaires.

## FAQ sur le contenu sponsorisé {#sponsored-content-faq}

**Qu’est-ce qu’une part sombre ?**

Un partage obscur est un message où il n’est jamais publié sur la page de l’entreprise et est immédiatement créé et ajouté directement en tant que créatif. Donc, [!DNL Marketo Measure]Les créatifs créés n’apparaissent pas en haut de la page d’une entreprise et sont à nouveau promus. Des partages noirs sont utilisés pour qu’ils puissent être lancés en coulisses.

**Quelles sont les instructions ? [!DNL Marketo Measure] balise réelle ?**

Il existe quatre statuts différents sur un [!DNL LinkedIn] Campagne et création : active, en pause, archivée et annulée. Nous marquons uniquement les campagnes et les créatifs actifs. Le balisage d’autres états les redéfinit sur Actif. [!DNL Marketo Measure] ne marquera pas Campagnes ou créatifs en pause, archivés ou annulés, mais le balisage reprendra si l’état devient Actif.

**Quelle est la valeur de [!DNL Marketo Measure] utilise-t-il pour baliser ?**

À la fin de l’URL de destination, [!DNL Marketo Measure] ajoute le paramètre `&_bl={creativeId}`, où la variable `{creativeId}` est l’ID créatif de LinkedIn. Avec l’identifiant créatif, [!DNL Marketo Measure] peut également déterminer l’ID de campagne depuis [!DNL LinkedIn] possède une structure de publicités assez basique, car chaque élément créatif ne peut appartenir qu’à une seule campagne.

**Que se passe-t-il avec mon ancien créatif une fois ? [!DNL Marketo Measure] crée une nouvelle version de celle-ci ?**

When [!DNL Marketo Measure] Crée un Partage et le place dans un nouvel élément créatif, l’ancien élément créatif est archivé. C&#39;est également pourquoi [!DNL Marketo Measure] ne marquera pas les campagnes ou les créatifs archivés ; autrement il fonctionnerait avec [!DNL Marketo Measure] en essayant de le marquer indéfiniment.

**Pourquoi l’URL de destination de la publicité créée ne correspond-elle pas à ma publicité d’origine ?**

[!DNL Marketo Measure] doit ajouter les paramètres de suivi à une URL résolue, mais l’URL présentée dans l’API peut potentiellement être une URL raccourcie sans tous les paramètres présents. Pour contourner ce problème, [!DNL Marketo Measure] recherche des URL raccourcies avant de recréer une publicité, la résout, puis crée la nouvelle publicité avec l’URL résolue et tous ses paramètres, ce qui permet [!DNL Marketo Measure] pour ajouter des balises.

**Est-ce que vous balisez toutes mes publicités ? Je ne vois pas le paramètre bl sur toutes mes landing pages ?**

Nous avons observé que certains spécialistes du marketing placent un lien d’image dans l’URL de destination, qui [!DNL Marketo Measure] ne peut pas être identifié. Nous recherchons donc l’URL dans le contenu de la publicité. If [!DNL Marketo Measure] dispose des autorisations nécessaires pour baliser les URL abrégées. Nous allons développer l’URL et la balise , mais en raison de la structure de copie de LinkedIn, elle est automatiquement abrégée dans le texte. La balise se trouve dans l’URL abrégée LinkedIn, qui apparaît dans le champ Contenu de la publicité du point de contact plutôt que dans le champ Page d’entrée - Brut .

**Oh non, quelqu&#39;un dans mon équipe a accidentellement cloné un partage. Puis-je le suspendre ?**

Pas de soucis. [!DNL Marketo Measure] recherche par programmation les partages qui ne sont plus uniques, ce qui signifie qu’ils ont depuis été copiés dans un autre créatif. Une fois la copie détectée, [!DNL Marketo Measure] suivra le flux habituel pour baliser et créer de nouvelles publicités.

**Ma publicité était en attente de révision plus tôt. Pourquoi la révision est-elle en attente après ? [!DNL Marketo Measure] l’a balisé ?**

LinkedIn exige que toutes les publicités créées ou modifiées passent par le processus de sécurité normal avant d’être publiées. [!DNL Marketo Measure] tente d’intercepter la publicité aussi rapidement que possible, car elle recherche de nouvelles publicités toutes les 6 heures, mais avec [!DNL LinkedIn's] En outre, le lancement peut être retardé de quelques heures.

**Mon annonce contient 2 URL. Lequel est balisé ?**

Les deux. La variable [!DNL Marketo Measure] l’intégration nous permet de baliser l’URL de destination à partir de l’image de clic publicitaire dans la publicité, mais met également automatiquement à jour l’URL abrégée dans la description de la publicité.

![](assets/five.png)

**J&#39;ai connecté mon [!DNL LinkedIn ads] compte . Pourquoi pas [!DNL Marketo Measure] balisage de mes liens ?**

La connexion [!DNL LinkedIn] L’utilisateur doit disposer d’un accès en édition correct, ce qui signifie qu’il doit être gestionnaire de compte, responsable de campagne ou responsable créatif.

**Comment savoir si mon créatif sera copié ? Puis-je voir si mes créatifs utilisent le même partage ?**

L’ID de partage n’est pas fourni dans un [!DNL LinkedIn] , il n’existe donc pas de méthode claire et évidente pour vérifier les mappages créatifs à partager. Si vous pensez qu’un créatif peut être une copie, vous pouvez le vérifier manuellement en ouvrant la publicité depuis votre [!DNL LinkedIn] Gestionnaire de campagnes : permet d’ouvrir la publicité dans un nouvel onglet et de trouver l’ID de partage dans l’URL.

![](assets/six.png)

## FAQ sur Lead Gen Forms {#lead-gen-forms-faq}

**Quel est le coût de cette amélioration ?**

Cette offre est incluse dans les [!DNL Marketo Measure] abonnement.

**L’intégration est-elle rétroactive ?**

Oui, nous téléchargerons les réponses historiques de formulaire de publicité depuis LinkedIn, bien que nous soyons limités à l’intervalle de recherche en amont de 90 jours. Plus la variable [!DNL Marketo Measure] et l’intégration de LinkedIn est activée, plus les points de contact du formulaire de génération de piste sont visibles par l’intermédiaire de [!DNL Marketo Measure].

Il n’existe pas d’option pour définir une date spécifique de téléchargement, mais vous pouvez éventuellement définir des règles de suppression des points de contact si vous devez supprimer des points de contact.

**Cette option sera-t-elle activée automatiquement si j’utilise déjà la variable [!DNL Marketo Measure] Intégration de publicités linkedIn ?**

Non, nous ne commencerons pas automatiquement à le télécharger pour tous les clients, mais c’est un commutateur très simple pour activer cette fonctionnalité dans les paramètres.

**Les données de formulaire sont-elles disponibles ?**

Les données de formulaire sont disponibles via [!DNL Marketo Measure] Découvrez comment inclure l’ID de formulaire et le nom du formulaire. Les détails du formulaire ne sont pas encore disponibles sur les objets de point de contact dans le CRM.

**Qu’advient-il de n’importe quel [!DNL LinkedIn] les pistes qui ont été synchronisées avec les programmes Marketo ou les campagnes CRM ?**

Il est recommandé d’ajuster les [!DNL Marketo Measure] règles pour générer des points de contact à partir de ces programmes ou campagnes spécifiques afin d’éviter la duplication. L’API LinkedIn présente une limite de recherche en amont de 90 jours. Par conséquent, si vous utilisez des règles Marketo ou CRM, il est recommandé de définir la date de fin de la règle sur 90 jours avant la date à laquelle vous avez activé l’intégration dans [!DNL Marketo Measure]. À partir de là, [!DNL Marketo Measure] Vous pouvez télécharger ces pistes pour vous en donner plus d’informations et de détails.

**Le balisage ou le suivi automatique sont-ils impliqués ?**

Non, c&#39;est différent de l&#39;autre [!DNL Marketo Measure] intégrations. Plutôt que de modifier la page d’entrée (puisqu’il n’y a pas de page d’entrée de clic publicitaire), nous téléchargeons uniquement les informations pertinentes à partir de LinkedIn et nous les traitons comme des activités dans [!DNL Marketo Measure].
