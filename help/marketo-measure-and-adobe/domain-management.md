---
description: Gestion des domaines - [!DNL Marketo Measure]
title: Gestion des domaines
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
feature: Integration, Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 1%

---

# Gestion des domaines {#domain-management}

Pour les clients compatibles IMS qui exécutent [!DNL Marketo Measure] dans l’interface d’Experience Cloud, [!DNL Marketo Measure] fournit une interface qui permet aux utilisateurs de gérer leur propre liste de domaines. [!DNL Marketo Measure] utilisateurs doivent d&#39;abord vérifier les domaines qu&#39;ils souhaitent suivre dans le [Adobe Admin Console](https://adminconsole.adobe.com/). Une fois les domaines vérifiés dans Admin Console, les utilisateurs peuvent déterminer s’[!DNL Marketo Measure] les utilise pour le suivi du trafic sur le site web.

## Ajout de domaines dans Admin Console {#adding-domains-in-admin-console}

Les utilisateurs IMS ayant accès au Adobe Admin Console peuvent ajouter et valider des domaines qu’ils détiennent. La validation de domaine implique l’ajout d’un enregistrement DNS pour chaque domaine, puis l’autorisation de la vérification de cet enregistrement par Admin Console.

![](assets/domain-management-1.png)

Vous trouverez des instructions pour l’ajout de domaines dans la documentation d’[Admin Console](https://helpx.adobe.com/fr/enterprise/using/add-domains-directories.html). Une fois qu&#39;un domaine est ajouté, il doit être [lié à un répertoire](https://helpx.adobe.com/fr/enterprise/using/add-domains-directories.html#link-domains-to-directoies).

## Gestion des domaines dans [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

Après l’ajout d’un domaine dans Admin Console, [!DNL Marketo Measure] synchronise régulièrement cet enregistrement dans la base de données. Cette synchronisation se produit de nuit, ainsi qu’à chaque fois qu’un utilisateur visite la page **[!UICONTROL Domaines]** de l’interface utilisateur de [!DNL Marketo Measure]. Par défaut, tous les enregistrements importés [!DNL Marketo Measure] sont désactivés et le client doit activer manuellement chaque domaine.

![](assets/domain-management-2.png)

Sur la page **[!UICONTROL Intégration]** > **[!UICONTROL Domaines]**, l’utilisateur voit tous les domaines qu’il a enregistrés dans Admin Console, ainsi que leur statut. Chaque domaine peut être activé ou désactivé. Si un domaine est activé, [!DNL Marketo Measure] suivi collecte tout trafic visible sur ce domaine. Si un domaine est désactivé, [!DNL Marketo Measure] ignore tout trafic provenant de ce domaine et ne crée pas de points de contact ni d’autres données. [!DNL Marketo Measure] confirme la désactivation d’un domaine et avertit de toutes les ramifications :

![](assets/domain-management-3.png)

L’impact du changement de domaine est immédiat et les modifications ne sont pas rétroactives. À l’avenir, [!DNL Marketo Measure] purgera les données des domaines désactivés après une période définie.

## Statuts {#statuses}

Les statuts d’Admin Console sont classés comme suit :

* **VALIDÉ** : ce domaine est validé dans Admin Console
* **NON VÉRIFIÉ** : ce domaine n’est pas entièrement vérifié dans Admin Console et n’est pas éligible pour le suivi dans [!DNL Marketo Measure]
* **NON VALIDE** : ce domaine a peut-être expiré ou a été supprimé d’Admin Console. Les données de tracking dans [!DNL Marketo Measure] sont marquées pour suppression
* **HÉRITÉ** : ce domaine a été créé en [!DNL Marketo Measure] et n’existe pas dans Admin Console

Les statuts du tracking peuvent être les suivants :

* **ACTIF** : [!DNL Marketo Measure] reçoit des données de ce domaine
* **DÉSACTIVÉ** : ce domaine est disponible pour le suivi, mais il est désactivé
* **UNAVAILABLE** : ce domaine n&#39;est pas disponible pour le suivi car il n&#39;est pas vérifié

Le survol d’un élément de statut individuel déclenche une info-bulle qui explique plus en détail ce statut.

## Questions fréquentes {#faq}

**Que se passe-t-il lorsqu’un domaine est supprimé dans Admin Console ?**

Lorsqu’un domaine est supprimé dans Admin Console, [!DNL Marketo Measure] marque le domaine comme supprimé. [!DNL Marketo Measure] arrête immédiatement le suivi du trafic sur ce domaine, mais ne supprime aucune donnée collectée précédemment.

**Pourquoi ne puis-je pas activer un domaine ?**

Il existe plusieurs raisons pour lesquelles la sélection d’un domaine sur cette page peut être refusée. Si le domaine n’est pas validé dans Admin Console, il n’est pas disponible dans [!DNL Marketo Measure]. De même, si le domaine appartient à une organisation Adobe différente du client [!DNL Marketo Measure] actuel, il peut ne pas être disponible à la sélection.

**Comment supprimer un domaine de cette liste ?**

Si le bouton « activé » est désactivé dans un domaine, [!DNL Marketo Measure] l’ignore et il est effectivement supprimé de [!DNL Marketo Measure]. Pour supprimer définitivement un domaine de [!DNL Marketo Measure], vous devez le désactiver dans [!DNL Marketo Measure], puis le supprimer d’Admin Console.
