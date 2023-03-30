---
description: "[!DNL Marketo Measure] Guide de création de rapports - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] Guide de création de rapports"
exl-id: 9b991f9e-c187-4b43-b0a8-8ed3e9a6056b
source-git-commit: 51397a02872035fef41d308c1f855bcaecc29c4e
workflow-type: tm+mt
source-wordcount: '6395'
ht-degree: 2%

---

# Guide de création de rapports [!DNL Marketo Measure] {#marketo-measure-reporting-guide}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans notre documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version et la nouvelle image sera bientôt répercutée dans votre CRM.

Avant de créer un [!DNL Marketo Measure] , il est essentiel de confirmer votre [!DNL Marketo Measure] Les paramètres du compte ont été examinés et configurés afin de garantir que les données des rapports sont exactes et reflètent les spécificités de votre entreprise. En outre, les projets de création de rapports fonctionnent mieux lorsqu’ils suivent un processus structuré. Justin Norris, un [!DNL Marketo Measure] utilisateur, défenseur et partenaire puissants de [Perkuto](https://perkuto.com/) résumé [approche de la création de rapports dans [!DNL Marketo Measure]](https://perkuto.com/blog/turning-attribution-data-into-actionable-insights/):

**Définition des objectifs**: &quot;La première question à poser est : &quot;pourquoi mesurons-nous ?&quot; Lori wizard of [Forrester Research](https://go.forrester.com/) pour résumer cela joliment dans un [Webinaire Marketo](https://www.marketo.com/webinars/beyond-revenue-performance-real-kpis-of-b2b-marketing/). Selon elle, &quot;nous mesurons pour prouver ou valider une décision ou la valeur du marketing ou pour obtenir de meilleurs résultats (amélioration des processus).&quot; Nous ajouterons que les informations issues de bonnes mesures fournissent également des informations et des conseils sur le processus de planification marketing.

Avant de commencer, il est essentiel d&#39;être clair comme du cristal sur vos objectifs, les questions auxquelles vous essayez de répondre, ou les problèmes que vous essayez de résoudre. Quelle histoire voulez-vous raconter ? Quelles décisions seront prises en conséquence ? Trop souvent, ces fondamentaux sont mal pensés, ce qui entraîne une frustration pour tous les acteurs impliqués.&quot;

**Conception de rapports**: &quot;Ensuite, vous devez concevoir le rapport et déterminer les dimensions, les mesures et le jeu de données spécifiques qu’il contiendra. Une expérience courante consiste à fournir à un utilisateur chargé de l’entreprise exactement ce qu’il demande, uniquement pour qu’il ait toujours l’impression que ses besoins ne sont pas satisfaits. Cela est dû au fait que l’information recherchée par un utilisateur chargé de la conception de parcours n’est pas toujours contenue dans le rapport qu’il demande. Un bon analyste (ou une personne du MOPS avec un analyste qui est là) posera des questions claires, établira des définitions communes (&quot;donc, qu&#39;est-ce que vous voulez vraiment dire par plomb ?&quot;) et même esquissera un visuel du rapport final pour s&#39;assurer qu&#39;il y a un alignement. C’est seulement alors que vous créez le rapport, en sachant que vous avez de solides exigences.&quot;

**Version du rapport**: &quot;Une fois que vous allez construire, il n&#39;est pas rare de rencontrer des barrages routiers ou des impasses. Par exemple, vous pouvez découvrir que vous ne disposez pas d’un point de données essentiel ou que vos objets ne sont pas liés de la manière dont vous en avez besoin. Pour résoudre ces problèmes, je pense aussi qu&#39;il est essentiel de comprendre ce qui se passe &quot;sous le capot&quot; dans votre &quot;machine&quot; de reportage. Cette aisance vous permet de dimensionner rapidement une demande de création de rapports et d’évaluer si elle est réalisable (et de concevoir plus facilement des solutions créatives dans le cas contraire).&quot;

Jetons un coup d&#39;oeil &quot;sous le capot&quot; pour mieux comprendre ce qui fait que [!DNL Marketo Measure] exécution de la machine de rapports d’attribution.

## Objets de point de contact client (CRM) {#buyer-touchpoint-objects-crm}

Au niveau supérieur, il existe deux catégories de rapports basées sur les deux objets de point de contact d’achat différents : Ces catégories déterminent le type de [!DNL Marketo Measure] données sur lesquelles vous souhaitez générer des rapports : données liées à un _individu_, ou les données liées à un _occasion_.

1. **Points de contact de l’utilisateur** (BAT) / Particuliers / Total des engagements

   * Généralement utilisé pour les mesures et les rapports relatifs à l’&quot;entonnoir&quot; (TOFU) _individus_ (Leads, contacts, [!DNL Marketo Measure] Personnes)
   * Les BT sont utilisés pour comprendre toutes les interactions marketing liées à **personnes**, car ils contiennent l’historique complet des points de contact pour chaque personne. Pour rappel, ces points de contact sont créés dans le CRM pour la Première touche anonyme, la Touche de création de piste et tout point de contact ou d’envoi de formulaire suivant que vous choisissez de synchroniser à partir d’une campagne ou d’une activité hors ligne.

1. **Points de contact d’attribution des acheteurs** (AT) / Opportunité / Niveau du compte / Recettes

   * Communément utilisé pour les mesures MOFU et BOFU (intermédiaire et/ou bas de l’entonnoir) et la création de rapports liés à _Opportunités_.
   * Les AT représentent les points de contact pertinents de toutes les personnes connectées au **occasion** (via Rôles de contact d’opportunité ou via un identifiant de compte partagé, selon vos paramètres). Contrairement aux BT qui ne concernent que les personnes, les MAT peuvent également être associées à **revenue**. Ainsi, vous utiliserez les BAT pour répondre aux questions relatives aux opportunités, notamment le nombre d’opportunités ouvertes ou fermées, ou la valeur du pipeline et les recettes gagnées.

>[!NOTE]
>
>Les AT sont créées à partir de BT. Essentiellement, le suivi commence au niveau individuel par le biais des BTs. Une fois qu’une opportunité a été créée sur un compte, tous les BAT de contacts du même compte sont référencés et peuvent créer des BAT en rapport avec l’opportunité. Vous souhaiterez donc utiliser l’un ou l’autre selon les questions auxquelles vous essayez de répondre : questions liées aux mesures &quot;Personnes&quot; (rapports BT) ou questions liées aux mesures &quot;Opportunité&quot; (rapports BAT)

Article de prise en charge : [Différence entre les points de contact d’un achat et les points de contact d’attribution d’un achat](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md#configuration-and-setup)

## Point de contact acheteur (BT) {#buyer-touchpoint-bt}

Le point de contact d’achat (BT) est l’objet utilisé pour effectuer le suivi de chaque interaction marketing qu’une personne a avec vos documents marketing. de chaque individu (prospect/contact/[!DNL Marketo Measure] Personne) Le parcours serait représenté par leurs BT associés. Dans [!DNL Marketo Measure], le parcours d’un individu se compose des éléments suivants :

1. Comment cette personne a-t-elle d&#39;abord interagi avec notre marque ? (Première touche ou _FT_)
1. Comment cette personne a-t-elle été convertie / devenue connue / devenue une piste ? (Création de piste ou _LC_)
1. Comment autrement cette personne a-t-elle interagi avec notre marque et notre matériel marketing depuis qu&#39;elle est devenue une &quot;Lead&quot; ? (_PostLC_)

Les points de contact de l’utilisateur sont utilisés pour répondre aux questions relatives aux _personnes_ (Les &quot;personnes&quot; sont représentées par des pistes ou des contacts au sein d’un CRM), telles que les mesures de génération de prospects/contacts ou d’acquisition, plutôt que les mesures liées aux opportunités. Par exemple :

* Quels sont les canaux qui diffusent le plus de pistes ?
* Quels canaux sont plus ou moins coûteux pour créer un nouveau prospect ?
* Avec quel contenu mes Leads/contacts s&#39;impliquent-ils ?
* Quelle est l&#39;histoire marketing de titres, rôles, personnages particuliers ?
* Quels canaux génèrent des MQL ou d’autres statuts de piste/contact ?

En premier lieu, les entreprises doivent savoir, &quot;d&#39;où viennent mes Leads/Contacts ?&quot;. Historiquement, une seule valeur dimensionnelle était utilisée pour y répondre (source de piste, par exemple). Cependant, comme indiqué dans #1 et #2 ci-dessus, nous savons que les Pistes peuvent avoir plusieurs points de contact lors de leur parcours de piste. Le point de contact de l’acheteur nous permet d’obtenir des informations sur les deux interactions les plus cruciales qui représentent la manière dont une piste a été générée : leur Première touche et leur Première touche de création de piste. Les points de contact de l’utilisateur sont également _multidimensionnel_ ce qui signifie qu’ils transportent des quantités de données marketing, principalement d’où provient la personne (canal marketing) et de ce avec quoi elle s’est engagée (contenu).

Le [modèles d’attribution](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) pour obtenir les meilleures informations sur les mesures basées sur les personnes, procédez comme suit :

* **Première touche** - Crédit d’attribution 100 % à la Première touche du prospect (FT)
* **Création de piste** : crédit d’attribution de 100 % à la touche de création de piste (LC) du prospect
* **En forme de U** - approche multi-tactile, avec un crédit de 40 % au FT, un crédit de 40 % au LC

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-1.png"></td> 
   <td>Le modèle de forme de U est conçu pour accorder du crédit à tous les points de contact d’acheteurs qui résument la manière dont une piste est devenue une piste. Bien que les points de contact suivants de ces pistes puissent également être signalés pour comprendre un engagement supplémentaire (Post LC), ils ne font pas partie des <strong>Parcours de création de piste</strong> ils n’obtiennent donc aucun crédit d’attribution dans les modèles en forme de FT, LC ou U.<p>

&#42;Le plus souvent, l’attribution en forme de U reflète une répartition 50/50 paire entre le FT et la LC. Si le prospect est converti au cours de la même session que la Première touche, un seul point de contact représente les positions des points de contact FT et LC. Par conséquent, 100 % de l’attribution serait attribuée à un seul point de contact.</td>
</tr>
 </tbody>
</table>

Ces modèles mettent fortement l’accent sur les interactions à un stade précoce et sur l’engagement dans l’entonnoir. L’attribution En forme de U est le modèle recommandé, car elle prend en compte les points de contact FT et LC, ce qui garantit que le crédit est attribué à tout contact qui a influencé la création du prospect. Toutefois, vous pouvez obtenir des informations supplémentaires à partir des modèles Première touche et Création de piste si vous souhaitez mieux comprendre ces parties spécifiques du parcours de piste.

## Rapports recommandés à l’aide du point de contact de l’utilisateur (BT) {#recommended-reports-using-the-buyer-touchpoint-bt}

1. **PISTES AVEC DES POINTS DE CONTACT D’ACHETEUR**

**1,1 | Nouvelles pistes par canal marketing**

Résumer les données de point de contact de l’acheteur de votre prospect par le champ &quot;Canal marketing&quot; est la vue de niveau supérieur qui représente les canaux/tactiques qui influencent les nouvelles pistes vers la création. La structuration de ce rapport autour d’un &quot;Type de date&quot; = &quot;Date de création&quot; garantit qu’une cohorte de &quot;nouvelles pistes nettes&quot; (lorsque la piste a été créée dans votre CRM) est établie dans le rapport.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels canaux marketing influencent les pistes vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   Mesure : Prospects ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création de piste (CRM) / Date de création (Discover)</td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de pistes, <strong>En forme de U</strong><br>
   *SUMULEZ les champs 'Comptage' dans vos rapports CRM (Comptage - Première touche, Comptage - Création de piste, Comptage - En forme de U)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout type de rapport &quot;Pistes avec points de contact client&quot;, commencez par personnaliser le rapport prédéfini intitulé &quot;[!DNL Marketo Measure] 101 | Pistes par canal&#39;. Ce rapport, qui est prêt à l’emploi, est un environnement de test prédéfini idéal, comme décrit dans le tableau ci-dessus. Il peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques.

**1,2 | Nouvelles pistes par campagne (ou informations plus granulaires)**

Pour obtenir des informations plus détaillées sur les données résumées dans le rapport &quot;Nouvelles pistes par canal marketing&quot; (1.1), ajoutez un résumé supplémentaire au niveau de la campagne. Cela vous permet non seulement de comprendre quels &quot;canaux marketing&quot; sont à l’origine de la création de nouvelles pistes, mais plus précisément, quelles campagnes au sein de ces canaux sont les plus performantes :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>campagnes</i> influencent les pistes vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   Mesure : Prospects ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création de piste (CRM) / Date de création (Discover)</td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Nom de la campagne publicitaire (CRM)</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de pistes, <strong>En forme de U</strong><br>
   *SUMULEZ les champs 'Comptage' dans vos rapports CRM (Comptage - Première touche, Comptage - Création de piste, Comptage - En forme de U)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Obtenez des informations encore plus granulaires en résumant le rapport avec d’autres champs disponibles à partir de l’objet point de contact Acheteur. Pour ce faire, définissez des regroupements (CRM) ou des dimensions supplémentaires (Discover). Selon le canal (qui peut être représentatif de votre rôle), il peut y avoir des détails supplémentaires au-delà du niveau de campagne dans lequel vous souhaitez obtenir des informations. Explorons &quot;Recherche payante&quot;, par exemple dans le tableau ci-dessous...

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>keywords</i> influencent les pistes vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   Mesure : Prospects ([!DNL Marketo Measure] Discover)</td> 
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
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Texte du mot-clé (CRM) / Mot-clé (Discover)</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de pistes, <strong>En forme de U</strong><br>
   *SUMULEZ les champs 'Comptage' dans vos rapports CRM (Comptage - Première touche, Comptage - Création de piste, Comptage - En forme de U)</td> 
  </tr>
 </tbody>
</table>

Le niveau de granularité peut varier en fonction du canal. L&#39;approche recommandée serait de vous demander : &quot;Et le &quot;canal X&quot; que vais-je chercher à comprendre plus en détail ?&quot; Les gestionnaires de recherche payante peuvent également être intéressés par d’autres dimensions, telles que :

* Nom de la campagne publicitaire
* Contenu publicitaire
* Groupe publicitaire

Les gestionnaires d’événements peuvent toutefois être plus intéressés par les événements spécifiques ou les types d’événements qui ont influencé le plus de pistes dans la création :

* Nom de la campagne publicitaire / Campagne Salesforce = événement spécifique
* Medium = Campaign &#39;Type&#39;

**RAPPEL**: Il se peut que des filtres supplémentaires doivent être ajoutés à l’une des variations de rapport décrites ci-dessus ou ci-dessous. Ces filtres seraient spécifiques à votre organisation et seraient utiles aux équipes des opérations marketing ou des opérations commerciales. Il n’est pas rare qu’une organisation exécute les mêmes filtres sur tous les rapports pour s’assurer que le rapport est aussi propre et précis que possible. Voici quelques exemples courants :

* Filtrage des enregistrements internes des tests, généralement par adresse email
* Filtrage basé sur certains &quot;types d’enregistrement&quot; qui peuvent être spécifiques à votre unité opérationnelle

**1,3 | Nouvelles pistes par contenu (rapports CRM uniquement)**

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>content</i> influencent les pistes vers la création ?</td> 
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
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Page d’entrée<br> 
   URL du formulaire</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de pistes, <strong>En forme de U</strong><br></td> 
  </tr>
 </tbody>
</table>

**RAPPEL**: Les deux champs Principaux pour la création de rapports sur le contenu/les ressources numériques sont &#39;Landing Page&#39; et &#39;Form URL&#39;. Ces deux valeurs peuvent être identiques si le prospect convertit (envoie un formulaire) sur la même page que celle sur laquelle il a accédé (Landing Page), _Cependant_, ces valeurs sont parfois différentes. Par exemple, le prospect peut cliquer sur un lien de Facebook qui l’amène à une page de votre site web (il s’agit de la valeur &quot;Page d’entrée&quot;). Il peut ensuite quitter cette page, poursuivre sa session sur le site et envoyer un formulaire sur une autre page (URL du formulaire). Cela serait résumé dans un seul point de contact qui représente l’origine du prospect (canal marketing), le contenu qui les a amenés sur le site (page d’entrée) et le contenu qu’ils ont fini par télécharger (URL du formulaire). &quot;URL du formulaire&quot; est également le champ d’orientation permettant de créer des rapports sur d’autres formulaires non associés à du contenu téléchargeable, tels que les formulaires &quot;Nous contacter&quot; ou &quot;Demo Request&quot;.

>[!TIP]
>
>Obtenir des informations sur un &quot;contenu&quot; spécifique avec des filtres supplémentaires
>
>* Filtrez par : &#39;Landing Page&#39; CONTIENT (par exemple :
   >   * /blog
   >   * /ebook
   >   * /webinaire
>
>* OU : &quot;URL du formulaire&quot; CONTIENT (par exemple :
   >   * /contact
   >   * /demo


Les rapports basés sur le &quot;contenu&quot; offrent une grande valeur lors de la création de rapports sur n’importe quelle partie de l’entonnoir. Toutefois, ils sont le plus souvent utilisés en haut de l’entonnoir pour fournir des informations supplémentaires sur un engagement initial de Leads. Dans la mesure où la &quot;recherche organique&quot; tend à être le canal le plus puissant pour générer l’engagement initial (FT), il n’y a pas autant de données au niveau de &quot;campagne&quot;.

Les rapports basés sur le &quot;contenu&quot; sont très utiles pour mieux comprendre ce qui motive les pistes plus spécifiquement dans le canal marketing de niveau supérieur, dans ce cas &quot;Recherche organique&quot;.

**1,4 | Total de l’engagement au prospect sur une période donnée**

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Les canaux marketing qui ont eu le plus de <i>engagement total en prospect</i> dans le passé (semaine/mois/trimestre) ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br> 
   Mesure : Prospects ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date du Touchpoint</td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing (ou plus granulaire)</td> 
  </tr>
  <tr>
   <td>Modèles optimaux*</td> 
   <td>*Ce rapport se concentre moins sur la mesure d’où proviennent les pistes avec un modèle d’attribution que sur la mesure <i>nombre total de points de contact (montant de l’engagement)</i>, y compris ceux qui suivent la touche de création de piste. Le nombre total d’enregistrements des points de contact refléterait les canaux ayant enregistré le plus d’engagements de piste.</td> 
  </tr>
 </tbody>
</table>

**RAPPEL**: Baser vos rapports sur la &quot;Date du point de contact&quot; est la manière la plus réfléchie de comprendre les performances marketing au cours d’une période donnée. La &quot;Date du point de contact&quot; structure le rapport d’une manière où l’attribution n’est pas seulement liée au canal, à la campagne ou au contenu, mais également au moment où le point de contact s’est produit. Il s’agit de la manière la plus efficace de comprendre ce qui se passait à un certain moment de l’engagement marketing. Il s’agit également de la manière recommandée de mesurer l’impact du marketing par rapport aux dépenses marketing investies au même moment. Il est recommandé d’effectuer toute analyse de dépenses marketing ou de retour sur investissement (voir 5.1).

**2. PISTES QUALIFIÉES MARKETING AVEC POINTS DE CONTACT D’ACHETEUR**

L’un des rapports les plus courants ne concerne pas seulement les nouveaux engagements au niveau des pistes ou des pistes, mais plus particulièrement les &quot;pistes qualifiées en marketing&quot; (MQL). Il existe deux approches différentes en ce qui concerne la création de rapports sur les MQL en fonction de [!DNL Marketo Measure] fonctionnalités auxquelles vous avez accès.

**2,1 | Pistes marketing qualifiées par canal (multi-touch)**

Cette approche permettant de mesurer l’impact du marketing sur l’influence des MQL est essentiellement une suite du rapport &quot;Nouvelles pistes par canal marketing&quot; (1.1), mais avec les critères supplémentaires que les pistes mesurées sont plus spécifiquement des MQL. Le modèle d’attribution En forme de U est toujours recommandé ici pour identifier les canaux marketing et le contenu qui génèrent des pistes qui sont ensuite _probable_ pour devenir un MQL :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Les canaux marketing qui génèrent le mieux de nouvelles pistes qui deviennent <i>MQL</i>?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br> 
   Mesure : Prospects ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>MQL = true*<br>
   *<i>Les MQL peuvent être définis différemment selon l’organisation. Assurez-vous que la variable [!DNL Marketo Measure] Le rapport est filtré pour les MQL à l’aide du ou des mêmes champs que les autres rapports basés sur MQL. Un filtre Segment doit être créé de la même manière pour la création de rapports sur les MQL dans [!DNL Marketo Measure] Découvrez-le.</i></td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date MQL (ou équivalente) / Date de création ([!DNL Marketo Measure] Discover)<br> <i>La date de création de piste peut également être utilisée dans les rapports CRM si la "date MQL" n’est pas une option dans votre CRM. Il est important de garder à l’esprit le champ de date que vous utilisez pour définir le jeu de données des cohortes.</i></td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Première touche, création de pistes, <strong>En forme de U</strong><br> 
   SOMMEZ les champs "Comptage" dans vos rapports CRM (Comptage - Première touche, Comptage - Création de piste, Comptage - En forme de U).</td> 
  </tr>
 </tbody>
</table>

**2,2 | Pistes marketing qualifiées par canal (touche unique, CRM uniquement)**

Cette approche permettant de mesurer l’impact du marketing sur l’influence des MQL est plus axée sur l’identification des MQL _point de contact unique_ était la dernière touche avant que le prospect n’atteigne MQL.

>[!NOTE]
>
>Pour exécuter ce rapport, une valeur &quot;État de piste&quot; de &quot;MQL&quot; est requise pour définir l’étape MQL à des fins de suivi (Évaluation de l’entonnoir). Si les MQL ne sont pas suivis via le champ &quot;État de la piste&quot;, la fonction Modèle d’attribution personnalisée avec étapes personnalisées est nécessaire pour créer une étape &quot;MQL&quot; personnalisée dans la variable [!DNL Marketo Measure] Paramètres du compte.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quels canaux marketing sont les plus efficaces pour pousser les Leads à atteindre l’état MQL ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact des prospects et des acheteurs (CRM)<br>
   <i>ce rapport n'est possible que dans les rapports CRM. Il n’est pas possible de filtrer certaines valeurs "Position du point de contact" dans [!DNL Marketo Measure] Discover</i></td> 
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
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td><i>Ce rapport étant filtré sur un seul point de contact, les modèles d’attribution au niveau de l’piste ne sont pas aussi pertinents. Tout comme le "rapport Engagement de piste" (1.4), le nombre d’enregistrements de point de contact sera utilisé ici pour déterminer les canaux les plus puissants (chaque piste n’aura qu’un seul point de contact MQL).</i></td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Explorer d’autres regroupements ou dimensions pour mieux comprendre les MQL. Comme mentionné dans les autres rapports &quot;Points de contact Pistes avec acheteurs&quot;, le point de contact Acheteur offre une granularité beaucoup plus grande que le canal marketing. Un rapport basé sur le &quot;contenu&quot; peut également être combiné avec l’un des rapports MQL ci-dessus pour mieux comprendre quel contenu influe le mieux sur les MQL.

**3. [!DNL MARKETO MEASURE] PERSONNES AYANT DES POINTS DE CONTACT D’ACHETEUR**

Il existe une troisième [!DNL Marketo Measure] dans Salesforce qui peut s’avérer très utile lors de la création de rapports sur les mesures liées aux personnes : **la valeur [!DNL Marketo Measure] Personne (BP)**. BP résout le vieux problème de la façon de représenter les informations des Leads et des Contacts dans le même rapport. Il regroupe tous les BT liés à une &quot;personne&quot; (une [!DNL Marketo Measure] L&#39;ID de personne est son adresse électronique). Qu&#39;il s&#39;agisse d&#39;un prospect ou d&#39;un contact, BP fait office d&#39;objet de passerelle, pour aider les rapports à s&#39;étendre sur les canaux &quot;Lead&quot; et &quot;contact&quot;, et se révèle particulièrement utile dans la production de rapports plus élaborés sur les personnes.

Le [!DNL Marketo Measure] La personne ne concerne qu’un seul objet de point de contact, le point de contact de l’acheteur (BT). Cela signifie qu’il ne peut pas être utilisé pour des mesures liées aux opportunités ou aux recettes. Un &#39;[!DNL Marketo Measure] Le type de rapport Points de contact personnes-acheteurs est idéal pour comprendre _engagement total_ car il fait surface à tous les BT, que ce dernier se rapporte plus spécifiquement à un prospect ou à un contact. Par exemple, si une campagne Salesforce est utilisée pour suivre un événement, il se peut que des membres de campagne de la campagne CRM existent sous la forme de Pistes OU de Contacts. [!DNL Marketo Measure] crée des points de contact pour les membres de la campagne, mais sans le [!DNL Marketo Measure] Les rapports de personne standard de Salesforce nécessitent deux rapports distincts pour comprendre combien de personnes _total_ points de contact de l’événement : un qui est &quot;Points de contact avec l’acheteur&quot; et un qui est &quot;Contacts avec les points de contact de l’acheteur&quot;. Quelques autres [!DNL Marketo Measure] Les cas d’utilisation des rapports basés sur les personnes sont répertoriés ci-dessous :

**3,1 [!DNL Marketo Measure] Personnes ayant téléchargé des &quot;livres électroniques&quot; ou des &quot;livres blancs&quot; (nombre total de téléchargements)**

Ce rapport serait identique à un rapport basé sur le &quot;contenu&quot; au niveau de l’piste. Cependant, plutôt que de chercher à mesurer le nombre de pistes pouvant être attribuées à chaque élément de contenu, utilisez une [!DNL Marketo Measure] Le rapport Personnes sera utile pour comprendre le total _nombre de téléchargements_ si la ressource est sécurisée (le nombre total de points de contact représente le nombre total de téléchargements/envois de formulaire).

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
   <td>"URL du formulaire" CONTIENT (par exemple :<br>
   <li>/ebook</li>
   <li>/whitepaper</li>
   <i>Les valeurs de filtre ci-dessus ne sont que des exemples. La valeur réelle sera basée sur la structure d’URL de chaque organisation.</i></td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date du point de contact <i>(quand la ressource a-t-elle été téléchargée)</i></td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>URL du formulaire</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Il s’agit moins de mesurer d’où viennent les Leads ou les contacts avec un modèle d’attribution que d’en savoir plus sur les <i>nombre total de points de contact (montant de l’engagement)</i>, y compris ceux qui suivent la touche de création de piste. Avec ce rapport, nous cherchons à comprendre la variable <i>montant total de l’engagement</i>. Le nombre total d’enregistrements des points de contact reflète les ressources qui ont été les plus téléchargées.</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Pour tout &quot;Piste avec [!DNL Marketo Measure] Type de rapport Personnes, commencez par personnaliser le rapport prédéfini intitulé &quot;&quot;**[!DNL Marketo Measure]101 | Pistes/contacts par canal**&#39;. Ce rapport est prêt à l’emploi et constitue un excellent [!DNL Marketo Measure] Environnement de test basé sur les personnes. Il est prédéfini et peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques.

>[!TIP]
>
>Vous pouvez utiliser ce rapport pour mieux comprendre l’engagement total d’une dimension marketing à partir de l’objet point de contact Acheteur, et pas seulement les téléchargements de contenu comme présenté dans l’exemple. Le rapport peut plutôt être groupé ou filtré selon des dimensions telles que &quot;Canal marketing&quot; ou &quot;Nom de la campagne publicitaire&quot; afin de mieux comprendre l’engagement total des Leads et des contacts dans votre base de données. Il vous suffit de modifier les filtres ou les regroupements du rapport en les remplaçant par zéro dans d’autres dimensions représentées par d’autres champs à partir de l’objet de point de contact.

**3,2 [!DNL Marketo Measure] Personnes qui se sont enregistrées pour un événement (CRM uniquement)**

_Ce rapport ne s’applique que si des formulaires d’enregistrement sont hébergés sur votre ou vos sites web qui [!DNL Marketo Measure] peut effectuer un suivi numérique._

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
   <td>"URL du formulaire" CONTIENT (par exemple :<br>
   <li>/événement</li>
   <i>La valeur de filtre ci-dessus ne sont que des exemples. La valeur réelle sera basée sur la structure d’URL de chaque organisation.</i></td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date du point de contact <i>(lors de l’envoi du formulaire d’enregistrement)</i></td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
   <td><i>sélectionner la période souhaitée ;</i></td> 
  </tr>
  <tr>
   <td>Groupe/Dimension</td> 
   <td>URL du formulaire<br>
   Canal marketing</td> 
  </tr>
  <tr>
   <td>Modèles optimaux</td> 
   <td>Il s’agit moins de mesurer d’où viennent les Leads ou les contacts avec un modèle d’attribution que d’en savoir plus sur les <i>nombre total de points de contact (nombre d’inscriptions)</i>, y compris ceux qui suivent la touche de création de piste. Avec ce rapport, nous recherchons des informations sur les causes des inscriptions aux événements. Le nombre total d’enregistrements des points de contact par "Canal marketing" refléterait les canaux qui ont généré le plus d’inscriptions.</td> 
  </tr>
 </tbody>
</table>

L’élément essentiel de ce rapport est que les données du point de contact de l’acheteur fourniront également des données sur le canal marketing. Bien que vous ayez déjà des informations sur le nombre de personnes qui se sont enregistrées pour vos événements, ce rapport vous donnera également des informations sur les canaux marketing numériques, les sources et/ou les campagnes qui amènent des personnes à votre site web pour s’inscrire à l’événement.

>[!TIP]
>
>Cette même approche peut être utilisée pour mieux comprendre les inscriptions aux webinaires ou peut-être les téléchargements de webinaires à la demande (s’il s’agit d’une ressource fermée). La seule différence serait la valeur de filtre dans &quot;URL du formulaire&quot; si ces formulaires sont hébergés sur des pages uniques de votre site web. L&#39;objectif est le même, cependant. Il répond aux questions &quot;lequel de mes canaux marketing génère le plus d’inscriptions/téléchargements de webinaires à la demande.

**3,3 [!DNL Marketo Measure] Personnes avec des points de contact d’achat (validation des points de contact)**

En prenant en compte la variable [!DNL Marketo Measure] Personne nous permet de créer des rapports sur tous les points de contact d’un seul rapport. Il s’agit du type de rapport idéal à utiliser pour valider vos données. Nous voulons nous assurer que nous n’ignorons aucun point de contact pouvant indiquer où, par exemple, il existe un problème dans la configuration de vos &quot;canaux marketing&quot; (voir les articles de prise en charge liés ci-dessous pour plus d’informations sur la configuration de vos &quot;canaux marketing&quot;).

* [Configuration de canal personnalisé en ligne](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
* [Configuration de canal personnalisé hors ligne](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)

Essentiellement, les données du point de contact reflètent ce qui a été suivi par [!DNL Marketo Measure] et peuvent être contrôlés pour s’assurer que votre configuration corresponde aux entrées en fonction d’éléments tels que : Valeurs de paramètre UTM, pages de référence ou types de campagne. Si les données du point de contact ne correspondent pas à votre configuration, il est probable qu’une modification soit nécessaire. Au-delà de la configuration du &quot;canal marketing&quot;, vous pouvez consulter les données du point de contact pour déterminer les points de contact qui peuvent avoir besoin d’être [supprimé](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) ou [segmenté](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md). Il est recommandé de contrôler vos données de point de contact dans un[!DNL Marketo Measure] Rapport Points de contact personnes-acheteurs à la fin de chaque mois ou trimestre, si possible. Votre attribution sera ainsi aussi précise que possible. Le &quot;[!DNL Marketo Measure] 101 | Le rapport Leads/Contacts par canal, disponible d&#39;usine, est un bon point de départ. Insérez les champs suivants s’ils ne sont pas déjà inclus afin de passer en revue certains des éléments de configuration les plus essentiels :

* **Canal marketing** - Chemin = Canal marketing.Subchannel (valeurs définies dans [!DNL Marketo Measure])
* **Source du point de contact** = utm_source
* **Volume moyen** = utm_medium (points de contact en ligne) OU Type de campagne CRM (points de contact hors ligne)
* **Page du référent** (utilisation de la configuration &quot;Canaux en ligne&quot;)
* **Page d’entrée - Raw** (utilisation de la configuration &quot;Canaux en ligne&quot;) est également une entrée courante pour la suppression du point de contact dans l’onglet &quot;Paramètres du point de contact&quot; de vos paramètres.)
* **URL du formulaire** (entrée courante pour la suppression du point de contact dans l’onglet &quot;Paramètres du point de contact&quot; de vos paramètres)

**POINT DE CONTACT D’ATTRIBUTION DE L’ACHETEUR (BAT)**

Les points de contact d’attribution de l’acheteur (BAT) représentent les points de contact pertinents de tous les contacts connectés à l’opportunité (soit via les rôles de contact de l’opportunité, soit via un identifiant de compte partagé, selon vos paramètres). Contrairement aux BT (qui sont principalement liés aux personnes), les MAT peuvent être associées aux revenus. Ainsi, vous utiliserez les AT pour répondre à des questions liées aux opportunités, principalement ouvertes. _Opportunités/Recettes de pipeline_ et fermé gagné _Opportunités/Offres/Recettes_. Un MAT est créé par le biais des enregistrements BT d’un contact dès qu’une opportunité est créée sous le même compte que le contact (le MTA n’est pas converti en MTA). Les données de BT sont simplement référencées pour créer un enregistrement supplémentaire - le MTA qui se rapporte ensuite à l’opportunité).

Le point de contact d’attribution des acheteurs nous permet de mesurer l’impact du marketing de manière plus approfondie dans l’entonnoir. _La profondeur de l’entonnoir à laquelle vous souhaitez mesurer peut être représentée par les différents modèles d’attribution multi-touch._.

Compte tenu de la relation Principale entre les MAT et l’opportunité, elles sont utilisées pour répondre à des questions telles que :

* Quels sont mes efforts marketing qui ont influencé les opportunités les plus importantes ?
* Combien de nouvelles recettes de pipeline puis-je attribuer à chacun de mes canaux marketing ?
* Laquelle de mes campagnes a connu le meilleur retour sur investissement le trimestre dernier ?

Le [modèles d’attribution](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) Voici les meilleures informations sur les mesures basées sur les opportunités :

**En forme de W** - Le &quot;_Modèle de pipeline_&#39;. Trois points de contact de jalon sont inclus dans le modèle en forme de W. les points de contact FT, LC et OC se voient attribuer chacun 30 % du crédit d’attribution. Les 10 % restants sont attribués de manière égale à tous les points de contact intermédiaires qui se produisent entre les trois points de contact de jalon.

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

**Chemin complet** - Le &quot;_Modèle Won fermé_&#39;. Ce modèle comprend les quatre points de contact de jalon : FT, LC, OC et Fermé. Chacun reçoit 22,5 % du crédit Opportunity, et les 10 % restants sont répartis à parts égales entre les touches intermédiaires.

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

En général, les marketeurs doivent savoir d’où viennent mes opportunités. Tout comme pour les rapports au niveau des pistes, une seule valeur unidimensionnelle a été ajoutée à cette question lors de l’historique (source de campagne Principal, par exemple). Cependant, nous savons que le développement d’une opportunité est bien plus important qu’un seul point de contact d’un seul contact. Il existe généralement plusieurs points de contact de différents canaux et de plusieurs parties prenantes qui influencent une opportunité dans la création. Avec [!DNL Marketo Measure], nous pouvons faire apparaître tous les points de contact d’un compte pour mieux comprendre d’où provient une opportunité. Au-delà de cela, cependant, nous pouvons continuer à faire apparaître tout point de contact qui s’est produit après la création de l’opportunité et jusqu’au point où l’opportunité est fermée. Cela nous permet non seulement d’adopter une approche multi-touch pour comprendre d’où provient une opportunité, mais aussi ce qui l’a influencée pour fermer et finalement représenter des recettes gagnées fermées. Cela vous permet d’avoir un aperçu de différentes questions, telles que &quot;Quel est l’impact du marketing sur l’activation de la fermeture des transactions ?&quot;, &quot;Quel est le moteur de la fermeture des recettes par gagnant ?&quot;. et finalement, &quot;lequel de mes efforts de marketing affiche le meilleur retour sur investissement ?&quot;

## RAPPORTS RECOMMANDÉS À L’AIDE DU POINT DE CONTACT DE L’ATTRIBUTION DE L’ACHETEUR (TBAT) {#recommended-reports-using-the-buyer-attribution-touchpoint}

**4.1 | Nouvelles opportunités par canal marketing**

Résumer les données de point de contact d’attribution de vos opportunités par le champ &quot;Canal marketing&quot; est la vue de niveau supérieur qui représente les canaux/tactiques qui influencent les nouvelles opportunités dans la création. En structurant ce rapport autour d’un &quot;Type de date&quot; = &quot;Date de création de l’opportunité&quot;, vous vous assurez que nous résumerons également le rapport en fonction du moment où l’opportunité a été réellement créée dans votre CRM. Les points de contact peuvent provenir d’un certain temps auparavant, mais ils se rapportent toujours aux opportunités qui ont été créées au cours de la période définie et reçoivent ainsi du crédit d’attribution, car ils sont reconnus comme ayant influé sur l’opportunité.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>canaux marketing</i> influencent-elles les opportunités vers la création ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact d’attribution des acheteurs avec opportunités (CRM)<br> 
   Mesure : Opportunités ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>
   <li>Étape de l’opportunité* <i>(facultatif selon les opportunités spécifiques que vous souhaitez limiter au rapport. Vous pouvez uniquement souhaiter créer des rapports sur les MAT qui sont toujours associées uniquement aux opportunités "ouvertes" (par exemple).</i></li>
   <li>Type d’opportunité (il est courant de filtrer en fonction de certaines opportunités, par exemple : "Nouvelle entreprise" par opposition à <i>all</i> Opportunités)</li><br>
   *Un filtre de segment pour "Type d’opportunité" doit être utilisé dans [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création de l'opportunité (CRM) / Date de création (Discover)</td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
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
>Pour tout type de rapport &quot;Points de contact d’attribution des acheteurs avec opportunités&quot;, commencez par personnaliser le rapport prédéfini intitulé &quot;&quot;.[!DNL Marketo Measure] 101 | Opportunités par canal&#39;. Ce rapport, qui est prêt à l’emploi, est un environnement de test prédéfini idéal, comme décrit dans le tableau ci-dessus. Il peut être rapidement personnalisé pour des besoins de création de rapports plus spécifiques (le rapport utilise un modèle Chemin complet prêt à l’emploi. Veillez donc à personnaliser le rapport afin d’inclure tout autre modèle d’attribution, le modèle En forme de W, dans ce cas).

>[!TIP]
>
>Le rapport présenté ci-dessus serait également utilisé pour déterminer la quantité de devise à attribuer. Lors de la création de rapports au niveau des opportunités à l’aide des MTA, deux mesures clés sont résumées : devise (le montant de l’opportunité) et l’enregistrement d’opportunité lui-même. Dans l’exemple ci-dessus, nous mesurons plus spécifiquement les opportunités ouvertes et les nouvelles recettes de pipeline.

>[!TIP]
>
>Obtenez des informations encore plus granulaires en résumant le rapport avec d’autres champs disponibles à partir de l’objet Point de contact d’attribution des acheteurs. Cette opération s’effectue de la même manière qu’au niveau de l’piste avec les points de contact d’achat (1.2). Pour ce faire, ajoutez des regroupements (CRM) ou des dimensions supplémentaires (Discover). Selon le canal (qui peut être représentatif de votre rôle), il peut y avoir des détails supplémentaires au-delà du niveau de campagne dans lequel vous souhaitez obtenir plus d’informations. Explorons la section &quot;Recherche payante&quot; ci-dessous :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Quel <i>keywords</i> de mes annonces de recherche payante génèrent le plus de recettes de pipeline ?
</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact d’attribution des acheteurs avec opportunités (CRM)<br> 
   Mesure : Opportunités ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>
   <li>Canal marketing = Recherche payante</li>
   <li>Étape de l’opportunité* <i>(facultatif selon les opportunités spécifiques que vous souhaitez limiter au rapport. Cet exemple est basé sur les recettes du pipeline, qui sont définies dans [!DNL Marketo Measure] par "Ouverture" Opportunités représentant les recettes potentielles/pipeline ouvert)</i></li>
   <li>Type d’opportunité (il est courant de filtrer en fonction de certaines opportunités, par exemple : "Nouvelle entreprise" par opposition à <i>all</i> Opportunités)</li><br>
   *Un filtre de segment pour "Type d’opportunité" doit être utilisé dans [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de création d'opportunité</td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
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

Ce rapport serait essentiellement le même que le premier exemple de point de contact d’attribution de l’achat (4.1), sauf que la mesure est désormais passée d’opportunités ouvertes à Offres gagnées clôturées. La mesure doit toujours être celle qui informe le modèle d’attribution à utiliser. Dans la mesure où nous étudions maintenant les affaires conclues et les MAT connexes, nous devrions utiliser un modèle qui représente l&#39;ensemble du parcours de l&#39;acheteur (Deal). Cela garantit que tout suivi de contact marketing pendant le parcours de l’acheteur reçoit un crédit d’attribution :

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>canaux marketing</i> influencent-elles la conclusion des accords ?</td> 
  </tr>
  <tr>
   <td>Type de rapport</td> 
   <td>Points de contact d’attribution des acheteurs avec opportunités (CRM)<br> 
   Mesure : Transactions ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtres</td> 
   <td>
   <li>Étape d’opportunité (<i>Seules les opportunités de gains fermées doivent être incluses dans le rapport.</i>) OU,</li>
   <li>Opportunité gagnée = Vrai</li>
   <li>Type d’opportunité (il est courant de filtrer en fonction de certaines opportunités, par exemple : "Nouvelle entreprise" par opposition à toutes les opportunités)<br>
   </td> 
  </tr>
  <tr>
   <td>Champ de date/Type de date</td> 
   <td>Date de fermeture de l'opportunité</td> 
  </tr>
  <tr>
   <td>Plage de dates</td> 
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

**RAPPEL**: Il est essentiel de ne pas oublier de filtrer les opportunités spécifiques que vous souhaitez inclure dans les rapports basés sur les AT, en particulier lorsqu’il s’agit d’&quot;opportunités ouvertes et revenus du pipeline&quot; ou &#39;Deals and Closed Won Revenue&#39;. Cela est généralement effectué par le biais d’un filtre &quot;Étape de l’opportunité&quot; (le filtre &quot;Gagnant de l’opportunité&quot; = vrai/faux peut également s’avérer très utile ici).

**5. ROI ([!DNL Marketo Measure] Discover uniquement)**

Le [!DNL Marketo Measure] Les tableaux de bord de Discover offrent une vue de haut niveau de vos performances marketing à l’aide de [!DNL Marketo Measure] données d’attribution. Ces tableaux de bord agrégés fournissent des données de retour sur investissement et de dépenses marketing clés qui ne sont pas disponibles dans les rapports CRM. Cet environnement prédéfini vous permet d’afficher vos performances marketing en phase avec vos données de retour sur investissement, ce qui vous permet de prendre des décisions pratiques relatives à votre marketing.

>[!TIP]
>
>Lorsque vous avez une question relative au retour sur investissement, aux dépenses ou aux coûts, [!DNL Marketo Measure] Discover sera le meilleur endroit pour la création de rapports.

Le [!DNL Marketo Measure] Les tableaux de bord de Discover comprennent les données Point de contact de l’achat et Points de contact de l’attribution de l’achat, ainsi que les données CRM clés. Principale différence entre le reporting CRM et le reporting dans [!DNL Marketo Measure] Discover indique que les données de point de contact sont présentées de manière &quot;agrégée&quot; et résumées par dimension (canal marketing, campagne, etc.). par opposition aux enregistrements de points de contact individuels qui peuvent ensuite être résumés. [!DNL Marketo Measure] Discover permet de déterminer à un niveau élevé quel type d’effort a le plus d’impact sur les pistes, les ouvertures, les affaires et le montant des recettes à leur attribuer. Une fois que les recettes attribuées sont calculées à l’aide des différents modèles d’attribution (le chemin complet est recommandé pour l’attribution des recettes/réservations gagnées fermées), nous pouvons les mesurer par rapport au montant dépensé dans la même dimension (canal marketing, sous-canal ou campagne). Cela nous donne ensuite la variable **ROI**.

>[!TIP]
>
>Lors de la création de rapports dans Discover, l’une des choses les plus importantes à retenir est le type de données que vous utilisez pour filtrer. Le type de date détermine le jeu de données. [!DNL Marketo Measure] utilise dans les différentes mosaïques.

* **Date du point de contact**: Affiche les données associées dont la &quot;date du point de contact&quot; était définie dans la période spécifiée.
* **Date de création**: Affiche les données associées dont la &quot;date de création&quot; était définie dans la période spécifiée.
* **Date de fermeture**: Affiche les données associées dont la &quot;date de fermeture&quot; était définie dans la période spécifiée.

Lors de la création de rapports sur le ROI dans [!DNL Marketo Measure] Discover, il est recommandé d’utiliser un &quot;Type de date&quot; = &quot;Date du point de contact&quot;. Afin de déterminer le rendement de chaque dollar investi, nous devons nous assurer que les recettes sont réattribuées à la date à laquelle l’investissement a été effectué. &quot;Type de date&quot; = &quot;Date du point de contact&quot; permet de s’assurer que les rapports sont structurés de cette manière, contrairement à la date de création (Date de création) ou de fermeture (Date de fermeture) de l’opportunité. Regardons de plus près :

Les filtres mis en évidence ci-dessous sont essentiels pour un rapport axé sur le retour sur investissement dans [!DNL Marketo Measure] (il est probable que vous définissiez ces filtres dans les panoramas &quot;Aperçu&quot;, &quot;CMO&quot; ou &quot;ROI&quot;) :

**5.1 | ROI dans le panorama &quot;Aperçu&quot;**

![](assets/bizible-reporting-guide-4.png)

La plage &quot;Date&quot; définit non seulement la cohorte de points de contact (par date de point de contact) qui reçoivent l’attribution, mais elle définit également la plage que la mosaïque &quot;Dépense&quot; ou les colonnes représentent.
[!DNL Marketo Measure] Il suffit de regarder la plage &quot;Date&quot; pour déterminer le montant total dépensé, ou aux niveaux Canal marketing, Sous-canal ou Campagne. Voir ci-dessous :

![](assets/bizible-reporting-guide-5.png)

La capture d’écran ci-dessus montre les données des dépenses marketing des 3 derniers mois. Dans cet exemple, 12 970 $ ont été dépensés sur tous les canaux. Ce nombre comprend les données de dépenses marketing. [!DNL Marketo Measure] est issu d’intégrations à l’un de vos comptes de publicités connectés (Google AdWords, Bing Ads, Facebook Ads, LinkedIn, DoubleClick) et à toute dépense marketing supplémentaire qui a été chargée dans votre compte ou qui est automatiquement extraite d’un enregistrement Campaign dans votre CRM. L’exemple indique également combien de &quot;Recettes&quot; gagnées peuvent également être attribuées aux points de contact qui se sont produits au cours de la même période (zones vertes). Voici comment le ROI est calculé : les recettes attribuées aux points de contact provenant de l’investissement dans la même période :

![](assets/bizible-reporting-guide-6.png)

**RAPPEL**: [!DNL Marketo Measure] définit &quot;Recettes&quot; comme recettes ou réservations gagnées fermées et définit &quot;Recettes du pipeline&quot; comme _des recettes ouvertes/potentielles provenant d’opportunités ouvertes_.

Un autre élément important du rapport sur le retour sur investissement ci-dessus est le &quot;Chiffre d’affaires du pipeline&quot; représenté dans la zone rouge. Cela signifie que, sur les 12 970 USD investis au cours des 3 derniers mois, nous attribuons actuellement 705 199 $ de &quot;Recettes&quot; en won, mais nous attribuons également 6 905 532 $ de recettes potentielles ouvertes (recettes de pipeline) aux points de contact créés à partir du même investissement ! Ce que nous nous attendrions à voir, c’est une partie des &quot;recettes du pipeline&quot; qui se ferme au fil du temps, en alimentant le nombre de &quot;recettes&quot;, et par conséquent, le nombre de retour sur investissement augmenterait au fil du temps. Le nombre de &quot;Dépense&quot; est fixe car nous ne pouvons pas revenir dans le temps pour dépenser plus dans les 3 derniers mois complets. Il est important d’utiliser un &quot;type de date&quot; de &quot;date du point de contact&quot; dans tout rapport de retour sur investissement : Il définit le montant (**I**) imbriqué et assure la quantité de (**R**)les recettes attribuées sont réattribuées aux mêmes points de contact que ceux provenant de l’investissement (pour chaque dollar dépensé, combien a été effectué ?).

>[!TIP]
>
>Filtrez-les sur les canaux marketing, sous-canaux et/ou campagnes dans lesquels vous savez que les données des dépenses marketing sont complètes et précises. L’exemple ci-dessus concerne tous les canaux marketing, mais si les données relatives aux dépenses marketing ne sont pas chargées pour certains canaux, la création de rapports sur le retour sur investissement peut s’avérer inexacte. Consultez l’exemple ci-dessous, cette fois dans le panorama &quot;ROI&quot; axé sur les campagnes dans le canal marketing de &quot;recherche payante&quot;, un canal avec des données de dépenses marketing très granulaires via les intégrations.

![](assets/bizible-reporting-guide-7.png)
