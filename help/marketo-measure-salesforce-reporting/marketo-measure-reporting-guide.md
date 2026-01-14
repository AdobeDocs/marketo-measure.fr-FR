---
description: Guide de création de rapports [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Guide de création de rapports [!DNL Marketo Measure]
exl-id: 9b991f9e-c187-4b43-b0a8-8ed3e9a6056b
feature: Reporting
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '6506'
ht-degree: 2%

---

# Guide de création de rapports [!DNL Marketo Measure] {#marketo-measure-reporting-guide}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Avant de créer un rapport [!DNL Marketo Measure], il est essentiel de confirmer que les paramètres de votre compte [!DNL Marketo Measure] ont été examinés et configurés afin de vous assurer que les données contenues dans les rapports sont exactes et reflètent les spécificités de votre entreprise. En outre, les projets de création de rapports fonctionnent mieux lorsqu’ils suivent un processus structuré. Justin Norris, un [!DNL Marketo Measure] utilisateur, défenseur et partenaire de [Perkuto](https://perkuto.com/) a résumé avec expertise [comment aborder le reporting dans  [!DNL Marketo Measure]](https://perkuto.com/blog/turning-attribution-data-into-actionable-insights/) :

**Établir des objectifs** : « La première question à se poser est « pourquoi mesurer ? » Lori Wizdo de [Forrester Research](https://go.forrester.com/) l&#39;a bien résumé dans un webinaire [Marketo](https://www.marketo.com/webinars/beyond-revenue-performance-real-kpis-of-b2b-marketing/). Selon elle, «nous mesurons pour prouver ou valider une décision ou la valeur du marketing ou pour obtenir mieux (amélioration du processus).» Nous ajouterions que les données tirées d&#39;une bonne mesure fournissent également des données et des conseils pour le processus de planification du marketing.

Donc, avant de commencer, il est essentiel d&#39;être parfaitement clair sur vos objectifs, les questions auxquelles vous essayez de répondre ou les problèmes que vous essayez de résoudre. Quelle histoire voulez-vous raconter ? Quelles seront les décisions qui en découleront? Trop souvent, ces principes fondamentaux sont mal conçus, ce qui entraîne une frustration pour toutes les parties concernées. »

**Conception de rapport** : « Ensuite, vous devez concevoir le rapport et déterminer les dimensions, mesures et jeux de données spécifiques qu’il contiendra. Une expérience courante consiste à fournir à un utilisateur chargé de la conception de parcours exactement ce qu’il demande, uniquement pour qu’il ou elle ait toujours le sentiment que ses besoins ne sont pas satisfaits. En effet, l’insight qu’une personne utilisatrice professionnelle recherche n’est pas toujours contenue dans le rapport qu’elle demande. Un bon analyste (ou une personne du SPM qui a un rôle d&#39;analyste) posera des questions pour clarifier les choses, établira des définitions communes (« qu&#39;entendez-vous vraiment par « plomb ») et dressera même un portrait du rapport final pour s&#39;assurer qu&#39;il y a harmonisation. Ce n’est qu’à ce moment que vous créez le rapport, en sachant que vous avez un ensemble solide d’exigences. »

**Report Build** : « Une fois la génération effectuée, il n’est pas rare de se heurter à des obstacles ou des impasses. Par exemple, vous pouvez découvrir que vous ne disposez pas d’un point de données essentiel ou que vos objets ne se lient pas de la manière dont vous le souhaitez. Pour résoudre ces problèmes, je pense également qu&#39;il est essentiel de comprendre ce qui se passe « sous le capot » dans votre « machine » de création de rapports. Cette maîtrise vous permettra de dimensionner rapidement une demande de création de rapports et d’évaluer si elle est réalisable (et de concevoir plus facilement des solutions créatives lorsqu’elle ne l’est pas). »

Jetons un coup d’œil « sous le capot » pour mieux comprendre ce qui fait fonctionner la machine de création de rapports d’attribution [!DNL Marketo Measure].

## Objets Buyer Touchpoint (CRM) {#buyer-touchpoint-objects-crm}

Au niveau le plus élevé, il existe deux catégories de création de rapports basées sur les deux différents objets Buyer Touchpoint : ces catégories déterminent le type de données de [!DNL Marketo Measure] sur lesquelles vous souhaitez créer des rapports : les données liées à un _individu_ ou les données liées à une _opportunité_.

1. **Points de contact de l’acheteur** (BT) / Individus / Engagement total

   * Généralement utilisé pour les mesures et les rapports « top of the funnel » (TOFU) liés aux _individus_ (prospects, contacts [!DNL Marketo Measure] personnes)
   * Les BT sont utilisés pour comprendre toutes les interactions marketing liées aux **personnes**, car ils contiennent l’historique complet des points de contact pour chaque personne. Pour rappel, ces points de contact sont créés dans CRM pour le premier contact anonyme, le contact de création de lead, ainsi que pour tout envoi de formulaire ou point de contact ultérieur que vous choisissez de synchroniser
une campagne ou une activité hors ligne.

1. **Points de contact d’attribution de l’acheteur** (BAT) / Opportunité / Niveau de compte / Chiffre d’affaires

   * Généralement utilisé pour les mesures et les rapports « au milieu et/ou en bas du funnel » (MOFU et BOFU) liés à _Opportunités_.
   * Les BAT représentent les points de contact pertinents de toutes les personnes connectées à l’**opportunité** (via les rôles de contact d’opportunité ou un identifiant de compte partagé, selon vos paramètres). Contrairement aux MTD qui ne concernent que les personnes, les MTD peuvent également être associées aux **recettes**. Par conséquent, vous utiliserez les MTD pour répondre aux questions relatives aux opportunités, y compris le nombre d’opportunités ouvertes ou fermées, ou la valeur du pipeline et le chiffre d’affaires gagné.

>[!NOTE]
>
>Les MTD sont créées à partir des BT. Essentiellement, le suivi commence au niveau individuel par l&#39;intermédiaire des BT. Une fois qu’une opportunité est créée sur un compte, tous les BT des contacts appartenant au même compte sont référencés et éligibles à la création de BAT qui se rapportent à l’opportunité. Vous souhaiterez donc utiliser l’un ou l’autre selon les questions auxquelles vous tentez de répondre : les questions liées aux mesures « Personnes » (rapports BT) ou les questions liées aux mesures « Opportunités » (rapports BAT)

Article d’assistance : [différence entre les points de contact de l’acheteur et les points de contact d’attribution de l’acheteur](/help/configuration-and-setup/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md)

## Point de contact acheteur (BT) {#buyer-touchpoint-bt}

Le Buyer Touchpoint (BT) est l’objet utilisé pour effectuer le suivi de chaque interaction marketing qu’une personne entretient avec vos ressources marketing. Le parcours de chaque personne (lead/contact/personne [!DNL Marketo Measure]) serait représenté par les BT qui lui sont associés. En [!DNL Marketo Measure], le parcours d&#39;un individu comprend :

1. Comment cette personne a-t-elle interagi pour la première fois avec notre marque ? (Première touche ou _FT_)
1. Comment cette personne a-t-elle effectué sa conversion/est-elle devenue un prospect ? (Création de lead ou _LC_)
1. De quelle autre manière cette personne a-t-elle interagi avec notre marque et nos supports marketing depuis qu’elle est devenue Lead ? (_PostLC_)

Les points de contact de l’acheteur sont utilisés pour répondre aux questions liées aux _personnes_ (« personnes » sont représentées par des leads ou des contacts dans un CRM), telles que la génération de leads/contacts ou les mesures d’acquisition, plutôt que par des mesures liées aux opportunités. Par exemple :

* Quels canaux diffusent le plus de leads ?
* Quels canaux sont plus ou moins coûteux pour créer un nouveau prospect ?
* Avec quel contenu mes leads/contacts interagissent-ils ?
* Quelle est l’histoire marketing de titres, rôles et personnages spécifiques ?
* Quels canaux génèrent des MQL ou d’autres statuts de lead/contact ?

En premier lieu, les entreprises doivent savoir « d’où viennent mes Leads/Contacts ? ». Historiquement, la réponse à cette question était donnée par une seule valeur dimensionnelle (Source de lead, par exemple). Cependant, comme indiqué dans les sections #1 et #2 ci-dessus, nous savons que les prospects peuvent avoir plusieurs points de contact au cours de leur parcours de devenir un prospect. Le Buyer Touchpoint nous permet d’amener insight dans les deux interactions les plus cruciales qui représentent la manière dont un lead a été généré : sa première touche et sa touche de création de lead. Les points de contact de l’acheteur sont également _multidimensionnels_ ce qui signifie qu’ils contiennent une grande quantité de données marketing, principalement l’origine de la personne (canal marketing) et ce avec quoi elle s’est engagée (contenu).

Les [modèles d’attribution](/help/attribution-models.md) qui fournissent le meilleur d’insight pour les mesures basées sur les personnes sont les suivants :

* **Première touche** - Crédit d’attribution 100 % au premier contact du prospect (FT)
* **Création de lead** - Crédit d’attribution de 100 % à l’interface de création de lead (LC) du lead
* **En U** - approche multipoint, avec 40 % de crédit au FT, 40 % de crédit au LC

<table>
 <tbody>
  <tr>
   <td>&lt;img alt=« bizible guide 1 » src= »assets/bizible-guide-1.png »</td>
   <td>Le modèle en U est conçu pour reconnaître les points de contact de l’acheteur qui résument la façon dont un prospect est devenu un prospect. Bien qu’il soit possible de signaler les points de contact suivants de ces prospects pour expliquer un engagement supplémentaire (post LC), ils ne font pas partie du <strong>parcours de création de leads</strong> ils n’obtiennent donc aucun crédit d’attribution dans les modèles FT, LC ou en forme de U.<p>

&#42;Le plus souvent, l’attribution en U reflète une répartition égale de 50/50 entre FT et LC. Si le prospect effectue une conversion dans la même session que le premier contact, un seul point de contact représenterait les positions des points de contact FT et LC. Par conséquent, 100 % de l’attribution serait attribuée à un seul point de contact.</td>
</tr>
 </tbody>
</table>

Ces modèles mettent fortement l’accent sur les interactions à un stade précoce et l’engagement de funnel. L’attribution en U est le modèle recommandé, car elle tient compte des points de contact FT et LC, ce qui garantit que tout contact ayant influencé le prospect dans sa création est crédité. Cependant, il est possible d’obtenir des insight supplémentaires à partir des modèles Première touche et Étape de création de lead si vous souhaitez approfondir votre compréhension de ces parties spécifiques du parcours de lead.

## Rapports recommandés à l’aide de Buyer Touchpoint (BT) {#recommended-reports-using-the-buyer-touchpoint-bt}

1. **LEADS avec points de contact ACHETEUR**

**1,1 | Nouveaux leads par canal marketing**

La synthèse des données Buyer Touchpoint de votre prospect par le champ « Canal marketing » est la vue de plus haut niveau qui représente les canaux/tactiques qui influencent les nouveaux prospects dans la création. La structuration de ce rapport autour d’un « Type de date » = « Date de création » garantit l’établissement d’une cohorte de « nouveaux prospects nets » (lorsque le prospect a été créé dans votre CRM) dans le rapport.

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels canaux marketing influencent les prospects lors de la création ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Leads et points de contact des acheteurs (CRM)<br>
   Mesure : Leads ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date de création du lead (CRM)/Date de création (Discover)</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Canal marketing</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td>Première Touche, Création De Lead, <strong>En U</strong><br>
   *ADDITIONNEZ les champs « Comptage » dans vos rapports CRM (Nombre - Première touche, Nombre - Création de lead, Nombre - En forme de U).</td>
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout type de rapport « Leads avec points de contact d’acheteur », commencez par personnaliser le rapport préconfiguré intitulé « [!DNL Marketo Measure] 101 » | Leads par canal ». Ce rapport prêt à l’emploi est un excellent sandbox préconfiguré, comme décrit dans le tableau ci-dessus, et peut rapidement être personnalisé pour des besoins de création de rapports plus spécifiques.

1,2 **| Nouveaux leads par campagne (ou informations plus granulaires)**

Pour une insight plus granulaire dans les données résumées dans le rapport « Nouveaux leads par canal marketing » (1.1), ajoutez un résumé supplémentaire au niveau de la campagne. Cela vous permettra non seulement de comprendre quels « canaux marketing » poussent de nouveaux prospects à la création, mais plus spécifiquement, quelles campagnes de ces canaux ont les meilleures performances :

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quelles <i>campagnes</i> influencent les leads dans la création ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Leads et points de contact des acheteurs (CRM)<br>
   Mesure : Leads ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date de création du lead (CRM)/Date de création (Discover)</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Nom de la campagne publicitaire (CRM)</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td>Première Touche, Création De Lead, <strong>En U</strong><br>
   *ADDITIONNEZ les champs « Comptage » dans vos rapports CRM (Nombre - Première touche, Nombre - Création de lead, Nombre - En forme de U).</td>
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Obtenez une insight encore plus granulaire en résumant le rapport avec d’autres champs disponibles à partir de l’objet Buyer Touchpoint. Pour ce faire, définissez des regroupements (CRM) ou des dimensions supplémentaires (Découvrir). Selon le canal (qui peut être représentatif de votre rôle), il peut y avoir des détails supplémentaires au-delà du niveau de la campagne dans laquelle vous souhaitez obtenir insight. Accédons à « Référencement payant » par exemple dans le tableau ci-dessous...

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels <i>mots-clés</i> influencent les leads dans la création ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Leads et points de contact des acheteurs (CRM)<br>
   Mesure : Leads ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td>Canal marketing = référencement payant</td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date de création du lead (CRM)/Date de création (Discover)</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Texte du mot-clé (CRM) / Mot-clé (Discover)</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td>Première Touche, Création De Lead, <strong>En U</strong><br>
   *ADDITIONNEZ les champs « Comptage » dans vos rapports CRM (Nombre - Première touche, Nombre - Création de lead, Nombre - En forme de U).</td>
  </tr>
 </tbody>
</table>

Le niveau de granularité peut varier en fonction du canal. L’approche recommandée serait de vous demander : « Qu’en est-il du « canal X » que je cherche à comprendre plus en détail ? » Les gestionnaires de référencement payant peuvent également être intéressés par des dimensions supplémentaires telles que :

* Nom de la campagne publicitaire
* Contenu publicitaire
* Groupe publicitaire

Cependant, les responsables d’événements peuvent être plus intéressés par les événements spécifiques ou par les types d’événements qui ont influencé le plus les leads à la création :

* Nom de la campagne publicitaire / Campagne Salesforce = événement spécifique
* Medium = Campagne &#39;Type&#39;

**RAPPEL** : il peut être nécessaire d’ajouter des filtres supplémentaires à l’une des variations de rapport décrites ci-dessus ou ci-dessous. Ces filtres seraient spécifiques à votre organisation et pourraient être conseillés par vos équipes d’opérations marketing ou de ventes. Il n’est pas rare qu’une organisation exécute les mêmes filtres sur tous les rapports pour s’assurer que le rapport est aussi propre et précis que possible. Voici quelques exemples courants :

* Filtrer les enregistrements internes des tests, généralement par adresse e-mail
* Filtrage basé sur certains « types d’enregistrements » qui peuvent être spécifiques à votre unité opérationnelle

1,3 **| Nouveaux leads par contenu (rapports CRM uniquement)**

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels <i>contenu</i> influencent les leads dans la création ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Leads et points de contact des acheteurs (CRM)</td>
  </tr>
  <tr>
   <td>Champ de date</td>
   <td>Date de création du lead</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Page de destination <br>
   URL du formulaire</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td>Première Touche, Création De Lead, <strong>En U</strong><br></td>
  </tr>
 </tbody>
</table>

**RAPPEL** : les deux principaux champs pour le compte rendu des performances sur le contenu/les ressources numériques sont « Page de destination » et « URL du formulaire ». Ces deux valeurs peuvent être identiques si le prospect convertit (envoie un formulaire) sur la page à laquelle il est arrivé (page de destination), _toutefois_ ces valeurs sont parfois différentes. Par exemple, le prospect peut cliquer sur un lien sur Facebook qui mène à une page de votre site Web (il s’agit de la valeur « Page de destination »). Le prospect peut alors quitter cette page, poursuivre sa session sur le site et envoyer un formulaire sur une autre page (URL du formulaire). Cela serait résumé dans un point de contact unique qui représente l’origine du prospect (canal marketing), le contenu qui l’a amené sur le site (page de destination) et le contenu qu’il a fini par télécharger (URL du formulaire). « URL du formulaire » est également le champ d’accès pour le compte rendu des performances d’autres formulaires non associés à du contenu téléchargeable, tels que les formulaires « Nous contacter » ou « Demande de démonstration ».

Placez insight dans un « contenu » spécifique avec des filtres supplémentaires.

* Filtrer par : &#39;Landing Page&#39; CONTAINS (par exemple) :
   * /blog
   * /ebook
   * /webinar

* OU : « URL du formulaire » CONTIENT (par exemple)
   * /contact
   * /demo

Les rapports basés sur le « contenu » offrent une grande valeur lors de la création de rapports sur n’importe quelle partie de funnel. Cependant, ils sont le plus souvent utilisés en haut du funnel pour fournir des insight supplémentaires dans un engagement initial de Leads. Étant donné que la « recherche organique » tend à être le canal le plus puissant pour stimuler l’engagement initial (FT), il n’y a pas autant de données au niveau de la « campagne ».

Les rapports basés sur le « contenu » sont très utiles pour attirer insight sur ce qui motive les prospects plus spécifiquement dans le canal marketing de niveau supérieur, dans ce cas « Recherche organique ».

1,4 **| Engagement total du prospect dans une période donnée**

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels canaux marketing ont reçu le plus <i>engagement total des prospects</i> au cours des dernières (semaine/mois/trimestre) ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Leads et points de contact des acheteurs (CRM)<br>
   Mesure : Leads ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date du point de contact</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Canal marketing (ou plus granulaire)</td>
  </tr>
  <tr>
   <td>Modèles optimaux*</td>
   <td>*Ce rapport ne porte pas tant sur la mesure de la provenance des leads avec un modèle d’attribution que sur le <i>nombre total de points de contact (quantité d’engagement)</i>, y compris ceux postérieurs à l’étape de création des leads. Le nombre total d’enregistrements des points de contact reflète les canaux qui ont vu le plus d’engagement de lead.</td>
  </tr>
 </tbody>
</table>

**RAPPEL** : la base de vos rapports sur la « Date de point de contact » est le moyen le plus réfléchi de comprendre les performances marketing au cours d’une certaine période. La « Date du point de contact » structure le rapport de manière à ce que l’attribution soit non seulement liée au canal, à la campagne ou au contenu, mais indique également le moment où le point de contact s’est produit. Il s’agit de la méthode la plus efficace pour comprendre ce qui se passait dans le cadre de l’engagement marketing à un moment donné. Il s’agit également de la méthode recommandée pour mesurer l’impact du marketing par rapport aux dépenses marketing investies au cours de la même période. Il est recommandé lors de l’analyse des dépenses marketing ou du retour sur investissement (voir 5.1).

**2. LEADS QUALIFIÉS MARKETING AVEC POINTS DE CONTACT D’ACHETEUR**

L’un des rapports les plus courants ne porte pas uniquement sur les nouveaux prospects ou l’engagement au niveau du prospect, mais plus spécifiquement sur les « prospects qualifiés pour le marketing » (MQL). Il existe plusieurs approches différentes lorsqu’il s’agit de créer des rapports sur les MQL en fonction des fonctionnalités [!DNL Marketo Measure] auxquelles vous avez accès.

**2.1 | Leads qualifiés par marketing par canal (multipoint)**

Cette approche de la mesure de l’impact du marketing sur l’influence des MQL est essentiellement la suite du rapport « Nouvelles pistes par canal marketing » (1.1), mais avec les critères supplémentaires selon lesquels les pistes mesurées sont plus spécifiquement des MQL. Le modèle d’attribution en U est toujours recommandé ici pour identifier les canaux marketing et le contenu qui génèrent des prospects _susceptibles_ de devenir un MQL :

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels canaux marketing sont les mieux à même de générer de nouveaux prospects qui deviennent des <i>MQL</i> ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Leads et points de contact des acheteurs (CRM)<br>
   Mesure : Leads ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td>MQL = true*<br>
   *<i>Les MQL peuvent être définis différemment par organisation. Assurez-vous que le rapport [!DNL Marketo Measure] est filtré pour les MQL en utilisant le ou les mêmes champs que les autres rapports basés sur MQL. Un filtre de segments doit être créé de la même manière pour la création de rapports sur les MQL dans [!DNL Marketo Measure] Discover.</i></td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date MQL (ou équivalente) / Date de création ([!DNL Marketo Measure] Discover)<br> <i>la date de création du lead peut également être utilisée dans les rapports CRM si « Date MQL » n’est pas une option dans votre CRM. Il est important de garder à l’esprit le champ de date que vous utilisez pour définir le jeu de données de cohortes.</i></td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Canal marketing</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td>Première Touche, Création De Lead, <strong>En U</strong><br>
   ADDITIONNER les champs « Comptage » dans vos rapports CRM (Nombre - Première touche, Nombre - Création de lead, Nombre - En forme de U)</td>
  </tr>
 </tbody>
</table>

2,2 **| Leads qualifiés marketing par canal (touche unique, CRM uniquement)**

Cette approche de la mesure de l’impact du marketing sur l’influence de MQL est davantage axée sur l’identification du _point de contact unique_ qui était le dernier contact avant que le prospect n’atteigne MQL.

>[!NOTE]
>
>Pour exécuter ce rapport, une valeur « Statut du lead » de « MQL » est requise pour définir l’étape MQL à des fins de suivi (étape Funnel). Si les fichiers MQL ne sont pas suivis via le champ « Statut du lead », la fonction Modèle d’attribution personnalisé avec étapes personnalisées est nécessaire pour créer une étape « MQL » personnalisée dans les paramètres du compte [!DNL Marketo Measure].

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels canaux marketing sont les plus efficaces pour pousser les prospects à atteindre le statut MQL ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Leads et points de contact des acheteurs (CRM)<br>
   <i>ce rapport n’est possible que dans le cadre du reporting CRM. Il n’est pas possible de filtrer selon certaines valeurs « Position du point de contact » dans [!DNL Marketo Measure] Discover</i></td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td><strong>Position du point de contact CONTENANT « MQL »</strong></td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date MQL (ou équivalent)</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Canal marketing</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td><i>Comme ce rapport est filtré sur un seul point de contact, les modèles d’attribution au niveau du lead ne sont pas aussi pertinents. À l’instar du « rapport d’engagement des leads » (1.4), le nombre d’enregistrements de points de contact serait utilisé ici pour comprendre quels canaux sont les plus puissants (chaque lead n’aurait qu’un seul point de contact MQL).</i></td>
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Explorez d’autres regroupements ou dimensions pour obtenir des insight supplémentaires dans les MQL. Comme mentionné dans les autres rapports « Leads avec points de contact d’acheteur », le Buyer Touchpoint offre beaucoup plus de granularité que le seul canal marketing. Un rapport basé sur « Contenu » peut également être combiné avec l’un des rapports MQL ci-dessus pour mieux comprendre quel contenu influence le mieux les MQL.

**3. [!DNL MARKETO MEASURE] DES PERSONNES AVEC LES POINTS DE CONTACT DE L’ACHETEUR**

Il existe un troisième objet [!DNL Marketo Measure] personnalisé dans Salesforce qui peut s’avérer très utile lors de la création de rapports sur des mesures liées aux personnes : **la personne [!DNL Marketo Measure] (BP)**. Le BP résout le vieux problème de la représentation des informations des Leads et Contacts dans le même rapport. Il regroupe tous les BT liés à une « personne » (l’ID d’une personne [!DNL Marketo Measure] est son adresse e-mail). Qu’il existe en tant que lead ou contact, le BP fait office d’objet de liaison afin d’aider les rapports à couvrir les leads et les contacts. Il est très utile pour produire des rapports plus sophistiqués sur les personnes.

La personne [!DNL Marketo Measure] ne se rapporte qu’à un seul des objets de point de contact, le Buyer Touchpoint (BT). Cela signifie qu’il ne peut pas être utilisé pour des mesures liées à une opportunité ou à un chiffre d’affaires. Un type de rapport « Points de contact de la personne et de l’acheteur [!DNL Marketo Measure] » est idéal pour comprendre l’_engagement total_ car il fait apparaître tous les BT, que le BT se rapporte à un lead ou à un contact plus précisément. Par exemple : si une campagne Salesforce est utilisée pour suivre un événement, certains membres de la campagne au sein de la campagne CRM peuvent exister en tant que leads OU contacts. [!DNL Marketo Measure] créera néanmoins des points de contact pour les membres de la campagne, mais sans la personne [!DNL Marketo Measure], la création de rapports Salesforce standard nécessiterait deux rapports distincts pour connaître le nombre _total_ de points de contact que vous avez issus de l’événement : l’un « Leads avec points de contact d’acheteur » et l’autre « Contacts avec points de contact d’acheteur ». Voici quelques autres cas d’utilisation de création de rapports basés sur des personnes [!DNL Marketo Measure] :

**3.1 [!DNL Marketo Measure] Personnes ayant téléchargé des livres numériques ou des livres blancs (total des téléchargements)**

Ce rapport est identique à un rapport basé sur le contenu au niveau du prospect. Cependant, plutôt que de chercher à mesurer le nombre de prospects attribuables à chaque élément de contenu, l’utilisation d’un rapport [!DNL Marketo Measure] Personnes permet de comprendre le _nombre total de téléchargements_ si la ressource est contrôlée (le nombre total de points de contact représente le nombre total de téléchargements/envois de formulaire).

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Combien de personnes ont téléchargé une ressource en particulier ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>[!DNL Marketo Measure] Points de contact des personnes et des acheteurs (CRM)</td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td>'URL du formulaire' CONTAINS (par exemple)<br>
   <li>/ebook</li>
   <li>/livre blanc</li>
   <i>Les valeurs de filtre ci-dessus ne sont que des exemples. La valeur réelle sera basée sur la structure d’URL de chaque organisation.</i></td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date du point de contact <i>(quand la ressource a-t-elle été téléchargée)</i></td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>URL du formulaire</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td>Ce rapport ne porte pas tant sur la mesure de la provenance des leads ou des contacts avec un modèle d’attribution que sur le <i>nombre total de points de contact (quantité d’engagement)</i>, y compris ceux postérieurs à l’étape de création de leads. Avec ce rapport, nous cherchons à comprendre le <i>montant total de l'engagement</i>. Le nombre total d’enregistrements des points de contact reflète les ressources qui ont été le plus téléchargées.</td>
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout type de rapport « Leads avec [!DNL Marketo Measure] personnes », commencez par personnaliser le rapport préconfiguré intitulé « **[!DNL Marketo Measure]101 » | Leads/contacts par canal** ». Ce rapport est prêt à l’emploi et constitue un excellent sandbox basé sur les personnes [!DNL Marketo Measure]. Il est préconfiguré et peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques.

>[!TIP]
>
>Vous pouvez utiliser ce rapport pour qu’insight bénéficie de l’engagement total de toute dimension marketing à partir de l’objet Buyer Touchpoint, et pas seulement des téléchargements de contenu comme présenté dans l’exemple. Le rapport peut plutôt être regroupé ou filtré sur des dimensions telles que « Canal marketing » ou « Nom de la campagne publicitaire » pour mieux comprendre l’engagement total des prospects et des contacts de votre base de données. Remplacez les filtres ou les regroupements du rapport par zéro dans d’autres dimensions représentées par d’autres champs de l’objet de point de contact.

**3.2 [!DNL Marketo Measure] Personnes qui se sont inscrites à un événement (CRM uniquement)**

_Ce rapport ne s’applique que si les formulaires d’enregistrement sont hébergés sur votre ou vos sites web et que [!DNL Marketo Measure] pouvez les suivre numériquement._

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels canaux marketing génèrent mes enregistrements à l’événement ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>[!DNL Marketo Measure] Points de contact des personnes et des acheteurs (CRM)</td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td>'URL du formulaire' CONTAINS (par exemple)<br>
   <li>/event</li>
   <i>La valeur de filtre ci-dessus est fournie uniquement à titre d’exemple. La valeur réelle sera basée sur la structure d’URL de chaque organisation.</i></td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date du point de contact <i>(date à laquelle le formulaire d’enregistrement a été envoyé)</i></td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>URL du formulaire <br>
   Canal marketing</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td>Ce rapport ne porte pas tant sur la mesure de la provenance des leads ou des contacts avec un modèle d’attribution que sur le <i>nombre total de points de contact (nombre d’enregistrements)</i>, y compris ceux postérieurs à l’étape de création de leads. Avec ce rapport, nous souhaitons expliquer à insight ce qui motive les enregistrements d’événements. Le nombre total d’enregistrements des points de contact par « canal marketing » reflète les canaux qui ont généré le plus d’enregistrements.</td>
  </tr>
 </tbody>
</table>

La principale leçon à tirer de ce rapport est que les données Buyer Touchpoint fourniront également des données de canal marketing. Bien que vous disposiez peut-être déjà d’insight concernant le nombre de personnes inscrites à vos événements, ce rapport fournit également à insight des informations sur les canaux, sources et/ou campagnes marketing numérique qui amènent les personnes sur votre site web pour qu’elles s’inscrivent à l’événement.

>[!TIP]
>
>Cette même approche peut être adoptée lorsque vous cherchez à intégrer insight aux enregistrements de webinaires ou peut-être aux téléchargements de webinaires à la demande (s’il s’agit d’une ressource sécurisée). La seule différence serait la valeur de filtre dans « URL du formulaire » si ces formulaires sont hébergés sur des pages uniques de votre site web. Le but est le même cependant. Il répond aux questions « Quels canaux marketing génèrent le plus d’enregistrements/de téléchargements de webinaires à la demande ? ».

**3.3 [!DNL Marketo Measure] de personnes avec des points de contact acheteur (validation des points de contact)**

Étant donné que la personne [!DNL Marketo Measure] nous permet de générer des rapports sur tous les points de contact dans un seul rapport, il s’agit du type de rapport idéal à utiliser lors de la validation des données. Nous voulons nous assurer de ne pas négliger des points de contact qui pourraient révéler où, par exemple, il y a un problème dans la configuration de vos « Canaux marketing » (voir les articles d’assistance liés ci-dessous pour plus d’informations sur la configuration de vos « Canaux marketing »).

* [Configuration de canal personnalisé en ligne](/help/channel-tracking-and-setup/online-custom-channel-setup.md)
* [Configuration de canal personnalisé hors ligne](/help/channel-tracking-and-setup/offline-custom-channel-setup.md)

Pour l’essentiel, les données de point de contact refléteront ce qui a été suivi par [!DNL Marketo Measure] et peuvent être contrôlées pour vous assurer que votre configuration correspond aux entrées en fonction d’éléments tels que : les valeurs de paramètre UTM, les pages de référence ou les types de campagne. Si les données de point de contact ne correspondent pas à votre configuration, un élément doit probablement être ajusté. Au-delà de la configuration « Canal marketing », vous pouvez examiner les données de point de contact pour déterminer les points de contact qui doivent être [supprimés](/help/channel-tracking-and-setup/touchpoint-removal-and-touchpoint-suppression.md) ou [segmentés](/help/channel-tracking-and-setup/custom-segmentation.md). Il est recommandé d’auditer vos données de point de contact dans un rapport « Points de contact des personnes et des acheteurs [!DNL Marketo Measure] » à la fin de chaque mois ou trimestre, si possible. Cela permet de s’assurer que votre attribution est aussi précise que possible. Le &#39;[!DNL Marketo Measure] 101 | Le rapport Leads/Contacts par canal prêt à l’emploi est un bon point de départ. Insérez les champs suivants s’ils ne sont pas déjà inclus pour passer en revue certains des éléments de configuration les plus importants :

* **Canal marketing** - Chemin = Canal marketing.Sous-canal (valeurs définies dans [!DNL Marketo Measure])
* **Touchpoint Source** = utm_source
* **Medium** = utm_medium (points de contact en ligne) OU type de campagne CRM (points de contact hors ligne)
* **Page du référent** (utilise la configuration &#39;Canaux en ligne&#39;)
* **Page de destination - Brute** (utilisée dans la configuration « Canaux en ligne ») est également une entrée courante pour la suppression des points de contact dans l’onglet « Paramètres des points de contact » de vos paramètres)
* **URL du formulaire** (entrée courante pour la suppression du point de contact dans l’onglet « Paramètres de point de contact » de vos paramètres)

**BUYER ATTRIBUTION TOUCHPOINT (BAT)**

Les points de contact d’attribution de l’acheteur (BAT) représentent les points de contact pertinents de tous les contacts connectés à l’opportunité (via les rôles de contact de l’opportunité ou un identifiant de compte partagé, selon vos paramètres). Contrairement aux MTD (qui sont principalement liées aux personnes), les MTD peuvent être associées aux revenus. Par conséquent, vous utiliserez les BAT pour répondre aux questions relatives aux opportunités, principalement les opportunités ouvertes _Opportunités/Chiffre d’affaires de pipeline_ et les opportunités/affaires/chiffres d’affaires clôturées _Opportunités/affaires_. Un BAT est créé à partir des enregistrements BT d’un contact dès qu’une opportunité est créée sous le même compte que le contact (le BT n’est pas converti en BAT. Les données BT sont simplement référencées pour créer un enregistrement supplémentaire (le BAT qui se rapporte ensuite à l’opportunité).

Le Buyer Attribution Touchpoint nous permet de mesurer l’impact du marketing plus précisément dans le funnel. _La profondeur du funnel auquel vous souhaitez mesurer peut être représentée par les différents modèles d’attribution multipoint_.

Étant donné que la relation principale entre les BAT est avec l’opportunité, ils sont utilisés pour répondre à des questions telles que :

* Quels efforts de marketing ont eu la plus grande influence sur les opportunités ?
* Quel nouveau chiffre d’affaires de pipeline puis-je attribuer à chacun de mes canaux marketing ?
* Laquelle de mes campagnes a affiché le meilleur retour sur investissement le trimestre dernier ?

Les [modèles d’attribution](/help/attribution-models.md) qui fournissent les meilleures mesures insight basées sur les opportunités sont les suivants :

**En W** - « _Modèle De Pipeline_ » Trois points de contact jalonnés sont inclus dans le modèle en W. les points de contact FT, LC et OC se voient attribuer chacun 30 % du crédit d’attribution. Les 10 % restants sont attribués de manière égale à tous les points de contact intermédiaires qui se produisent entre les trois points de contact jalonnés.

<table>
 <tbody>
  <tr>
   <td>&lt;img alt=« bizible guide 2 » src= »assets/bizible-guide-2.png »</td>
   <td>Ce modèle résume essentiellement le parcours d’une nouvelle opportunité qui est généralement synonyme de génération de nouveaux revenus de pipeline.<p>
   <p>
   Lorsque vous souhaitez mesurer l’impact du marketing sur les nouvelles opportunités ou les nouveaux pipelines générés, le modèle en W est recommandé.</td>
  </tr>
 </tbody>
</table>

**Chemin Complet** _- « Modèle Fermé Et Confirmé_ ». Ce modèle comprend les quatre points de contact jalonnés suivants : FT, LC, OC et Fermé. Chacun reçoit 22,5 % du crédit d’opportunité, et les 10 % restants sont répartis également entre les contacts intermédiaires.

<table>
 <tbody>
  <tr>
   <td>&lt;img alt=« guide bizible 3 » src= »assets/bizible-guide-3.png »</td>
   <td>Ce modèle résume essentiellement le parcours d’une transaction conclue et confirmée qui est généralement synonyme de chiffre d’affaires/réservations conclu et confirmé.<p>
   <p>
   Lorsque vous souhaitez mesurer l’impact du marketing sur les affaires conclues et confirmées clôturées ou sur le chiffre d’affaires conclu, le modèle de chemin complet est recommandé.</td>
  </tr>
 </tbody>
</table>

Ce modèle résume essentiellement le parcours d’une transaction conclue et confirmée qui est généralement synonyme de chiffre d’affaires/réservations conclu et confirmé.

Lorsque vous souhaitez mesurer l’impact du marketing sur les affaires conclues et confirmées clôturées ou sur le chiffre d’affaires conclu, le modèle de chemin complet est recommandé.

**Personnalisé** - [!DNL Marketo Measure] propose également un modèle d’attribution personnalisé qui permet aux utilisateurs et aux utilisatrices de choisir les points de contact ou les étapes personnalisées à inclure dans leur modèle. En outre, les utilisateurs et utilisatrices peuvent contrôler le pourcentage de crédit d’attribution attribué à ces points de contact et étapes. Selon la configuration de votre modèle personnalisé, il peut être utilisé de la manière la plus appropriée pour mesurer les opportunités et les opportunités ou les opportunités de pipeline, les affaires et les revenus confirmés. Gardez cela en tête lorsque vous l’utilisez dans vos rapports.

>[!NOTE]
>
>Le modèle d’attribution personnalisé est une fonctionnalité supplémentaire qui n’est pas disponible pour tous les clients. Contactez l’équipe du compte Adobe (votre gestionnaire de compte) pour en savoir plus sur la manière d’ajouter cette fonctionnalité à votre compte.

En règle générale, les professionnels du marketing doivent savoir d’où viennent leurs opportunités. De la même manière que pour le reporting au niveau du prospect, la réponse à cette question était historiquement donnée par une seule valeur unidimensionnelle (par exemple, Principal Campaign Source). Cependant, nous savons que le développement d’une opportunité implique bien plus qu’un seul point de contact d’un seul contact. Plusieurs points de contact provenant de différents canaux et de plusieurs parties prenantes influencent généralement la création d’une opportunité. Avec [!DNL Marketo Measure], nous pouvons faire apparaître tous les points de contact d’un compte pour mieux comprendre d’où vient une opportunité. Au-delà de cela, cependant, nous pouvons continuer à faire apparaître tout point de contact qui s’est produit après la création de l’opportunité et jusqu’à ce que l’opportunité soit fermée. Cela nous permet non seulement d’adopter une approche multi-touch pour comprendre d’où vient une opportunité, mais aussi ce qui l’a influencée à se fermer et, finalement, à représenter un chiffre d’affaires fermé. Cela permet à insight de répondre à différentes questions, telles que « Quel est l’impact du marketing sur l’influence des affaires à conclure ? » ou « Quel marketing génère un chiffre d’affaires clôturé ? » et, finalement, « lequel de mes efforts marketing présente le meilleur retour sur investissement ? »

## RAPPORTS RECOMMANDÉS À L’AIDE DE BUYER ATTRIBUTION TOUCHPOINT (BAT) {#recommended-reports-using-the-buyer-attribution-touchpoint}

4,1 **| Nouvelles opportunités par canal marketing**

La synthèse des données Buyer Attribution Touchpoint de vos opportunités par le champ « Canal marketing » est la vue de plus haut niveau qui représente les canaux/tactiques qui influencent les nouvelles opportunités dans la création. Structurer ce rapport autour d’un « Type de date » = « Date de création de l’opportunité » garantit que nous résumons également le rapport en fonction de la date de création réelle de l’opportunité dans votre CRM. Les points de contact peuvent avoir été créés à un moment antérieur, mais ils resteront liés aux opportunités créées au cours de la période définie et recevront donc un crédit d’attribution, car ils sont reconnus comme ayant une influence sur l’opportunité.

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels <i>canaux marketing</i> influencent les opportunités dans la création ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Points de contact d’attribution de l’acheteur avec les opportunités (CRM)<br>
   Mesure : Opportunités ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td>
   <li>Phase de l’opportunité* <i>(facultatif selon les opportunités spécifiques que vous souhaitez limiter au rapport. Vous pouvez uniquement générer des rapports sur les BAT qui sont toujours associées uniquement aux opportunités « ouvertes » (par exemple, )</i></li>
   <li>Type d’opportunité (il est courant de filtrer selon certaines opportunités, c’est-à-dire « Nouvelle entreprise » plutôt que <i> toutes </i> opportunités).</li><br>
   *Un filtre Segment pour 'Type d’opportunité' doit être utilisé dans [!DNL Marketo Measure] Discover</td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date de création de l’opportunité (CRM) / Date de création (Discover)</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Canal marketing</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td><strong>En W</strong><br>
   ADDITIONNEZ les champs en W dans vos rapports CRM (Nombre - En W, Chiffre d’affaires - En W).</td>
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout type de rapport « Points de contact d’attribution de l’acheteur avec opportunités », commencez par personnaliser le rapport préconfiguré intitulé « [!DNL Marketo Measure] 101 | Opportunités par canal ». Ce rapport est prêt à l’emploi. Il s’agit d’un excellent sandbox préconfiguré, comme décrit dans le tableau ci-dessus, et peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques (le rapport utilise un modèle de chemin complet prêt à l’emploi. Veillez donc à personnaliser le rapport afin d’inclure tout autre modèle d’attribution, dans ce cas, le modèle en W).

>[!TIP]
>
>Le rapport décrit ci-dessus serait également utilisé pour déterminer le montant de la monnaie qui devrait également être attribué. Lors de la création de rapports au niveau de l’opportunité à l’aide de BAT, deux mesures clés doivent être résumées : la devise (le montant de l’opportunité) et l’enregistrement de l’opportunité lui-même. Dans l&#39;exemple ci-dessus, nous mesurons plus précisément les opportunités ouvertes et les nouveaux revenus du pipeline.

>[!TIP]
>
>Obtenez une insight encore plus granulaire en résumant le rapport avec d’autres champs disponibles à partir de l’objet Buyer Attribution Touchpoint. Cette opération s’effectue de la même manière qu’au niveau du prospect avec les points de contact de l’acheteur (1.2). Pour ce faire, ajoutez des regroupements (CRM) ou des dimensions supplémentaires (Discover). Selon le canal (qui peut être représentatif de votre rôle), il peut y avoir des détails supplémentaires au-delà du niveau de la campagne dans laquelle vous souhaitez obtenir plus d’insight. Explorons le référencement payant ci-dessous :

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels <i>mots-clés</i> de mes annonces de référencement payant génèrent le plus de chiffre d’affaires de pipeline ?
</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Points de contact d’attribution de l’acheteur avec les opportunités (CRM)<br>
   Mesure : Opportunités ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td>
   <li>Canal marketing = référencement payant</li>
   <li>Phase de l’opportunité* <i>(facultatif selon les opportunités spécifiques que vous souhaitez limiter au rapport. Cet exemple est basé sur le chiffre d’affaires de pipeline qui est défini dans [!DNL Marketo Measure] par les opportunités « ouvertes » représentant le chiffre d’affaires potentiel (pipeline ouvert)</i></li>
   <li>Type d’opportunité (il est courant de filtrer selon certaines opportunités, c’est-à-dire « Nouvelle entreprise » plutôt que <i> toutes </i> opportunités).</li><br>
   *Un filtre Segment pour 'Type d’opportunité' doit être utilisé dans [!DNL Marketo Measure] Discover</td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date de création d'opportunité</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Texte du mot-clé (CRM)<br>
   Mot-clé (Discover)</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td><strong>En W</strong><br>
   ADDITIONNEZ les champs en W dans vos rapports CRM (Nombre - En W, Chiffre d’affaires - En W).</td>
  </tr>
 </tbody>
</table>

4,2 **| Offres par canal marketing**

Ce rapport serait essentiellement le même que le premier exemple Buyer Attribution Touchpoint (4.1), sauf que la mesure a été modifiée, passant d’Opportunités ouvertes à Offres conclues. La mesure doit toujours indiquer le modèle d’attribution à utiliser. Étant donné que nous examinons actuellement les transactions conclues et leurs MTD associées, nous devons utiliser un modèle qui représente l’ensemble du parcours de l’acheteur (transaction). Cela garantit que toute piste tactile marketing pendant le parcours de l’acheteur reçoit un crédit d’attribution :

<table>
 <tbody>
  <tr>
   <td>Question</td>
   <td>Quels <i>canaux marketing</i> influencent la conclusion des affaires ?</td>
  </tr>
  <tr>
   <td>Type de rapport</td>
   <td>Points de contact d’attribution de l’acheteur avec les opportunités (CRM)<br>
   Mesure : Offres ([!DNL Marketo Measure] Discover)</td>
  </tr>
  <tr>
   <td>Filtres</td>
   <td>
   <li>Étape de l’opportunité (<i>seules les opportunités closes et confirmées doivent être dans le rapport</i>) OU,</li>
   <li>Opportunité confirmée = Vrai</li>
   <li>Type d’opportunité (il est courant de filtrer selon certaines opportunités, c’est-à-dire « Nouvelle entreprise », par opposition à toutes les opportunités)<br>
   </td>
  </tr>
  <tr>
   <td>Champ de date/type de date</td>
   <td>Date de fermeture de l’opportunité</td>
  </tr>
  <tr>
   <td>Période</td>
   <td><i>sélectionner la période souhaitée</i></td>
  </tr>
  <tr>
   <td>Groupe / Dimension</td>
   <td>Canal marketing</td>
  </tr>
  <tr>
   <td>Modèles optimaux</td>
   <td><strong>Chemin complet</strong><br>
   ADDITIONNEZ les champs « Chemin complet » dans vos rapports CRM (Nombre - Chemin complet, Chiffre d’affaires - Chemin complet)</td>
  </tr>
 </tbody>
</table>

**RAPPEL** : n’oubliez pas de filtrer les opportunités spécifiques que vous souhaitez inclure dans les rapports basés sur BAT, en particulier lorsqu’il s’agit d’« opportunités ouvertes et chiffre d’affaires de pipeline » par rapport aux « affaires et chiffres d’affaires confirmés ». Cette opération s’effectue généralement via un filtre « Étape de l’opportunité » (le filtre « Opportunité confirmée » = true/false peut également s’avérer très utile dans ce cas).

**5. ROI ([!DNL Marketo Measure] Discover uniquement)**

Les tableaux de bord [!DNL Marketo Measure] Discover offrent une vue d’ensemble de vos performances marketing à l’aide de données d’attribution [!DNL Marketo Measure]. Ces tableaux de bord agrégés fournissent des données clés sur les dépenses marketing et le retour sur investissement qui ne sont pas disponibles dans vos rapports CRM. Cet environnement préconfiguré vous permet d’afficher vos performances marketing en accord avec vos données de retour sur investissement, ce qui vous permet de prendre des décisions exploitables concernant votre marketing.

>[!TIP]
>
>Chaque fois que vous avez des questions relatives au RSI, aux Dépenses ou aux Coûts, [!DNL Marketo Measure] Discover est le meilleur endroit pour créer des rapports.

Les tableaux de bord [!DNL Marketo Measure] Discover se composent de données Buyer Touchpoint et Buyer Attribution Touchpoints, ainsi que de données CRM essentielles. La principale différence entre les rapports CRM et les rapports dans [!DNL Marketo Measure] Discover réside dans le fait que les données de point de contact dans Discover sont présentées de manière « agrégée » et résumées par dimension (canal marketing, campagne, etc.), plutôt que par enregistrements de point de contact individuels, qui peuvent ensuite être résumés. [!DNL Marketo Measure] Discover est utilisé pour comprendre à un haut niveau quels efforts de votre part ont le plus d’impact sur les leads, les opportunités, les affaires et quel montant de chiffre d’affaires devrait leur être attribué. Une fois que le chiffre d’affaires attribué est calculé à l’aide des différents modèles d’attribution (le chemin complet est recommandé pour attribuer le chiffre d’affaires/les réservations clôturés), nous pouvons le mesurer par rapport au montant dépensé dans la même dimension (canal marketing, sous-canal ou campagne). Cela nous donne ensuite le **retour sur investissement**.

>[!TIP]
>
>L’une des choses les plus importantes à retenir lors de la création de rapports dans Discover est le type de données que vous utilisez pour filtrer. Le type de date détermine le jeu de données utilisé par [!DNL Marketo Measure] dans les différentes mosaïques.

* **Date du point de contact** : affiche les données associées ayant une « Date du point de contact » dans le délai spécifié
* **Date de création** : affiche les données associées ayant une « Date de création » dans le délai spécifié
* **Date de fermeture** : affiche les données associées ayant une « Date de fermeture » dans le délai spécifié

Lors de la création de rapports sur le retour sur investissement dans [!DNL Marketo Measure] Discover, il est recommandé d’utiliser un « Type de date » = « Date du point de contact ». Afin de déterminer le rendement de chaque dollar investi, nous devons nous assurer que le revenu est attribué à la date à laquelle l&#39;investissement a été fait. Le « Type de date » = « Date du point de contact » garantit que les rapports sont structurés de cette manière par rapport à la date de création de l’opportunité (date de création) ou de fermeture (date de fermeture). Regardons de plus près :

Les filtres mis en évidence ci-dessous sont essentiels pour un rapport axé sur le retour sur investissement dans [!DNL Marketo Measure] (il est probable que vous définirez ces filtres dans les tableaux « Vue d’ensemble », « CMO » ou « Retour sur investissement ») :

5,1 **| RSI dans le tableau « Présentation »**

5,1 ![ | RSI dans le tableau « Présentation »](assets/bizible-guide-1.png)

La plage « Date » définit non seulement la cohorte de points de contact (par date de point de contact) auxquels l’attribution est attribuée, mais elle définit également la plage que la mosaïque ou les colonnes « Dépenses » représentent.
[!DNL Marketo Measure] examine simplement la plage « Date » pour déterminer combien a été dépensé au total, ou au niveau du canal marketing, du sous-canal ou de la campagne. Voir ci-dessous :

![Marketo Measure examine simplement la plage « Date » pour déterminer comment](assets/bizible-guide-2.png)

La capture d’écran ci-dessus montre les données des dépenses marketing au cours des 3 derniers mois complets. Dans cet exemple, 12 970 $ ont été dépensés sur tous les canaux. Ce nombre comprend les données sur les dépenses marketing [!DNL Marketo Measure] proviennent des intégrations à l’un de vos comptes publicitaires connectés (Google AdWords, Bing Ads, Facebook Ads, LinkedIn, DoubleClick) et toutes les dépenses marketing supplémentaires qui ont été chargées dans votre compte ou extraites automatiquement des enregistrements Campaign dans votre CRM. L’exemple montre également combien de « chiffre d’affaires » fermé peut également être attribué aux points de contact qui se sont produits au cours de la même période (cases vertes). Voici comment le retour sur investissement est calculé : chiffre d’affaires attribué aux points de contact provenant d’un investissement dans la même période :

![La capture d’écran ci-dessus montre les données des dépenses marketing au cours des 3 dernières ](assets/bizible-guide-3.png)

**RAPPEL** : [!DNL Marketo Measure] définit le « chiffre d’affaires » comme étant le chiffre d’affaires ou les réservations confirmés et définit le « chiffre d’affaires de pipeline » comme _le chiffre d’affaires ouvert/potentiel des opportunités ouvertes_.

Un autre point important à retenir du rapport de RSI ci-dessus est le « chiffre d’affaires de pipeline » représenté dans la zone rouge. Cela signifie que sur les 12 970 $ US investis au cours des 3 derniers mois complets, nous attribuons actuellement 705 199 $ de « revenu gagné » fermé, mais nous attribuons également 6 905 532 $ de revenu potentiel ouvert (« revenu du pipeline ») aux points de contact créés à partir du même investissement ! Nous nous attendons à ce qu&#39;une partie des « revenus du pipeline » soit fermée au fil du temps, alimentant ainsi le chiffre des « revenus », et donc à ce que le nombre de RSI augmente au fil du temps. Le nombre « Dépenses » est corrigé, car nous ne pouvons pas revenir en arrière pour dépenser plus au cours des 3 derniers mois complets. C’est l’importance d’utiliser un « Type de date » de « Date de point de contact » dans tout rapport de RSI : cela définit le montant (**I**) investi et garantit que le montant du chiffre d’affaires (**R**) attribué est attribué aux mêmes points de contact qui ont été obtenus à partir de l’investissement (pour chaque dollar dépensé, combien a été gagné ?).

>[!TIP]
>
>Filtrez les canaux marketing, les sous-canaux et/ou les campagnes dans lesquels vous savez que les données sur les dépenses marketing sont complètes et précises. L’exemple ci-dessus concerne tous les canaux marketing. Toutefois, si les données relatives aux dépenses marketing de certains canaux ne sont pas chargées, les rapports sur le retour sur investissement peuvent être inexacts. Consultez l’exemple ci-dessous, cette fois dans le tableau « RSI » qui porte sur les campagnes au sein du canal marketing de « référencement payant », un canal contenant des données de dépenses marketing très granulaires via les intégrations .

![Filtrez les canaux marketing, sous-canaux et/ou campagnes que vous connaissez](assets/bizible-guide-4.png)
