---
unique-page-id: 37356132
description: "[!DNL Marketo Measure] Workflows des recettes pour Dynamics - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] Workflows des recettes pour Dynamics"
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# [!DNL Marketo Measure] Workflows des recettes pour Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Partie 1 : Recettes estimées par rapport aux recettes réelles {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] pointe vers un champ de recettes standard prêt à l’emploi (Recettes réelles), mais Dynamics a deux champs de recettes standard : Recettes réelles et Recettes estimées. Pour que les recettes de pipeline soient disponibles dans le tableau de bord de Discover, un champ personnalisé et un workflow sont nécessaires pour capturer le montant correct des recettes estimées ou des recettes réelles selon que l’opportunité est ouverte ou fermée (gagnante).

Étape 1 : Créer un champ de montant d’opportunité personnalisé dans Dynamics

>[!NOTE]
>
>Tous les champs de recettes Dynamics ont un champ de base et un champ normal. Ignorez le champ de base.

Étape 2 : Créez un workflow qui met à jour le champ de montant d’opportunité personnalisé créé à l’étape 1 et le [!DNL Marketo Measure] Champ Montant de l&#39;opportunité.

>[!NOTE]
>
>Nous ne pouvons pas pointer vers le [!DNL Marketo Measure] Montant de l’opportunité (bizible2_bizible_occasion_amount) dans Discover avec des comptes Dynamics. Les clients Dynamics doivent créer un champ de montant d’opportunité personnalisé pour [!DNL Marketo Measure] pour pointer vers dans Discover. Une fois terminé, le client doit créer un workflow qui met à jour **both** la valeur [!DNL Marketo Measure] Quantité d’opportunité (bizible2_bizible_occasion_amount) **et** le champ montant personnalisé de l’opportunité. Le [!DNL Marketo Measure] Le champ Montant de l&#39;opportunité est fourni avec le package, mais un champ personnalisé doit être créé.

Instructions de workflow Amount :

**#1 DE WORKFLOW**: Opportunité - Mise à jour [!DNL Marketo Measure] Champ Montant de l&#39;opportunité et champ personnalisé = Recettes estimées

Ce workflow s’exécute à chaque fois que des opportunités sont ouvertes et que les recettes estimées changent et met à jour la variable [!DNL Marketo Measure] Montant de l&#39;opportunité et votre champ personnalisé pour égal au champ Recettes estimées . Le workflow doit être défini pour exécuter &quot;Temps réel&quot;, mais peut également être exécuté &quot;à la demande&quot; pour mettre à jour les opportunités ouvertes.

Fournissez les [!DNL Marketo Measure] point de contact avec le nom du champ montant personnalisé de l&#39;opportunité. Ils mettent à jour la variable [!DNL Marketo Measure] Paramètres d’opportunité de l’application pour inclure le nom du champ de montant d’opportunité personnalisé. Cela indique à Discover le champ à utiliser dans les rapports.

**#2 DE WORKFLOW**: Opportunité - Mise à jour [!DNL Marketo Measure] Champ Montant de l&#39;opportunité et champ personnalisé = Recettes réelles

Ce workflow s’exécute en temps réel. Elle se déclenche lorsqu’un utilisateur ferme une opportunité et met à jour la variable [!DNL Marketo Measure] Montant de l&#39;opportunité et votre champ personnalisé avec le champ Recettes réelles ajouté au formulaire Fermeture de l&#39;opportunité avant que l&#39;opportunité ne se bloque comme fermée.

## Partie 2 : Date de fermeture estimée par rapport à la date de fermeture réelle {#part-estimated-close-date-vs-actual-close-date}

Les données de recettes de pipeline prêtes à l’emploi ne seront pas disponibles dans le tableau de bord car, par défaut, Dynamics dispose de deux champs de date de fin de stock : Date de fermeture estimée et Date de fermeture réelle. [!DNL Marketo Measure] ne peut pointer que vers un champ de date de fermeture dans le tableau de bord ; nous pointons actuellement vers la Date de fermeture réelle.

Si les opportunités d’ouverture ne comportent aucune donnée dans le champ Date de fermeture réelle , aucune donnée n’est visible dans le tableau de bord pour les opportunités d’ouverture. Cela dit, un workflow est nécessaire en fonction de l’étape d’opportunité pour prendre en charge les deux champs de date.

1. Créez un champ Date de fermeture personnalisée sur l’objet d’opportunité (c.-à-d. [!DNL Marketo Measure] Date de fermeture personnalisée).
1. Créer un workflow pour mettre à jour la variable [!DNL Marketo Measure] Champ Date de fermeture personnalisée avec la date de fermeture estimée ou la date de fermeture réelle, selon que l’opportunité est ouverte ou fermée (le workflow doit être enregistré pour s’exécuter en temps réel, mais il doit être exécuté &quot;à la demande&quot; au moins une fois pour mettre à jour toutes les opérations d’ouverture actuelles).
1. Testez le workflow et vérifiez qu&#39;il fonctionne.
1. Le client doit fournir le nom de l’API Date de fermeture personnalisée à [!DNL Marketo Measure].
1. [!DNL Marketo Measure] pour mettre à jour la variable [!DNL Marketo Measure] paramètres de l’application pour pointer vers [!DNL Marketo Measure] Champ Date de fermeture personnalisée dans le tableau de bord.

   Une fois les étapes ci-dessus terminées, nous devrons exécuter des workflows pour mettre à jour les [!DNL Marketo Measure] le champ Montant d’Opp et la variable [!DNL Marketo Measure] Le champ Date de fermeture personnalisée présente vos opportunités historiques de refléter les données correctes. Les champs on/by modifiés seront probablement modifiés, de sorte que vous voudrez vérifier auprès de votre équipe si cela présente des problèmes.

Pour mettre à jour les opportunités fermées...

1. Isolez les opportunités qui ont été fermées depuis votre [!DNL Marketo Measure] date de démarrage jusqu’à ce que le workflow soit principal. Il s’agit du groupe d’opportunités historiques que vous devrez mettre à jour via un workflow.
1. Exportez tous les enregistrements vers Excel.
1. Ouvrez le fichier Excel, activez le contenu.
1. Copier les données de date de fermeture réelle [!DNL Marketo Measure] Date de fermeture personnalisée.
1. Copier les données sur les recettes réelles dans [!DNL Marketo Measure] Montant d’opportunité personnalisé **et** [!DNL Marketo Measure] Montant de l’opportunité (il existe deux champs).
1. Enregistrez le fichier.
1. Importez le fichier. Dynamics reconnaîtra qu’il s’agit d’un fichier avec des enregistrements existants à mettre à jour.
1. Recherchez les échecs dans le fichier d’importation.

>[!NOTE]
>
>Les workflows décrits dans ce document ne sont qu’une façon de mettre à jour les champs. [!DNL Marketo Measure] peut afficher les données correctes dans Discover. Si vous avez une autre façon d&#39;accomplir la même tâche, vous pouvez y aller. En gros, ce dont nous avons besoin, c&#39;est d&#39;une sorte de workflow qui réalise ce qui suit :
>
> * Si Opp = Ouverture, mettez à jour le champ de date de fermeture personnalisé, le champ de valeur opp personnalisée et [!DNL Marketo Measure] le champ montant de l’opp est égal à la Date de fermeture estimée et au Chiffre d’affaires estimé, respectivement.
> * Si Opp = Permis fermé, mettez à jour le champ de date de fermeture personnalisé, le champ de montant d’opp personnalisé et [!DNL Marketo Measure] le champ montant de l’opp est égal à Date de fermeture réelle et Recettes réelles, respectivement.

