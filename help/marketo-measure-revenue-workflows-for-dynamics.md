---
description: Workflows pour aligner le chiffre d’affaires Dynamics et fermer les champs de date pour la création de rapports Marketo Measure
title: '[!DNL Marketo Measure] des workflows de chiffre d’affaires pour Dynamics'
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
feature: Microsoft Dynamics
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# [!DNL Marketo Measure] des workflows de chiffre d’affaires pour Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Partie 1 : Revenus estimés par rapport aux revenus réels {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] pointe vers un champ de revenu standard prêt à l&#39;emploi (revenu réel), mais Dynamics a deux champs de revenu standard : revenu réel et revenu estimé. Pour que les revenus du pipeline soient disponibles dans le tableau de bord de découverte, un champ personnalisé et un workflow sont nécessaires pour capturer le montant correct à partir du champ Revenu estimé ou Revenu réel selon que l’opportunité est ouverte ou fermée (Confirmée).

Étape 1 : créer un champ de montant de l’opportunité personnalisé dans Dynamics

>[!NOTE]
>
>Tous les champs de chiffre d’affaires Dynamics ont un champ de base et un champ normal. Ignorer le champ de base.

Étape 2 : créez un workflow qui met à jour le champ de montant de l’opportunité personnalisé créé à l’étape 1 et le champ de montant de l’opportunité [!DNL Marketo Measure].

>[!NOTE]
>
>Nous ne pouvons pas pointer vers le champ Montant de l’opportunité [!DNL Marketo Measure] (bizible2_bizible_opportunité_amount) dans Découvrir avec des comptes Dynamics. Les clients Dynamics doivent créer un champ de montant de l’opportunité personnalisé vers lequel [!DNL Marketo Measure] pointer dans Discover. Une fois l’opération terminée, le client ou la cliente doit créer un workflow qui met à jour **à la fois** le montant de l’opportunité [!DNL Marketo Measure] (bizible2_bizible_opportunité_amount) **et** le champ du montant de l’opportunité personnalisé. Le champ [!DNL Marketo Measure] le montant de l’opportunité est fourni avec le package, mais un champ personnalisé doit être créé.

Instructions de workflow de montant :

**#1 DE WORKFLOW** : Opportunité - Mettre à jour [!DNL Marketo Measure] champ Montant de l’opportunité et champ personnalisé = Revenu estimé

Ce workflow s’exécute sur les opportunités ouvertes chaque fois que le revenu estimé change et met à jour le champ [!DNL Marketo Measure] le montant de l’opportunité et votre champ personnalisé pour qu’ils soient égaux au champ Revenu estimé . Le workflow doit être défini pour s’exécuter en « temps réel », mais il peut également être exécuté « à la demande » pour mettre à jour les opportunités ouvertes.

Indiquez à votre point de contact [!DNL Marketo Measure] le nom du champ du montant de l’opportunité personnalisé. Ils mettent à jour les paramètres d’opportunité de l’application [!DNL Marketo Measure] pour inclure le nom du champ du montant de l’opportunité personnalisé. Cette option indique à Découvrir le champ à utiliser dans le compte rendu des performances.

**#2 WORKFLOW** : Opportunité - Mettre à jour [!DNL Marketo Measure] champ Montant de l’opportunité et champ personnalisé = Revenu réel

Ce workflow se déclenche lorsqu’un utilisateur ferme une opportunité et met à jour le champ [!DNL Marketo Measure] du montant de l’opportunité ainsi que votre champ personnalisé avec le revenu réel ajouté au formulaire de fermeture de l’opportunité avant que celle-ci ne se verrouille comme fermée.

## Partie 2 : Date de fermeture estimée par rapport à date de fermeture réelle {#part-estimated-close-date-vs-actual-close-date}

