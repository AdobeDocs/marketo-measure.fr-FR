---
unique-page-id: 18874578
description: Campagnes et membres de campagne - [!DNL Marketo Measure] - Documentation du produit
title: Campagnes et membres de campagne
exl-id: e4e2b154-39ac-4295-a541-7fa6112672e3
feature: Channels
source-git-commit: 31ffb58f5318b71d478056f9b914eb1d42c7719a
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 1%

---

# Campagnes et membres de campagne {#campaigns-and-campaign-members}

[!DNL Salesforce] Les campagnes sont destinées à effectuer le suivi des listes de pistes et de contacts associées à un programme ou à une activité marketing. Il s’agit généralement de webinaires, d’inscriptions ou de visites, par exemple. Les marketeurs peuvent indiquer si une campagne doit être créditée ou non dans un parcours de point de contact.

## Activation des points de contact {#enabling-touchpoints}

La variable [!DNL Marketo Measure] [!DNL Salesforce] Le package comprend un champ intitulé &quot;Activer les points de contact de l’acheteur&quot; sur l’objet Campaign. Une fois que le champ a été ajouté à la mise en page, il se présente comme suit :

![](assets/1.png)

Les options disponibles dans la liste de sélection sont les suivantes :

![](assets/2.png)

* Inclure tous les membres de campagne : chaque prospect ou contact ajouté à la campagne recevra un point de contact associé à cette campagne.
* Inclure uniquement les membres de campagne &quot;réactifs&quot; : seuls les Leads ou les contacts dont le statut de membre de campagne est &quot;réagit&quot; recevront un point de contact associé à cette campagne.
* Exclure tous les membres de campagne : aucun des chefs ou contacts ne recevra de point de contact associé à cette campagne.

Pour que la variable [!DNL Marketo Measure] pour créer un point de contact. Sans adresse email, [!DNL Marketo Measure] n’affectera pas de point de contact au membre de la campagne.

## Date de synchronisation de campagne {#campaign-sync-dates}

Avec l&#39;installation du package, [!DNL Marketo Measure] comprend également 2 champs de date sur l’objet Campaign : Date de début du point de contact et Date de fin du point de contact.

Ces dates indiquent [!DNL Marketo Measure] lorsque nous devons commencer ou arrêter l’inclusion des membres de la campagne dans le parcours du point de contact. Vous pouvez définir une date, les deux ou aucune.

## Cas d’utilisation de la date de début du point de contact {#use-case-for-touchpoint-start-date}

La date de début peut être utilisée dans le cas où une campagne existante est utilisée pour le suivi des Leads et des contacts, mais l&#39;utilisateur ne souhaite commencer à mesurer qu&#39;une fois de nouveaux systèmes ou processus en place, donc il décide de définir une date de début une fois. [!DNL Marketo Measure] doit commencer le suivi de ces membres de campagne.

## Cas d’utilisation de la date de fin du point de contact {#use-case-for-touchpoint-end-date}

Si vous utilisez [!DNL Marketo Measure], vous avez utilisé une plateforme d’automatisation marketing qui a suivi les interactions numériques de Leads (envois de formulaires IE), puis téléchargé ces Leads dans une [!DNL Saleforce] Dans Campaign, vous pouvez utiliser le champ Date de fin du point de contact . Vous définiriez la date de fin du point de contact comme date de début avec [!DNL Marketo Measure] et activez Points de contact d’achat, l’interaction numérique de ces Leads sera alors créée en tant que point de contact. La raison pour laquelle vous définirez la Date de fin du point de contact comme Date de début avec [!DNL Marketo Measure] car, à partir de maintenant, nous suivrons ces interactions numériques à travers notre javascript.

![](assets/3.png)

## Membres de la campagne {#campaign-members}

Les membres de campagne sont imbriqués sous [!UICONTROL Campagnes], et sont liés à un prospect ou à un contact. Un prospect ou un contact ne peut être ajouté qu&#39;une seule fois à une campagne, ce qui peut poser problème en fonction du cas d&#39;utilisation de la campagne. Lorsqu’une campagne est synchronisée, l’appartenance à la campagne est utilisée comme une activité marketing mise dans le parcours de point de contact et traitée comme un remplissage de formulaire.

## État du point de contact de l’achat {#buyer-touchpoint-status}

Si activée, [!DNL Marketo Measure] poussera une valeur d’état sur le membre de Campaign dans 4 champs différents inclus dans le package installé : État du point de contact (piste), État du point de contact (contact), État du point de contact (opportunité) et Date d’état du point de contact. Cela permet aux clients de vérifier si un point de contact a été créé ou non en tant que point de contact d’achat ou d’attribution d’achat, selon l’objet auquel il est lié. La Date d’état du point de contact est simplement la dernière date à laquelle l’état a été mis à jour sur le membre de Campaign.

![](assets/4.png)

## Date du point de contact de l’achat {#buyer-touchpoint-date}

Avec l&#39;installation du package, [!DNL Marketo Measure] comprend également un champ sur le membre de campagne intitulé &quot;Date du point de contact de l’achat&quot;. Cela permet à l’utilisateur de remplacer la date qui [!DNL Marketo Measure] utilisera pour la date du point de contact sur l’enregistrement du point de contact.

