---
description: Conseils sur les coûts de campagne CRM pour les utilisateurs de Marketo Measure
title: Coûts de campagne CRM
exl-id: d967cabe-b9f1-4ea1-a81b-e4484c703ecf
feature: Spend Management
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 1%

---

# Coûts de campagne CRM {#crm-campaign-costs}

La plupart des clients [!DNL Marketo Measure] utilisent des campagnes CRM pour effectuer le suivi des activités de marketing hors ligne. Les marketeurs qui utilisent ces campagnes surveillent également les coûts dans le CRM. Cette fonctionnalité facilite la tâche aux professionnels du marketing en [!DNL Marketo Measure] permettant de lire ces coûts et de les appliquer aux dépenses marketing signalées dans [!DNL Marketo Measure]. À ce jour, les clients ont dû saisir manuellement les coûts de chaque campagne par mois. Toutefois[!DNL Marketo Measure] avec les informations nécessaires fournies à , les utilisateurs peuvent automatiser ce processus afin que les professionnels du marketing puissent passer plus de temps à analyser leurs dépenses et leur retour sur investissement.

## Disponibilité {#availability}

Cette fonctionnalité est disponible pour tous les clients [!DNL Salesforce] et Dynamics.

## Fonctionnement {#how-it-works}

[!DNL Marketo Measure] commence par rechercher les campagnes qui ont été « activées » pour les points de contact. Une règle de synchronisation de campagne correspondante a donc été créée ou la valeur Activer les points de contact de l’acheteur est « Inclure tous les membres de la campagne » ou « Inclure les membres de la campagne ayant répondu ». En outre, [!DNL Marketo Measure] devez importer les valeurs correctes et savoir comment répartir les coûts. Par conséquent, les champs suivants doivent contenir une valeur :

**[!DNL Salesforce]** : `ActualCost`, `StartDate`, `EndDate`

**[!DNL Microsoft Dynamics]** : `totalactualcost`, `actualstart`, `actualend`

Si une valeur est manquante dans l’un des 3 champs, [!DNL Marketo Measure] n’importera pas les coûts. Vous pouvez corriger ce problème en mettant à jour l’enregistrement de la campagne dans le CRM. Les coûts ne sont pas importés s&#39;ils sont définis sur 0 $, car [!DNL Salesforce] traite les valeurs vides et 0 $ de la même manière.

Pour [!DNL Marketo Measure] de déterminer la répartition d’une campagne sur plusieurs mois, les dates de début et de fin de la campagne sont utilisées pour répartir uniformément le montant par jour.

![Pour que Marketo Measure détermine la répartition d’une campagne sur ](assets/spend-management-3.jpg)

Dans cet exemple, une campagne dure 109 jours, donc avec un coût total de 18 000 $, les dépenses quotidiennes s’élèvent à environ 165,14 $.

En fonction du nombre de jours par mois, nous obtenons ces totaux mensuels, comme vous pouvez le voir dans le tableau :

Juil 2018 : (18 000 $/109) x 31 = 5 119,27 $

Août 2018 : (18 000 $/109) x 31 = 5 119,27 $

Sep 2018 : (18 000 $/109) x 30 = 4 954,13 $

Oct 2018 : (18 000 $/109) x 17 = 2 807,34 $

## Historique des dépenses signalées {#historical-reported-spend}

Si vous avez saisi des dépenses pour des campagnes qui ont fait l’objet d’un suivi dans le passé et qui ont été mappées à une campagne CRM, elles ne remplacent aucun des coûts que vous avez saisis. Si la même campagne est modifiée dans le CRM, elle l’ignore et donne la priorité aux modifications que vous avez précédemment effectuées dans le téléchargement CSV.

Si vous préférez que nous prenions désormais le coût de la campagne CRM, modifiez la valeur dans le fichier CSV à 0 $ ce qui annule l’entrée. La prochaine fois que les traitements seront exécutés pour importer les coûts, les rapports précédemment modifiés seront intégrés.

## Campagnes sans points de contact {#campaigns-with-no-touchpoints}

De nombreux professionnels du marketing choisissent de signaler les dépenses marketing sur des campagnes CRM qui n’ont généré aucun point de contact ou qui ne disposent d’aucun membre de campagne à des fins de suivi des dépenses. Tant que les trois champs sont renseignés (date de début, date de fin, coût) et que la campagne est activée pour les points de contact, [!DNL Marketo Measure] extrait ce coût, même si aucun point de contact n’y est associé.

Cela peut s’avérer utile pour effectuer le suivi des dépenses liées aux coûts marketing excédentaires ou pour intégrer ces coûts dans vos calculs de retour sur investissement.

## Synchronisation du programme Marketo {#marketo-program-sync}

