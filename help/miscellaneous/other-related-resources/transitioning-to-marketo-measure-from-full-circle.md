---
unique-page-id: 18874535
description: Transition vers  [!DNL Marketo Measure] à partir du cercle complet - [!DNL Marketo Measure]
title: Transition vers [!DNL Marketo Measure] depuis Full Circle
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
feature: Attribution, Fundamentals
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# Transition vers [!DNL Marketo Measure] à partir du cercle complet {#transitioning-to-marketo-measure-from-full-circle}

Effectuer le déplacement de l’ensemble du cercle vers [!DNL Marketo Measure] ? Vous n&#39;êtes pas seule. Voici les principales considérations à garder à l’esprit et les leçons que nous avons apprises d’autres clients qui ont opéré le changement.

## Suivi basé sur une campagne ou suivi multi-Source {#campaign-based-tracking-vs-multi-source-tracking}

Toutes les interactions dans [!UICONTROL Full Circle] sont suivies via l’appartenance à une campagne CRM. Avec [!DNL Marketo Measure], le parcours d’achat est compilé à l’aide d’une combinaison de nos enregistrements d’activité JavaScript, d’appartenance à une campagne CRM et d’activité CRM. Il peut s’avérer difficile de passer le changement mental de &quot;toutes les interactions doivent être suivies dans une campagne CRM afin que notre rapport d’attribution fonctionne&quot; à &quot;seul ce sous-ensemble d’interactions doit être suivi dans une campagne CRM pour que notre rapport d’attribution fonctionne&quot;.

En règle générale, [!DNL Marketo Measure] crée des enregistrements de point de contact pour les principaux types d’interactions :

* Renseignez les formulaires sur vos sites : [!DNL Marketo Measure] JavaScript
* Pages vues sur vos sites : créées par [!DNL Marketo Measure] JavaScript uniquement si cette page vue a généré un jalon CRM désigné (comme la création de pistes ou d’opportunités)
* Interactions hors ligne telles que conférences ou dépannages : appartenance à une campagne CRM
* Interactions numériques qui se produisent n’importe où sur Internet et qui ne correspond pas à votre site (comme un webinaire hébergé sur un site tiers qui génère un téléchargement de liste) : appartenance à une campagne CRM
* Interactions avec l’équipe des ventes : enregistrements d’activité CRM

Si vous maîtrisez la gestion des campagnes CRM et que vous préférez conserver les processus existants en place, c&#39;est très bien. La poursuite du suivi de toutes les interactions dans les campagnes CRM n&#39;a pas de problème [!DNL Marketo Measure]. Vous pouvez concevoir une logique qui crée uniquement des points de contact à partir d’un sous-ensemble de campagnes souhaité afin d’éviter la duplication des points de contact.

## Visibilité et attribution {#visibility-vs-attribution}

Avec la plupart des configurations de cercles complets, vous voyez chaque interaction d’une personne avec vos efforts marketing ou de vente. Pages vues, visites de pages répétées, appartenance à des campagnes en trois exemplaires : le cercle complet apparaît à tous. Si vous affichez une page 300 fois, le cercle complet crée 300 campagnes en double et vous donne un abonnement à chacune d’elles. [!DNL Marketo Measure] ne le fait pas, et c&#39;était une décision de conception consciente de notre part.

[!DNL Marketo Measure] vise à vous fournir un article d’attribution qui surface les interactions significatives et distribue le poids parmi les points de contact les plus influents de manière appropriée. Par exemple, la structure [!DNL Marketo Measure] ne fera pas apparaître les pages vues (sans remplissage de formulaire) comme des points de contact de routine. Il est peu probable qu’une page vue autonome ait un impact sur le déclenchement d’un parcours d’achat, mais nous créons un point de contact s’il s’agit de la dernière interaction avant un jalon CRM désigné (comme la création de piste ou d’opportunités). Nous ne voulons pas tout vous montrer. Nous voulons vous montrer ce qui importe, du point de vue de l’attribution.

Contactez votre représentant [!DNL Marketo Measure] pour définir les attentes appropriées concernant les données qui ne seront plus disponibles pour votre équipe.

## Données pré-[!DNL Marketo Measure] {#pre-marketo-measure-data}

La recommandation standard consiste à commencer la création de rapports et la collecte de données à partir du jour où vous avez déployé le JavaScript [!DNL Marketo Measure] vers l’avant, ce qui est le double pour les anciens clients Full Circle. Réfléchissez aux deux sections ci-dessus : Vous êtes habitué à voir une plus grande quantité de données et vous êtes habitué à toutes ces données provenant de l’adhésion à une campagne CRM. Si vous choisissez d’inclure une partie ou la totalité de ces données avant votre mise en oeuvre [!DNL Marketo Measure], vous ne comparerez pas les pommes aux pommes à la date de mise en oeuvre de JavaScript.

Cela dit, nous comprenons certainement que de nombreux clients ont besoin de ces données historiques. En particulier, si votre cycle de vente est plus long (plus de 90 jours), vous pouvez vouloir donner à [!DNL Marketo Measure] une visibilité sur les données antérieures à[!DNL Marketo Measure]. Parlez-en avec votre représentant [!DNL Marketo Measure] et gardez toujours à l’esprit que le décalage entre la date de mise en oeuvre peut entraîner l’apparition d’améliorations ou de baisses des performances ou de l’engagement des canaux, ainsi que d’autres inférences potentiellement incorrectes.

## En résumé {#in-summary}

Vous êtes en bonne compagnie, et nous avons aidé de nombreux autres clients à gérer ces modifications. Contactez votre représentant [!DNL Marketo Measure] pour comprendre les impacts ci-dessus et toute autre préoccupation que vous pouvez avoir.
