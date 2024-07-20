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

L’intégration [!DNL Marketo Measure] à LinkedIn se présente en deux parties :

Contenu sponsorisé : l’intégration du contenu sponsorisé permet à [!DNL Marketo Measure] de baliser les URL de destination sur [!DNL LinkedIn] annonces, ce qui permet finalement à [!DNL Marketo Measure] de suivre un utilisateur à travers tout son parcours de point de contact et de mapper l’activité à l’activité spécifique [!DNL LinkedIn] Campaign et Creative. Cela fournit aux clients des informations sur le retour sur investissement de leur activité [!DNL LinkedIn].

Forms Lead Gen : grâce à l’intégration à LinkedIn Lead Gen Forms, Marketo Measure obtient des informations sur les formulaires qui ont été envoyés par le biais de la plateforme LinkedIn. Ces remplissages de formulaires sont comparés aux prospects de votre instance CRM ou [!DNL Marketo Engage] afin qu’ils soient éligibles pour l’attribution. Grâce aux informations sur les formulaires, les créatifs et les campagnes qui ont contribué à générer les formulaires, les équipes peuvent désormais optimiser davantage leur marketing LinkedIn et leurs dépenses publicitaires.

## Disponibilité {#availability}

Disponible pour tous les utilisateurs.

## Exigences {#requirements}

**Rôles du gestionnaire de campagnes**

Pour que [!DNL Marketo Measure] puisse télécharger les données de coût des publicités et publicités, vous devez disposer de l’un des rôles suivants dans le Gestionnaire de campagnes :

* Administrateur de facturation
* Responsable des comptes
* Gestionnaire de campagnes

En savoir plus : [Rôles utilisateur et fonctions dans Campaign Manager](https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager).

**Rôles d’administration des médias payants**

Pour que [!DNL Marketo Measure] puisse créer/mettre à jour des créatifs sponsorisés, vous devez avoir l’un des rôles d’administrateur de médias payants suivants :

* Affiche de contenu sponsorisé
* Gestionnaire Forms de génération de pistes

