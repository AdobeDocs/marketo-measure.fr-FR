---
unique-page-id: 18874688
description: Coûts de la campagne CRM - [!DNL Marketo Measure]
title: Coûts de campagne CRM
exl-id: d967cabe-b9f1-4ea1-a81b-e4484c703ecf
feature: Spend Management
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '1187'
ht-degree: 0%

---

# Coûts de campagne CRM {#crm-campaign-costs}

La plupart des clients [!DNL Marketo Measure] utilisent des campagnes CRM pour effectuer le suivi des activités marketing hors ligne. Les marketeurs qui utilisent ces campagnes contrôlent également les coûts au sein du CRM. Cette fonctionnalité permet aux marketeurs de lire plus facilement ces coûts et de les appliquer aux dépenses marketing rapportées dans [!DNL Marketo Measure]. [!DNL Marketo Measure] À ce jour, les clients ont dû saisir manuellement les coûts pour chaque campagne par mois, mais avec les informations nécessaires fournies à [!DNL Marketo Measure], les utilisateurs peuvent automatiser ce processus afin que les marketeurs puissent passer plus de temps à analyser leurs dépenses et leur retour sur investissement.

## Disponibilité {#availability}

Cette fonctionnalité est disponible pour tous les clients [!DNL Salesforce] et Dynamics.

## Fonctionnement {#how-it-works}

[!DNL Marketo Measure] commence par rechercher les campagnes qui ont été &quot;activées&quot; pour les points de contact. Il existe donc une règle de synchronisation de campagne correspondante qui a été créée, ou la valeur Activer les points de contact de l’acheteur est &quot;Inclure tous les membres de campagne&quot; ou &quot;Inclure les membres de campagne &quot;réactifs&quot;. En outre, [!DNL Marketo Measure] doit importer les valeurs correctes et savoir distribuer les coûts. Par conséquent, nous exigeons que les champs suivants contiennent une valeur :

**[!DNL Salesforce]** : `ActualCost`, `StartDate`, `EndDate`

**[!DNL Microsoft Dynamics]** : `totalactualcost`, `actualstart`, `actualend`

Si une valeur est manquante dans l’un des trois champs, [!DNL Marketo Measure] n’importera pas les coûts. Vous pouvez corriger ce problème en mettant à jour l&#39;enregistrement Campaign dans le CRM. Les coûts ne sont pas importés s’ils sont définis sur 0 $, car [!DNL Salesforce] traite vide et 0 $ comme le même.

Pour [!DNL Marketo Measure], afin de déterminer la distribution d’une campagne sur plusieurs mois, les dates de début et de fin de la campagne sont utilisées pour répartir le montant uniformément par jour.

![](assets/1.jpg)

Dans cet exemple, une campagne dure 109 jours. Avec un coût total de 18 000 $, les dépenses quotidiennes s’élèvent donc à environ 165,14 $.

En fonction du nombre de jours par mois, nous obtenons ces totaux mensuels, comme vous pouvez le voir dans le tableau :

Juillet 2018 : (18,000/109) x 31 = 5 119,27 $

Août 2018 : (18,000/109) x 31 = 5 119,27 $

Septembre 2018 : (18,000/109) x 30 = 4 954,13 $

Oct 2018 : (18,000/109) x 17 = 2 807,34 $

## Historique des dépenses signalées {#historical-reported-spend}

Si vous avez renseigné des dépenses pour des campagnes qui ont été suivies dans le passé et qui ont été mappées à une campagne CRM, cela ne remplace pas les coûts que vous avez renseignés. Si la même campagne dans le CRM est modifiée, elle l’ignore et donne la priorité aux modifications que vous avez précédemment apportées au transfert CSV.

Si vous préférez que nous prenions le coût de la campagne CRM à partir de maintenant, modifiez la valeur du fichier CSV à 0 $, ce qui annule l’entrée. La prochaine fois que les traitements seront exécutés pour importer les coûts, les rapports précédemment modifiés seront récupérés.

## Campagnes sans points de contact {#campaigns-with-no-touchpoints}

De nombreux spécialistes du marketing choisissent de signaler les dépenses marketing liées aux campagnes CRM qui n’ont généré aucun point de contact ou qui n’ont aucun membre de campagne à des fins de suivi des dépenses. Tant que les trois champs sont renseignés (date de début, date de fin, coût) et que la campagne est activée pour les points de contact, [!DNL Marketo Measure] récupère ce coût, même si aucun point de contact ne lui est associé.

Cela peut s’avérer utile pour effectuer le suivi des dépenses sur les coûts ou outils marketing excédentaires afin de les cumuler dans vos calculs de retour sur investissement.

## Synchronisation du programme Marketo {#marketo-program-sync}

