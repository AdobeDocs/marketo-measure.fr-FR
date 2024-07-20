---
description: "[!DNL Marketo Measure] 101 - Aperçu des rapports - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] 101 - Aperçu des rapports"
exl-id: 83977b81-8055-47fd-8a6b-5ef32d280269
feature: Reporting
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 3%

---

# Vue d’ensemble basique des rapports [!DNL Marketo Measure] {#marketo-measure-101-reports-overview}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Tous les clients [!DNL Marketo Measure] utilisant [!DNL Marketo Measure] et [!DNL Salesforce] ont accès au dossier &quot;Rapports points de contact d’achat&quot; dans leur instance SFDC. Ce dossier contient un certain nombre de rapports prédéfinis qui peuvent vous aider à commencer à créer des rapports avec les données Buyer Touchpoint.

![](assets/bizible-101-reports-overview-1.png)

Bien que la plupart de ces rapports aient déjà des objectifs de création de rapports spécifiques, il existe six &quot;_[!DNL Marketo Measure]101..._&quot; représentés par trois types de rapports clés qui couvrent la majorité des besoins de création de rapports.

* Pistes avec points de contact d’achat
* [!DNL Marketo Measure] Personnes avec des points de contact d’achat
* Points de contact d’attribution des acheteurs avec opportunités

![](assets/bizible-101-reports-overview-2.png)

Ces rapports vous fournissent les champs de base et l’infrastructure nécessaires pour tout rapport lié à [!DNL Marketo Measure] que vous souhaitez créer. Nous encourageons tous les clients, anciens et nouveaux, à commencer par ces rapports lorsqu’ils explorent les questions d’attribution marketing. Vous trouverez ci-dessous une explication de chacun des six rapports &quot;_[!DNL Marketo Measure]101..._&quot;.

_Si vous ne trouvez pas le dossier du rapport Points de contact de l’acheteur ou les six rapports &quot;_[!DNL Marketo Measure] 101..._&quot; dans ce dossier, contactez l’assistance._

**Pistes avec points de contact d’achat** | Les deux variantes suivantes génèrent des rapports sur les pistes et leurs points de contact d’achat. Bien qu’ils utilisent le même type de rapport de base, ils sont regroupés selon différentes mesures, ID de piste ou Canal marketing, afin de fournir deux vues clés des données. Ce type de rapport, qui s’ajoute aux rapports Entonnoir, est idéal pour explorer la manière dont vos pistes s’engagent dans vos efforts marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les éléments suivants :

**[!DNL Marketo Measure]101 : Pistes par canal** | Vue de haut niveau de l’influence de vos canaux marketing sur la création de pistes et de leurs engagements supplémentaires.
**[!DNL Marketo Measure]101 : Pistes par ID** | Il affiche l’histoire des Pistes et est un rapport beaucoup plus granulaire, présentant chaque prospect et les points de contact d’achat associés.

**Pistes/contacts avec les points de contact de l’acheteur** | Ces rapports sont généralement appelés rapports [!DNL Marketo Measure] sur les personnes. Ils utilisent l’objet personnalisé [!DNL Marketo Measure] _[!DNL Marketo Measure]Personne_ par opposition à l’objet Lead dans les rapports mentionnés ci-dessus.

L’objet de personne [!DNL Marketo Measure] associe les objets Lead et Contact. [!DNL Salesforce] ne permet pas de créer des rapports à l’aide de l’objet Lead et Contact dans le même rapport. En se référant à l’objet Lead et Contact à l’aide de l’identifiant unique d’une personne, l’adresse électronique de celle-ci permet à la [!DNL Marketo Measure] personne de créer des rapports sur les points de contact des acheteurs associés aux prospects et aux contacts dans le même rapport. Ce type de rapport est idéal pour vérifier les paramètres de votre compte [!DNL Marketo Measure], car il s’agit du niveau de création de rapports de point de contact le plus inclusif.

