---
description: Présentation des rapports [!DNL Marketo Measure] 101 - [!DNL Marketo Measure]
title: Vue d’ensemble basique des rapports [!DNL Marketo Measure]
exl-id: 83977b81-8055-47fd-8a6b-5ef32d280269
feature: Reporting
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 4%

---

# Vue d’ensemble basique des rapports [!DNL Marketo Measure] {#marketo-measure-101-reports-overview}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Tous les clients [!DNL Marketo Measure] utilisant [!DNL Marketo Measure] et [!DNL Salesforce] ont accès au dossier « Rapports des points de contact des acheteurs » dans leur instance SFDC. Ce dossier contient un certain nombre de rapports préconfigurés qui peuvent vous aider à commencer à créer des rapports avec les données Buyer Touchpoint.

![](assets/bizible-101-reports-overview-1.png)

Bien que bon nombre de ces rapports aient déjà des objectifs précis en matière de rapports, il y a six « _[!DNL Marketo Measure]101..._ », représentés par trois types de rapports clés qui couvrent la majorité des besoins en matière de rapports.

* Leads avec points de contact de l’acheteur
* [!DNL Marketo Measure] des personnes avec des points de contact d&#39;acheteur
* Points de contact d’attribution de l’acheteur avec des opportunités

![](assets/bizible-101-reports-overview-2.png)

Ces rapports fournissent les champs et l’infrastructure de base nécessaires à tout rapport lié au [!DNL Marketo Measure] que vous souhaitez créer. Nous encourageons tous les clients, nouveaux et anciens, à commencer par ces rapports lorsqu’ils explorent les questions d’attribution marketing. Vous trouverez ci-dessous une explication de chacun des six rapports « _[!DNL Marketo Measure]101..._ ».

_Si vous ne trouvez pas le dossier Rapport des points de contact de l&#39;acheteur ou les six rapports «_[!DNL Marketo Measure] 101..._» dans ce dossier, contactez l&#39;assistance technique pour obtenir de l&#39;aide._

**Prospects avec points de contact acheteur** | Les deux variations suivantes signalent les leads et leurs points de contact d’acheteur. Bien qu’ils utilisent le même type de rapport de base, ils sont regroupés par mesures différentes, ID de lead par rapport au canal marketing, afin de fournir deux vues principales des données. Ce type de rapport est conçu pour s’ajouter aux rapports funnel. Il est idéal lorsque vous souhaitez découvrir comment vos prospects interagissent avec vos efforts marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les informations suivantes :

**[!DNL Marketo Measure]101 : Leads par canal** | Une vue d’ensemble de la manière dont vos canaux marketing influencent la création de prospects et de leurs engagements supplémentaires.
**[!DNL Marketo Measure]101 : Leads par ID** | Il s’agit d’un rapport beaucoup plus granulaire qui affiche l’histoire de chaque lead et les points de contact d’acheteur qui lui sont associés.

**Leads/contacts avec les points de contact de l’acheteur** | Ces rapports sont communément appelés rapports Personnes [!DNL Marketo Measure]. Ils utilisent l’objet personnalisé [!DNL Marketo Measure] _[!DNL Marketo Measure]Personne_ par opposition à l’objet Lead dans les rapports mentionnés ci-dessus.

L’objet de personne [!DNL Marketo Measure] met en relation les objets de lead et de contact. Par défaut, [!DNL Salesforce] ne fournit pas la possibilité de créer des rapports à l’aide de l’objet Lead et Contact dans le même rapport. En associant l’objet de lead et de contact à l’aide de l’identifiant unique d’une personne, son adresse électronique, la personne [!DNL Marketo Measure] peut créer des rapports sur les points de contact d’acheteur liés au lead et au contact dans le même rapport. Ce type de rapport est idéal lorsque vous souhaitez valider l’un des paramètres de votre compte [!DNL Marketo Measure], car il s’agit du niveau de rapport de point de contact le plus inclusif.