Si vous importez des programmes Marketo dans le CRM sous forme de campagnes, assurez-vous que la mise en correspondance de la date de début, de la date de fin et du coût de la période est activée pour les champs CRM obligatoires. Comme il n’existe aucun mappage vers le champ Activer les points de contact de l’acheteur , vous devez tout de même activer ces campagnes afin que les coûts puissent être extraits.

## Modifier les coûts {#editing-the-costs}

Une fois qu’une campagne est importée depuis le CRM, elle est traitée de la même manière qu’un fournisseur d’API Ads et n’apparaît pas dans le fichier CSV pour apporter des modifications de coût.

Toute modification du coût ou de la distribution doit être effectuée dans le CRM afin que nous puissions pointer vers un seul point de vérité.

## Questions fréquentes {#faq}

**J’ai apporté une modification à ma campagne - quand dois-je m’attendre à voir les modifications dans le tableau Dépenses marketing ou dans mes rapports ?**

3-4 heures

**La date de début, la date de fin et le coût sont renseignés, mais pourquoi mes coûts ne sont-ils toujours pas affichés dans [!DNL Marketo Measure] ?**

Vérifiez que la valeur « Activer Buyer Touchpoint » est définie sur « Inclure tous les membres de la campagne » ou au moins sur « Inclure les membres de la campagne « Répondus » », ou que vous avez créé une règle de synchronisation de campagne personnalisée qui inclut cette campagne. Si vous l’avez confirmé et que vous ne voyez toujours pas la campagne, contactez l’assistance technique de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} afin que nous puissions vérifier que vos campagnes sont correctement importées.

**Je dois modifier la répartition de ma campagne afin de pouvoir la pondérer plus lourdement certains mois. Comment est-ce que je fais ça ?**

La répartition des coûts est purement basée sur une répartition uniforme de la date de début à la date de fin. Malheureusement, nous ne pouvons pas le modifier pour que vos coûts aient une pondération différente des dates fixées. Vous pouvez contrôler cela en ajustant les dates de début et de fin de votre campagne, car chaque jour du mois compte.

**Des coûts sont configurés sur ma campagne parent - Comment les coûts de la campagne parent sont-ils répartis sur les campagnes enfants ?**

En fait, les coûts seront directement tirés d&#39;une seule campagne, peu importe la relation parent-enfant. Nous vous conseillons d’imputer le coût aux campagnes enfants, ainsi qu’aux dates de la campagne, puis d’utiliser la campagne parent comme campagne parapluie lorsque la campagne parent ne serait pas activée pour les points de contact.

**Comment puis-je modifier le coût pour un mois en [!DNL Marketo Measure] ?**

Comme nous comptons sur le CRM comme seule source de vérité, tous les changements doivent être effectués dans le CRM. Une fois la campagne importée par [!DNL Marketo Measure], les valeurs de la campagne ne sont plus modifiables dans [!DNL Marketo Measure] ni dans le fichier CSV.

**Dans quel scénario une campagne apparaîtrait-elle dans le tableau Dépenses marketing, puis n’apparaîtrait plus ?**

Nous continuons à exiger que les trois champs clés aient une valeur : Date de début, Date de fin et Coût. Par défaut, nous importons uniquement les campagnes dont la valeur est supérieure à 0 $. Idéalement, nous devrions importer les campagnes où existe un $0 explicite et ne pas importer celles qui sont laissées vides, mais l’API Salesforce les importe toutes les deux en tant que $0, quelle que soit la valeur. De plus, si la valeur Activer Buyer Touchpoint passe de « Tout inclure » ou « Inclure les réponses » à « Tout exclure », nous supprimons la campagne et le coût du tableau Dépenses marketing .

**Quel coût serait prioritaire si une ligne était déjà téléchargée à partir du CRM et que j’en saisissais une autre dans le fichier CSV avec le même identifiant de campagne ?**

Bien que vous puissiez charger le fichier avec succès, [!DNL Marketo Measure] n’utiliserez pas cette ligne, car nous avons déjà un ID de campagne avec la même valeur qui a été automatiquement extrait de l’intégration.

**Comment suggéreriez-vous que nous apportions les coûts de nos campagnes numériques que nous avons mises en place dans le CRM ?**

Comme notre javascript [!DNL Marketo Measure] effectue déjà le suivi de l’activité web à partir de votre site, nous vous déconseillons de synchroniser les campagnes qui effectuent le suivi des membres de la campagne à partir de formulaires web ou d’autres activités de site, car cela doublera le nombre de contacts. Pour cette raison, vous pouvez continuer à utiliser l’option Chargement de CSV dans les dépenses marketing pour suivre ces coûts en ligne/numériques si nous ne sommes pas déjà intégrés à cette plateforme (c’est-à-dire Twitter, Adroll).