En savoir plus : [Rôles d’administration de page LinkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

Il existe d&#39;autres rôles [!DNL LinkedIn] dont nous n&#39;avons **pas** besoin pour notre intégration. Ces rôles sont souvent confondus avec les rôles requis. Notez donc qu’il y a une différence.

**Rôles d’administrateur de page**

Pour que [!DNL Marketo Measure] puisse télécharger/intégrer des pistes à partir de formulaires de génération de piste, vous devez disposer du rôle d’administrateur de page suivant :

* Super administrateur

En savoir plus : [Rôles d’administration de page LinkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

## Types de publicité linkedIn {#linkedin-ad-types}

[!DNL Marketo Measure] prendra en charge :

**Contenu sponsorisé :** Le contenu sponsorisé vous permet de diffuser du contenu au flux [!DNL LinkedIn] des membres au-delà de ceux qui suivent votre entreprise. Le contenu sponsorisé peut être ciblé vers une audience spécifique et peut aider les annonceurs à atteindre les membres [!DNL LinkedIn] chaque fois qu’ils se connectent à la plateforme [!DNL LinkedIn] sur un ordinateur de bureau, un mobile ou une tablette. Le contenu sponsorisé avec Lead Gen Forms est pris en charge.

Les types de formats d’annonces de contenu sponsorisé pris en charge par [!DNL Marketo Measure] sont des annonces avec image unique et des publicités vidéo (via Lead Gen Forms). En raison de la complexité du schéma, nous ne prenons pas en charge les annonces carrousel.

[!DNL Marketo Measure] ne prend pas en charge la messagerie sponsorisée, les publicités textuelles ou les publicités dynamiques.

![](assets/one.png)

>[!TIP]
>
>Pour toutes vos campagnes/dépenses provenant d&#39;une source de contenu non sponsorisé (comme le type de campagne de &quot;publicité texte&quot; ou &quot;sponsorisée dansMail&quot;), [!DNL Marketo Measure] ne prend _pas_ par nature pour le suivi de ces types de campagne. Si vous souhaitez effectuer le suivi des dépenses pour des campagnes comme celles-ci avec votre dépense de &quot;contenu sponsorisé&quot;, veillez à utiliser notre fichier CSV de dépenses marketing pour consigner manuellement ces dépenses.

## Fonctionnement : Contenu sponsorisé {#how-it-works-sponsored-content}

>[!NOTE]
>
>Avant la première utilisation, ce paramètre de fonctionnalité doit être activé en accédant à [!DNL Marketo Measure] [!UICONTROL Paramètres] > [!UICONTROL Intégrations] > [!UICONTROL Publicités] > [!UICONTROL Activer LinkedIn Lead Gen Forms].

**[!DNL LinkedIn's]Exigences uniques de balisage automatique**

[!DNL Marketo Measure] peut vous aider à suivre les performances de votre campagne [!DNL LinkedIn] en balisant automatiquement vos landing pages.

[!DNL Marketo Measure] recherche des créatifs avec un partage LinkedIn unique et ajoute un paramètre `?_bl={creativeId}` à la fin.

**Copie de partages**

Avec cette intégration [!DNL Marketo Measure/LinkedIn], nous demandons aux clients de ne pas copier/cloner/dupliquer des créatifs existants. Si des partages sont détectés et ne sont utilisés que sur un seul élément créatif, [!DNL Marketo Measure] peut baliser le partage en l’état sans avoir à recréer aucun élément créatif ou partage, et l’historique de toutes les publicités (impressions, clics, partages) reste inchangé.

Dès qu’un partage est trouvé pour être partagé sur plusieurs créatifs, [!DNL Marketo Measure] devra passer par un processus de mise en pause, de copie et de rebalisage pour créer un ensemble unique. [!DNL Marketo Measure] interrompt et archive les créatifs en direct et efface donc l’historique des publicités, y compris les impressions, les clics et les partages sur les réseaux sociaux, afin de tout baliser automatiquement correctement.

Désormais, [!DNL Marketo Measure] recommande de ne pas dupliquer de partages [!DNL LinkedIn] et de conserver tous les créatifs et partages aussi uniques que possible afin que nous puissions simplement ajouter notre suivi sans avoir à effacer l’historique des publicités.

**URL raccourcies**

La raison de l’étape supplémentaire est que LinkedIn permet aux URL de destination d’être une URL abrégée (bit.ly, goog.le, etc.), ce qui signifie que [!DNL Marketo Measure] ne voit pas l’URL longue et résolue et [!DNL Marketo Measure] doit ajouter des paramètres de suivi à une URL résolue. Pour contourner ce problème, [!DNL Marketo Measure] recherche des URL raccourcies avant de recréer une publicité, développe l’URL, puis crée la nouvelle publicité avec l’URL résolue et tous ses paramètres, ce qui permet à [!DNL Marketo Measure] d’ajouter des balises. La création d’une nouvelle publicité effacera l’historique des publicités (impressions, clics, partages), d’où la nécessité d’autoriser le balisage des URL raccourcies.

Si vous utilisez massivement des URL raccourcies, cela peut fortement impacter vos créatifs. Nous vous recommandons de ne plus utiliser d’URL raccourcies afin que [!DNL Marketo Measure] puisse baliser les pages d’entrée sans avoir à créer de nouvelles publicités et effacer l’historique des publicités.

**The Process**

Commençons par quelques exemples. Disons que nous avons....

Creative A : Partager 123\
Creative B : Partager 234\
Creative C : Partager 234\
Creative D : Partager 234

![](assets/two.png)

`1)` [!DNL Marketo Measure] parcourra d’abord toutes les campagnes, tous les créatifs et tous les partages avec un état &quot;actif&quot;. [!DNL Marketo Measure] ne marquera pas les publicités suspendues, archivées ou annulées. Si une publicité a été suspendue, puis définie sur [!UICONTROL active], nous la marquerons une fois qu’elle sera à nouveau active. Si nous pouvons trouver un partage unique, ce qui signifie qu’il n’est pas utilisé sur plusieurs créatifs ou campagnes (par exemple, Creative A : Partager 123), [!DNL Marketo Measure] ajoutera notre paramètre personnalisé `>> ?_bl={creativeId}` à l’URL de partage.

`2)` Maintenant, si le partage a été partagé et qu’il a perdu son unicité (par exemple, Creative B : Share 234 and Creative C : Share 234 and Creative D : Share 234), [!DNL Marketo Measure] interrompt et archive tous les créatifs similaires (qui seraient Creative B, Creative C et Creative D).

`3)` [!DNL Marketo Measure] va créer 3 nouveaux créatifs, Creative E, Creative F et Creative G, qui copient le contenu de Creative B, qui est archivé.

`4)` [!DNL Marketo Measure] va également créer 3 nouveaux partages, Partager 345, Partager 456 et Partager 567, qui copie le contenu de Partager 234, mais il aura son propre balisage `?_bl` unique.

`5)` [!DNL Marketo Measure] devra vérifier régulièrement que les partages ne sont pas partagés et, s’ils le font, nous allons redémarrer le processus à l’étape 2 ci-dessus.

>[!NOTE]
>
>La mise en oeuvre de cela signifie que nos clients perdront l’historique des publicités de Creative B : Share 234, Creative C : Share 234 et Creative D : Share 234, car il est désormais recréé avec Creative E : Share 345, Share F : Share 456 et Creative G : Share 567 respectivement.

![](assets/three.png)

## Fonctionnement : Lead Gen Forms {#how-it-works-lead-gen-forms}

**[!DNL LinkedIn's]Exigences uniques de balisage automatique**

[!DNL Marketo Measure] peut vous aider à suivre les performances de votre campagne [!DNL LinkedIn] en balisant automatiquement vos landing pages.

[!DNL Marketo Measure] recherche des créatifs avec un partage LinkedIn unique et ajoute un paramètre `?_bl={creativeId}` à la fin.

**The Process**

Grâce à l’ [!DNL LinkedIn's] API de formulaire d’annonce et l’ API de réponse de formulaire d’annonce , nous pouvons rassembler les données d’envoi de formulaire pour un compte d’annonce et associer l’adresse électronique à un prospect à partir du CRM ou de Marketo.

Les formulaires linkedIn peuvent contenir plusieurs adresses électroniques. Lorsque nous téléchargeons les réponses de formulaire, nous recherchons les adresses électroniques avec la priorité suivante : Adresse électronique professionnelle, Adresse électronique (champ de formulaire principal) ou champs personnalisés avec une valeur de courrier électronique valide.

Quel que soit l’état Campaign ou Creative, toutes les réponses au formulaire auront un point de contact. [!DNL Marketo Measure] a une restriction de recherche arrière de 90 jours, de sorte que [!DNL Marketo Measure] ne peut pas accéder aux réponses de formulaire datant de plus de 90 jours, mais plus l’intégration [!DNL Marketo Measure] et [!DNL LinkedIn] est activée, plus les points de contact du formulaire de génération de piste sont visibles via [!DNL Marketo Measure].

>[!NOTE]
>
>Les coûts linkedIn sont toujours téléchargés dans le cadre des campagnes de contenu sponsorisé.

**Suivi de la génération de piste Forms dans le CRM ou Marketo**

Avant l’existence de l’ [!DNL Marketo Measure] et de l’ intégration Forms LinkedIn Lead Gen , il était courant pour les clients de transmettre leurs envois de formulaire à un programme Marketo et/ou à une campagne CRM afin de suivre les formulaires et de recevoir l’attribution sur ces activités. Une fois que le paramètre Lead Gen Forms est activé, nous voulons nous assurer que ces envois de formulaire ne sont pas comptabilisés deux fois. Vérifiez les éléments suivants :

* Le champ &quot;Activer les points de contact de l’acheteur&quot; sur l’objet CRM est défini sur &quot;Aucun&quot; ou &quot;Exclure tous les membres de campagne&quot;.
* Mettre à jour tout programme Marketo ou règle d’activité Marketo associé
* Mettre à jour les règles de Campaign CRM associées

>[!NOTE]
>
>L’API LinkedIn présente une limite de recherche en amont de 90 jours. Par conséquent, si vous utilisez des règles Marketo ou CRM, il est recommandé de définir la date de fin de la règle sur 90 jours avant la date à laquelle vous avez activé l’intégration dans [!DNL Marketo Measure].

## Détails du Touchpoint {#touchpoint-details}

Une fois que [!DNL Marketo Measure] a balisé correctement votre page d’entrée sur l’élément créatif LinkedIn, vous pouvez afficher les données d’annonces résolues sur le point de contact. Voici le mappage des valeurs de données que vous devriez voir :

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

**&#42;** _Le champ &quot;URL de destination de l’annonce&quot; n’est renseigné que pour le contenu sponsorisé. Il n’est pas renseigné pour le Forms du Lead Gen._

<br>

## Coûts {#costs}

[!DNL Marketo Measure] ayant une intégration directe avec [!DNL LinkedIn], nous téléchargeons les dépenses enregistrées pour chaque campagne et chaque créatif chaque jour. Il n’est plus nécessaire qu’un client signale les dépenses [!DNL LinkedIn] effectuées dans l’application [!DNL Marketo Measure].

Comme pour les autres intégrations d’annonces, [!DNL Marketo Measure] a défini une règle de canal marketing pour placer toutes les campagnes, tous les créatifs et tous les coûts [!DNL LinkedIn]. Pour utiliser la règle, le client souhaite insérer une nouvelle ligne pour ses efforts [!DNL LinkedIn] payants. Il peut s’agir d’un canal nouveau ou existant. Dans la colonne Référent, utilisez la définition &quot;[[!DNL LinkedIn] Payée]&quot; que [!DNL Marketo Measure] a définie comme tout point de contact avec une balise [!DNL Marketo Measure].

![](assets/four.png)

## [!DNL Marketo Measure] Discover {#marketo-measure-discover}

Certaines améliorations ont été apportées à [!DNL Marketo Measure] Discover pour prendre en charge la création de rapports Forms Lead Gen.

**Panorama de médias payants**

Mosaïque Forms de génération de pistes : nouvelle mosaïque qui comprend le nombre de remplissages de formulaires LinkedIn. L’exploration de ce nombre affichera l’ID d’activité, la date du formulaire, le nom du formulaire et l’adresse électronique.

**Panorama des chemins d’engagement**

Parcours des événements : inclut le type d’événement &quot;Activité&quot; et le &quot;formulaire de génération de piste&quot; moyen pour les formulaires issus de l’intégration. La vue d’exploration comprend les détails sur les campagnes, les créatifs et les formulaires.

## FAQ sur le contenu sponsorisé {#sponsored-content-faq}

**Qu’est-ce qu’un partage noir ?**

Un partage obscur est un message où il n’est jamais publié sur la page de l’entreprise et est immédiatement créé et ajouté directement en tant que créatif. Pour que les créatifs créés par [!DNL Marketo Measure] n’apparaissent pas en haut de la page d’une entreprise et soient à nouveau promus, des partages noirs sont utilisés afin qu’ils puissent être lancés en coulisses.

**Quels états [!DNL Marketo Measure] balise-t-il réellement ?**

Il existe quatre statuts différents sur une campagne [!DNL LinkedIn] et sur un compte créatif : actif, en pause, archivé et annulé. Nous marquons uniquement les campagnes et les créatifs actifs. Le balisage d’autres états les redéfinit sur Actif. [!DNL Marketo Measure] ne marquera pas les campagnes ou les créatifs en pause, archivés ou annulés, mais le balisage reprendra si l’état devient Actif.

**Quelle est la valeur que [!DNL Marketo Measure] utilise pour baliser ?**

À la fin de l’URL de destination, [!DNL Marketo Measure] ajoute le paramètre `&_bl={creativeId}`, où `{creativeId}` est l’ID créatif de LinkedIn. Avec l’ID de création, [!DNL Marketo Measure] peut également déterminer l’ID de campagne, étant donné que [!DNL LinkedIn] a une structure de publicités assez basique, car chaque élément créatif ne peut appartenir qu’à une seule campagne.

**Que se passe-t-il avec mon ancien créatif une fois que [!DNL Marketo Measure] en a créé une nouvelle version ?**

Lorsque [!DNL Marketo Measure] recrée un partage et le place dans un nouveau créatif, l’ancien créatif est archivé. C&#39;est également la raison pour laquelle [!DNL Marketo Measure] ne marquera pas les campagnes ou les créatifs archivés, sinon il fonctionnerait en boucle avec [!DNL Marketo Measure] qui essaierait de le marquer indéfiniment.

**Pourquoi l’URL de destination de la publicité créée ne correspond-elle pas à ma publicité d’origine ?**

[!DNL Marketo Measure] doit ajouter les paramètres de suivi à une URL résolue, mais l’URL présentée dans l’API peut potentiellement être une URL raccourcie sans tous les paramètres présents. Pour contourner ce problème, [!DNL Marketo Measure] recherche des URL abrégées avant de recréer un ajout, le résout, puis crée la nouvelle publicité avec l’URL résolue et tous ses paramètres, ce qui permet à [!DNL Marketo Measure] d’ajouter des balises.

**Balisez-vous toutes mes publicités ? Je ne vois pas le paramètre bl sur toutes mes landing pages ?**

Nous avons observé que certains spécialistes du marketing placent un lien d’image dans l’URL de destination, que [!DNL Marketo Measure] ne peut pas baliser, de sorte que nous recherchons l’URL dans le contenu de la publicité. Si [!DNL Marketo Measure] est autorisé à baliser les URL abrégées, nous allons développer l’URL et la balise, mais en raison de la structure de copie de LinkedIn, elle est automatiquement abrégée dans le texte. La balise se trouve dans l’URL abrégée LinkedIn, qui apparaît dans le champ Contenu de la publicité du point de contact plutôt que dans le champ Page d’entrée - Brut .

**Oh non, quelqu&#39;un dans mon équipe a accidentellement cloné un partage. Puis-je le suspendre ?**

Pas de soucis. [!DNL Marketo Measure] recherche par programmation les partages qui ne sont plus uniques, ce qui signifie qu’ils ont depuis été copiés dans un autre créatif. Une fois cette copie détectée, [!DNL Marketo Measure] suit le flux habituel pour baliser et créer de nouvelles publicités.

**Ma publicité était en attente de révision plus tôt. Pourquoi la révision est-elle en attente une fois que [!DNL Marketo Measure] l’a balisé ?**

LinkedIn exige que toutes les publicités créées ou modifiées passent par le processus de sécurité normal avant d’être publiées. [!DNL Marketo Measure] tente d’intercepter la publicité aussi rapidement que possible, car il recherche de nouvelles publicités toutes les 6 heures, mais avec [!DNL LinkedIn's] étape supplémentaire, il peut retarder le lancement de quelques heures.

**Il y a 2 URL dans ma publicité. Lequel est balisé ?**

Les deux. L’intégration [!DNL Marketo Measure] nous permet de baliser l’URL de destination à partir de l’image de clic publicitaire dans la publicité, mais met également automatiquement à jour l’URL abrégée dans la description de la publicité.

![](assets/five.png)

**J’ai connecté mon compte [!DNL LinkedIn ads]. Pourquoi [!DNL Marketo Measure] ne tagging pas mes liens ?**

L&#39;utilisateur [!DNL LinkedIn] connecté doit disposer d&#39;un accès en édition correct, ce qui signifie qu&#39;il doit être gestionnaire de compte, responsable de campagne ou responsable créatif.

**Comment savoir si mon créatif sera copié ? Puis-je voir si mes créatifs utilisent le même partage ?**

L’ID de partage n’est pas fourni dans un rapport [!DNL LinkedIn]. Il n’existe donc pas de méthode claire et évidente pour vérifier les mappages entre créatifs et partages. Si vous pensez qu’un créatif peut être une copie, vous pouvez le vérifier manuellement en ouvrant la publicité dans votre gestionnaire de campagne [!DNL LinkedIn]. Cela ouvre la publicité dans un nouvel onglet et vous pouvez trouver l’ID de partage dans l’URL.

![](assets/six.png)

## FAQ sur Lead Gen Forms {#lead-gen-forms-faq}

**Quel est le coût de cette amélioration ?**

Cette offre est incluse avec tout abonnement [!DNL Marketo Measure] payant.

**L&#39;intégration est-elle rétroactive ?**

Oui, nous téléchargerons les réponses historiques de formulaire de publicité depuis LinkedIn, bien que nous soyons limités à l’intervalle de recherche en amont de 90 jours. Plus l’intégration [!DNL Marketo Measure] et LinkedIn est activée, plus les points de contact de formulaire de génération de piste sont visibles via [!DNL Marketo Measure].

Il n’existe pas d’option pour définir une date spécifique de téléchargement, mais vous pouvez éventuellement définir des règles de suppression des points de contact si vous devez supprimer des points de contact.

**Cela sera-t-il automatiquement activé si j’utilise déjà l’intégration de publicité LinkedIn [!DNL Marketo Measure] ?**

Non, nous ne commencerons pas automatiquement à le télécharger pour tous les clients, mais c’est un commutateur très simple pour activer cette fonctionnalité dans les paramètres.

**Les données de formulaire sont-elles disponibles ?**

Les données de formulaire sont disponibles via [!DNL Marketo Measure] Discover, y compris l’identifiant de formulaire et le nom du formulaire. Les détails du formulaire ne sont pas encore disponibles sur les objets de point de contact dans le CRM.

**Qu’advient-il des [!DNL LinkedIn] pistes qui ont été synchronisées avec des programmes Marketo ou des campagnes CRM ?**

Il est recommandé d’ajuster n’importe quelle règle [!DNL Marketo Measure] pour générer des points de contact à partir de ces programmes ou campagnes spécifiques afin d’éviter la duplication. L’API LinkedIn présente une limite de recherche en amont de 90 jours. Par conséquent, si vous utilisez des règles Marketo ou CRM, il est recommandé de définir la date de fin de la règle sur 90 jours avant la date à laquelle vous avez activé l’intégration dans [!DNL Marketo Measure]. À partir de là, [!DNL Marketo Measure] peut télécharger ces pistes pour vous apporter davantage d’informations et de détails.

**Y a-t-il un balisage automatique ou un suivi impliqué ?**

Non, cela diffère des autres intégrations [!DNL Marketo Measure]. Plutôt que de modifier la page d’entrée (puisqu’il n’y a pas de page d’entrée de clic publicitaire), nous téléchargeons uniquement les informations pertinentes à partir de LinkedIn et nous les traitons comme des activités dans [!DNL Marketo Measure].