Les deux variations de rapport suivantes utilisent le même type de rapport, mais sont regroupées par mesures différentes, ID de personne (e-mail) et Canal marketing. Voici les premiers rapports funnel/middle of funnel qui sont très utiles lorsque vous cherchez à explorer la manière dont vos prospects et contacts interagissent avec vos efforts marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les informations suivantes :

**[!DNL Marketo Measure]101 : Lead/contacts par canal** | Une vue d’ensemble de la manière dont vos canaux marketing influencent la création de leads ou de contacts et leurs engagements supplémentaires. Ce rapport est idéal pour comprendre l’engagement total sur vos canaux marketing et les canaux marketing qui génèrent de nouveaux noms nets dans votre instance Salesforce.
**[!DNL Marketo Measure]101 : lead/contacts par ID** | Il affiche l’histoire de chaque personne [!DNL Marketo Measure] et constitue un rapport beaucoup plus granulaire, présentant chaque personne et ses points de contact d’acheteur, que le point de contact se soit produit lorsqu’elle était un prospect ou en tant que contact.

**Opportunités avec les points de contact d’attribution de l’acheteur** | Les deux derniers rapports « _[!DNL Marketo Measure]101..._ » se trouvent au bas des rapports funnel qui affichent les données Buyer Attribution Touchpoint liées aux opportunités. Le principal facteur de différenciation de ces rapports est qu’ils sont créés à partir des _points de contact d’attribution de l’acheteur_ qui se rapportent aux données au niveau de l’opportunité et de l’opportunité, telles que le chiffre d’affaires. Lorsque vous souhaitez créer un état sur les opportunités ou le revenu attribué, utilisez ce type d&#39;état. Les deux rapports ci-dessous utilisent le même type de rapport. Toutefois, ils sont regroupés par mesures différentes, Identifiant de l’opportunité par rapport au Canal marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les informations suivantes :

**[!DNL Marketo Measure]101 : Opportunités par canal** | Une vue d’ensemble de la manière dont vos canaux marketing influencent et génèrent le chiffre d’affaires attribué à vos opportunités.
**[!DNL Marketo Measure]101 : opportunités par ID** | Cette version de rapport granulaire vous présente le parcours complet de vos opportunités. Dans ce rapport, vous pouvez voir chaque Buyer Attribution Touchpoint associée à une opportunité et son chiffre d’affaires attribué à travers les différents modèles d’attribution.

Il est recommandé de traiter les rapports « _[!DNL Marketo Measure]101..._ » comme des modèles pour vos besoins de création de rapports. Commencer par l’un des rapports ci-dessus vous permet de gagner du temps et vous assure que vous utilisez les champs corrects liés aux données [!DNL Marketo Measure]. Veillez toujours à « Enregistrer sous » chaque fois que vous effectuez des personnalisations des modèles « _[!DNL Marketo Measure]101..._ » afin de conserver la variation d’origine du rapport.

Le dossier « Rapports Buyer Touchpoint » est conçu pour vous aider à commencer à créer des rapports [!DNL Marketo Measure]. Pour les rapports exploitables, vous devez personnaliser ces rapports afin qu’ils soient adaptés à vos besoins de création de rapports. vous devrez ajouter les filtres nécessaires pour vous assurer que les enregistrements du rapport (et leurs points de contact associés) sont alignés avec votre objectif de création de rapports.

Lorsque vous connaissez les rapports « _[!DNL Marketo Measure]101..._ », vous pouvez les recréer à partir de types de rapports personnalisés pour répondre à d’autres besoins de création de rapports personnalisés. La création des [[!DNL Marketo Measure] types de rapports personnalisés](/help/marketo-measure-salesforce-reporting/new-report-types/creating-custom-marketo-measure-report-types.md) vous permet d’extraire des champs personnalisés que vous pouvez couramment utiliser dans d’autres rapports CRM. Cela vous aidera à passer [!DNL Marketo Measure] rapports au niveau supérieur.