Si vous intégrez des programmes Marketo dans le CRM en tant que campagnes, assurez-vous que les champs CRM requis sont bien configurés pour la Date de début, la Date de fin et le Coût de la période. Puisqu’il n’existe aucun mapping vers le champ Activer les points de contact des acheteurs , vous devez tout de même activer ces campagnes pour que les coûts puissent être relevés.

## Modification des coûts {#editing-the-costs}

Une fois qu’une campagne est importée à partir du CRM, elle est traitée de la même manière qu’un fournisseur d’annonces API et n’apparaîtra pas dans le fichier CSV pour apporter des modifications aux coûts.

Toute modification du coût ou de la distribution doit être effectuée dans le CRM afin que nous puissions pointer vers un seul point de vérité.

## Questions fréquentes {#faq}

**J’ai apporté une modification à ma campagne. Quand dois-je m’attendre à voir les modifications dans la table des dépenses marketing ou dans mes rapports ?**

3-4 heures

**J’ai complété la date de début, la date de fin et le coût, mais pourquoi mes coûts ne s’affichent toujours pas dans [!DNL Marketo Measure] ?**

Vérifiez que la valeur &quot;Activer Buyer Touchpoint&quot; est définie sur &quot;Inclure tous les membres de campagne&quot; ou au moins &quot;Inclure les membres de campagne &quot;Réactifs&quot;, ou que vous avez créé une règle de synchronisation de campagne personnalisée qui inclut cette campagne. Si vous l’avez confirmé et que la campagne ne s’affiche toujours pas, contactez l’ [assistance Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} afin que nous puissions vérifier que vos campagnes sont correctement importées.

**Je dois modifier la répartition de ma campagne pour pouvoir la peser plus lourd dans certains mois. Comment faire ?**

La répartition des coûts est uniquement basée sur une répartition uniforme, de la date de début à la date de fin. Malheureusement, nous ne pouvons pas le changer pour que vos coûts aient un poids différent des dates prévues. Vous pouvez le contrôler en ajustant les dates de début et de fin de votre campagne, car chaque jour du mois compte.

**J’ai des coûts configurés dans ma campagne parente. Comment les campagnes pour enfants reçoivent les coûts de la campagne parente ?**

En fait, la façon dont les coûts seront entraînés sera directement à partir d&#39;une seule campagne, indépendamment de toute relation Parent ou Enfant. Nous vous conseillons d’utiliser le coût des campagnes pour enfants, ainsi que les dates de la campagne, puis d’utiliser le Parent comme campagne parapluie où la campagne parent n’est pas activée pour les points de contact.

**Comment puis-je modifier le coût d&#39;un mois dans [!DNL Marketo Measure] ?**

Puisque nous nous appuyons sur le CRM comme source unique de vérité, tous les changements doivent être apportés dans le CRM. Une fois la campagne importée par [!DNL Marketo Measure], les valeurs de Campaign ne sont pas modifiables dans [!DNL Marketo Measure] ou dans le fichier CSV.

**Dans quel scénario une campagne apparaîtra-t-elle dans la table des dépenses marketing, puis n&#39;apparaîtra-t-elle plus ?**

Nous continuons à exiger que les trois champs clés aient une valeur : Date de début, Date de fin et Coût. Par défaut, nous importons uniquement les campagnes dont la valeur est supérieure à 0 $. Dans l’idéal, nous importerions les campagnes pour lesquelles un montant explicite de 0 $ est indiqué, sans les importer si rien n’est indiqué, mais l’API Salesforce les importe à la fois comme 0 $, quelle que soit la valeur. En outre, si la valeur Activer Buyer Touchpoint passe de &quot;Inclure tout&quot; ou &quot;Inclure &quot;Répondu&quot; à &quot;Exclure tout&quot;, nous supprimons la campagne et le coût de la table des dépenses marketing.

**Quel coût serait prioritaire si une ligne était déjà téléchargée à partir du CRM et que je suis entré dans une autre ligne du fichier CSV avec le même identifiant de campagne ?**

Bien que vous puissiez transférer le fichier avec succès, [!DNL Marketo Measure] n’utilisera pas cette ligne, car nous avons déjà un identifiant de campagne avec la même valeur qui a été automatiquement extraite de l’intégration.

**Comment suggéreriez-vous que nous le fassions payer par nos campagnes numériques que nous configurons dans le CRM ?**

Comme notre JavaScript [!DNL Marketo Measure] effectue déjà le suivi de l’activité web à partir de votre site, nous vous déconseillons de synchroniser les campagnes qui effectuent le suivi des membres de campagne à partir de formulaires web ou d’autres activités du site, car cela comptabilisera deux fois les touches. Pour cette raison, vous pouvez continuer à utiliser l’option Téléchargement CSV dans les dépenses marketing pour effectuer le suivi de ces coûts en ligne/numériques si nous ne sommes pas déjà intégrés à cette plate-forme (c’est-à-dire, Twitter, Adroll).
