---
description: Bonnes pratiques pour l’attribution des activités - [!DNL Marketo Measure]
title: Bonnes pratiques relatives à l’attribution des activités
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
feature: Attribution
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 4%

---

# Bonnes pratiques relatives à l’attribution des activités {#best-practices-for-activities-attribution}

## Vue d’ensemble {#overview}

La fonction [!DNL Marketo Measure] Attribution des activités permet aux clients de créer des points de contact à partir des enregistrements d’activité dans votre gestion de la relation client. Cette méthode de création de points de contact est flexible. Il vous permet de créer des règles basées sur des champs &quot;Tâche&quot; ou &quot;Événement&quot; afin d’informer [!DNL Marketo Measure] de l’activité à partir de laquelle il doit produire des points de contact et, par conséquent, de recevoir un crédit d’attribution.

Le cas d’utilisation le plus courant de cette fonctionnalité consiste à élaborer des règles qui intègrent les interactions de vente dans vos données de point de contact Acheteur. L’attribution des activités vous permet d’aligner vos données commerciales et marketing en un seul parcours.

Pour de nombreuses instances [!DNL Salesforce], l’objet Activité peut héberger différents types d’enregistrements. Il est donc important que vos règles d’activité soient spécifiques et personnalisées aux enregistrements que vous essayez de traduire en points de contact. Les bonnes pratiques suivantes vous permettent de vous assurer que vous créez des points de contact significatifs et précieux via l’attribution de vos activités.

## Bonne pratique {#best-practice}

Que vous définissiez des règles d’activité pour la première fois ou que vous examiniez simplement des règles d’activité qui ont été configurées précédemment, tenez compte des bonnes pratiques suivantes.

* Commencer simple
   * Identifiez quelques types d’activités clés que vous souhaitez incorporer à vos données [!DNL Marketo Measure], puis ajoutez d’autres types lorsque vous vous familiarisez avec la manière dont ces points de contact sont attribués.
   * Comme mentionné, le principal cas d’utilisation de cette fonctionnalité est de créer des points de contact qui effectuent le suivi de l’efficacité de votre équipe de développement des ventes, en particulier les appels téléphoniques sortants et les e-mails sortants.

>[!NOTE]
>
>Il est **NOT** recommandé de suivre les activités de vente qui se produisent après la création de l’opportunité, car le suivi d’un processus de directeurs commerciaux n’offre pas beaucoup d’informations. L’objectif est de suivre l’influence des ventes aux côtés de l’influence marketing, principalement dans le développement d’une nouvelle génération d’opportunités/de pipelines.

* Ne pas utiliser de champs de formule pour définir vos règles
* Créer des règles spécifiques et précises
   * Le seuil de création d’un point de contact d’activité doit être le même (ou similaire) qu’un formulaire rempli ou un abonnement à une campagne : Réponses à un courrier électronique sortant ou à des conversations téléphoniques terminées
* Toujours valider les nouvelles règles dans [!DNL Salesforce] avant d’enregistrer et de traiter
   * La réplication des règles d’activité dans un type de rapport &quot;Tâches et événements&quot; vous permet de comprendre exactement combien de points de contact se trouvent dans la règle.
* Travail avec votre équipe d’Opt-marketing
   * L’intégration de l’équipe qui travaille le plus avec vos enregistrements d’activité ou votre outil d’activation des ventes vous permet de vous assurer que vous utilisez les champs appropriés pour définir vos règles.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

En examinant vos règles d’attribution d’activité au moins deux fois par an, vous avez la garantie que vos points de contact d’activité sont précis et à jour. Vous souhaitez vous assurer que ces règles ne créent pas de points de contact indésirables qui diluent vos données d’attribution d’achat. Un examen de la manière dont vos règles sont définies vous aidera, ainsi que votre équipe, à vous sentir confiant dans votre attribution des activités et dans son rôle dans vos données [!DNL Marketo Measure].

D’autres raisons pouvant déclencher une révision de vos règles d’activité incluent...

* Changements au sein de votre équipe marketing
* Modifications apportées aux champs utilisés pour définir les enregistrements d’activité
* Modifications ou mises à jour de vos outils d’activation des ventes

>[!MORELIKETHIS]
>
>* [Attribution des activités](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [FAQ sur l’attribution des activités de vente](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
