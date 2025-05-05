---
unique-page-id: 37356132
description: "[!DNL Marketo Measure] Workflows des recettes pour Dynamics - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Workflows des recettes pour Dynamics"
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
feature: Microsoft Dynamics
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---

# [!DNL Marketo Measure] Workflows de recettes pour Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Partie 1 : Recettes estimées par rapport aux recettes réelles {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] pointe vers un champ de recettes standard prêt à l’emploi (Recettes réelles), mais Dynamics a deux champs de recettes standard : Recettes réelles et Recettes estimées. Pour que les recettes de pipeline soient disponibles dans le tableau de bord de Discover, un champ personnalisé et un workflow sont nécessaires pour capturer le montant correct des recettes estimées ou des recettes réelles selon que l’opportunité est ouverte ou fermée (gagnante).

Étape 1 : Créer un champ de montant d’opportunité personnalisé dans Dynamics

>[!NOTE]
>
>Tous les champs de recettes Dynamics ont un champ de base et un champ normal. Ignorez le champ de base.

Étape 2 : créez un workflow qui met à jour le champ de montant d’opportunité personnalisé créé à l’étape 1 et le champ [!DNL Marketo Measure] Montant d’opportunité.

>[!NOTE]
>
>Nous ne pouvons pas pointer vers le champ [!DNL Marketo Measure] Montant de l’opportunité (bizible2_bizible_opportunité_amount) dans Discover avec des comptes Dynamics. Les clients Dynamics doivent créer un champ de montant d’opportunité personnalisé pour [!DNL Marketo Measure] vers lequel pointer dans Discover. Une fois l’opération terminée, le client doit créer un workflow qui met à jour **à la fois** le [!DNL Marketo Measure] montant de l’opportunité (bizible2_bizible_opportunité_amount) **et** le champ de montant personnalisé de l’opportunité. Le champ [!DNL Marketo Measure] Montant de l’opportunité est fourni avec le package, mais un champ personnalisé doit être créé.

Instructions de workflow Amount :

**WORKFLOW #1** : Opportunité - Mettre à jour [!DNL Marketo Measure] Champ Montant de l’opportunité et champ personnalisé = Recettes estimées

Ce workflow s’exécute à chaque fois que des opportunités sont ouvertes. Le revenu estimé change et met à jour le champ [!DNL Marketo Measure] Montant de l’opportunité et votre champ personnalisé pour qu’il soit égal au champ Recettes estimées . Le workflow doit être défini pour exécuter &quot;Temps réel&quot;, mais peut également être exécuté &quot;à la demande&quot; pour mettre à jour les opportunités ouvertes.

Indiquez à votre point de contact [!DNL Marketo Measure] le nom du champ de montant d’opportunité personnalisé. Ils mettent à jour les paramètres d’opportunité de l’application [!DNL Marketo Measure] afin d’inclure le nom du champ de montant d’opportunité personnalisé. Cela indique à Discover le champ à utiliser dans les rapports.

**WORKFLOW #2&lbrace;1: Opportunity - Update [!DNL Marketo Measure] Opportunity Amount Field &amp; Custom Field = Revenus réels**

Ce workflow se déclenche lorsqu’un utilisateur ferme une opportunité et met à jour le champ [!DNL Marketo Measure] Montant de l’opportunité et votre champ personnalisé avec les Recettes réelles ajoutées au formulaire Fermeture de l’opportunité avant que l’opportunité ne se bloque comme fermée.

## Partie 2 : Date de fermeture estimée par rapport à la date de fermeture réelle {#part-estimated-close-date-vs-actual-close-date}

Les données de recettes de pipeline prêtes à l’emploi ne sont pas disponibles dans le tableau de bord car, par défaut, Dynamics dispose de deux champs de date de fin de stock : Date de fermeture estimée et Date de fermeture réelle. [!DNL Marketo Measure] ne peut pointer que vers un champ de date de fermeture du tableau de bord et pointe vers la Date de fermeture réelle.

Si les opportunités d’ouverture ne comportent aucune donnée dans le champ Date de fermeture réelle , le tableau de bord ne contient aucune donnée pour les opportunités d’ouverture. Cela dit, un workflow est nécessaire en fonction de l’étape d’opportunité pour prendre en charge les deux champs de date.

1. Créez un champ Date de fermeture personnalisée sur l’objet d’opportunité ([!DNL Marketo Measure] Date de fermeture personnalisée).
1. Créez un workflow pour mettre à jour le champ [!DNL Marketo Measure] Date de fermeture personnalisée avec la date à partir de la Date de fermeture estimée ou de la Date de fermeture réelle, selon que l&#39;opportunité est ouverte ou fermée (le workflow doit être enregistré pour s&#39;exécuter en temps réel, mais doit être exécuté &quot;à la demande&quot; au moins une fois pour mettre à jour toutes les opérations d&#39;ouverture actuelles).
1. Testez le workflow et vérifiez qu&#39;il fonctionne.
1. Le client doit fournir le nom de l’API Date de fermeture personnalisée à [!DNL Marketo Measure].
1. [!DNL Marketo Measure] pour mettre à jour les paramètres de l’application [!DNL Marketo Measure] afin qu’ils pointent vers le champ [!DNL Marketo Measure] Date de fermeture personnalisée dans le tableau de bord.

   Une fois les étapes ci-dessus terminées, exécutez les workflows pour mettre à jour le champ Montant d’Opp [!DNL Marketo Measure] personnalisé et le champ [!DNL Marketo Measure] Date de Fermeture personnalisée sur vos opportunités historiques de refléter les données correctes. Les champs on/by modifiés seront alors modifiés. Vérifiez donc auprès de votre équipe si cela présente des problèmes.

Pour mettre à jour les opportunités fermées...

1. Isolez les opportunités qui se sont fermées depuis la date de démarrage de votre [!DNL Marketo Measure] jusqu&#39;à ce que le workflow soit actif. Il s’agit du groupe d’opportunités historiques que vous devez mettre à jour via un workflow.
1. Exportez tous les enregistrements vers Excel.
1. Ouvrez le fichier Excel, activez le contenu.
1. Copiez les données Date de fermeture réelle dans [!DNL Marketo Measure] Date de fermeture personnalisée.
1. Copiez les données Recettes réelles dans [!DNL Marketo Measure] Montant d’opportunité personnalisé **et** [!DNL Marketo Measure] Montant d’opportunité (il existe deux champs).
1. Enregistrez le fichier.
1. Importez le fichier. Dynamics reconnaîtra qu’il s’agit d’un fichier avec des enregistrements existants à mettre à jour.
1. Recherchez les échecs dans le fichier d’importation.

>[!NOTE]
>
>Les workflows décrits dans ce document ne sont qu’une façon de mettre à jour les champs afin que [!DNL Marketo Measure] puisse afficher les données correctes dans Discover. Si vous avez une autre façon d&#39;accomplir la même tâche, vous pouvez y aller. Fondamentalement, ce dont nous avons besoin de la part d&#39;eux est une sorte de workflow qui effectue les opérations suivantes :
>
> * Si Opp = Ouverture, mettez à jour le champ Date de fermeture personnalisée, le champ Montant opp personnalisé et le champ [!DNL Marketo Measure] Montant opp afin d’obtenir respectivement la Date de fermeture estimée et le Chiffre d’affaires estimé.
> * Si Opp = Gagnant fermé, mettez à jour le champ de date de fermeture personnalisé, le champ de montant d’opp personnalisé et le champ de montant d’opp [!DNL Marketo Measure] pour qu’ils soient égaux respectivement à Date de fermeture réelle et Recettes réelles.
