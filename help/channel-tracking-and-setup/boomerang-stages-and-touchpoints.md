---
description: Conseils sur les étapes de boomerang et les points de contact pour les utilisateurs de Marketo Measure
title: Étapes et points de contact de boomerang
exl-id: e58169a3-3637-4878-8a0e-1920d873ff52
feature: Boomerang, Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 1%

---

# Étapes et points de contact de boomerang {#boomerang-stages-and-touchpoints}

>[!AVAILABILITY]
>
>La fonction Boomerang est uniquement activée pour les clients de niveau 2 et 3. Pour demander un niveau de compte supérieur, contactez l’équipe du compte Adobe (votre gestionnaire de compte).

[!DNL Marketo Measure] a lancé la fonction d’évaluation Boomerang ! La fonction Phase de boomerang a été créée pour offrir une meilleure visibilité sur le parcours du client pour [!DNL Marketo Measure] clients ayant de longs cycles de vente. Cette fonctionnalité permet aux spécialistes marketing de créer des points de contact pour toutes les transitions d’étape qui se produisent dans le parcours d’opportunité, par exemple lorsqu’un contact MQL passe à SAL, puis revient à l’étape MQL. Lorsque les contacts « repassent à l’étape MQL » ou « repassent à l’étape MQL », le MQL est considéré comme une étape de boomerang. La fonction Phase de boomerang fonctionne avec les étapes personnalisées [!DNL Marketo Measure].

## Fonctionnement De Cette Fonctionnalité {#what-this-feature-does}

* Crée un point de contact « boomerang » pour toutes les transitions d’étape qui se produisent dans le parcours d’une opportunité
* Effectue le suivi des transitions répétées entre chaque étape personnalisée (par exemple, lorsqu’un MQL de contact passe à SAL, puis revient à l’étape MQL)
* Permet de spécifier le nombre et l’ensemble de transitions d’étape à inclure dans l’opportunité (par exemple, Les 10 premiers MQL OU les 5 derniers MQL)
* Si vous êtes un utilisateur de modèle personnalisé, vous pouvez déterminer la pondération d’attribution et le crédit en pourcentage que vous souhaitez affecter à chacune de ces étapes (par exemple, Désigner le poids d’attribution à la première ou à la dernière occurrence MQL ou répartir équitablement le poids d’attribution entre toutes les occurrences)

>[!NOTE]
>
>[Instructions sur la configuration des étapes de boomerang](/help/channel-tracking-and-setup/setting-up-boomerang-stages.md).

## À quoi ressemblent les étapes et les points de contact de Boomerang dans votre CRM {#what-boomerang-stages-and-touchpoints-look-like-in-your-crm}

Sans les étapes Boomerang (l’« avant »), vous ne voyez que le dernier point de contact MQL ou SQL associé à un enregistrement Lead/Contact.

![Sans les étapes de boomerang (l’« avant »), seul le MQL le plus récent s’affiche](assets/boomerang-stages-18.png)

Avec les étapes et les points de contact Boomerang, vous voyez les points de contact qui se produisent pour chaque transition d’étape. La convention d’affectation des noms de ces points de contact boomerang est la suivante :

**[Nom de l’étape]-00.**

En reprenant l’exemple ci-dessous, ce compte [!DNL Marketo Measure] a inclus MQL et SQL dans ses étapes de boomerang et a choisi d’afficher 2 points de contact de boomerang par étape.

![Dans l’exemple ci-dessous, ce compte Marketo Measure a inclus MQL](assets/boomerang-stages-19.png)

**MQL-01** est la première transition d’étape MQL.

La valeur numérique à la position du point de contact indique l’ordre dans lequel la transition d’étape s’est produite. Le dernier point de contact de boomerang doit être marqué comme suit :

MQL-02 **(dernier)**

## Modification Des Données Existantes Par Les Étapes De Boomerang {#how-boomerang-stages-change-your-existing-data}

Impact des phases de boomerang :

**Attribution par canal**

* Étant donné que [!DNL Boomerang Stages] crée plus de points de contact, cela modifie la manière dont l’attribution est répartie entre les points de contact qui existent actuellement dans vos données. Par conséquent, cela peut signifier que la valeur des revenus se déplace entre les canaux marketing. Prenez cela en compte avant d’implémenter [!DNL Boomerang stages] ou contactez votre gestionnaire de compte pour plus d’informations.

**Tous les rapports qui utilisent « est égal à [Position du point de contact] »**

* Les phases de boomerang introduisent de nouvelles positions de point de contact dans vos données. [!DNL Marketo Measure] modifie le format de la position du point de contact afin d’inclure l’occurrence de l’étape, comme « MQL-01 » ou « MQL-05 (dernier) ». Dans cet exemple, les étapes de boomerang affectent tous les rapports qui utilisent « La position du point de contact est égale à MQL ». Pour ajuster ces rapports, le filtre doit utiliser l’opérateur « contains » à la place.

## Questions fréquentes {#faq}

**Combien de phases de boomerang puis-je inclure dans mon modèle d’attribution ?**

Vous pouvez sélectionner jusqu’à 15 étapes.

**Q : Combien de points de contact « boomerang » puis-je avoir par étape ?**

Vous pouvez sélectionner jusqu’à dix points de contact de boomerang par étape.

**Q : Pourquoi y a-t-il une limite de dix boomerangs par étape ?**

[!DNL Marketo Measure] doit limiter le nombre d’étapes pour garder les temps de traitement sous contrôle. Si vous choisissez d’inclure les 15 étapes de boomerang dans votre modèle d’attribution et 10 points de contact de boomerang par étape, vous pouvez éventuellement avoir plus de 150 points de contact par enregistrement Lead/Contact.

**Q : J&#39;ai Data Warehouse. Est-ce que j’obtiens toutes les données ou est-ce que la limite de Boomerang Stages s’applique également à moi ?**

La limite s’applique à Data Warehouse et aux CRM en raison des limites de traitement que [!DNL Marketo Measure] a mises en place. Data Warehouse verra également la limite de dix points de contact par étape.

**Q : Quel est l’avantage d’utiliser les étapes de boomerang avec la modélisation personnalisée ?**

L’utilisation des étapes [!UICONTROL Boomerang] avec la modélisation personnalisée vous permet d’attribuer une pondération d’attribution aux points de contact [!UICONTROL Boomerang], ce qui attribue un crédit de chiffre d’affaires à ces étapes.

Sans modélisation personnalisée, [!DNL Marketo Measure] crée des points de contact pour chaque transition de boomerang et d’étape, mais n’attribue aucun crédit d’attribution à ces points de contact. Les seuls points de contact de boomerang qui reçoivent des crédits d’attribution sont les points de contact d’envoi. Sans modèle personnalisé, les points de contact [!DNL Boomerang] sont considérés comme identiques à une « touche intermédiaire » et reçoivent un crédit d’attribution en conséquence.