Par défaut, les données de chiffre d’affaires de pipeline ne sont pas disponibles dans le tableau de bord, car Dynamics comporte deux champs de date de fermeture du stock : Date de fermeture estimée et Date de fermeture effective. [!DNL Marketo Measure] ne peut pointer que vers un seul champ de date de fermeture dans le tableau de bord et il pointe vers la date de fermeture réelle.

Si les opportunités ouvertes ne contiennent aucune donnée dans le champ Date de clôture réelle , aucune donnée n’est présente dans le tableau de bord des opportunités ouvertes. Cela dit, un workflow basé sur l’étape d’opportunité est nécessaire pour prendre en charge les deux champs de date.

1. Créez un champ de date de fermeture personnalisé sur l’objet d’opportunité ([!DNL Marketo Measure] la date de fermeture personnalisée).
1. Créez un workflow pour mettre à jour le champ Date de fermeture personnalisée [!DNL Marketo Measure] avec la date de la date de fermeture estimée ou de la date de fermeture réelle, selon que l’opportunité est ouverte ou fermée (le workflow doit être enregistré pour s’exécuter en temps réel, mais il doit être exécuté « à la demande » au moins une fois pour mettre à jour toutes les opportunités ouvertes actuelles).
1. Testez le workflow et vérifiez qu’il fonctionne.
1. Le client doit fournir le nom d’API de date de fermeture personnalisé à [!DNL Marketo Measure].
1. [!DNL Marketo Measure] de mettre à jour les paramètres de l’application [!DNL Marketo Measure] pour pointer vers le champ Date de fermeture personnalisée [!DNL Marketo Measure] dans le tableau de bord.

   Une fois les étapes ci-dessus terminées, exécutez les workflows pour mettre à jour le champ Montant de l’opportunité de [!DNL Marketo Measure] personnalisée et le champ Date de fermeture personnalisée [!DNL Marketo Measure] sur vos opportunités historiques afin de refléter les données correctes. Les champs modifiés le/par seront probablement modifiés. Vous devez donc vérifier auprès de votre équipe si cela présente des problèmes.

Pour mettre à jour les opportunités closes...

1. Isolez les opportunités clôturées depuis la date de début de votre [!DNL Marketo Measure] jusqu’à ce que le workflow soit actif. Il s’agit du groupe d’opportunités historiques que vous devez mettre à jour via le workflow.
1. Exporter tous les enregistrements vers Excel.
1. Ouvrez le fichier Excel, activez le contenu.
1. Copiez les données de la date de fermeture réelle vers [!DNL Marketo Measure] date de fermeture personnalisée.
1. Copiez les données de revenu réel dans [!DNL Marketo Measure] montant de l’opportunité personnalisé **et** [!DNL Marketo Measure] montant de l’opportunité (il existe deux champs).
1. Enregistrez le fichier .
1. Importer un fichier. Dynamics le reconnaîtra comme un fichier avec des enregistrements existants à mettre à jour.
1. Recherchez les échecs sur le fichier d’importation.

>[!NOTE]
>
>Les workflows décrits dans ce document ne sont qu’une façon de mettre à jour les champs afin que [!DNL Marketo Measure] puissiez afficher les données correctes dans Discover. Si vous avez une autre façon d&#39;accomplir la même tâche, vous pouvez y aller. En gros, ce dont nous avons besoin de leur part, c&#39;est d&#39;un processus qui accomplirait ce qui suit :
>
> * Si Opportunité = Ouverture, mettez à jour le champ personnalisé de date de fermeture, le champ personnalisé de montant de l’opportunité et [!DNL Marketo Measure] champ de montant de l’opportunité pour qu’ils soient égaux à Date de fermeture estimée et Revenu estimé, respectivement.
> * Si Opportunité = close et confirmée, mettez à jour le champ personnalisé de date de clôture, le champ personnalisé de montant d’opportunité et [!DNL Marketo Measure] champ de montant d’opportunité pour qu’ils soient égaux à Date de clôture effective et Revenu réel, respectivement.
