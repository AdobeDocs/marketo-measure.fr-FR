---
description: Transition  [!DNL Marketo Measure]  conseils « Cercle complet » pour les utilisateurs de Marketo Measure
title: Transition vers [!DNL Marketo Measure] depuis Full Circle
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
feature: Attribution, Fundamentals
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Transitionner vers [!DNL Marketo Measure] à partir d’un cercle complet {#transitioning-to-marketo-measure-from-full-circle}

Passer d&#39;un cercle complet à l&#39;[!DNL Marketo Measure] ? Vous n&#39;êtes pas seul. Voici les principales considérations à garder à l’esprit et les leçons que nous avons apprises des autres clients qui ont opéré le changement.

## Suivi basé sur Campaign vs. suivi multi-Source {#campaign-based-tracking-vs-multi-source-tracking}

Toutes les interactions dans [!UICONTROL Cercle complet] sont suivies par l’abonnement à la campagne CRM. Avec [!DNL Marketo Measure], le parcours d’achat est compilé à partir d’une combinaison de nos enregistrements JavaScript, Abonnement à une campagne CRM et Activité CRM . Il peut être difficile de s’éloigner mentalement de « toutes les interactions doivent être suivies dans une campagne CRM pour que nos rapports d’attribution fonctionnent » pour passer à « seul ce sous-ensemble d’interactions doit être suivi dans une campagne CRM pour que nos rapports d’attribution fonctionnent ».

En règle générale, voici comment [!DNL Marketo Measure] crée des enregistrements de point de contact pour les principaux types d’interactions :

* Remplissages de formulaires sur vos sites : [!DNL Marketo Measure] JavaScript
* Pages vues sur vos sites : créées par [!DNL Marketo Measure] JavaScript uniquement si cette page vue a franchi un jalon CRM désigné (tel que la création d’un prospect ou d’une opportunité)
* Interactions hors ligne telles que des conférences ou des salons professionnels : adhésion à une campagne CRM
* Les interactions numériques qui se produisent n’importe où sur Internet et qui ne sont pas votre site (par exemple, un webinaire hébergé sur un site tiers qui génère un téléchargement de liste) : l’adhésion à une campagne CRM
* Interactions avec l’équipe commerciale : enregistrements d’activité CRM

Si la gestion de campagnes CRM vous convient et que vous préférez conserver les processus existants, c&#39;est très bien. Le suivi de toutes les interactions dans les campagnes CRM n’[!DNL Marketo Measure] pas affecté. Vous pouvez concevoir une logique qui crée uniquement des points de contact à partir d’un sous-ensemble de campagnes souhaité afin d’éviter la duplication des points de contact.

## Visibilité et attribution {#visibility-vs-attribution}

Avec la plupart des configurations en cercle complet, vous voyez chaque interaction d’une personne avec vos efforts de marketing ou de vente. Pages vues, visites de pages répétées, appartenance à des campagnes en triple exemplaire : le Cercle complet fait apparaître tout cela. Si vous affichez une page 300 fois, Full Circle crée 300 campagnes en double et vous donne une adhésion à chacune d’elles. [!DNL Marketo Measure] ne le fait pas, et c&#39;était une décision délibérée de notre part.

[!DNL Marketo Measure] vise à vous fournir une histoire d’attribution qui fait apparaître les interactions significatives et répartit correctement le poids entre les points de contact les plus significatifs. Par exemple, le framework [!DNL Marketo Measure] ne fait pas apparaître les pages vues (sans remplissage de formulaire) comme points de contact de routine. Une page vue seule n’a pas de chances d’avoir un impact sur la progression d’un parcours d’achat, mais nous créons un point de contact s’il s’agit de la dernière interaction avant un jalon CRM désigné (tel que la création d’un prospect ou d’une opportunité). Nous ne voulons pas tout vous montrer. Nous voulons vous montrer ce qui compte, du point de vue de l&#39;attribution.

Contactez votre représentant [!DNL Marketo Measure] pour définir les attentes appropriées concernant les données qui ne seront plus disponibles pour votre équipe.

## Données [!DNL Marketo Measure] {#pre-marketo-measure-data}

La recommandation standard est de commencer la création de rapports et la collecte de données à partir du jour où vous avez déployé le [!DNL Marketo Measure] JavaScript, et cela double pour les anciens clients Full Circle. Pensez aux deux sections ci-dessus : vous êtes habitué à voir une quantité plus élevée de données et vous êtes habitué à toutes ces données provenant de l’appartenance à une campagne CRM. Si vous choisissez d’inclure une partie ou la totalité de ces données antérieures à votre implémentation [!DNL Marketo Measure], vous ne comparerez pas des pommes avec des pommes tout au long de la date d’implémentation de JavaScript.

Cela dit, nous comprenons parfaitement que de nombreux clients ont besoin de ces données historiques. En particulier si votre cycle de vente est plus long (plus de 90 jours), vous souhaiterez peut-être donner [!DNL Marketo Measure] de visibilité aux données de pré-[!DNL Marketo Measure]. Discutez-en soigneusement avec votre représentant de [!DNL Marketo Measure] et gardez toujours à l’esprit que le décalage au cours de la date d’implémentation peut entraîner l’apparition d’améliorations ou de baisses des performances ou de l’engagement des canaux, ainsi que d’autres inférences potentiellement incorrectes.

## En résumé {#in-summary}

Vous êtes en bonne compagnie, et nous avons aidé de nombreux autres clients à gérer ces changements. Contactez votre représentant [!DNL Marketo Measure] pour comprendre les impacts ci-dessus et toute autre préoccupation que vous pourriez avoir.
