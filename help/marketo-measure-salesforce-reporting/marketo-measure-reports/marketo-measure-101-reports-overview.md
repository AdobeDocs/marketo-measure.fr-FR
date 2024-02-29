---
description: "[!DNL Marketo Measure] Présentation des 101 rapports - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Présentation des rapports 101"
exl-id: 83977b81-8055-47fd-8a6b-5ef32d280269
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 2%

---

# Vue d’ensemble basique des rapports [!DNL Marketo Measure] {#marketo-measure-101-reports-overview}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans la documentation, mais consultez toujours &quot;Bizible&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version. Notre nouvelle identité (rebranding) sera bientôt répercutée dans votre CRM.

Tous [!DNL Marketo Measure] clients utilisant [!DNL Marketo Measure] et [!DNL Salesforce] ont accès au dossier &quot;Rapports de points de contact d’achat&quot; dans leur instance SFDC. Ce dossier contient un certain nombre de rapports prédéfinis qui peuvent vous aider à commencer à créer des rapports avec les données de point de contact de l’achat.

![](assets/bizible-101-reports-overview-1.png)

Bien que la plupart de ces rapports aient déjà des objectifs spécifiques en matière de création de rapports, il en existe six &quot;_[!DNL Marketo Measure]101.._&quot; représentés par trois types de rapports clés qui couvrent la majorité des besoins en matière de rapports.

* Pistes avec points de contact d’achat
* [!DNL Marketo Measure] Personnes avec des points de contact d’achat
* Points de contact d’attribution des acheteurs avec opportunités

![](assets/bizible-101-reports-overview-2.png)

Ces rapports vous fournissent les champs de base et l’infrastructure nécessaires à toute [!DNL Marketo Measure] rapport associé que vous souhaitez créer. Nous encourageons tous les clients, anciens et nouveaux, à commencer par ces rapports lorsqu’ils explorent les questions d’attribution marketing. Vous trouverez ci-dessous une explication de chacun des six &quot;_[!DNL Marketo Measure]101.._&quot;.

_Si vous ne trouvez pas le dossier du rapport Points de contact de l’acheteur ou les six points &quot;_[!DNL Marketo Measure] 101.._&quot; dans ce dossier, contactez la prise en charge pour obtenir de l’aide._

**Pistes avec points de contact d’achat** | Les deux variantes suivantes génèrent des rapports sur les pistes et leurs points de contact d’achat. Bien qu’ils utilisent le même type de rapport de base, ils sont regroupés selon différentes mesures, ID de piste ou Canal marketing, afin de fournir deux vues clés des données. Ce type de rapport, qui s’ajoute aux rapports Entonnoir, est idéal pour explorer la manière dont vos pistes s’engagent dans vos efforts marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les éléments suivants :

**[!DNL Marketo Measure]101 : Pistes par canal** | Vue de haut niveau de l’influence de vos canaux marketing sur la création de pistes et de leurs engagements supplémentaires.
**[!DNL Marketo Measure]101 : Pistes par identifiant** | Il affiche l’histoire des Pistes et est un rapport beaucoup plus granulaire, présentant chaque prospect et les points de contact d’achat associés.

**Prospects/contacts avec les points de contact de l’acheteur** | Ces rapports sont généralement appelés [!DNL Marketo Measure] Rapports de personnes. Ils utilisent la variable [!DNL Marketo Measure] objet personnalisé _[!DNL Marketo Measure]Personne_ par opposition à l’objet Lead dans les rapports mentionnés ci-dessus.

La variable [!DNL Marketo Measure] Objet Personne associe les objets Lead et Contact. Prêt à l’emploi, [!DNL Salesforce] ne permet pas de créer des rapports à l’aide de l’objet Lead et Contact dans le même rapport. En fonction de l’objet de piste et de contact à l’aide de l’identifiant unique d’une personne, son e-mail, la variable [!DNL Marketo Measure] Les personnes peuvent créer des rapports sur les points de contact d’acheteurs associés aux prospects et aux contacts dans le même rapport. Ce type de rapport est idéal lorsque vous souhaitez valider l’une de vos [!DNL Marketo Measure] Paramètres du compte, car il s’agit du niveau de création de rapports de point de contact le plus inclusif.

