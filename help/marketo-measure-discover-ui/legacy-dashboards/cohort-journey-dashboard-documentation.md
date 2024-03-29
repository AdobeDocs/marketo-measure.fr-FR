---
unique-page-id: 42762648
description: Documentation du tableau de bord des Parcours de cohortes - [!DNL Marketo Measure]
title: Documentation du tableau de bord des parcours de cohortes
exl-id: b139f720-86ae-4f6d-9dfc-cc67b4186f88
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---

# Documentation du tableau de bord des parcours de cohortes {#cohort-journey-dashboard-documentation}

Les tableaux de bord Impact des cohortes et Entonnoir permettent aux marketeurs d’afficher la progression à partir de l’étape de cohorte de départ pour une période sélectionnée et de mesurer le taux de conversion.

La principale différence est la manière dont nous comptabilisons chaque entité à l’étape de cohorte.

* Entonnoir de cohorte : le résultat de chaque étape est directement dérivé de l’étape précédente.

   * Seuls les enregistrements qui ont traversé chaque étape de l’entonnoir après l’heure de début définie de la cohorte sont comptabilisés.

![](assets/cohort-journey-dashboard-documentation-1.png)

* Impact sur les cohortes : le résultat de chaque étape est dérivé de l’étape sur les cohortes, et non de l’étape précédente.

   * Tous les enregistrements de chaque étape sont comptabilisés tant qu’ils se sont produits après l’heure de début définie de la cohorte. Ce tableau de bord aura naturellement plus d’enregistrements que le tableau de bord Entonnoir, car nous examinons l’impact des entités à l’étape de la cohorte, et pas seulement le mouvement dans l’entonnoir.

![](assets/cohort-journey-dashboard-documentation-2.png)

Chaque tableau de bord comporte deux mosaïques :

* Recettes des cohortes : le total des opportunités provenant de toutes les opportunités à l’étape Transactions de la mosaïque Parcours de cohortes.
* Parcours de cohortes : progression vers chaque étape de parcours à partir de l’étape de cohorte de départ pour une période sélectionnée.

>[!NOTE]
>
>Dans tous les tableaux de bord de Discover, un seul objet de personne, prospect ou contact, peut faire l’objet d’un rapport. Défini dans [!UICONTROL Paramètres] > [!UICONTROL Reporting] > [!UICONTROL Paramètres d’attribution] > [!UICONTROL Objet de tableau de bord par défaut].

Les tableaux de bord prennent en charge les filtres suivants :

* Évaluation des cohortes : sélectionnez l’étape de cohorte de départ. Les enregistrements de toutes les étapes suivantes sont issus des enregistrements de l’étape de cohorte.
* Période des cohortes : sélectionnez la période de l’étape de cohorte sélectionnée. Avec Cohort Stage, il définit le jeu de données de départ.
* Date de coupure : sélectionnez la date à laquelle doit se produire la progression de l&#39;enregistrement dans toutes les étapes suivantes. La valeur par défaut est aujourd’hui. Notez que cela s’applique à toutes les étapes autres que l’étape de cohorte.
* Canal : filtrer les enregistrements par canaux. Un enregistrement est associé à un canal si l’un de ses points de contact est associé au canal.
* Sous-canal : filtrez les enregistrements par sous-canaux. Un enregistrement est associé à un sous-canal si l’un de ses points de contact est associé au sous-canal.
* Campagne : filtrez les enregistrements par campagnes. Un enregistrement est associé à une campagne si l’un de ses points de contact est associé à la campagne.
* Source de la campagne : filtrez les enregistrements par sources de la campagne. Exemples de sources de campagne : [!DNL Adwords], [!DNL BingAds], [!DNL Facebook], [!DNL LinkedIn], etc. Un enregistrement est associé à une source de campagne si l’un de ses points de contact est associé à la source de la campagne.
* Filtres de segments : filtrez les enregistrements par segments personnalisés. Un enregistrement est associé à un segment si l’un de ses points de contact est associé au segment.

La logique &quot;AND&quot; est utilisée sur tous les filtres.

>[!NOTE]
>
>Les filtres de segments s’appliquent uniquement à l’étape LC et après. Si l’étape de cohorte est Inconnu ou Connu et que l’un des filtres de segments a une valeur, le tableau de bord ne renvoie aucun résultat.

Les étapes comprennent Inconnu, Connu, LC, les étapes d’entonnoir sélectionnées dans les étapes Ouvrir le prospect/contact (Paramètres > CRM > Mappage dans l’environnement intermédiaire), OC, les étapes d’entonnoir sélectionnées dans les étapes d’ouverture des opportunités (Paramètres > CRM > Mappage dans l’environnement intermédiaire) et les opérations (opportunités Won fermées).

>[!NOTE]
>
>Le décompte des enregistrements d’une étape de parcours, défini comme toute étape autre que l’étape de cohorte, inclut tous les nouveaux enregistrements, liés aux enregistrements de cohorte, qui sont créés après la date de début de la période sélectionnée et avant la date d’arrêt. C&#39;est une causalité déduite.

Vous pouvez descendre dans chaque barre pour afficher les enregistrements pour chaque étape.

* Pour Inconnu, il affiche les détails du visiteur anonyme.
* Pour Connu, il affiche les détails connus du visiteur.
* Pour les phases LC et Open Lead/Contact, il affiche les détails de piste/contact.
* Pour les phases OC, Open Opportunity et Deals, il affiche les détails des opportunités.
