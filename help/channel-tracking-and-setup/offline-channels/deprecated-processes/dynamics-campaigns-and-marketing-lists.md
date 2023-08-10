---
unique-page-id: 18874610
description: Campagnes Dynamics et listes marketing - [!DNL Marketo Measure] - Documentation du produit
title: Campagnes Dynamics et listes marketing
exl-id: 7b3d4032-5edf-489d-b86b-1e2a5755b258
feature: Microsoft Dynamics
source-git-commit: e01738222e8845112892c0258cb084a4f0ebb257
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---

# Campagnes Dynamics et listes marketing {#dynamics-campaigns-and-marketing-lists}

>[!NOTE]
>
>Cet article couvre un processus obsolète. Nous encourageons les utilisateurs à utiliser la variable [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Campagnes {#campaigns}

Les campagnes Dynamics sont adaptées au suivi des activités marketing hors ligne et à leur inclusion dans le parcours omnicanal. Les campagnes doivent être en relation avec les Leads ou les contacts et peuvent être cumulées à la campagne via les Réponses de campagne ou les Listes marketing.

## Réponses de campagne {#campaign-responses}

Lorsque des Leads ou des contacts sont directement ajoutés à une campagne, ils sont renseignés en tant qu&#39;enregistrement de réponse à la campagne.

![](assets/1.png)

## Activation des points de contact {#enable-touchpoints}

Pour inclure ces enregistrements dans le parcours du point de contact, il existe quelques options de synchronisation des types de réponses de campagne. Sur l’enregistrement Campaign, un champ personnalisé doit apparaître à partir de la solution installée, intitulé &quot;[!UICONTROL Activation des points de contact d’achat].&quot; Si vous ne voyez pas cela, le champ devra être ajouté via l’éditeur de formulaire.

![](assets/2.png)

Vous pouvez choisir d’inclure tous les enregistrements ayant une réponse de campagne dans la campagne, ou uniquement ceux ayant une réponse &quot;Intéressée&quot;, ou par défaut, vous ne pouvez pas du tout inclure les réponses de campagne. Vous pouvez laisser le champ vide ou choisir explicitement de l’exclure.

[!DNL Marketo Measure] ne prend pas en charge les valeurs de réponse personnalisées.

![](assets/3.png)

Il s’agit des valeurs de réponse du stock pour la réponse de campagne :

![](assets/4.png)

En fonction de votre sélection, ces enregistrements sont désormais éligibles pour les points de contact dans le parcours de piste, de contact ou d’opportunité. S’ils remplissent les critères, un point de contact &quot;Dynamics Campaign&quot; s’affiche dans le parcours.

L’une des raisons pour lesquelles une réponse de campagne n’apparaît pas est qu’une activité Première touche et/ou Contact de création de piste avait déjà été enregistrée pour le prospect/Contact et que la fonction &quot;PostLC&quot; est désactivée ou a atteint son nombre maximal de points de contact.

## Date du Touchpoint {#touchpoint-date}

La date du point de contact d’une campagne correspond généralement à la date à laquelle la réponse de la campagne a été ajoutée à la campagne. Il peut être remplacé si le champ personnalisé de la solution installée &quot;Date du point de contact de l’acheteur&quot; est renseigné. Si vous ne voyez pas cela, le champ devra être ajouté via l’éditeur de formulaire.

Un exemple courant d’utilisation de ce champ concerne les événements où une liste d’analyses de badge d’un événement est ajoutée aux jours de la gestion de la relation client après que l’événement s’est produit, de sorte que l’utilisateur peut redéfinir la date du point de contact de l’acheteur sur le moment où l’événement s’est produit.

![](assets/5.png)

## Listes marketing {#marketing-lists}

Les listes marketing sont une autre manière d’inclure des pistes ou des contacts dans un parcours marketing. Les listes marketing sont uniques pour un groupe de Leads ou de Contacts, ce qui signifie que l’utilisateur doit indiquer si sa liste est un ensemble de Leads ou un ensemble de Contacts.

[!DNL Marketo Measure] ne prend en charge que les listes marketing statiques. Les listes de marketing dynamique ne sont pas prises en charge, car notre traitement requiert que nous vérifiions la date de modification d’un enregistrement. Cependant, comme une liste dynamique est fréquemment en train de changer, il n’existe aucune date de modification pour [!DNL Marketo Measure] à vérifier. Cela nécessiterait un téléchargement constant de l’ensemble de données tout au long de la journée.

![](assets/6.png)

La capture d’écran ci-dessus est une liste marketing pour les pistes. Les listes marketing sont associées aux campagnes et peuvent être associées à plusieurs campagnes. , sauf si vous ne créez jamais qu&#39;une seule liste marketing pour une campagne, [!DNL Marketo Measure] ne recommande pas aux clients d’utiliser des listes marketing pour effectuer le suivi de leurs campagnes. Il est peu probable que la même liste exacte de pistes/contacts soit éligible aux points de contact pour plusieurs campagnes.

## Activation des points de contact {#enable-touchpoints-1}

Pour activer une liste marketing pour les points de contact, un paramètre distinct est appliqué à l’enregistrement Campaign intitulé &quot;&quot;.[!UICONTROL Listes marketing de synchronisation],&quot; qui est un simple commutateur &quot;oui/non&quot;. Si vous ne voyez pas cela, le champ devra être ajouté via l’éditeur de formulaire. Lors de l’enregistrement de campagne, vous pouvez voir quelles listes marketing sont liées à la campagne afin de connaître le nombre de listes que vous activez.

![](assets/7.png)

## Date du Touchpoint {#touchpoint-date-1}

La date de point de contact d’une liste marketing est généralement la date de création du membre de liste, de sorte que la date à laquelle le prospect ou le contact a été ajouté à la liste marketing. Il peut être remplacé si le champ personnalisé de la solution installée &quot;Date du point de contact de l’acheteur&quot; est renseigné. Si vous ne voyez pas cela, le champ devra être ajouté via l’éditeur de formulaire.

![](assets/8.png)

## Mappage de canaux {#channel-mapping}

Les campagnes Dynamics sont regroupées dans vos canaux marketing personnalisés à l’aide du champ Type de campagne . Elles peuvent être modifiées dans le menu Personnalisations de Dynamics.

Les valeurs du menu Type de campagne sont extraites dans la variable [!DNL Marketo Measure] Application. **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]** > **[!UICONTROL Canaux hors ligne]**.

Pour chaque type de campagne, il peut être mappé à une combinaison Canal et Sous-canal afin que chaque point de contact qui dérive de la campagne ait le canal et le sous-canal mappés appropriés.

![](assets/9.png)

![](assets/10.png)

## Date de synchronisation de campagne {#campaign-sync-date}

Ceci n’est pas disponible pour les clients Dynamics

## Questions fréquentes {#faq}

**Pouvons-nous activer les points de contact sur les listes marketing ou uniquement les campagnes dans Dynamics ?**

Vous pouvez activer une liste marketing, mais elle doit être associée à une campagne, car l’option de synchronisation d’une liste marketing se trouve sur la campagne.

**Pouvons-nous utiliser des réponses de campagne ET des listes marketing sur une campagne ?**

Oui.