Les deux variations suivantes utilisent le même type de rapport, mais sont regroupées par mesures différentes, ID de personne (adresse électronique) et Canal marketing. Ces rapports s’ajoutent aux rapports Entonnoir/Milieu de l’entonnoir qui sont très utiles lorsque vous cherchez à découvrir comment vos Leads et contacts interagissent avec vos efforts marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les éléments suivants :

**[!DNL Marketo Measure]101 : Prospérité/contacts par canal** | Vue de haut niveau de l’influence de vos canaux marketing sur la création de pistes ou de contacts et de leurs engagements supplémentaires. Ce rapport est idéal pour comprendre l’engagement total sur vos canaux marketing et pour identifier les canaux marketing qui génèrent de nouveaux noms dans votre instance Salesforce.
**[!DNL Marketo Measure]101 : Prospérité/contacts par identifiant** | Chaque [!DNL Marketo Measure] L’histoire de la personne et est un rapport beaucoup plus granulaire, présentant chaque individu et ses points de contact d’acheteur, qu’il s’agisse d’un prospect ou d’un contact.

**Opportunités avec des points de contact d’attribution d’achat** | Les deux derniers &quot;_[!DNL Marketo Measure]101.._&quot;Les rapports se trouvent au bas des rapports Entonnoir qui affichent les données du point de contact d’attribution de l’achat liées aux opportunités. Le principal facteur de différenciation de ces rapports est qu’ils sont construits à partir de _Points de contact d’attribution des acheteurs_ qui se rapportent aux données au niveau des opportunités et des opportunités, telles que les recettes. Lorsque vous souhaitez générer des rapports sur les opportunités ou les recettes attribuées, ce type de rapport doit être utilisé. Toutefois, les deux rapports ci-dessous utilisent le même type de rapport. Ils sont regroupés par mesures différentes, Identifiant d’opportunité ou Canal marketing. Avant toute personnalisation, les deux rapports ci-dessous affichent les éléments suivants :

**[!DNL Marketo Measure]101 : Opportunités par canal** | Vue de haut niveau de l’influence de vos canaux marketing et de la manière dont ils génèrent des recettes attribuées par rapport à vos opportunités.
**[!DNL Marketo Measure]101 : Opportunités par identifiant** | Cette version de rapport granulaire vous présente l’parcours complet de vos opportunités. Dans ce rapport, vous pouvez voir chaque point de contact d’attribution de l’acheteur associé à une opportunité et ses recettes attribuées via les différents modèles d’attribution.

Il est recommandé de traiter le _[!DNL Marketo Measure]101.._&quot; comme modèles pour vos besoins de création de rapports. Commencer avec l’un des rapports ci-dessus vous fera gagner du temps et vous assurera que vous travaillez avec les champs corrects liés à [!DNL Marketo Measure] data. Veillez toujours à &quot;Enregistrer sous&quot; chaque fois que vous apportez des personnalisations au _[!DNL Marketo Measure]101.._&quot; afin de conserver la variante originale du rapport.

Le dossier &quot;Rapports points de contact client&quot; est conçu pour vous aider à prendre en main vos [!DNL Marketo Measure] création de rapports, pour les rapports pratiques, vous devez personnaliser ces rapports afin qu’ils soient adaptés à vos besoins de création de rapports. vous devez ajouter les filtres nécessaires pour vous assurer que les enregistrements du rapport (et leurs points de contact associés) sont alignés sur votre objectif de création de rapports.

Une fois que vous connaissez le &quot;_[!DNL Marketo Measure]101.._&quot; , vous pouvez les recréer à partir de types de rapports personnalisés pour des besoins de création de rapports plus personnalisés. Création de la variable [[!DNL Marketo Measure] Types de rapports personnalisés](/help/marketo-measure-salesforce-reporting/new-report-types/creating-custom-marketo-measure-report-types.md) vous permettra d’extraire des champs personnalisés que vous pouvez généralement utiliser dans d’autres rapports de gestion de la relation client. Cela vous aidera à vous amener [!DNL Marketo Measure] création de rapports au niveau suivant !
