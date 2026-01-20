---
unique-page-id: 18874704
description: FAQ sur l’attribution des activités - [!DNL Marketo Measure]
title: Questions fréquentes sur l’attribution des activités
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 2%

---

# Questions fréquentes sur l’attribution des activités {#activities-attribution-faq}

[!DNL Marketo Measure] Activités importe tous vos enregistrements d’activités et génère des points de contact pour ces activités, ce qui permet à ces activités de recevoir un crédit d’attribution. Le cas d’utilisation le plus courant consiste à effectuer le suivi des activités de l’équipe des ventes, car elles créent généralement un enregistrement des appels téléphoniques ou des e-mails envoyés aux prospects. Les autres éléments uniques qui peuvent être suivis sont les interactions de contenu telles que les téléchargements de ressources ou les vues vidéo.

>[!AVAILABILITY]
>
>Cette fonctionnalité est activée uniquement pour les clients de niveau 2. Pour demander un niveau de compte supérieur, contactez l’équipe du compte Adobe (votre gestionnaire de compte).

**En quoi est-ce différent des campagnes hors ligne ?**

La plus grande différence est que les campagnes ne peuvent fournir qu’un seul point de contact, car les campagnes n’autorisent qu’un seul membre de campagne pour chaque lead ou contact. Cela signifie que vous ne pouvez pas effectuer le suivi d’événements récurrents tels que des appels sortants, des démonstrations ou des participants à des webinaires, sauf si vous créez des campagnes individuelles pour chaque regroupement. Les activités vous permettent de mesurer chaque événement.

**Y a-t-il une différence entre Tâche, Événements et Activités ?**

L&#39;objet Activities agit comme parapluie, ou parent, sur les objets Task et Event. Les activités couvrent essentiellement les tâches et les événements. Les tâches sont généralement utilisées pour enregistrer des éléments ponctuels rapides tels qu’un appel téléphonique ou un e-mail. Les événements sont généralement utilisés pour des éléments pouvant avoir une date de début ou de fin, comme des réunions ou des conférences.

**Si j’ai un lead ou un contact avec la même tâche récurrente, verrai-je apparaître les points de contact de l’acheteur pour toutes ces tâches ?**

Oui. Il existe une relation :1 entre vos activités synchronisées et les points de contact créés.

**Comment savoir quels enregistrements entraînent la création de points de contact ?**

Il est conseillé de configurer vos filtres en utilisant d’abord l’objet Activity dans votre CRM. En fonction des règles de filtrage, vous avez ainsi une bonne idée du nombre d’enregistrements répondant à ce critère, puis vous pouvez l’affiner si nécessaire. Cela n’est pas obligatoire, mais permet aux utilisateurs de comprendre le nombre de points de contact d’activités qui seront créés une fois les règles d’activités configurées.

**Quel est le nom de la campagne [!DNL Marketo Measure] ?**

Comme ces activités génèrent un point de contact, [!DNL Marketo Measure] devez savoir à quel canal et à quel sous-canal elles appartiennent. Pour chaque règle, vous devez fournir un nom de campagne [!DNL Marketo Measure]. Une fois créé, utilisez le fichier CSV des canaux en ligne pour mapper ce nom de campagne [!DNL Marketo Measure] à son canal approprié. Le nom de la campagne [!DNL Marketo Measure] apparaît également sur le point de contact lui-même dans le champ [!UICONTROL Nom de la campagne publicitaire].

**Quels autres champs de point de contact sont renseignés ?**

| **Champ de point de contact** | **Valeur** |
|---|---|
| Lead/Contact | Toutes les activités sont liées à un lead ou à un contact |
| Campagne | Channel.Subchannel [[!DNL Marketo Measure]] |
| Source du point de contact | Activité CRM |
| Support | Activity.Type |
| Type de point de contact | Activity.Type |
| Nom de la campagne publicitaire | Nom de la campagne [!DNL Marketo Measure] |
| Contenu publicitaire | Sujet de l&#39;activité |
| Id De L’Annonce Publicitaire | Identifiant Externe De L’Activité |
| Date du point de contact | [personnalisé - défini dans les applications] |

**Que faire si je dois créer une règle différente pour chaque représentant commercial ? Dois-je créer une campagne [!DNL Marketo Measure] différente pour chacune ?**

Non, pas du tout. « Noms de campagnes dynamiques » vous permet de renseigner une partie (ou la totalité) du nom de campagne [!DNL Marketo Measure] à l’aide d’un « paramètre de remplacement » qui fait référence à un champ de l’objet Activité . Par exemple, si vous avez un nom de campagne [!DNL Marketo Measure] intitulé « Appel sortant » mais que vous souhaitez que le commercial soit à la fin, prenez le nom du champ CRM et appelez le nom de campagne [!DNL Marketo Measure] « {AssignedTo} d’appel sortant » ou « {CreatedBy} d’appel sortant ».

**Comment configurer des activités dans l’application [!DNL Marketo Measure] ?**

Vous trouverez des instructions sur la configuration des activités dans l’application de mesure [!UICONTROL Marketo] dans l’article Prise en charge des activités [!DNL Marketo Measure] .

**Que signifient les différents opérateurs ?**

* est égal à : correspondance exacte avec la valeur (ou : social).
* contient : le texte est au milieu (alias : &#42;social&#42;).
* commence par : la valeur commence par le texte (alias : social&#42;)
* se termine par : la valeur se termine par le texte (alias : &#42;social)
* correspond à n’importe lequel : plusieurs valeurs séparées par des virgules peuvent être ajoutées. Si des opérateurs [!UICONTROL commence par], [!UICONTROL se termine par] ou contient doivent être appliqués, utilisez le caractère générique (&#42;)
* supérieur à : utilisé pour les champs numériques ou les champs date/heure
* inférieur à : utilisé pour les champs numériques ou les champs date/heure

**Sous quel canal ces activités se déroulent-elles ?**

Lorsque la règle Activité et son nom de campagne [!DNL Marketo Measure] correspondant sont créés, utilisez les définitions des canaux en ligne pour placer ces campagnes sous le canal marketing correct. [!DNL Marketo Measure] pouvez définir des canaux à l’aide non seulement du support et de la source, mais également de campaign.

Dans l’exemple ci-dessus, pour affecter la campagne « {Assigned To} d’appel sortant » au canal BDR, insérez une ligne dans le fichier CSV de vos canaux en ligne pour le canal BDR avec une définition de campagne « Appel sortant &#42; » : l’astérisque indique une valeur générique, de sorte que toutes les campagnes commençant par « Appel sortant » seront incluses dans le canal BDR, plutôt que de devoir créer une ligne distincte pour chaque nom de campagne.