Les deux variations suivantes utilisent le même type de rapport, mais sont regroupées par mesures différentes, ID de personne (adresse électronique) et Canal marketing. Ces rapports s’ajoutent aux rapports Entonnoir/Milieu de l’entonnoir qui sont très utiles lorsque vous cherchez à découvrir comment vos Leads et contacts interagissent avec vos efforts marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les éléments suivants :

**[!DNL Marketo Measure]101 : prospect/contacts par canal** | Vue de haut niveau de l’influence de vos canaux marketing sur la création de pistes ou de contacts et de leurs engagements supplémentaires. Ce rapport est idéal pour comprendre l’engagement total sur vos canaux marketing et pour identifier les canaux marketing qui génèrent de nouveaux noms dans votre instance Salesforce.
**[!DNL Marketo Measure]101 : Lead/contacts par ID** | Cette section présente l’histoire de chaque personne [!DNL Marketo Measure] et constitue un rapport beaucoup plus granulaire, présentant chaque personne et ses points de contact d’achat, qu’il s’agisse d’un prospect ou d’un contact.

**Opportunités avec des points de contact d’attribution d’achat** | Les deux derniers rapports &quot;_[!DNL Marketo Measure]101..._&quot; se trouvent au bas des rapports entonnoir qui affichent les données Buyer Attribution Touchpoint liées aux opportunités. Le facteur de différenciation clé de ces rapports est qu’ils sont construits à partir des _points de contact d’attribution de l’achat_ qui se rapportent aux données au niveau des opportunités et des opportunités, telles que les recettes. Lorsque vous souhaitez générer des rapports sur les opportunités ou les recettes attribuées, ce type de rapport doit être utilisé. Toutefois, les deux rapports ci-dessous utilisent le même type de rapport. Ils sont regroupés par mesures différentes, Identifiant d’opportunité ou Canal marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les éléments suivants :

**[!DNL Marketo Measure]101 : opportunités par canal** | Vue de haut niveau de l’influence de vos canaux marketing et de la manière dont ils génèrent des recettes attribuées par rapport à vos opportunités.
**[!DNL Marketo Measure]101 : opportunités par identifiant** | Cette version de rapport granulaire vous présente l’parcours complet de vos opportunités. Dans ce rapport, vous pouvez voir chaque Buyer Attribution Touchpoint associée à une opportunité et ses recettes attribuées via les différents modèles d’attribution.

Il est recommandé de traiter les rapports &quot;_[!DNL Marketo Measure]101..._&quot; comme des modèles pour vos besoins de création de rapports. En commençant par l’un des rapports ci-dessus, vous gagnerez du temps et vous assurez que vous travaillez avec les champs corrects liés aux données [!DNL Marketo Measure]. Veillez toujours à &quot;Enregistrer sous&quot; chaque fois que vous effectuez des personnalisations sur les modèles &quot;_[!DNL Marketo Measure]101..._&quot; afin de conserver la variante d’origine du rapport.

Le dossier &quot;Rapports Buyer Touchpoint&quot; est conçu pour vous aider à prendre en main vos rapports [!DNL Marketo Measure]. Pour les rapports pratiques, vous devrez personnaliser ces rapports afin qu’ils soient adaptés à vos besoins de création de rapports. vous devez ajouter les filtres nécessaires pour vous assurer que les enregistrements du rapport (et leurs points de contact associés) sont alignés sur votre objectif de création de rapports.

Lorsque vous connaissez les rapports &quot;_[!DNL Marketo Measure]101..._&quot;, vous pouvez les recréer à partir de types de rapports personnalisés pour des besoins de création de rapports plus personnalisés. La création des [[!DNL Marketo Measure] types de rapports personnalisés](/help/marketo-measure-salesforce-reporting/new-report-types/creating-custom-marketo-measure-report-types.md) vous permet d’extraire des champs personnalisés que vous pouvez généralement utiliser dans d’autres rapports de gestion de la relation client. Cela vous aidera à passer le reporting [!DNL Marketo Measure] au niveau suivant !
