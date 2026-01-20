---
unique-page-id: 35586080
description: Intégration LinkedIn - [!DNL Marketo Measure]
title: Intégration LinkedIn
exl-id: 705209ef-1ece-496c-ac2f-6a31055bd993
feature: APIs, Integration
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '2653'
ht-degree: 1%

---

# Intégration LinkedIn {#linkedin-integration}

## Vue d’ensemble {#overview}

L’intégration de [!DNL Marketo Measure] à LinkedIn se divise en deux parties :

Contenu sponsorisé : l’intégration du contenu sponsorisé [!DNL Marketo Measure] permet de baliser les URL de destination sur les publicités [!DNL LinkedIn], ce qui [!DNL Marketo Measure] permet finalement de suivre un utilisateur à travers l’ensemble de son parcours de points de contact et de mapper l’activité à [!DNL LinkedIn] Campaign et Creative spécifiques. Cela permet aux clients d’obtenir des informations sur le retour sur investissement de leur activité [!DNL LinkedIn].

Forms de génération de leads : grâce à l’intégration au Forms de génération de leads de LinkedIn, Marketo Measure intègre insight aux formulaires qui ont été envoyés via la plateforme LinkedIn. Ces remplissages de formulaires sont associés aux prospects de votre instance CRM ou [!DNL Marketo Engage] afin qu’ils soient éligibles à l’attribution. Grâce à insight dans les campagnes, Creative et formulaires qui a permis de générer les formulaires, les équipes peuvent désormais optimiser leurs dépenses publicitaires et marketing sur LinkedIn.

## Disponibilité {#availability}

Disponible pour tous les utilisateurs.

## Exigences {#requirements}

**Rôles de responsable de campagne**

Pour que [!DNL Marketo Measure] puissiez télécharger les données de coût des données et publicités des publicités, vous devez disposer de l’un des rôles suivants dans le gestionnaire de campagne :

* Administrateur de facturation
* Responsable des comptes
* Responsable de campagne

En savoir plus : [Rôles et fonctions des utilisateurs dans Campaign Manager](https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager).

**Rôles d’administration de médias payants**

Pour que [!DNL Marketo Measure] puissiez créer/mettre à jour des contenus publicitaires sponsorisés, vous devez disposer de l’un des rôles d’administrateur de médias payants suivants :

* Poster de contenu sponsorisé
* Responsable Forms gén. de leads

