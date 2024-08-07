---
unique-page-id: 18874558
description: Étapes et points de contact Boomerang - [!DNL Marketo Measure]
title: Étapes et points de contact de boomerang
exl-id: e58169a3-3637-4878-8a0e-1920d873ff52
feature: Boomerang, Touchpoints
source-git-commit: ea113b02b910fbc894311200aff83286636d4b32
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 1%

---

# Étapes et points de contact de boomerang {#boomerang-stages-and-touchpoints}

>[!AVAILABILITY]
>
>La fonction Boomerang n’est activée que pour les clients des niveaux 2 et 3. Pour demander un niveau de compte supérieur, contactez l’équipe Compte d’Adobe (votre gestionnaire de compte).

[!DNL Marketo Measure] a lancé la fonctionnalité Boomerang Stage ! La fonction d’évaluation Boomerang a été créée pour offrir une meilleure visibilité sur le parcours du client pour les clients [!DNL Marketo Measure] ayant de longs cycles de vente. Cette fonctionnalité permet aux marketeurs de créer des points de contact pour toutes les transitions d’étape qui se produisent dans le parcours d’opportunité, par exemple lorsqu’un MQL de contact, passe ensuite à SAL, puis revient à l’étape MQL. Lorsque des contacts &quot;entrent à nouveau dans la scène MQL&quot; ou &quot;re-MQL&quot;, le MQL est considéré comme une scène de boomerang. La fonction d’évaluation Boomerang fonctionne à côté des [!DNL Marketo Measure] étapes personnalisées.

## Fonctionnement de cette fonctionnalité {#what-this-feature-does}

* Crée un point de contact &quot;boomerang&quot; pour toutes les transitions d’étape qui se produisent dans le parcours d’une opportunité
* Effectue le suivi des transitions répétées entre toutes les étapes personnalisées (ex. lorsqu’un MQL de contact est déplacé vers SAL, puis revient à l’étape MQL).
* Permet de spécifier le nombre et l’ensemble de transitions intermédiaires que vous souhaitez inclure dans l’ opportunité (ex. Les 10 premiers MQL ou les 5 derniers MQL)
* Si vous êtes un utilisateur de modèle personnalisé, vous pouvez déterminer la pondération d’attribution et le crédit en pourcentage que vous souhaitez allouer à chacune de ces étapes (par exemple, désigner le poids de l’attribution à la première ou à la dernière occurrence de MQL ou répartir uniformément la pondération de l’attribution entre toutes les occurrences) ;

>[!NOTE]
>
>[Instructions sur la configuration des phases Boomerang](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md).

## À quoi ressemblent les étapes et points de contact Boomerang dans votre CRM {#what-boomerang-stages-and-touchpoints-look-like-in-your-crm}

Sans scènes Boomerang (le &quot;before&quot;), vous ne voyez que le MQL le plus récent ou le point de contact SQL le plus récent associé à un enregistrement Lead/contact.

![](assets/1.png)

Avec les étapes Boomerang et les points de contact, vous voyez les points de contact qui se produisent pour chaque transition d’étape. La convention de dénomination de ces points de contact boomerang est la suivante :

**[Nom de l’état]-00.**

En reprenant l’exemple ci-dessous, ce compte [!DNL Marketo Measure] a inclus MQL et SQL dans ses phases de boomerang, et a choisi d’afficher 2 points de contact boomerang par étape.

![](assets/2.png)

**MQL-01** est la première transition d’étape MQL.

La valeur numérique dans la position du point de contact indique l’ordre dans lequel la transition de l’étape s’est produite. Le dernier point de contact boomerang doit être marqué comme :

MQL-02 **(Dernier)**

## Comment les phases Boomerang changent vos données existantes {#how-boomerang-stages-change-your-existing-data}

Boomerang Les étapes ont un impact :

**Attribution par canal**

* Puisque [!DNL Boomerang Stages] crée plus de points de contact, cela modifie la manière dont l’attribution est distribuée parmi les points de contact qui existent actuellement dans vos données. Cela peut donc signifier que les valeurs des recettes changent entre les canaux marketing. Tenez compte de cela avant d’implémenter [!DNL Boomerang stages] ou contactez votre gestionnaire de compte pour plus d’informations.

**Tous les rapports qui utilisent &quot;est égal à [Position du point de contact]&quot;**

* Les phases Boomerang introduisent de nouvelles positions de points de contact pour vos données. [!DNL Marketo Measure] modifie le format de la position du point de contact afin d’inclure l’occurrence de la scène, comme &quot;MQL-01&quot; ou &quot;MQL-05 (Dernier)&quot;. Dans cet exemple, les phases de boomerang ont un impact sur tous les rapports qui utilisent &quot;La position du point de contact est égale à MQL&quot;. Pour ajuster ces rapports, le filtre doit utiliser l’opérateur &quot;contient&quot; à la place.

## Questions fréquentes {#faq}

**Combien de scènes boomerang puis-je inclure dans mon modèle d’attribution ?**

Vous pouvez sélectionner jusqu’à 15 étapes.

**Q : Combien de points de contact &quot;boomerang&quot; puis-je avoir par étape ?**

Vous pouvez sélectionner jusqu’à dix points de contact boomerang par étape.

**Q : Pourquoi y a-t-il une limite de dix boomerangs par étape ?**

[!DNL Marketo Measure] doit limiter le nombre d’étapes pour que les temps de traitement restent sous contrôle. Si vous choisissez d’inclure les 15 étapes Boomerang dans votre modèle d’attribution et 10 points de contact boomerang par étape, vous pouvez avoir potentiellement plus de 150 points de contact par enregistrement de piste/contact.

**Q : J’ai un Data Warehouse. Est-ce que j&#39;obtiens toutes les données ou est-ce que la limite des phases Boomerang s&#39;applique aussi à moi ?**

La limite s’applique aux Data Warehouse et aux CRM en raison des limites de traitement mises en place par [!DNL Marketo Measure]. Data Warehouse affiche également la limite de dix points de contact par étape.

**Q : Quel est l’avantage de l’utilisation des étapes Boomerang avec la modélisation personnalisée ?**

L’utilisation de [!UICONTROL phases Boomerang] avec modélisation personnalisée vous permet d’affecter une pondération d’attribution aux points de contact [!UICONTROL Boomerang], qui alloue du crédit de recettes à ces étapes.

Sans modélisation personnalisée, [!DNL Marketo Measure] crée des points de contact pour chaque boomerang et transition d’étape, mais n’attribue aucun crédit d’attribution à ces points de contact. Les seuls points de contact boomerang qui reçoivent des crédits d’attribution proviennent des points de contact d’envoi. Sans modèle personnalisé, les points de contact [!DNL Boomerang] sont considérés comme identiques à une &quot;touche intermédiaire&quot; et reçoivent un crédit d’attribution en conséquence.
