---
description: Bonnes pratiques pour l’attribution des activités - [!DNL Marketo Measure]
title: Bonnes pratiques relatives à l’attribution des activités
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
feature: Attribution
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 4%

---


# Bonnes pratiques relatives à l’attribution des activités {#best-practices-for-activities-attribution}

## Vue d’ensemble {#overview}

La fonction d’attribution des activités [!DNL Marketo Measure] permet aux clients de créer des points de contact à partir des enregistrements d’activité dans votre CRM. Cette méthode de création de points de contact est flexible. Il vous permet de créer des règles basées sur des champs « Tâche » ou « Événement » afin d’indiquer [!DNL Marketo Measure] les enregistrements d’activité à partir desquels il doit produire des points de contact et qui, par conséquent, peuvent recevoir un crédit d’attribution.

Le cas d’utilisation le plus courant de cette fonctionnalité consiste à concevoir des règles qui intègrent les interactions commerciales dans vos données de point de contact Acheteur. L’attribution des activités vous permet d’aligner vos données de ventes et de marketing sur un seul parcours.

Pour de nombreuses instances [!DNL Salesforce], l’objet Activity peut héberger divers types d’enregistrements. Il est donc important que vos règles Activity soient spécifiques et adaptées aux enregistrements que vous essayez de traduire en points de contact. Les bonnes pratiques suivantes vous aident à vous assurer que vous créez des points de contact significatifs et utiles via votre attribution d’activités.

## Bonne pratique {#best-practice}

Que vous définissiez des règles d’activité pour la première fois ou que vous examiniez simplement des règles d’activité précédemment configurées, gardez à l’esprit les bonnes pratiques suivantes.

* Démarrer simple
   * Identifiez quelques types clés d’activités que vous souhaitez incorporer dans vos données [!DNL Marketo Measure], puis ajoutez d’autres types au fur et à mesure que vous vous familiarisez avec la manière dont ces points de contact sont attribués
   * Comme mentionné, le principal cas d’utilisation de cette fonctionnalité consiste à créer des points de contact qui surveillent l’efficacité de votre équipe de développement des ventes, en particulier les appels téléphoniques sortants et les e-mails sortants

>[!NOTE]
>Il n’est **PAS** recommandé de suivre les activités de vente qui se produisent après la création de l’opportunité, car le suivi d’un processus de directeurs commerciaux n’offre pas grand-chose d’insight. L’objectif est de suivre l’influence des ventes aux côtés de l’influence du marketing, principalement dans le développement d’une nouvelle génération d’opportunités/de pipelines

* Ne pas utiliser de champs de formule pour définir vos règles
* Créer des règles spécifiques et précises
   * Le seuil de création d’un point de contact d’activité doit être identique (ou similaire) à un remplissage de formulaire ou à une adhésion à une campagne : réponses à un e-mail sortant ou conversations téléphoniques terminées
* Toujours valider les nouvelles règles dans [!DNL Salesforce] avant d’enregistrer et de traiter
   * La réplication des règles d’activité dans un type de rapport « Tâches et événements » vous permet de comprendre clairement le nombre exact de points de contact de la règle
* Travailler avec votre équipe d’opportunités commerciales
   * Si vous faites appel à l’équipe qui travaille le plus étroitement avec votre enregistrement d’activité ou votre outil de promotion des ventes, vous vous assurerez d’utiliser les champs appropriés pour définir vos règles

## Bonne pratique de maintenance {#best-practice-for-maintenance}

En examinant vos règles d’attribution d’activité au moins deux fois par an, vous vous assurez que vos points de contact d’activité sont précis et à jour. Vous devez vous assurer que ces règles ne créent pas de points de contact indésirables qui diluent vos données d’attribution de l’acheteur. Un examen de la manière dont vos règles sont définies vous aidera, vous et votre équipe, à avoir confiance dans votre attribution d’activités et dans son rôle dans vos données [!DNL Marketo Measure].

Autres raisons de déclencher une révision de vos règles d’activité :

* Changements au sein de votre équipe marketing
* Modifications apportées aux champs utilisés pour définir les enregistrements d’activité
* Modifications ou mises à jour de vos outils de promotion des ventes

>[!MORELIKETHIS]
> [Attribution des activités](/help/advanced-features/activities-attribution/salesforce-activities-attribution.md)
> [FAQ sur l’attribution des activités de vente &#x200B;](/help/advanced-features/activities-attribution/activities-attribution-faq.md)
