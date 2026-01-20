---
unique-page-id: 18874710
description: Suppression des points de contact et suppression des points de contact - [!DNL Marketo Measure]
title: Suppression et retrait des points de contact
exl-id: 201af648-6525-4a80-a7e5-3cbeeb1670b6
feature: Touchpoints
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 2%

---

# Suppression et retrait des points de contact {#touchpoint-removal-and-touchpoint-suppression}

Découvrez comment supprimer ou supprimer de votre CRM des points de contact qui répondent à des critères spécifiques. Cela peut s’avérer utile pour libérer de l’espace de données si vous disposez de limites de stockage de données [!DNL Salesforce].

Il existe une différence majeure entre les règles de suppression de point de contact et les règles de suppression de point de contact :

* Suppression de points de contact : [!DNL Marketo Measure] purgera (c’est-à-dire supprimera) tous les points de contact de votre CRM qui correspondent aux critères de la règle. Les données _peuvent_ sont signalées dans le tableau de bord du retour sur investissement [!DNL Marketo Measure], mais plus dans le CRM.
* Suppression de point de contact : similaire à la suppression de point de contact, mais les données NE PEUVENT PAS être consignées dans le tableau de bord du retour sur investissement.

Avant de commencer à créer des règles de suppression de point de contact, il est recommandé de partager votre plan de mise en œuvre avec votre équipe marketing et commerciale. Vous devriez déjà avoir une idée des types ou valeurs à supprimer. Voici quelques cas d’utilisation courants :

* Supprimer les points de contact des opportunités fermées et perdues
* Supprimer des points de contact d’anciens prospects
* Supprimer les points de contact des leads non qualifiés

Une fois les règles enregistrées, [!DNL Marketo Measure] nettoiera et redistribuera votre modèle d’attribution. Cela signifie que les jalons et les positions changeront, et que le crédit d’attribution de votre canal changera ! Cela modifiera vos données. Si vous avez besoin d’aide, contactez votre responsable du succès client.

`1)` Il existe deux sections pour les paramètres de suppression. Vous avez la possibilité de le configurer pour les points de contact d’acheteur (leads et contacts) ou les points de contact d’attribution d’acheteur (contacts, opportunités et comptes).

Commencez par ajouter une règle et par sélectionner le champ qui définira vos critères.

Faites votre choix dans une liste d’opérateurs qui se rapportent au prochain ensemble de valeurs, que vous ajouterez dans la colonne suivante.

![](assets/1-1.png)

>[!TIP]
>
>Pour ajouter plusieurs valeurs dans un champ, utilisez l’opérateur « correspond à n’importe quelle » avec des virgules séparant chaque valeur.

>[!TIP]
>
>Pour tenir compte d’une valeur vide ou NULL dans un champ, laissez simplement la zone [!UICONTROL Valeur] vide. Cela prend en compte des scénarios tels que l’évaluation par rapport à un point de contact sans URL de formulaire.

>[!NOTE]
>
>Les champs de formule ne peuvent pas être utilisés dans vos règles et n&#39;apparaîtront pas dans la liste de sélection. Étant donné que les formules calculent en arrière-plan et ne modifient pas un enregistrement, [!DNL Marketo Measure] ne pouvez pas détecter si un enregistrement correspond ou non à une règle.

`2)` Ajoutez des règles au sein du même groupe pour utiliser la logique « AND » dans votre instruction.
Vous pouvez également ajouter de nouvelles instructions en dehors du groupe pour utiliser la logique « OR » dans votre instruction.

![](assets/2.png)

`3)` Si vos règles deviennent complexes et que vous devez recréer des groupes et apporter de petites modifications à chaque instruction, utilisez l’option [!UICONTROL Cloner] pour simplifier les choses.

![](assets/3.png)

Si vous faites une erreur, ne vous inquiétez pas. Vous pouvez également supprimer des lignes individuelles de votre instruction ou des groupes complets.

![](assets/4.png)

`4)` Configurez des règles pour les points de contact d’attribution de l’acheteur si vous souhaitez les appliquer aux deux objets. Notre flexibilité vous permet de définir des règles pour un objet ou les deux et peut choisir de les configurer pour les deux s&#39;ils s&#39;appliquent.

![](assets/5.png)

Pour terminer, [!UICONTROL  Enregistrer et traiter ] vos règles. Si vous apportez de nombreuses modifications, veillez à les enregistrer au fur et à mesure. [!DNL Marketo Measure] ne commencera pas réellement à supprimer vos points de contact avant que vous ne cliquiez
[!UICONTROL **Enregistrer et traiter**].

| **Opérateur** | **Exemple d’utilisation** |
|---|---|
| Est égal à | Valeur unique - correspondance exacte |
| Contient | Valeur unique - contient la valeur |
| Correspond à l’un des | Valeurs multiples - Correspondance exacte |
| Correspond À N’Importe Quel (Contient) | Valeurs multiples : &#42;value&#42;, &#42;value, &#42;value&#42; |

Pour les clients utilisant Dynamics qui souhaitent configurer des règles de suppression basées sur Status et/ou Statecode, la mise en forme suivante est nécessaire lors de la configuration de la règle : `[Object].Statecode` est égal/différent de `[Status Value]`. Par exemple, si le code d&#39;état dans Dynamics indique « 1 » sur un contact et que le statut indique « Inactif », et que vous souhaitez supprimer tous ces contacts, le format suivant serait incorrect pour votre règle de suppression : Contact.Statecode est égal à 1. Au lieu de cela, vous devriez utiliser le format suivant : comme Statecode et Status fonctionnent deux à deux, [!DNL Marketo Measure] lit la valeur de Status dans notre requête : Contact.Statecode est égal à Inactif.
