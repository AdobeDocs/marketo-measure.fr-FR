---
description: Gestion des domaines - [!DNL Marketo Measure]
title: Gestion des domaines
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
feature: Integration, Tracking
source-git-commit: 4c68fa08797c252a89ba097c723fb8afee82451f
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 1%

---

# Gestion des domaines {#domain-management}

Pour les clients IMS exécutant [!DNL Marketo Measure] dans l’interface Experience Cloud, [!DNL Marketo Measure] fournit une interface qui permet aux utilisateurs de gérer leur propre liste de domaines. Les utilisateurs de [!DNL Marketo Measure] doivent d’abord vérifier tous les domaines dont ils souhaitent effectuer le suivi dans le [Adobe Admin Console](https://adminconsole.adobe.com/). Une fois les domaines vérifiés dans l’Admin Console, les utilisateurs peuvent gérer si [!DNL Marketo Measure] utilise ces domaines pour le suivi du trafic sur le site web.

## Ajout de domaines dans Admin Console {#adding-domains-in-admin-console}

Les utilisateurs IMS ayant accès à Adobe Admin Console peuvent ajouter et valider des domaines qu’ils détiennent. La validation du domaine implique l’ajout d’un enregistrement DNS pour chaque domaine, puis la possibilité pour l’Admin Console de vérifier cet enregistrement.

![](assets/domain-management-1.png)

Vous trouverez des instructions pour l’ajout de domaines dans la [documentation Admin Console](https://helpx.adobe.com/enterprise/using/add-domains-directories.html). Une fois qu’un domaine est ajouté, il doit être [ lié à un répertoire ](https://helpx.adobe.com/enterprise/using/add-domains-directories.html#link-domains-to-directoies).

## Gestion des domaines dans [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

Une fois qu’un domaine est ajouté à l’Admin Console, [!DNL Marketo Measure] synchronise régulièrement cet enregistrement dans la base de données. Cette synchronisation se produit de nuit, et également chaque fois qu’un utilisateur visite la page **[!UICONTROL Domaines]** dans l’interface utilisateur de [!DNL Marketo Measure]. Par défaut, tous les enregistrements importés par [!DNL Marketo Measure] sont désactivés, et le client doit activer manuellement chaque domaine.

![](assets/domain-management-2.png)

Sur la page **[!UICONTROL Intégration]** > **[!UICONTROL Domaines]** , l’utilisateur voit tous les domaines qu’il a enregistrés dans l’Admin Console, ainsi que leur état. Chaque domaine peut être activé ou désactivé. Si un domaine est activé, le suivi [!DNL Marketo Measure] collecte le trafic qui s’affiche sur ce domaine. Si un domaine est désactivé, [!DNL Marketo Measure] ignore le trafic provenant de ce domaine et ne crée pas de points de contact ni d’autres données. [!DNL Marketo Measure] confirme la désactivation d’un domaine et avertit les autres ramifications :

![](assets/domain-management-3.png)

L’impact du changement de domaine est immédiat, et les modifications ne sont pas rétroactives. À l’avenir, [!DNL Marketo Measure] va purger les données des domaines désactivés après une période définie.

## Statuts {#statuses}

Les états Admin Console sont classés comme suit :

* **VALIDATED** : ce domaine est vérifié en Admin Console
* **UNVERIFIED** : ce domaine n’est pas entièrement vérifié en Admin Console et n’est pas éligible au suivi dans [!DNL Marketo Measure]
* **INVALID** : ce domaine peut avoir expiré ou avoir été supprimé de l’Admin Console. Le suivi des données dans [!DNL Marketo Measure] est marqué pour suppression
* **LEGACY** : ce domaine a été créé dans [!DNL Marketo Measure] et n’existe pas dans l’Admin Console

Les statuts de tracking peuvent être les suivants :

* **ACTIVE** : [!DNL Marketo Measure] reçoit des données de ce domaine
* **DISABLED** : ce domaine est disponible pour le suivi, mais est désactivé
* **UNAVAILABLE** : ce domaine n’est pas disponible pour le suivi car il n’est pas vérifié

Le survol d’un élément d’état individuel déclenche une info-bulle qui explique plus en détail cet état.

## Questions fréquentes {#faq}

**Que se passe-t-il lorsqu’un domaine est supprimé dans l’Admin Console ?**

Lorsqu’un domaine est supprimé dans l’Admin Console, [!DNL Marketo Measure] le marque comme supprimé. [!DNL Marketo Measure] arrête immédiatement le suivi du trafic sur ce domaine, mais ne supprime aucune donnée précédemment collectée.

**Pourquoi ne puis-je pas activer un domaine ?**

Sur cette page, il existe plusieurs raisons pour lesquelles la sélection d’un domaine peut être refusée. Si le domaine n’est pas validé dans l’Admin Console, il n’est pas disponible dans [!DNL Marketo Measure]. De même, si le domaine est détenu par une autre organisation d’Adobe du client actuel [!DNL Marketo Measure], il peut ne pas être disponible pour la sélection.

**Comment supprimer un domaine de cette liste ?**

Si le commutateur &quot;activé&quot; d’un domaine est désactivé, [!DNL Marketo Measure] l’ignore et il est effectivement supprimé de [!DNL Marketo Measure]. Pour supprimer définitivement un domaine de [!DNL Marketo Measure], vous devez le désactiver dans [!DNL Marketo Measure], puis le supprimer de l’Admin Console.
