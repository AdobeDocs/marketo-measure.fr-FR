---
unique-page-id: 18874710
description: Suppression des points de contact et suppression des points de contact - [!DNL Marketo Measure]
title: Suppression et retrait des points de contact
exl-id: 201af648-6525-4a80-a7e5-3cbeeb1670b6
feature: Touchpoints
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 1%

---

# Suppression et retrait des points de contact {#touchpoint-removal-and-touchpoint-suppression}

Découvrez comment supprimer ou supprimer des points de contact qui répondent à des critères spécifiques de votre CRM. Cela peut s’avérer utile pour libérer de l’espace de données si vous avez des limites de stockage de données [!DNL Salesforce].

Il existe une différence clé entre les règles de suppression du point de contact et les règles de suppression du point de contact :

* Retrait du point de contact : [!DNL Marketo Measure] purge (c’est-à-dire supprime) tous les points de contact de votre CRM qui correspondent aux critères de la règle. Les données _peuvent_ faire l&#39;objet de rapports dans le tableau de bord du retour sur investissement [!DNL Marketo Measure], mais ne sont plus dans le CRM.
* Suppression des points de contact : similaire à la suppression des points de contact, mais les données ne peuvent PAS être consignées dans le tableau de bord du retour sur investissement.

Avant de commencer à créer des règles de suppression/suppression de points de contact, il est conseillé de partager votre plan de mise en oeuvre avec votre équipe marketing et d’opérations commerciales. Vous devriez déjà avoir une idée des types ou valeurs à supprimer. Voici quelques cas d’utilisation courants :

* Supprimer les points de contact des opportunités perdues fermées
* Suppression de points de contact de pistes très anciennes
* Suppression de points de contact de pistes non qualifiées

Une fois les règles enregistrées, [!DNL Marketo Measure] nettoie et redistribue votre modèle d’attribution. Cela signifie que les jalons et les positions changeront et que le crédit d’attribution de votre canal changera ! Cela modifiera vos données. Contactez votre gestionnaire de succès si vous avez besoin d’aide.

`1)` Il existe deux sections pour les paramètres de suppression/suppression. Vous avez la possibilité de le configurer pour les points de contact des acheteurs (Leads et contacts) ou les points de contact d’attribution des acheteurs (contacts, opportunités et comptes).

Commencez par ajouter une règle et sélectionnez le champ qui définira vos critères.

Effectuez une sélection dans une liste d’ Opérateurs qui se rapportent au prochain ensemble de valeurs que vous allez ajouter dans la colonne suivante.

![](assets/1-1.png)

>[!TIP]
>
>Pour ajouter plusieurs valeurs dans un champ, utilisez l’opérateur &quot;correspond à n’importe quel&quot; avec des virgules séparant chaque valeur.

>[!TIP]
>
>Pour comptabiliser une valeur vide ou NULL dans un champ, laissez simplement la zone [!UICONTROL Valeur] vide. Cela prend en compte des scénarios tels que l’évaluation par rapport à un point de contact sans URL de formulaire.

>[!NOTE]
>
>Les champs de formule ne peuvent pas être utilisés dans vos règles et n’apparaîtront pas dans la liste de sélection. Comme les formules sont calculées en arrière-plan et ne modifient pas d’enregistrement, [!DNL Marketo Measure] ne peut pas détecter si un enregistrement correspond ou non à une règle.

`2)` Ajoutez des règles au sein du même groupe pour utiliser la logique &quot;AND&quot; dans votre instruction.
Vous pouvez également ajouter de nouvelles instructions en dehors du groupe pour utiliser la logique &quot;OU&quot; dans votre instruction.

![](assets/2.png)

`3)` Si vos règles deviennent complexes et que vous devez recréer des groupes et apporter de petites modifications à chaque instruction, utilisez l’option [!UICONTROL Clone] pour rendre les choses plus simples.

![](assets/3.png)

Si vous faites une erreur, ne vous inquiétez pas. Vous pouvez également supprimer des lignes individuelles de votre instruction ou des groupes complets.

![](assets/4.png)

`4)` Configurez des règles pour les points de contact d’attribution si vous souhaitez qu’ils soient appliqués aux deux objets. Notre flexibilité vous permet de définir des règles pour un objet ou les deux objets et peut choisir de les configurer pour les deux s’ils s’appliquent.

![](assets/5.png)

Pour terminer, [!UICONTROL Enregistrez et traitez] vos règles. Si vous effectuez de nombreuses modifications, veillez à enregistrer vos modifications en cours de route. [!DNL Marketo Measure] ne commencera pas réellement à supprimer vos points de contact tant que vous n’aurez pas cliqué sur
[!UICONTROL **Enregistrer et traiter**].

| **Opérateur** | **Cas d’utilisation** |
|---|---|
| Est égal à | Valeur unique : correspondance exacte |
| contient | Valeur unique : contient la valeur |
| Correspond à n’importe quel | Plusieurs valeurs - Correspondance exacte |
| Correspond à n’importe quel (contient) | Plusieurs valeurs - &#42;value&#42;, &#42;value, &#42;value&#42; |

Pour les clients utilisant Dynamics qui souhaitent configurer des règles de suppression en fonction de l’état et/ou du code d’état, nous avons besoin de la mise en forme suivante lors de la configuration de la règle : `[Object].Statecode` est égal/différent de `[Status Value]`. Par exemple, si le Statecode dans Dynamics indique &quot;1&quot; sur un contact et que l’état indique &quot;Inactif&quot;, et que vous souhaitez supprimer tous ces contacts, le format suivant serait incorrect pour votre règle de suppression : Contact.Statecode est égal à 1. Au lieu de cela, vous souhaitez utiliser le format suivant : puisque Statecode et Status fonctionnent comme une paire, [!DNL Marketo Measure] lit la valeur de Status dans notre interrogation : Contact.Statecode est égal à Inactif.
