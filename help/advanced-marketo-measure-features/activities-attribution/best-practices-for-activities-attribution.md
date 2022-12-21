---
description: Bonnes pratiques pour l’attribution des activités - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques pour l’attribution des activités
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Bonnes pratiques pour l’attribution des activités {#best-practices-for-activities-attribution}

## APERÇU {#overview}

Le [!DNL Marketo Measure] La fonction Attribution des activités permet aux clients de créer des points de contact à partir des enregistrements d’activité dans votre gestion de la relation client. Cette méthode de création de points de contact est flexible dans la mesure où elle vous permet de créer des règles basées sur des champs de tâche ou d’événement pour informer [!DNL Marketo Measure] d’activité à partir de laquelle elle doit produire des points de contact et recevoir par la suite un crédit d’attribution.

Le cas d’utilisation le plus courant de cette fonctionnalité consiste à élaborer des règles qui intègrent les interactions de vente dans vos données de point de contact Acheteur. L’attribution des activités vous permet d’aligner vos données commerciales et marketing en un seul parcours.

Pour plusieurs [!DNL Salesforce] , l’objet Activité peut héberger divers types d’enregistrements. Il est donc important que vos règles d’activité soient spécifiques et adaptées aux enregistrements que vous essayez de traduire en points de contact. Les bonnes pratiques suivantes vous aideront à vous assurer que vous créez des points de contact significatifs et précieux via l’attribution de vos activités.

## Bonne pratique {#best-practice}

Que vous définissiez des règles d’activité pour la première fois ou que vous examiniez simplement des règles d’activité qui ont été configurées précédemment, tenez compte des bonnes pratiques suivantes.

* Démarrer simple
   * Identifiez quelques types clés d’activités que vous souhaitez incorporer à votre [!DNL Marketo Measure] données, puis ajoutez d’autres types lorsque vous vous familiarisez avec la manière dont ces points de contact sont attribués.
   * Comme mentionné, le Principal cas d’utilisation de cette fonctionnalité consiste à créer des points de contact qui effectuent le suivi de l’efficacité de votre équipe de développement des ventes, en particulier les appels téléphoniques sortants et les e-mails sortants.

>[!NOTE]
>
>Il s’agit de **NOT** recommandé pour effectuer le suivi des activités de vente qui se produisent après la création de l’opportunité, car le suivi d’un processus des directeurs des ventes n’offrira pas beaucoup d’informations. L’objectif est de suivre l’influence des ventes aux côtés de l’influence marketing, principalement dans le développement d’une nouvelle génération d’opportunités/de pipelines.

* Ne pas utiliser de champs de formule pour définir vos règles
* Créer des règles spécifiques et précises
   * Vous souhaitez que le seuil de création d’un point de contact d’activité soit le même (ou similaire) qu’un remplissage de formulaire ou une adhésion à une campagne, c’est-à-dire (Réponses à un email sortant ou à des conversations téléphoniques terminées)
* Toujours valider les nouvelles règles dans [!DNL Salesforce] avant enregistrement et traitement
   * La réplication de votre ou vos règles d’activité dans un type de rapport &quot;Tâches et événements&quot; vous permettra de comprendre clairement combien de points de contact seront créés à partir de cette règle.
* Travail avec votre équipe d’Opt-marketing
   * L’intégration de l’équipe qui travaille le plus près de vos enregistrements d’activité ou de votre outil d’activation des ventes vous permet de vous assurer que vous utilisez les champs appropriés pour définir vos règles.

## Bonne pratique pour la maintenance {#best-practice-for-maintenance}

En examinant vos règles d’attribution d’activité au moins deux fois par an, vous vous assurez que vos points de contact d’activité sont précis et à jour. Vous souhaitez vous assurer que ces règles ne créent pas de points de contact indésirables qui diluent vos données d’attribution d’achat. Un examen de la manière dont vos règles sont définies vous aidera, ainsi qu’à votre équipe, à vous sentir confiant dans votre attribution des activités et dans son rôle dans votre [!DNL Marketo Measure] data.

D’autres raisons pouvant déclencher une révision de vos règles d’activité incluent...

* Chiffre d’affaires de votre équipe marketing
* Modifications apportées aux champs utilisés pour définir les enregistrements d’activité
* Modifications ou mises à jour de vos outils d’activation commerciale

>[!MORELIKETHIS]
>
>* [Attribution des activités](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [FAQ sur l’attribution des activités de vente](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)


