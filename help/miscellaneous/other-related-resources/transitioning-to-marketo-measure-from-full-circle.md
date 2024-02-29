---
unique-page-id: 18874535
description: Transition vers [!DNL Marketo Measure] à partir du cercle complet - [!DNL Marketo Measure]
title: Transition vers [!DNL Marketo Measure] depuis Full Circle
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
feature: Attribution, Fundamentals
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---

# Transition vers [!DNL Marketo Measure] à partir du cercle complet {#transitioning-to-marketo-measure-from-full-circle}

Passage de l’option Cercle complet à [!DNL Marketo Measure]? Vous n&#39;êtes pas seule. Voici les principales considérations à garder à l’esprit et les leçons que nous avons apprises d’autres clients qui ont opéré le changement.

## Suivi basé sur les campagnes et suivi multi-source {#campaign-based-tracking-vs-multi-source-tracking}

Toutes les interactions dans [!UICONTROL Cercle complet] font l’objet d’un suivi par le biais de l’adhésion aux campagnes CRM. Avec [!DNL Marketo Measure], le parcours d&#39;achat est compilé grâce à une combinaison de nos enregistrements d&#39;activité JavaScript, d&#39;appartenance à une campagne CRM et d&#39;activité CRM. Il peut s’avérer difficile de passer le changement mental de &quot;toutes les interactions doivent être suivies dans une campagne CRM afin que notre rapport d’attribution fonctionne&quot; à &quot;seul ce sous-ensemble d’interactions doit être suivi dans une campagne CRM pour que notre rapport d’attribution fonctionne&quot;.

En général, voici comment [!DNL Marketo Measure] crée des enregistrements de point de contact pour les principaux types d’interactions :

* Le formulaire se remplit sur votre ou vos sites : [!DNL Marketo Measure] Javascript
* Pages vues sur votre ou vos sites : créées par [!DNL Marketo Measure] JavaScript uniquement si cette page vue a généré un jalon CRM désigné (comme piste ou création d’opportunités)
* Interactions hors ligne telles que conférences ou dépannages : appartenance à une campagne CRM
* Interactions numériques qui se produisent n’importe où sur Internet et qui ne correspond pas à votre site (comme un webinaire hébergé sur un site tiers qui génère un téléchargement de liste) : appartenance à une campagne CRM
* Interactions avec votre équipe des ventes : enregistrements d’activité CRM

Si vous maîtrisez la gestion de vos campagnes CRM et que vous préférez conserver les processus existants en place, c&#39;est très bien. Ça ne fait pas mal. [!DNL Marketo Measure] pour continuer à suivre toutes les interactions dans les campagnes CRM. Vous pouvez concevoir une logique qui crée uniquement des points de contact à partir d’un sous-ensemble de campagnes souhaité afin d’éviter la duplication des points de contact.

## Visibilité et attribution {#visibility-vs-attribution}

Avec la plupart des configurations de cercles complets, vous voyez chaque interaction d’une personne avec vos efforts marketing ou de vente. Pages vues, visites de pages répétées, appartenance à des campagnes en double et en triple : le cercle complet apparaît à toutes ces étapes. Si vous affichez une page 300 fois, le cercle complet crée 300 campagnes en double et vous donne un abonnement à chacune d’elles. [!DNL Marketo Measure] ne le fait pas, et c&#39;était une décision de conception consciente de notre part.

[!DNL Marketo Measure] vise à vous fournir un récit d’attribution qui fait apparaître des interactions significatives et distribue le poids parmi les points de contact les plus influents de manière appropriée. Par exemple, la variable [!DNL Marketo Measure] La structure ne fait pas apparaître les pages vues (sans remplissage de formulaire) comme des points de contact de routine. Il est peu probable qu’une page vue autonome ait un impact sur le déclenchement d’un parcours d’achat, mais nous allons créer un point de contact s’il s’agit de la dernière interaction avant un jalon CRM désigné (comme la création de piste ou d’opportunités). Nous ne voulons pas tout vous montrer. Nous voulons vous montrer ce qui importe, du point de vue de l’attribution.

Travaillez avec votre [!DNL Marketo Measure] représentant afin de définir les attentes appropriées concernant les données qui ne seront plus disponibles pour votre équipe.

## Pre-[!DNL Marketo Measure] Données {#pre-marketo-measure-data}

La recommandation standard consiste à commencer la création de rapports et la collecte de données à partir du jour où vous avez déployé la variable [!DNL Marketo Measure] JavaScript à l’avenir, ce qui est le double pour les anciens clients Full Circle. Réfléchissez aux deux sections ci-dessus : Vous êtes habitué à voir une plus grande quantité de données, et vous êtes habitué à toutes ces données provenant de l’appartenance à une campagne CRM. Si vous choisissez d’inclure une partie ou la totalité de ces données avant votre [!DNL Marketo Measure] implémentation, vous ne comparerez pas apples aux apples à la date de mise en oeuvre de JavaScript.

Cela dit, nous comprenons certainement que de nombreux clients ont besoin de ces données historiques. En particulier, si vous avez un cycle de vente plus long (plus de 90 jours), vous pouvez donner [!DNL Marketo Measure] visibilité dans pre-[!DNL Marketo Measure] data. Discutez-en avec soin avec votre [!DNL Marketo Measure] et gardez toujours à l’esprit que le décalage entre la date de mise en oeuvre peut entraîner l’apparition d’améliorations ou de baisses des performances ou de l’engagement des canaux, ainsi que d’autres inférences potentiellement incorrectes.

## En résumé {#in-summary}

Vous êtes en bonne compagnie, et nous avons aidé de nombreux autres clients à gérer ces modifications. Travaillez avec votre [!DNL Marketo Measure] pour comprendre les impacts ci-dessus, ainsi que toute autre préoccupation que vous pouvez avoir.
