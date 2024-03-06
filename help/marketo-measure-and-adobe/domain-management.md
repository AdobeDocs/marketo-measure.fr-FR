---
description: Gestion des domaines - [!DNL Marketo Measure]
title: Gestion des domaines
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
feature: Integration, Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 1%

---

# Gestion des domaines {#domain-management}

Pour les clients compatibles avec IMS exécutés [!DNL Marketo Measure] dans l’interface Experience Cloud, [!DNL Marketo Measure] fournit une interface qui permet aux utilisateurs de gérer leur propre liste de domaines. [!DNL Marketo Measure] Les utilisateurs doivent d’abord vérifier tous les domaines dont ils souhaitent effectuer le suivi dans la variable [Adobe Admin Console](https://adminconsole.adobe.com/). Une fois les domaines vérifiés dans le Admin Console, les utilisateurs peuvent gérer si [!DNL Marketo Measure] utilise ces domaines pour effectuer le suivi du trafic sur le site web.

## Ajout de domaines dans Admin Console {#adding-domains-in-admin-console}

Les utilisateurs IMS ayant accès à Adobe Admin Console peuvent ajouter et valider des domaines qu’ils détiennent. La validation du domaine implique l’ajout d’un enregistrement DNS pour chaque domaine, puis la possibilité pour le Admin Console de vérifier cet enregistrement.

![](assets/domain-management-1.png)

Les instructions pour l’ajout de domaines se trouvent dans la section [Documentation du Admin Console](https://helpx.adobe.com/enterprise/using/set-up-identity.html#setup-domains). Une fois un domaine ajouté, il doit être [lié à un répertoire](https://helpx.adobe.com/enterprise/using/set-up-identity.html#link-domains-to-directories).

## Gestion des domaines dans [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

Après l’ajout d’un domaine dans le Admin Console, [!DNL Marketo Measure] synchronise régulièrement cet enregistrement dans la base de données. Cette synchronisation se produit de nuit, et également chaque fois qu’un utilisateur visite la fonction **[!UICONTROL Domaines]** dans la [!DNL Marketo Measure] Interface utilisateur. Par défaut, tout enregistrement qui [!DNL Marketo Measure] Les imports sont désactivés et le client doit activer manuellement chaque domaine.

![](assets/domain-management-2.png)

Sur le **[!UICONTROL Intégration]** > **[!UICONTROL Domaines]** , l’utilisateur voit tous les domaines qu’il a enregistrés dans le Admin Console, ainsi que leur état. Chaque domaine peut être activé ou désactivé. Si un domaine est activé, [!DNL Marketo Measure] Le suivi collecte tout trafic qui s’affiche sur ce domaine. Si un domaine est désactivé, [!DNL Marketo Measure] ignore le trafic provenant de ce domaine et ne crée pas de points de contact ni d’autres données. [!DNL Marketo Measure] confirme la désactivation d’un domaine et avertit les utilisateurs de toutes ramifications :

![](assets/domain-management-3.png)

L’impact du changement de domaine est immédiat, et les modifications ne sont pas rétroactives. À l&#39;avenir, [!DNL Marketo Measure] purge les données des domaines désactivés après une période définie.

## Statuts {#statuses}

Les états du Admin Console sont classés comme suit :

* **VALIDÉ**: ce domaine est vérifié en Admin Console
* **UNVERIFIED**: ce domaine n’est pas entièrement vérifié en Admin Console et n’est pas éligible au suivi dans [!DNL Marketo Measure]
* **INVALIDE**: ce domaine peut avoir expiré ou avoir été supprimé du Admin Console. Suivi des données dans [!DNL Marketo Measure] est marqué comme suppression
* **HÉRITÉ**: ce domaine a été créé dans [!DNL Marketo Measure] et n’existe pas dans le Admin Console

Les statuts de tracking peuvent être les suivants :

* **ACTIF**: [!DNL Marketo Measure] reçoit des données de ce domaine
* **DISABLED**: ce domaine est disponible pour le suivi, mais il est désactivé.
* **INDISPONIBLE**: ce domaine n’est pas disponible pour le suivi, car il n’est pas vérifié

Le survol d’un élément d’état individuel déclenche une info-bulle qui explique plus en détail cet état.

## Questions fréquentes {#faq}

**Que se passe-t-il lorsqu’un domaine est supprimé dans le Admin Console ?**

Lorsqu’un domaine est supprimé dans le Admin Console, [!DNL Marketo Measure] marque le domaine comme supprimé. [!DNL Marketo Measure] arrête immédiatement le suivi du trafic sur ce domaine, mais ne supprime aucune donnée précédemment collectée.

**Pourquoi est-ce que je ne parviens pas à activer un domaine ?**

Sur cette page, il existe plusieurs raisons pour lesquelles la sélection d’un domaine peut être refusée. Si le domaine n’est pas validé dans le Admin Console, il n’est pas disponible dans [!DNL Marketo Measure]. De même, si le domaine est détenu par une autre organisation d’Adobe que la propriété actuelle [!DNL Marketo Measure] client, il peut être indisponible pour la sélection.

**Comment supprimer un domaine de cette liste ?**

Si le commutateur &quot;activé&quot; d’un domaine est désactivé, [!DNL Marketo Measure] l’ignore et il est effectivement supprimé de [!DNL Marketo Measure]. Pour supprimer définitivement un domaine de [!DNL Marketo Measure], vous devez la désactiver dans [!DNL Marketo Measure], puis supprimez-le du Admin Console.