Cela peut s’avérer nécessaire si une liste a été chargée plusieurs jours/semaines/mois après qu’un événement se soit réellement produit. Il existe des moyens de mettre à jour tous les enregistrements à la fois, comme expliqué ci-dessous.

![](assets/5.png)

Pour savoir si vous devez utiliser ou non la date du point de contact de l’acheteur, voici comment les dates sont déterminées par [!DNL Marketo Measure] selon le [!UICONTROL Type de synchronisation] qui est sélectionné pour la campagne.

Si la variable [!UICONTROL Type de synchronisation] est définie sur &quot;Inclure tous les membres de campagne&quot;, la priorité de définition de la date du point de contact est de haut en bas :

* Date du point de contact de l’achat
* Date de création du membre de campagne

Si la variable [!UICONTROL Type de synchronisation] est définie sur &quot;Inclure uniquement les membres de campagne &quot;réactifs&quot;. La priorité de définition de la date du point de contact est de haut en bas :

* Date du point de contact de l’achat
* Date première réponse
   * La date de première réponse est automatiquement définie dès que l’état est défini sur &quot;Répondu&quot; et est une date standard. [!DNL Salesforce] champ non modifiable

* Date de création du membre de campagne

## Date de point de contact de mise à jour en bloc {#bulk-update-touchpoint-date}

La date du point de contact de mise à jour en bloc est incluse dans la [!DNL Marketo Measure] [!DNL Salesforce] Le module et le bouton doivent être ajoutés à la mise en page.

![](assets/6.png)

Si un grand nombre d&#39;enregistrements de membre de Campaign doivent être mis à jour, vous pouvez utiliser la variable [!UICONTROL Date de point de contact de mise à jour en bloc] pour effectuer une modification en masse.

Si cette interface ne couvre pas certains cas d’utilisation uniques, vous pouvez également utiliser la variable [Chargeur de données](https://dataloader.io/){target="_blank"} pour exporter les enregistrements, effectuez la modification et chargez à nouveau les enregistrements dans .

Commencez par rechercher les enregistrements et par filtrer ceux pour lesquels vous souhaitez définir une Date de point de contact de l’acheteur.

>[!CAUTION]
>
>Une recherche ne fonctionne pas, comme illustré dans l’exemple ci-dessous. L’interface utilisateur ne prend pas en charge la recherche de dates de points de contact d’achat nulles (la recherche ci-dessous ne fonctionnerait pas) :

![](assets/7.png)

Si vous n’avez pas besoin d’utiliser la recherche et appliquer simplement les dates à chaque enregistrement de membre de campagne, utilisez le[!UICONTROL Inclure tous les enregistrements]&quot; (voir la capture d’écran ci-dessous), qui vérifie tous les enregistrements sur toutes les pages.

Sélectionnez la date et l’heure dans le sélecteur de calendrier. Si vous souhaitez sélectionner la date et l’heure actuelles, cliquez sur la date/l’heure qui s’affiche en regard du sélecteur de calendrier.

Une fois la date et l’heure définies, cliquez sur le bouton **[!UICONTROL Mettre à jour les enregistrements sélectionnés]** pour appliquer les modifications.

![](assets/8.png)

## Coûts de la campagne {#campaign-costs}

En savoir plus sur les coûts de campagne [dans cet article](/help/marketing-spend/spend-management/crm-campaign-costs.md).

## Retrait des membres de campagne {#campaign-member-removal}

La manière dont [!DNL Marketo Measure] tient compte des enregistrements supprimés dans Salesforce, qu’ils soient supprimés dans les pistes ou les comptes ou qu’il s’agisse de voir ces enregistrements dans l’API et de suivre qu’une entrée est marquée comme &quot;IsDeleted&quot;. Malheureusement avec les membres de Campaign, Salesforce a introduit une autre manière de supprimer ces membres de Campaign d’une campagne et ils sont simplement marqués comme &quot;supprimés&quot; par opposition à &quot;supprimés&quot;. Le problème est donc que les points de contact vivaient toujours dans Salesforce qui étaient liés aux membres de Campaign supprimés.

Pour contourner ce problème, procédez comme suit : [!DNL Marketo Measure] a créé une [!DNL Marketo Measure] Objet d’historique et déclencheur à suivre chaque fois que des membres de campagne sont supprimés, puis supprimez le point de contact correspondant. **Vous aurez besoin de [!DNL Marketo Measure] Package Marketing Analytics V6.15 ou version ultérieure** pour utiliser cette fonctionnalité.

>[!CAUTION]
>
>Gardez à l’esprit que ce déclencheur ne suit aucun membre de campagne qui a été supprimé par le passé. Cela ne fonctionne donc qu’à l’avenir. Si vous devez supprimer un grand nombre de points de contact de membres de la campagne précédents, contactez [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Université : champs d’objet de campagne](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
>
>[[!DNL Marketo Measure] Université : mappage des canaux hors ligne](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