En savoir plus : [Rôles d’administration de page LinkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

Il y a d&#39;autres rôles [!DNL LinkedIn] que nous n&#39;avons **pas** requis pour notre intégration. Ces rôles sont souvent confondus avec les rôles requis. Notez donc qu’il y a une différence !

**Rôles d’administration de page**

Pour que [!DNL Marketo Measure] puissiez télécharger/intégrer des prospects à partir de formulaires de génération de leads, vous devez disposer du rôle d’administrateur de page suivant :

* Super Administrateur

En savoir plus : [Rôles d’administration de page LinkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

## Types d’annonces LinkedIn {#linkedin-ad-types}

[!DNL Marketo Measure] prend en charge les éléments suivants :

**Contenu sponsorisé :** contenu sponsorisé permet de diffuser du contenu sur le flux [!DNL LinkedIn] des membres au-delà de ceux qui suivent votre entreprise. Le contenu sponsorisé peut être ciblé sur une audience spécifique et peut aider les annonceurs à atteindre les membres du [!DNL LinkedIn] où et quand ils s’engagent sur la plateforme [!DNL LinkedIn] sur un ordinateur, un mobile ou une tablette. Le contenu sponsorisé avec le Forms de génération de leads est pris en charge.

Les types de formats d’annonces de contenu sponsorisé pris en charge par [!DNL Marketo Measure] sont les annonces à image unique et les annonces vidéo (via Lead Gen Forms). En raison de la complexité du schéma, nous ne prenons pas en charge les annonces de carrousel.

[!DNL Marketo Measure] ne prend pas en charge les messages sponsorisés, les annonces textuelles ou les annonces dynamiques.

![](assets/one.png)

>[!TIP]
>
>Pour toutes vos campagnes/dépenses provenant d’une source de contenu non sponsorisé (tel que le type de campagne « Annonce texte » ou « InMail sponsorisé »), [!DNL Marketo Measure] ne prend _pas_ en soi le suivi de ces types de campagnes. Si vous souhaitez suivre les dépenses pour des campagnes telles que celles-ci en même temps que vos dépenses « Contenu sponsorisé », veillez à utiliser notre fichier CSV Dépenses marketing pour consigner manuellement lesdites dépenses.

## Fonctionnement : contenu sponsorisé {#how-it-works-sponsored-content}

>[!NOTE]
>
>Avant la première utilisation, ce paramètre de fonctionnalité doit être activé en accédant à [!DNL Marketo Measure] [!UICONTROL Paramètres] > [!UICONTROL Intégrations] > [!UICONTROL Publicités] > [!UICONTROL Activer le Forms de génération de leads LinkedIn].

**[!DNL LinkedIn's]des exigences de balisage automatique uniques**

[!DNL Marketo Measure] pouvez suivre les performances de votre campagne [!DNL LinkedIn] en identifiant automatiquement vos pages de destination.

[!DNL Marketo Measure] recherchera des contenus publicitaires avec un partage LinkedIn unique et ajoutera un paramètre de `?_bl={creativeId}` à la fin.

**Copie de partages**

Avec cette intégration [!DNL Marketo Measure/LinkedIn], nous demandons aux clients de ne pas copier/cloner/dupliquer les contenus publicitaires existants. Si des partages sont détectés et ne sont utilisés que sur un seul Creative, [!DNL Marketo Measure] pouvez les baliser tels quels sans avoir à recréer de contenu publicitaire ou de partages et l’historique de toutes les publicités (impressions, clics, partages) restera.

Dès qu’un partage est partagé entre plusieurs contenus publicitaires, [!DNL Marketo Measure] devez effectuer un processus de mise en pause, de copie et de rebalisage pour créer un ensemble unique. [!DNL Marketo Measure] va suspendre et archiver les contenus publicitaires en direct et par conséquent supprimer l’historique des publicités, y compris les impressions, les clics et les partages sur les réseaux sociaux, afin de tout baliser automatiquement correctement.

À l’avenir, [!DNL Marketo Measure] vous recommande de ne pas dupliquer de partages [!DNL LinkedIn] et de garder tous les contenus publicitaires et partages aussi uniques que possible, afin que nous puissions simplement ajouter notre suivi sans avoir à effacer l’historique de publicités.

**URL raccourcies**

La raison de cette étape supplémentaire est que LinkedIn permet aux URL de destination d’être une URL raccourcie (bit.ly, goog.le, etc.), ce qui signifie que [!DNL Marketo Measure] ne voit pas l’URL longue résolue et que [!DNL Marketo Measure] doit ajouter des paramètres de suivi à une URL résolue. Pour contourner ce problème, [!DNL Marketo Measure] recherche des URL raccourcies avant de recréer une publicité, développe l’URL, puis crée la nouvelle publicité avec l’URL résolue et tous ses paramètres, ce qui [!DNL Marketo Measure] permet d’ajouter des balises. La création d’une nouvelle publicité effacera l’historique des publicités (impressions, clics, partages), d’où la nécessité d’obtenir des autorisations pour baliser les URL raccourcies.

L’utilisation intensive d’URL raccourcies peut avoir de graves répercussions sur vos contenus publicitaires. Nous vous recommandons de ne plus utiliser d’URL raccourcies afin que [!DNL Marketo Measure] puissiez baliser les pages de destination sans avoir à créer de nouvelles annonces et à effacer l’historique des annonces.

**Le processus**

Commençons par quelques exemples. Disons que nous l&#39;avons fait....

Creative A : Partage 123\
Creative B : partage 234\
Creative C : Partager 234\
Creative D : Partager 234

![](assets/two.png)

`1)` [!DNL Marketo Measure] va d’abord parcourir toutes les campagnes, les contenus publicitaires et les partages ayant un statut « Actif ». [!DNL Marketo Measure] publicités ne seront pas marquées comme suspendues, archivées ou annulées. Si une publicité a été mise en pause, puis définie sur [!UICONTROL active], nous la marquerons une fois qu’elle sera à nouveau active. Si nous trouvons un Partage unique, ce qui signifie qu’il n’est pas utilisé dans plusieurs contenus publicitaires ou campagnes (par exemple, Creative A : Partager 123), [!DNL Marketo Measure] ajouterons notre `>> ?_bl={creativeId}` de paramètre personnalisé à l’URL de partage.

`2)` Maintenant, si le partage a été partagé et a perdu son unicité (par exemple, Creative B : partage 234 et Creative C : partage 234 et Creative D : partage 234), [!DNL Marketo Measure] va suspendre et archiver tous les contenus publicitaires similaires (qui seraient Creative B, Creative C et Creative D).

`3)` [!DNL Marketo Measure] créera 3 nouveaux contenus publicitaires, Creative E, Creative F et Creative G, qui copieront le contenu de Creative B, qui sera archivé.

`4)` [!DNL Marketo Measure] créera également 3 nouvelles actions, Share 345, Share 456 et Share 567, qui copieront le contenu de Share 234, mais elle aura son propre balisage `?_bl` unique.

`5)` [!DNL Marketo Measure] devrez vérifier régulièrement que les partages ne sont pas partagés et, s’ils le sont, nous relancerons le processus à l’étape 2 ci-dessus.

>[!NOTE]
>
>Si vous implémentez ceci, vos clients perdront l’historique des publicités de Creative B : Share 234, Creative C : Share 234 et Creative D : Share 234, car celui-ci est maintenant recréé avec Creative E : Share 345, Share F : Share 456 et Creative G : Share 567, respectivement.

![](assets/three.png)

## Fonctionnement : Forms gén. de leads {#how-it-works-lead-gen-forms}

**[!DNL LinkedIn's]des exigences de balisage automatique uniques**

[!DNL Marketo Measure] pouvez suivre les performances de votre campagne [!DNL LinkedIn] en identifiant automatiquement vos pages de destination.

[!DNL Marketo Measure] recherchera des contenus publicitaires avec un partage LinkedIn unique et ajoutera un paramètre de `?_bl={creativeId}` à la fin.

**Le processus**

Grâce à [!DNL LinkedIn's]’API de formulaire publicitaire et à l’API de réponse de formulaire publicitaire, nous pouvons collecter les données d’envoi de formulaire pour un compte publicitaire et associer l’adresse e-mail à un prospect à partir du CRM ou de Marketo.

Les formulaires LinkedIn peuvent contenir plusieurs adresses e-mail. Lorsque nous téléchargeons des réponses de formulaire, nous recherchons des adresses e-mail avec la priorité suivante : E-mail professionnel, Adresse e-mail (champ de formulaire principal) ou champs personnalisés avec une valeur d’e-mail valide.

Quel que soit le statut de Campaign ou de Creative, toutes les réponses de formulaire génèrent un point de contact. [!DNL Marketo Measure] dispose d’une restriction de recherche en amont de 90 jours. [!DNL Marketo Measure] ne peut donc pas accéder aux réponses de formulaire datant de plus de 90 jours, mais plus l’intégration [!DNL Marketo Measure] et [!DNL LinkedIn] est activée, plus les points de contact du formulaire de génération de leads seront visibles via [!DNL Marketo Measure].

>[!NOTE]
>
>Les coûts LinkedIn sont toujours téléchargés dans le cadre des campagnes de contenu sponsorisées.

**Forms de génération de leads de suivi dans CRM ou Marketo**

Avant l’intégration de Forms de génération de leads [!DNL Marketo Measure] et LinkedIn, il était courant pour les clients de pousser leurs envois de formulaires vers un programme Marketo et/ou une campagne CRM pour suivre les formulaires et recevoir l’attribution sur ces activités. Une fois que le paramètre Forms de génération de leads est activé, nous voulons nous assurer que ces envois de formulaires ne sont pas comptabilisés deux fois. Vérifiez les points suivants :

* Le champ « Activer les points de contact de l’acheteur » de l’objet CRM est défini sur « Aucun » ou « Exclure tous les membres de la campagne »
* Mettre à jour tout programme Marketo ou toute règle d’activité Marketo associée
* Mettre à jour toutes les règles de campagne CRM associées

>[!NOTE]
>
>L’API LinkedIn est limitée à 90 jours de recherche en amont. Par conséquent, si vous utilisez des règles Marketo ou CRM, il est recommandé de définir la date de fin de la règle sur 90 jours avant la date d’activation de l’intégration dans [!DNL Marketo Measure].

## Détails du Touchpoint {#touchpoint-details}

Une fois que [!DNL Marketo Measure] a balisé votre page de destination sur le contenu créatif LinkedIn, vous pouvez afficher les données de publicités résolues sur le point de contact. Voici le mappage des valeurs de données que vous devriez vous attendre à voir :

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
   <td>Id De L’Annonce Publicitaire</td>
   <td>84186224</td>
  </tr> 
  <tr> 
   <td>Contenu publicitaire</td>
   <td>copy-1-image-2-man 95 % des spécialistes #B2B marketing considèrent que la stratégie de création de demande est une réussite. En savoir plus : [!DNL https]://lnkd.in/jgdi50vKrgv</td>
  </tr> 
  <tr> 
   <td>ID de groupe publicitaire</td>
   <td>(vide)</td>
  </tr> 
  <tr> 
   <td>Nom de groupe publicitaire</td>
   <td>(vide)</td>
  </tr> 
  <tr> 
   <td>ID de campagne publicitaire</td>
   <td>138949954</td>
  </tr> 
  <tr> 
   <td>Nom de la campagne publicitaire</td>
   <td>SU - Comptes COM - Compétences à la demande</td>
  </tr> 
  <tr> 
   <td>Ajouter l’URL de destination <b>*</b></td>
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
   <td>Id Du Mot-Clé</td> 
   <td>(vide)</td> 
  </tr> 
  <tr> 
   <td>Type de correspondance de mots-clés</td> 
   <td>(vide)</td> 
  </tr> 
  <tr> 
   <td>Page de destination</td> 
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders</td> 
  </tr> 
  <tr> 
   <td>Page de destination - Brute</td> 
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217</td> 
  </tr> 
  <tr> 
   <td>Canal marketing</td> 
   <td>Référencement social payant</td> 
  </tr> 
  <tr> 
   <td>Canal marketing - Chemin</td> 
   <td>Réseaux sociaux payants.LinkedIn</td> 
  </tr> 
  <tr> 
   <td>Support</td> 
   <td>« cpc » ou « formulaire gén. de lead »</td> 
  </tr> 
  <tr> 
   <td>Page du référent</td> 
   <td>www.linkedin.com/</td> 
  </tr> 
  <tr> 
   <td>Page du référent - brute</td> 
   <td>www.linkedin.com/</td> 
  </tr> 
  <tr> 
   <td>Phrase de recherche</td> 
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

**&#42;** champ _« URL de destination de l’annonce publicitaire » n’est renseigné que pour le contenu sponsorisé. Il n’est pas renseigné pour le Forms de génération de leads._

<br>

## Coûts {#costs}

[!DNL Marketo Measure] ayant une intégration directe avec [!DNL LinkedIn], nous téléchargeons quotidiennement les dépenses enregistrées pour chaque campagne et Creative. Il n’est plus nécessaire pour un client de générer des rapports sur [!DNL LinkedIn] dépenses dans l’application [!DNL Marketo Measure].

Comme pour d’autres intégrations d’annonces, [!DNL Marketo Measure] a défini une règle de canal marketing pour placer toutes les campagnes [!DNL LinkedIn], les contenus publicitaires et les coûts. Pour utiliser la règle, le client souhaite insérer une nouvelle ligne pour ses efforts de [!DNL LinkedIn] payante. Il peut s’agir d’un canal nouveau ou existant. Dans la colonne Référent , utilisez la définition « [[!DNL LinkedIn] Payant] » que [!DNL Marketo Measure] a définie comme n’importe quel point de contact avec une balise [!DNL Marketo Measure].

![](assets/four.png)

## [!DNL Marketo Measure] Discover {#marketo-measure-discover}

Des améliorations ont été apportées à [!DNL Marketo Measure] Discover pour prendre en charge la création de rapports de Forms de génération de leads.

**Paid Media Board**

Mosaïque Forms de génération de leads : nouvelle mosaïque qui comprend le nombre de remplissages de formulaires LinkedIn. L’exploration en amont de ce nombre affiche l’ID d’activité, la date du formulaire, le nom du formulaire et l’adresse électronique.

**Tableau du chemin d’engagement**

Parcours d’événements : inclut le type d’événement « Activité » et le format intermédiaire « Formulaire de génération de leads » pour les formulaires qui passent par l’intégration. La vue d’exploration comprend les détails de la campagne, du Creative et du formulaire.

## FAQ sur le contenu sponsorisé {#sponsored-content-faq}

**Qu’est-ce qu’un partage sombre ?**

Un partage sombre est une publication qui n’est jamais publiée sur la page de la société et qui est immédiatement créée et ajoutée directement en tant que Creative. Pour que les créatifs créés par [!DNL Marketo Measure] n&#39;apparaissent pas en haut de la page d&#39;une entreprise et soient promus à nouveau, les partages sombres sont utilisés afin qu&#39;ils puissent être lancés en coulisses.

**Quels statuts [!DNL Marketo Measure]-t-il réellement baliser ?**

Il existe quatre statuts différents pour une campagne [!DNL LinkedIn] et Creative : Actif, En pause, Archivé et Annulé. Nous n’étiquetons que les campagnes et les contenus publicitaires actifs. Le balisage d’autres statuts les a définis sur Actif à nouveau. [!DNL Marketo Measure] ne balisera pas les campagnes en pause, archivées ou annulées ni les contenus publicitaires, mais reprendra le balisage si le statut passe à Actif.

**Quelle est la valeur que [!DNL Marketo Measure] utilise pour baliser ?**

À la fin de l’URL de destination, [!DNL Marketo Measure] ajoute le paramètre `&_bl={creativeId}`, où le `{creativeId}` correspond à l’ID Creative provenant de LinkedIn. Avec l’identifiant Creative, [!DNL Marketo Measure] pouvez également déterminer l’identifiant de campagne, car [!DNL LinkedIn] dispose d’une structure publicitaire assez basique, chaque Creative ne pouvant appartenir qu’à une seule campagne.

**Que se passe-t-il avec mon ancien contenu créatif une fois que [!DNL Marketo Measure] en crée une nouvelle version ?**

Lorsque [!DNL Marketo Measure] recrée un partage et le place dans un nouveau Creative, l’ancien Creative est archivé. C’est également la raison pour laquelle [!DNL Marketo Measure] ne balisera pas les campagnes ou les contenus publicitaires archivés. En effet, dans le cas contraire, [!DNL Marketo Measure] les baliserait indéfiniment.

**Pourquoi l’URL de destination de l’annonce créée ne correspond-elle pas à mon annonce d’origine ?**

[!DNL Marketo Measure] doit ajouter les paramètres de tracking à une URL résolue, mais l’URL présentée dans l’API peut éventuellement être une URL abrégée sans tous les paramètres présents. Pour contourner ce problème, [!DNL Marketo Measure] recherche des URL raccourcies avant de recréer un ajout, le résout, puis crée la nouvelle annonce avec l’URL résolue et tous ses paramètres, ce qui [!DNL Marketo Measure] permet d’ajouter des balises.

**Étiquetez-vous toutes mes publicités ? Je ne vois pas le paramètre bl sur toutes mes pages de destination ?**

Nous avons observé que certains professionnels du marketing placent un lien d’image dans l’URL de destination, que [!DNL Marketo Measure] ne pouvez pas baliser. Nous recherchons donc l’URL dans le contenu publicitaire. Si [!DNL Marketo Measure] est autorisé à baliser les URL raccourcies, nous développerons l’URL et la balise, mais en raison de la structure de copie de LinkedIn, elle est automatiquement raccourcie dans le texte. La balise se trouve dans l’URL abrégée LinkedIn, qui apparaît dans le champ Contenu publicitaire du point de contact plutôt que dans le champ Page de destination - Données brutes .

**Oh non, quelqu&#39;un de mon équipe a accidentellement cloné un partage. Puis-je le mettre en pause ?**

Pas de soucis. [!DNL Marketo Measure] vérifie par programmation les partages qui ne sont plus uniques, ce qui signifie qu’ils ont depuis été copiés dans un autre Creative. Une fois cette copie détectée, [!DNL Marketo Measure] suit le flux habituel pour marquer et créer de nouvelles annonces.

**Mon annonce était en attente de révision auparavant. Pourquoi cet élément est-il en attente d’examen une fois qu’[!DNL Marketo Measure] l’a balisé ?**

LinkedIn exige que toutes les publicités créées ou modifiées passent par le processus de sécurité normal avant d&#39;être publiées. [!DNL Marketo Measure] essaie d’intercepter la publicité le plus rapidement possible, car il recherche de nouvelles publicités toutes les 6 heures, mais avec [!DNL LinkedIn's] étape supplémentaire, il peut retarder le lancement de quelques heures.

**Il y a 2 URL sur mon annonce. Lequel est marqué ?**

Les deux. L’intégration de [!DNL Marketo Measure] nous permet de baliser l’URL de destination à partir de l’image de clics publicitaires dans la publicité, mais elle met également automatiquement à jour l’URL raccourcie dans la description de la publicité.

![](assets/five.png)

**J&#39;ai connecté mon compte [!DNL LinkedIn ads]. Pourquoi mes liens ne sont-ils [!DNL Marketo Measure] balisés ?**

L’utilisateur [!DNL LinkedIn] connecté doit disposer d’un accès en modification approprié, ce qui signifie qu’il doit être un gestionnaire de compte, de campagne ou de Creative Manager.

**Comment savoir si mon contenu créatif sera copié ? Puis-je voir si mes créatifs utilisent la même part ?**

L’identifiant de partage n’est pas fourni dans un rapport [!DNL LinkedIn]. Il n’existe donc pas de moyen clair et évident de vérifier les mappages de contenu créatif à partager. Si vous pensez qu’un contenu publicitaire pourrait être une copie, vous pouvez vérifier manuellement en ouvrant l’annonce depuis votre gestionnaire [!DNL LinkedIn] Campaign. L’annonce s’ouvre alors dans un nouvel onglet et l’identifiant de partage est disponible dans l’URL.

![](assets/six.png)

## FAQ sur le Forms de génération de leads {#lead-gen-forms-faq}

**Quel est le coût de cette amélioration ?**

Cette offre est incluse avec tout abonnement payant à [!DNL Marketo Measure].

**L’intégration est-elle rétroactive ?**

Oui, nous téléchargerons les réponses historiques aux formulaires publicitaires à partir de LinkedIn, bien que nous soyons limités à l’intervalle de recherche en amont de 90 jours. Plus l’intégration [!DNL Marketo Measure] et LinkedIn est activée longtemps, plus les points de contact du formulaire de génération de leads seront visibles via [!DNL Marketo Measure].

Il n’existe pas d’option permettant de définir une date de téléchargement spécifique, mais vous pouvez éventuellement définir des règles de suppression de point de contact si vous devez supprimer des points de contact.

**Cela sera-t-il automatiquement activé si j’utilise déjà l’intégration publicitaire [!DNL Marketo Measure] LinkedIn ?**

Non, nous ne commencerons pas automatiquement à le télécharger pour tous les clients, mais il s&#39;agit d&#39;un changement très simple pour activer cette fonctionnalité dans les paramètres.

**Les données de formulaire sont-elles disponibles ?**

Les données de formulaire sont disponibles via [!DNL Marketo Measure] Discover, y compris l’ID et le nom du formulaire. Les détails du formulaire ne sont pas encore disponibles sur les objets de point de contact dans le CRM.

**Qu’advient-il des prospects [!DNL LinkedIn] qui ont été synchronisés précédemment avec les programmes Marketo ou les campagnes CRM ?**

Il est recommandé d’ajuster les règles de [!DNL Marketo Measure] pour générer des points de contact à partir de ces programmes ou campagnes spécifiques afin d’éviter la duplication. L’API LinkedIn est limitée à 90 jours de recherche en amont. Par conséquent, si vous utilisez des règles Marketo ou CRM, il est recommandé de définir la date de fin de la règle sur 90 jours avant la date d’activation de l’intégration dans [!DNL Marketo Measure]. À partir de maintenant, [!DNL Marketo Measure] pouvez télécharger ces prospects pour vous avec plus d’insight et de détails.

**Y a-t-il un balisage ou un suivi automatique impliqués ?**

Non, cela diffère des autres intégrations [!DNL Marketo Measure]. Plutôt que de modifier la landing page (puisqu’il n&#39;y a pas de clic sur la landing page), nous téléchargeons uniquement les informations pertinentes depuis LinkedIn et les traitons comme des activités dans [!DNL Marketo Measure].
