---
description: "[!DNL Marketo Measure] Reporting Guide - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Reporting Guide"
exl-id: 9b991f9e-c187-4b43-b0a8-8ed3e9a6056b
feature: Reporting
source-git-commit: 3119b1754bba49139c1a6756851ada580e09c1ef
workflow-type: tm+mt
source-wordcount: '5602'
ht-degree: 2%

---

# Guide de création de rapports [!DNL Marketo Measure] {#marketo-measure-reporting-guide}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Avant de créer un rapport [!DNL Marketo Measure], il est essentiel de confirmer que les paramètres de votre compte [!DNL Marketo Measure] ont été vérifiés et configurés afin de s’assurer que les données contenues dans les rapports sont exactes et reflètent les spécificités de votre entreprise. En outre, les projets de création de rapports fonctionnent mieux lorsqu’ils suivent un processus structuré. Justin Norris, un [!DNL Marketo Measure] utilisateur, défenseur et partenaire de [Perkuto](https://perkuto.com/){target="_blank"} a merveilleusement résumé [la manière d&#39;approcher le reporting dans  [!DNL Marketo Measure]](https://perkuto.com/blog/turning-attribution-data-into-actionable-insights/){target="_blank"} :

**Établissement d’objectifs** : &quot;La première question à poser est &quot;Pourquoi mesurons-nous ?&quot; Lori wizard de [Forrester Research](https://go.forrester.com/) l&#39;a bien résumé dans un [webinaire Marketo](https://www.marketo.com/webinars/beyond-revenue-performance-real-kpis-of-b2b-marketing/){target="_blank"}. Selon elle, &quot;nous mesurons pour prouver ou valider une décision ou la valeur du marketing ou pour obtenir de meilleurs résultats (amélioration des processus).&quot; Nous ajouterons que les informations issues de bonnes mesures fournissent également des informations et des conseils sur le processus de planification marketing.

Avant de commencer, il est essentiel d&#39;être clair comme du cristal sur vos objectifs, les questions auxquelles vous essayez de répondre, ou les problèmes que vous essayez de résoudre. Quelle histoire voulez-vous raconter ? Quelles décisions seront prises en conséquence ? Trop souvent, ces fondamentaux sont mal pensés, ce qui entraîne une frustration pour tous les acteurs impliqués.&quot;

**Conception de rapport** : &quot;Ensuite, vous devez concevoir le rapport et déterminer les dimensions, les mesures et le jeu de données spécifiques qu’il contiendra. Une expérience courante consiste à fournir à un utilisateur chargé de l’entreprise exactement ce qu’il demande, uniquement pour qu’il ait toujours l’impression que ses besoins ne sont pas satisfaits. Cela est dû au fait que l’information recherchée par un utilisateur chargé de la conception de parcours n’est pas toujours contenue dans le rapport qu’il demande. Un bon analyste (ou une personne du MOPS avec un analyste qui est là) posera des questions claires, établira des définitions communes (&quot;donc, qu&#39;est-ce que vous voulez vraiment dire par plomb ?&quot;) et même esquissera un visuel du rapport final pour s&#39;assurer qu&#39;il y a un alignement. C’est seulement alors que vous créez le rapport, en sachant que vous avez de solides exigences.&quot;

**Report Build** : &quot;Une fois que vous avez créé, il n’est pas rare de rencontrer des obstacles ou des impasses. Par exemple, vous pouvez découvrir que vous ne disposez pas d’un point de données essentiel ou que vos objets ne sont pas liés de la manière dont vous en avez besoin. Pour résoudre ces problèmes, je pense aussi qu&#39;il est essentiel de comprendre ce qui se passe &quot;sous le capot&quot; dans votre &quot;machine&quot; de reportage. Cette aisance vous permet de dimensionner rapidement une demande de création de rapports et d’évaluer si elle est réalisable (et de concevoir plus facilement des solutions créatives dans le cas contraire).&quot;

Jetons un coup d’oeil &quot;sous le capot&quot; pour mieux comprendre ce qui fait fonctionner la machine de création de rapports d’attribution [!DNL Marketo Measure].

## Objets Buyer Touchpoint (CRM) {#buyer-touchpoint-objects-crm}

Au niveau le plus élevé, il existe deux catégories de rapports basées sur les deux objets Buyer Touchpoint différents : ces catégories déterminent le type de données [!DNL Marketo Measure] sur lequel vous souhaitez créer des rapports : les données liées à un _individu_ ou les données liées à une _opportunité_.

1. **Points de contact de l’utilisateur** (BT) / Individus / Total des engagements

   * Communément utilisé pour les mesures et les rapports &quot;top of the funnel&quot; (TOFU) liés à _individus_ (Leads, contacts, [!DNL Marketo Measure] personnes)
   * BT sont utilisés pour comprendre toutes les interactions marketing liées à **personnes**, car ils contiennent l’historique complet des points de contact pour chaque personne. Pour rappel, ces points de contact sont créés dans la gestion de la relation client pour la Première touche anonyme, la Première touche de création de piste et tout point de contact ou d’envoi de formulaire suivant que vous choisissez de synchroniser.
une campagne ou une activité hors ligne.

1. **Points de contact d’attribution de l’achat** (BAT) / Niveau de l’opportunité / niveau du compte / Recettes

   * Généralement utilisé pour les mesures et les rapports &quot;intermédiaire et/ou inférieur de l’entonnoir&quot; (MOFU et BOFU) liés à _Opportunités_.
   * BAT représentent les points de contact pertinents de toutes les personnes connectées à l’ **opportunité** (soit via les rôles Contact opportunité ou via un ID de compte partagé, selon vos paramètres). Contrairement aux BT qui ne concernent que les personnes, BAT peut également être associé à **revenue**. Ainsi, vous utiliserez BAT pour répondre à des questions relatives aux opportunités, notamment le nombre d’opportunités ouvertes ou fermées, ou la valeur du pipeline et les recettes gagnées.

>[!NOTE]
>
>BAT sont créés à partir de BT. Essentiellement, le suivi commence au niveau individuel par le biais du BT. Une fois qu’une opportunité a été créée sur un compte, toutes les BT des contacts du même compte sont référencées et peuvent créer des BAT en relation avec l’opportunité. Vous souhaiterez donc l’utiliser ou l’autre selon les questions auxquelles vous essayez de répondre : questions liées aux mesures &quot;Personnes&quot; (rapports de type &quot;Personnes&quot;) ou questions liées aux mesures &quot;Opportunité&quot; (rapports de type ).

Article de prise en charge : [Différence entre les points de contact des acheteurs et les points de contact d’attribution des acheteurs](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md#configuration-and-setup){target="_blank"}

## Point de contact acheteur (BT) {#buyer-touchpoint-bt}

Buyer Touchpoint (BT) est l’objet utilisé pour effectuer le suivi de chaque interaction marketing qu’une personne a avec vos documents marketing. Le parcours (prospect/contact/[!DNL Marketo Measure] personne) de chaque individu serait représenté par son BT associé. Dans [!DNL Marketo Measure], le parcours d’un individu se compose des éléments suivants :

1. Comment cette personne a-t-elle d&#39;abord interagi avec notre marque ? (Première touche ou _FT_)
1. Comment cette personne a-t-elle été convertie / devenue connue / devenue une piste ? (Création de piste ou _LC_)
1. Comment autrement cette personne a-t-elle interagi avec notre marque et notre matériel marketing depuis qu&#39;elle est devenue une &quot;Lead&quot; ? (_PostLC_)

Les points de contact d’acheteur sont utilisés pour répondre aux questions relatives aux _personnes_ (&quot;personnes&quot; sont représentées par des pistes ou des contacts dans un CRM), telles que la génération de pistes/contacts ou les mesures d’acquisition, plutôt que les mesures liées aux opportunités. Par exemple :

* Quels sont les canaux qui diffusent le plus de pistes ?
* Quels canaux sont plus ou moins coûteux pour créer un nouveau prospect ?
* Avec quel contenu mes Leads/contacts s&#39;impliquent-ils ?
* Quelle est l&#39;histoire marketing de titres, rôles, personnages particuliers ?
* Quels canaux génèrent des MQL ou d’autres statuts de piste/contact ?

En premier lieu, les entreprises doivent savoir, &quot;d&#39;où viennent mes Leads/Contacts ?&quot; Historiquement, une seule valeur dimensionnelle était utilisée pour y répondre (Source de piste, par exemple). Cependant, comme indiqué dans #1 et #2 ci-dessus, nous savons que les Pistes peuvent avoir plusieurs points de contact lors de leur parcours de piste. Buyer Touchpoint nous permet d’avoir un aperçu des deux interactions les plus cruciales qui représentent la manière dont une piste a été générée : leur Première touche et leur Première touche de création de piste. Les points de contact d’achat sont également _multidimensionnels_, ce qui signifie qu’ils transportent des quantités de données marketing, principalement d’où provient la personne (canal marketing) et de ce avec quoi elle s’est engagée (contenu).

Les [modèles d’attribution](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md){target="_blank"} qui offrent les meilleures informations sur les mesures basées sur les personnes sont les suivants :

* **Première touche** - Crédits d’attribution 100 % à la Première touche du prospect (FT)
* **Création de piste** - Crédit d’attribution 100 % à la touche de création de piste (LC) du prospect
* **En forme de U** - approche multi-tactile, avec un crédit de 40 % au FT, un crédit de 40 % au LC

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-1.png"></td> 
   <td>Le modèle de forme de U est conçu pour accorder du crédit à tous les points de contact d’acheteurs qui résument la manière dont une piste est devenue une piste. Bien que les points de contact suivants de ces pistes puissent également être signalés pour comprendre un engagement supplémentaire (Post LC), ils ne font pas partie du <strong>parcours de création de piste</strong>. Ils n’obtiennent donc aucun crédit d’attribution dans les modèles en forme de FT, LC ou U.<p>

&#42;L’attribution en forme de U reflète le plus souvent une répartition paire 50/50 entre le mode FT et le mode LC. Si le prospect est converti au cours de la même session que la Première touche, un seul point de contact représente les positions des points de contact FT et LC. Par conséquent, 100 % de l’attribution serait attribuée à un seul point de contact.</td>
</tr>
 </tbody>
</table>

Ces modèles mettent fortement l’accent sur les interactions à un stade précoce et sur l’engagement dans l’entonnoir. L’attribution En forme de U est le modèle recommandé, car elle prend en compte les points de contact FT et LC, ce qui garantit que le crédit est attribué à tout contact qui a influencé la création du prospect. Toutefois, vous pouvez obtenir des informations supplémentaires à partir des modèles Première touche et Création de piste si vous souhaitez mieux comprendre ces parties spécifiques du parcours de piste.

## Rapports recommandés à l’aide de Buyer Touchpoint (BT) {#recommended-reports-using-the-buyer-touchpoint-bt}

1. **LEADS with BUYER TOUCHPOINTS**

**1.1 | Nouvelles pistes par canal marketing**

Résumer les données Buyer Touchpoint de votre prospect par le champ &quot;Canal marketing&quot; est la vue de niveau supérieur qui représente les canaux/tactiques qui influencent la création de pistes. Le fait de structurer ce rapport autour d’un &quot;Type de date&quot; = &quot;Date de création&quot; garantit qu’une cohorte de &quot;nouvelles pistes nettes&quot; (lorsque la piste a été créée dans votre CRM) est établie dans le rapport.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels canaux marketing influencent les pistes vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   Mesure : Pistes ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création de piste (CRM) / Date de création (Discover)</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de piste, <strong>En forme de U</strong><br>
   *SUM des champs 'Comptage' dans vos rapports CRM (Décompte - Première touche, Comptage - Création de piste, Comptage - En forme de U)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout type de rapport &quot;Pistes avec points de contact client&quot;, commencez par personnaliser le rapport prédéfini intitulé &#39;[!DNL Marketo Measure] 101 | Pistes par canal&#39;. Ce rapport, qui est prêt à l’emploi, est un environnement de test prédéfini idéal, comme décrit dans le tableau ci-dessus. Il peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques.

**1.2 | Nouvelles pistes par campagne (ou informations plus granulaires)**

Pour obtenir des informations plus détaillées sur les données résumées dans le rapport &quot;Nouvelles pistes par canal marketing&quot; (1.1), ajoutez un résumé supplémentaire au niveau de la campagne. Cela vous permet non seulement de comprendre quels &quot;canaux marketing&quot; sont à l’origine de la création de nouvelles pistes, mais plus précisément, quelles campagnes au sein de ces canaux sont les plus performantes :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quelles <i>campagnes</i> influencent les pistes vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   Mesure : Pistes ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création de piste (CRM) / Date de création (Discover)</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Nom de la campagne publicitaire (CRM)</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de piste, <strong>En forme de U</strong><br>
   *SUM des champs 'Comptage' dans vos rapports CRM (Décompte - Première touche, Comptage - Création de piste, Comptage - En forme de U)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Obtenez des informations encore plus granulaires en résumant le rapport avec d’autres champs disponibles de l’objet Buyer Touchpoint. Pour ce faire, définissez des regroupements (CRM) ou des dimensions supplémentaires (Discover). Selon le canal (qui peut être représentatif de votre rôle), il peut y avoir des détails supplémentaires au-delà du niveau de campagne dans lequel vous souhaitez obtenir des informations. Explorons &quot;Recherche payante&quot;, par exemple dans le tableau ci-dessous...

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels <i>mots-clés</i> influencent les pistes vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   Mesure : Pistes ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>Canal marketing = Recherche payante</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création de piste (CRM) / Date de création (Discover)</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Texte du mot-clé (CRM) / Mot-clé (Discover)</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de piste, <strong>En forme de U</strong><br>
   *SUM des champs 'Comptage' dans vos rapports CRM (Décompte - Première touche, Comptage - Création de piste, Comptage - En forme de U)</td> 
  </tr>
 </tbody>
</table>

Le niveau de granularité peut varier en fonction du canal. L&#39;approche recommandée serait de vous demander : &quot;Et le &quot;canal X&quot; que vais-je chercher à comprendre plus en détail ?&quot; Les gestionnaires de recherche payante peuvent également être intéressés par d’autres dimensions, telles que :

* Nom de la campagne publicitaire
* Contenu publicitaire
* Groupe publicitaire

Les gestionnaires d’événements peuvent toutefois être plus intéressés par les événements spécifiques ou les types d’événements qui ont influencé le plus de pistes dans la création :

* Nom de la campagne publicitaire / Campagne Salesforce = événement spécifique
* Medium = &quot;Type&quot; de la campagne

**REMINDER** : il se peut que des filtres supplémentaires doivent être ajoutés à l’une des variations de rapport décrites ci-dessus ou ci-dessous. Ces filtres seraient spécifiques à votre organisation et seraient utiles aux équipes des opérations marketing ou des opérations commerciales. Il n’est pas rare qu’une organisation exécute les mêmes filtres sur tous les rapports pour s’assurer que le rapport est aussi propre et précis que possible. Voici quelques exemples courants :

* Filtrage des enregistrements internes des tests, généralement par adresse email
* Filtrage basé sur certains &quot;types d’enregistrement&quot; qui peuvent être spécifiques à votre unité opérationnelle

**1.3 | Nouvelles pistes par contenu (rapports CRM uniquement)**

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quel <i>contenu</i> influence les pistes vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)</td> 
  </tr>
  <tr>
   <td>Champ de date</td> 
   <td>Date de création du lead</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Page d’entrée<br> 
   URL du formulaire</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de piste, <strong>En forme de U</strong><br></td> 
  </tr>
 </tbody>
</table>

**REMINDER** : les deux champs principaux pour la création de rapports sur le contenu/les ressources numériques sont &#39;Landing Page&#39; et &#39;Form URL&#39;. Ces deux valeurs peuvent être identiques si le prospect convertit (envoie un formulaire) sur la même page que celle sur laquelle il est &quot;arrivé&quot; (page d’entrée), _cependant_, ces valeurs sont parfois différentes. Par exemple, le prospect peut cliquer sur un lien de Facebook qui l’amène à une page de votre site web (il s’agit de la valeur &quot;Page d’entrée&quot;). Il peut ensuite quitter cette page, poursuivre sa session sur le site et envoyer un formulaire sur une autre page (URL du formulaire). Cela serait résumé dans un seul point de contact qui représente l’origine du prospect (canal marketing), le contenu qui les a amenés sur le site (page d’entrée) et le contenu qu’ils ont fini par télécharger (URL du formulaire). &quot;URL du formulaire&quot; est également le champ d’orientation permettant de créer des rapports sur d’autres formulaires non associés à du contenu téléchargeable, tels que les formulaires &quot;Nous contacter&quot; ou &quot;Demo Request&quot;.

>[!TIP]
>
>Obtenir des informations sur un &quot;contenu&quot; spécifique avec des filtres supplémentaires
>
>* Filtrez par : &#39;Landing Page&#39; CONTIENT (par exemple :
>   * /blog
>   * /ebook
>   * /webinaire
>
>* OU : &quot;URL du formulaire&quot; CONTIENT (par exemple,
>   * /contact
>   * /demo

Les rapports basés sur le &quot;contenu&quot; offrent une grande valeur lors de la création de rapports sur n’importe quelle partie de l’entonnoir. Toutefois, ils sont le plus souvent utilisés en haut de l’entonnoir pour fournir des informations supplémentaires sur un engagement initial de Leads. Dans la mesure où la &quot;recherche organique&quot; tend à être le canal le plus puissant pour générer l’engagement initial (FT), il n’y a pas autant de données au niveau de &quot;campagne&quot;.

Les rapports basés sur le &quot;contenu&quot; sont très utiles pour mieux comprendre ce qui motive les pistes plus spécifiquement dans le canal marketing de niveau supérieur, dans ce cas &quot;Recherche organique&quot;.

**1.4 | Total de l’engagement au prospect sur une période donnée**

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels sont les canaux marketing qui ont eu le plus <i>engagement total de piste</i> au cours de la dernière semaine (semaine/mois/trimestre) ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br> 
   Mesure : Pistes ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date du point de contact</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing (ou plus granulaire)</td> 
  </tr>
  <tr>
   <td>Modèles optimaux*</td> 
   <td>*Ce rapport porte moins sur la mesure d’où proviennent les pistes avec un modèle d’attribution que sur le <i>nombre total de points de contact (montant de l’engagement)</i>, y compris ceux qui suivent la touche de création de pistes. Le nombre total d’enregistrements des points de contact refléterait les canaux ayant enregistré le plus d’engagements de piste.</td> 
  </tr>
 </tbody>
</table>

**REMINDER** : baser vos rapports sur la &quot;date du point de contact&quot; est la manière la plus réfléchie de comprendre les performances marketing au cours d’une période donnée. La &quot;Date du point de contact&quot; structure le rapport d’une manière où l’attribution n’est pas seulement liée au canal, à la campagne ou au contenu, mais elle indique également le moment où le point de contact s’est produit. Il s’agit de la manière la plus efficace de comprendre ce qui se passait à un certain moment de l’engagement marketing. Il s’agit également de la manière recommandée de mesurer l’impact du marketing par rapport aux dépenses marketing investies au même moment. Il est recommandé d’effectuer toute analyse de dépenses marketing ou de retour sur investissement (voir 5.1).

**2. MARKETING QUALIFIED LEADS with BUYER TOUCHPOINTS**

L’un des rapports les plus courants ne concerne pas seulement les nouveaux engagements au niveau des pistes ou des pistes, mais plus particulièrement les &quot;pistes qualifiées en marketing&quot; (MQL). Il existe deux approches différentes en ce qui concerne la création de rapports sur les MQL en fonction des fonctionnalités [!DNL Marketo Measure] auxquelles vous avez accès.

**2.1 | Pistes qualifiées marketing par canal (multi-touch)**

Cette approche permettant de mesurer l’impact du marketing sur l’influence des MQL est essentiellement une suite du rapport &quot;Nouvelles pistes par canal marketing&quot; (1.1), mais avec les critères supplémentaires que les pistes mesurées sont plus spécifiquement des MQL. Le modèle d’attribution En forme de U est toujours recommandé ici pour identifier les canaux marketing et le contenu qui génèrent des pistes qui sont alors _susceptibles_ de devenir un MQL :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels canaux marketing sont les mieux à même de générer de nouvelles pistes qui deviennent <i>MQLs</i> ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br> 
   Mesure : Pistes ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>MQL = true*<br>
   *<i>Les MQL peuvent être définis différemment par organisation. Assurez-vous que le rapport [!DNL Marketo Measure] est filtré pour les MQL à l’aide du ou des mêmes champs que les autres rapports basés sur MQL. Un filtre Segment doit être créé de la même manière pour la création de rapports sur les MQL dans [!DNL Marketo Measure] Discover.</i></td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date MQL (ou équivalente) / Date de création ([!DNL Marketo Measure] Discover)<br> <i> La date de création de piste peut également être utilisée dans les rapports CRM si "Date MQL" n’est pas une option dans votre CRM. Il est important de garder à l’esprit le champ de date que vous utilisez pour définir le jeu de données de cohortes.</i></td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de piste, <strong>En forme de U</strong><br> 
   SOMMEZ les champs "Comptage" dans vos rapports CRM (Comptage - Première touche, Comptage - Création de piste, Comptage - En forme de U).</td> 
  </tr>
 </tbody>
</table>

**2.2 | Pistes qualifiées marketing par canal (touche unique, CRM uniquement)**

Cette méthode de mesure de l’impact du marketing sur l’influence des MQL consiste à identifier le _point de contact unique_ qui était la dernière touche avant que le prospect n’atteigne MQL.

>[!NOTE]
>
>Pour exécuter ce rapport, une valeur &quot;État de piste&quot; de &quot;MQL&quot; est requise pour définir l’étape MQL à des fins de suivi (Évaluation de l’entonnoir). Si les MQL ne font pas l’objet d’un suivi via le champ &quot;État de la piste&quot;, la fonction Modèle d’attribution personnalisé avec étapes personnalisées est nécessaire pour créer une étape &quot;MQL&quot; personnalisée dans les paramètres du compte [!DNL Marketo Measure].

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels canaux marketing sont les plus efficaces pour pousser les Leads à atteindre l’état MQL ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   <i>ce rapport n’est possible que dans les rapports CRM. Il n’est pas possible de filtrer certaines valeurs "Position du point de contact" dans [!DNL Marketo Measure] Discover</i></td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td><strong>Position du point de contact CONTIENT "MQL"</strong></td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date MQL (ou équivalente)</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td><i>Ce rapport étant filtré sur un seul point de contact, les modèles d’attribution au niveau de l’piste ne sont pas aussi pertinents. À l’instar du "rapport Engagement de piste" (1.4), le nombre d’enregistrements de point de contact est utilisé ici pour déterminer les canaux les plus puissants (chaque piste ne possède qu’un seul point de contact MQL).</i></td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Explorez d’autres regroupements ou dimensions pour mieux comprendre les MQL. Comme mentionné dans les autres rapports &quot;Points de contact Pistes avec acheteurs&quot;, Buyer Touchpoint offre une granularité beaucoup plus grande que le canal marketing. Un rapport basé sur le &quot;contenu&quot; peut également être combiné avec l’un des rapports MQL ci-dessus pour mieux comprendre quel contenu influe le mieux sur les MQL.

**3. [!DNL MARKETO MEASURE] PERSONNES AVEC POINTS DE CONTACT DE L’ACHETEUR**

Il existe un troisième objet [!DNL Marketo Measure] personnalisé dans Salesforce qui peut être très utile lors de la création de rapports sur les mesures liées aux personnes : **la [!DNL Marketo Measure] personne (BP)**. BP résout le vieux problème de la façon de représenter les informations des Leads et des Contacts dans le même rapport. Il réunit tous les BT liés à une &quot;personne&quot; (l’ID de personne [!DNL Marketo Measure] correspond à son adresse électronique). Qu&#39;il s&#39;agisse d&#39;un prospect ou d&#39;un contact, BP fait office d&#39;objet de passerelle, pour aider les rapports à s&#39;étendre sur les canaux &quot;Lead&quot; et &quot;contact&quot;, et se révèle particulièrement utile dans la production de rapports plus élaborés sur les personnes.

La personne [!DNL Marketo Measure] ne se rapporte qu’à l’un des objets de point de contact, le Buyer Touchpoint (BT). Cela signifie qu’il ne peut pas être utilisé pour des mesures liées aux opportunités ou aux recettes. Un type de rapport &#39;[!DNL Marketo Measure] Points de contact de personne et d’acheteur&#39; est idéal pour comprendre l’ _engagement total_, car il BT tous si le BT se rapporte à un prospect ou à un contact plus spécifiquement. Par exemple, si une campagne Salesforce est utilisée pour le suivi d’un événement, il se peut que des membres de campagne au sein de la campagne CRM existent sous la forme de Pistes OU de Contacts. [!DNL Marketo Measure] crée des points de contact pour les membres de la campagne, mais sans la [!DNL Marketo Measure] Personne, les rapports Salesforce standard requièrent deux rapports distincts pour comprendre le nombre de points de contact _total_ de l’événement : un point de contact &quot;Leads with Buyer Touchpoints&quot; et un point de contact &quot;Contacts avec points de contact de l’acheteur&quot;. Quelques autres cas pratiques de rapports basés sur des personnes sont répertoriés ci-dessous :[!DNL Marketo Measure]

**3.1 [!DNL Marketo Measure] Personnes ayant téléchargé des &quot;livres électroniques&quot; ou des &quot;livres blancs&quot; (nombre total de téléchargements)**

Ce rapport serait identique à un rapport basé sur le &quot;contenu&quot; au niveau de l’piste. Cependant, au lieu de chercher à mesurer le nombre de pistes pouvant être attribuées à chaque élément de contenu, l’utilisation d’un rapport [!DNL Marketo Measure] Personnes sera utile pour comprendre le nombre total de _téléchargements_ si la ressource est sécurisée (le nombre total de points de contact représenterait le nombre total de téléchargements/envois de formulaire).

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Combien de personnes ont téléchargé une ressource spécifique ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>[!DNL Marketo Measure] Points de contact pour les personnes et les acheteurs (CRM)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>'URL du formulaire' CONTIENT (par exemple,<br>
   <li>/ebook</li>
   <li>/whitepaper</li>
   <i>Les valeurs de filtre ci-dessus ne sont que des exemples. La valeur réelle sera basée sur la structure d'URL de chaque organisation.</i></td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date du point de contact <i> (quand la ressource a été téléchargée)</i></td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>URL du formulaire</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Ce rapport porte moins sur la mesure d’où viennent les Leads ou les contacts avec un modèle d’attribution que sur le <i>nombre total de points de contact (montant de l’engagement)</i>, y compris ceux qui suivent la touche de création de piste. Avec ce rapport, nous cherchons à comprendre le <i>montant total de l’engagement</i>. Le nombre total d’enregistrements des points de contact reflète les ressources qui ont été les plus téléchargées.</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout type de rapport &#39;Leads with [!DNL Marketo Measure] Personnes&#39;, commencez par personnaliser le rapport prédéfini intitulé &#39;**[!DNL Marketo Measure]101 | Pistes/contacts par canal**&#39;. Ce rapport est disponible prêt à l’emploi et est un super environnement de test basé sur les [!DNL Marketo Measure] personnes. Il est prédéfini et peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques.

>[!TIP]
>
>Vous pouvez utiliser ce rapport pour mieux comprendre l’engagement total d’une dimension marketing à partir de l’objet Buyer Touchpoint, et pas seulement les téléchargements de contenu comme présenté dans l’exemple. Le rapport peut plutôt être groupé ou filtré selon des dimensions telles que &quot;Canal marketing&quot; ou &quot;Nom de la campagne publicitaire&quot; afin de mieux comprendre l’engagement total des Leads et des contacts dans votre base de données. Remplacez les filtres ou les groupements dans le rapport par zéro dans les autres dimensions représentées par d’autres champs de l’objet de point de contact.

**3.2 [!DNL Marketo Measure] Personnes qui se sont enregistrées pour un événement (CRM uniquement){2**

_Ce rapport ne s&#39;applique que si les formulaires d&#39;enregistrement sont hébergés sur votre ou vos sites web dont le suivi numérique est possible sur [!DNL Marketo Measure]._

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels sont les canaux marketing qui génèrent mes enregistrements d’événement ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>[!DNL Marketo Measure] Points de contact pour les personnes et les acheteurs (CRM)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>'URL du formulaire' CONTIENT (par exemple,<br>
   <li>/event</li>
   <i>La valeur de filtre ci-dessus ne sont que des exemples. La valeur réelle sera basée sur la structure d'URL de chaque organisation.</i></td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date du point de contact <i>(lorsque le formulaire d’enregistrement a été envoyé)</i></td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>URL du formulaire<br>
   Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Ce rapport porte moins sur la mesure d’où viennent les Leads ou les contacts avec un modèle d’attribution que sur le <i>nombre total de points de contact (nombre d’inscriptions)</i>, y compris ceux qui suivent la touche de création de piste. Avec ce rapport, nous recherchons des informations sur les causes des inscriptions aux événements. Le nombre total d’enregistrements des points de contact par "Canal marketing" refléterait les canaux qui ont généré le plus d’inscriptions.</td> 
  </tr>
 </tbody>
</table>

L’élément essentiel de ce rapport est que les données Buyer Touchpoint fournissent également des données de canal marketing. Bien que vous ayez déjà des informations sur le nombre de personnes qui se sont enregistrées pour vos événements, ce rapport vous donnera également des informations sur les canaux marketing numériques, les sources et/ou les campagnes qui amènent des personnes à votre site web pour s’inscrire à l’événement.

>[!TIP]
>
>Cette même approche peut être utilisée pour mieux comprendre les inscriptions aux webinaires ou peut-être les téléchargements de webinaires à la demande (s’il s’agit d’une ressource fermée). La seule différence serait la valeur de filtre dans &quot;URL du formulaire&quot; si ces formulaires sont hébergés sur des pages uniques de votre site web. L&#39;objectif est le même, cependant. Il répond aux questions &quot;lequel de mes canaux marketing génère le plus d’inscriptions/téléchargements de webinaires à la demande.

**3.3 [!DNL Marketo Measure] Personnes avec points de contact d’achat (validation de point de contact)**

Étant donné que la personne [!DNL Marketo Measure] nous permet de créer des rapports sur tous les points de contact d’un seul rapport, il s’agit du type de rapport idéal à utiliser pour valider vos données. Nous voulons nous assurer que nous n’ignorons aucun point de contact pouvant indiquer où, par exemple, il existe un problème dans la configuration de vos &quot;canaux marketing&quot; (voir les articles de support ci-dessous pour plus d’informations sur la configuration de vos &quot;canaux marketing&quot;).

* [Configuration de canal personnalisé en ligne](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md){target="_blank"}
* [Configuration de canal personnalisé hors ligne](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md){target="_blank"}

Essentiellement, les données du point de contact refléteront ce qui a été suivi par [!DNL Marketo Measure] et peuvent être contrôlées afin de vous assurer que votre configuration correspond aux entrées en fonction d’éléments tels que : les valeurs de paramètre UTM, les pages de référence ou les types de campagne. Si les données du point de contact ne correspondent pas à votre configuration, il est probable qu’une modification soit nécessaire. Au-delà de la configuration &quot;Canal marketing&quot;, vous pouvez consulter les données de point de contact pour déterminer quels points de contact doivent être [supprimés](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) ou [segmentés](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md){target="_blank"}. Il est recommandé de contrôler, si possible, vos données de point de contact dans un rapport &quot;[!DNL Marketo Measure] personne et points de contact d’achat&quot; à la fin de chaque mois ou trimestre. Votre attribution sera ainsi aussi précise que possible. Le &#39;[!DNL Marketo Measure] 101 | Le rapport Leads/Contacts par canal, disponible d&#39;usine, est un bon point de départ. Insérez les champs suivants s’ils ne sont pas déjà inclus afin de passer en revue certains des éléments de configuration les plus essentiels :

* **Canal marketing** - Chemin = Canal marketing.Subchannel (valeurs définies dans [!DNL Marketo Measure])
* **Source point de contact** = utm_source
* **Medium** = utm_medium (points de contact en ligne) OU Type de campagne CRM (points de contact hors ligne)
* **Page du référent** (utilisation de la configuration &quot;Canaux en ligne&quot;)
* **Landing Page - Raw** (utilisation de la configuration &quot;Canaux en ligne&quot;) est également une entrée courante pour la suppression des points de contact dans l’onglet &quot;Paramètres des points de contact&quot; de vos paramètres.
* **URL du formulaire** (une entrée courante pour la suppression de point de contact dans l’onglet &quot;Paramètres du point de contact&quot; de vos paramètres)

**BUYER ATTRIBUTION TOUCHPOINT (BAT)**

Les points de contact d’attribution de l’acheteur (BAT) représentent les points de contact pertinents de tous les contacts connectés à l’opportunité (soit via les rôles de contact de l’opportunité, soit via un ID de compte partagé, selon vos paramètres). Contrairement aux BT (qui sont principalement liés aux personnes), BAT peut être associé aux revenus. À ce titre, vous utiliserez BAT pour répondre à des questions relatives aux opportunités, principalement pour ouvrir _Opportunités/Recettes de pipeline_ et fermer l’accès remporté _Opportunités/Offres/Recettes_. Un BAT est créé par le biais des enregistrements BT d&#39;un contact dès qu&#39;une Opportunité est créée sous le même compte que le contact (le  n&#39;est pas converti en . Les données BT sont simplement référencées pour créer un enregistrement supplémentaire (le BAT qui correspond ensuite à l’ opportunité ).

Buyer Attribution Touchpoint nous permet de mesurer l’impact du marketing plus profondément dans l’entonnoir. _La profondeur de l’entonnoir sur lequel vous souhaitez mesurer peut être représentée par les différents modèles d’attribution multi-touch_.

Étant donné BAT relation principale avec l’opportunité, elles sont utilisées pour répondre à des questions telles que :

* Quels sont mes efforts marketing qui ont influencé les opportunités les plus importantes ?
* Combien de nouvelles recettes de pipeline puis-je attribuer à chacun de mes canaux marketing ?
* Laquelle de mes campagnes a connu le meilleur retour sur investissement le trimestre dernier ?

Les [modèles d’attribution](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md){target="_blank"} qui offrent les meilleures informations sur les mesures basées sur les opportunités sont les suivants :

**En forme de W** - &#39;_Modèle de pipeline_&#39;. Trois points de contact de jalon sont inclus dans le modèle en forme de W. les points de contact FT, LC et OC se voient attribuer chacun 30 % du crédit d’attribution. Les 10 % restants sont attribués de manière égale à tous les points de contact intermédiaires qui se produisent entre les trois points de contact de jalon.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-2.png"></td> 
   <td>Ce modèle résume essentiellement le parcours d’une nouvelle opportunité, généralement synonyme de génération de nouvelles recettes de pipeline.<p>
   <p>
   Lorsque vous souhaitez mesurer l’impact du marketing sur les nouvelles opportunités ou le nouveau pipeline généré, le modèle en forme de W est recommandé.</td> 
  </tr>
 </tbody>
</table>

**Chemin Complet** - &#39;_Modèle Won Fermé_&#39;. Ce modèle comprend les quatre points de contact de jalon : FT, LC, OC et Fermé. Chacun reçoit 22,5 % du crédit Opportunity, et les 10 % restants sont répartis à parts égales entre les touches intermédiaires.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-3.png"></td> 
   <td>Ce modèle résume essentiellement l’parcours d’une transaction gagnée clôturée, généralement synonyme de recettes/réservations gagnées fermées.<p>
   <p>
   Lorsque vous essayez de mesurer l’impact du marketing sur les affaires clôturées gagnées ou les recettes clôturées gagnées, le modèle de chemin complet est recommandé.</td> 
  </tr>
 </tbody>
</table>

Ce modèle résume essentiellement l’parcours d’une transaction gagnée clôturée, généralement synonyme de recettes/réservations gagnées fermées.

Lorsque vous essayez de mesurer l’impact du marketing sur les affaires clôturées gagnées ou les recettes clôturées gagnées, le modèle de chemin complet est recommandé.

**Personnalisé** - [!DNL Marketo Measure] propose également un modèle d’attribution personnalisée qui permet aux utilisateurs de choisir les points de contact ou les étapes personnalisées à inclure dans leur modèle. En outre, les utilisateurs peuvent contrôler le pourcentage du crédit d’attribution attribué à ces points de contact et étapes. Selon la configuration de votre modèle personnalisé, il peut être utilisé le mieux pour mesurer les opportunités et le pipeline OU, les affaires et les recettes gagnantes fermées. Gardez cela à l’esprit lorsque vous l’utilisez dans vos rapports.

>[!NOTE]
>
>Le modèle d’attribution personnalisé est une fonctionnalité supplémentaire qui n’est pas disponible pour tous les clients. Contactez l’équipe du compte d’Adobe (votre gestionnaire de compte) pour en savoir plus sur la manière d’ajouter cette fonctionnalité à votre compte.

En général, les marketeurs doivent savoir d’où viennent mes opportunités. Tout comme pour les rapports au niveau des pistes, une seule valeur unidimensionnelle a été ajoutée à cette question lors de l’historique (par exemple, Source Campaign Principal). Cependant, nous savons que le développement d’une opportunité est bien plus important qu’un seul point de contact d’un seul contact. Il existe généralement plusieurs points de contact de différents canaux et de plusieurs parties prenantes qui influencent une opportunité dans la création. [!DNL Marketo Measure] permet de faire apparaître tous les points de contact d’un compte afin de mieux comprendre d’où provient une opportunité. Au-delà de cela, cependant, nous pouvons continuer à faire apparaître tout point de contact qui s’est produit après la création de l’opportunité et jusqu’au point où l’opportunité est fermée. Cela nous permet non seulement d’adopter une approche multi-touch pour comprendre d’où provient une opportunité, mais aussi ce qui l’a influencée pour fermer et finalement représenter des recettes gagnées fermées. Cela vous permet d’avoir un aperçu de différentes questions, telles que &quot;Quel est l’impact du marketing sur l’activation de la fermeture des transactions ?&quot;, &quot;Quel est le moteur de la fermeture des recettes par gagnant ?&quot;. et, finalement, &quot;lequel de mes efforts marketing voit le meilleur retour sur investissement ?&quot;

## RAPPORTS RECOMMANDÉS À L’AIDE DE BUYER ATTRIBUTION TOUCHPOINT (BAT) {#recommended-reports-using-the-buyer-attribution-touchpoint}

**4.1 | Nouvelles opportunités par canal marketing**

Résumer vos opportunités Les données Buyer Attribution Touchpoint par champ &quot;Canal marketing&quot; représentent la vue de niveau supérieur qui représente les canaux/tactiques qui influencent les nouvelles opportunités dans la création. En structurant ce rapport autour d’un &quot;Type de date&quot; = &quot;Date de création de l’opportunité&quot;, vous vous assurez que nous résumerons également le rapport en fonction du moment où l’opportunité a été réellement créée dans votre CRM. Les points de contact peuvent provenir d’un certain temps auparavant, mais ils se rapportent toujours aux opportunités qui ont été créées au cours de la période définie et reçoivent ainsi du crédit d’attribution, car ils sont reconnus comme ayant influé sur l’opportunité.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels <i>canaux marketing</i> influencent les opportunités dans la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact d’attribution des acheteurs avec opportunités (CRM)<br> 
   Mesure : opportunités ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>
   <li>Étape de l’opportunité* <i> (facultatif selon les opportunités spécifiques que vous souhaitez limiter au rapport. Vous pouvez uniquement souhaiter créer des rapports sur les BAT qui sont toujours associés uniquement aux opportunités "ouvertes" (par exemple)</i></li>
   <li>Type d’opportunité (il est courant de filtrer certaines opportunités, par exemple "Nouvelle entreprise", par opposition à <i>toutes</i> opportunités)</li><br>
   *Un filtre de segment pour "Type d’opportunité" doit être utilisé dans [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création de l'opportunité (CRM) / Date de création (Discover)</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td><strong>En forme de W</strong><br>
   SOMMEZ les champs "En forme de W" dans vos rapports CRM (Comptage - En forme de W, Recettes - En forme de W).</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout type de rapport &quot;Points de contact d’attribution de l’achat avec opportunités&quot;, commencez par personnaliser le rapport prédéfini intitulé &#39;[!DNL Marketo Measure] 101 | Opportunités par canal&quot;. Ce rapport, qui est prêt à l’emploi, est un environnement de test prédéfini idéal, comme décrit dans le tableau ci-dessus. Il peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques (le rapport utilise un modèle Chemin complet prêt à l’emploi. Veillez donc à personnaliser le rapport afin d’inclure tout autre modèle d’attribution, le modèle En forme de W, dans ce cas).

>[!TIP]
>
>Le rapport présenté ci-dessus serait également utilisé pour déterminer la quantité de devise à attribuer. Lors de la création de rapports au niveau de l’opportunité à l’aide de BAT, deux mesures clés doivent être résumées : la devise (le montant de l’opportunité) et l’enregistrement de l’opportunité lui-même. Dans l’exemple ci-dessus, nous mesurons plus spécifiquement les opportunités ouvertes et les nouvelles recettes de pipeline.

>[!TIP]
>
>Obtenez des informations encore plus granulaires en résumant le rapport avec d’autres champs disponibles de l’objet Buyer Attribution Touchpoint. Cette opération s’effectue de la même manière qu’au niveau de l’piste avec les points de contact d’achat (1.2). Pour ce faire, ajoutez des regroupements (CRM) ou des dimensions supplémentaires (Discover). Selon le canal (qui peut être représentatif de votre rôle), il peut y avoir des détails supplémentaires au-delà du niveau de campagne dans lequel vous souhaitez obtenir des informations supplémentaires. Explorons la section &quot;Recherche payante&quot; ci-dessous :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels <i>mots-clés</i> de mes annonces de recherche payante génèrent le plus de recettes de pipeline ?
</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact d’attribution des acheteurs avec opportunités (CRM)<br> 
   Mesure : opportunités ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>
   <li>Canal marketing = Recherche payante</li>
   <li>Étape de l’opportunité* <i> (facultatif selon les opportunités spécifiques que vous souhaitez limiter au rapport. Cet exemple est basé sur les recettes du pipeline, définies dans [!DNL Marketo Measure] par "Ouvrir" des opportunités représentant les recettes potentielles/l’ouverture d’un pipeline)</i></li>
   <li>Type d’opportunité (il est courant de filtrer certaines opportunités, par exemple "Nouvelle entreprise", par opposition à <i>toutes</i> opportunités)</li><br>
   *Un filtre de segment pour "Type d’opportunité" doit être utilisé dans [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création d'opportunité</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Texte du mot-clé (CRM)<br> 
   Mot-clé (Discover)</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td><strong>En forme de W</strong><br>
   SOMMEZ les champs "En forme de W" dans vos rapports CRM (Comptage - En forme de W, Recettes - En forme de W).</td> 
  </tr>
 </tbody>
</table>

**4.2 | Transactions par canal marketing**

Ce rapport serait essentiellement le même que le premier exemple Buyer Attribution Touchpoint (4.1), sauf que la mesure est désormais passée d’une option Opportunités ouvertes à une option Offres gagnées clôturée. La mesure doit toujours être celle qui informe le modèle d’attribution à utiliser. Dans la mesure où nous étudions maintenant les affaires à huis clos et leurs BAT connexes, nous devrions utiliser un modèle qui représente l&#39;ensemble du parcours de l&#39;acheteur (Deal). Cela garantit que tout suivi de contact marketing pendant le parcours de l’acheteur reçoit un crédit d’attribution :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels <i>canaux marketing</i> influencent la fermeture des transactions ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact d’attribution des acheteurs avec opportunités (CRM)<br> 
   Mesure : affaires ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>
   <li>Étape d’opportunité (<i>seules les opportunités gagnantes fermées doivent être dans le rapport{1) OU,</i></li>
   <li>Opportunité gagnée = Vrai</li>
   <li>Type d’opportunité (il est courant de filtrer en fonction de certaines opportunités, c’est-à-dire "Nouvelle entreprise" par opposition à toutes les opportunités)<br>
   </td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de fermeture de l'opportunité</td> 
  </tr>
  <tr>
   <td>Période</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td><strong>Chemin complet</strong><br>
   SUM des champs "Chemin complet" dans vos rapports CRM (Comptage - Chemin complet, Recettes - Chemin complet)</td> 
  </tr>
 </tbody>
</table>

**REMINDER** : il est essentiel de ne pas oublier de filtrer les opportunités spécifiques que vous souhaitez inclure dans les rapports basés sur BAT, en particulier lorsqu’il s’agit d’&quot;opportunités ouvertes et revenus du pipeline&quot; par rapport à &quot;affaires et recettes de gains clôturées&quot;. Cela est généralement effectué par le biais d’un filtre &quot;Étape de l’opportunité&quot; (le filtre &quot;Gagnant de l’opportunité&quot; = vrai/faux peut également s’avérer très utile ici).

>[!MORELIKETHIS]
>
>[Nouveau guide du tableau de bord Discover](/help/marketo-measure-discover-ui/dashboards/new-discover-dashboard-guide.md){target="_blank"}
