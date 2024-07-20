---
unique-page-id: 18874704
description: FAQ sur l’attribution des activités - [!DNL Marketo Measure]
title: Questions fréquentes sur l’attribution des activités
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 2%

---

# Questions fréquentes sur l’attribution des activités {#activities-attribution-faq}

[!DNL Marketo Measure] Les activités importent tous vos enregistrements d’activité et génèrent des points de contact pour eux, ce qui permet à ces activités de recevoir un crédit d’attribution. Le cas d’utilisation le plus courant consiste à effectuer le suivi des activités de l’équipe de vente, dans la mesure où elles créent généralement un enregistrement des appels téléphoniques ou des emails envoyés aux prospects. Les interactions de contenu, telles que les téléchargements de ressources ou les affichages de vidéos, peuvent également faire l’objet d’un suivi unique.

**En quoi cela diffère-t-il des campagnes hors ligne ?**

La principale différence réside dans le fait que les campagnes ne peuvent fournir qu’un seul point de contact, car elles ne permettent qu’un seul membre de campagne pour chaque prospect ou contact. Cela signifie que vous ne pouvez pas suivre les événements récurrents tels que les appels sortants ou les démonstrations ou les participants au webinaire, sauf si vous créez des campagnes individuelles pour chaque groupe. Les activités vous permettent de mesurer chaque événement.

**Y a-t-il une différence entre la tâche, les événements et les activités ?**

L’objet Activities agit comme un parapluie, ou parent, sur les objets Task et Event. Les activités couvrent essentiellement les tâches et les événements. Les tâches sont généralement utilisées pour enregistrer des éléments ponctuels rapides, tels qu’un appel téléphonique ou un courrier électronique. Les événements sont généralement utilisés pour des éléments qui peuvent avoir une date de début ou de fin, comme des réunions ou des conférences.

**Si je dispose d’un prospect ou d’un contact avec la même tâche récurrente, les points de contact de l’acheteur seront-ils affichés pour toutes ces tâches ?**

Oui. Il existe une relation 1:1 entre vos activités synchronisées et les points de contact créés.

**Comment puis-je savoir quels enregistrements entraînent la création de points de contact ?**

Il est conseillé de configurer d’abord vos filtres à l’aide de l’objet Activité dans votre CRM. En fonction des règles de filtrage, vous avez ainsi une bonne idée du nombre d’enregistrements qui tombent sous ce critère, puis vous pouvez l’affiner selon vos besoins. Cela n’est pas obligatoire, mais un moyen utile pour les utilisateurs de comprendre combien de points de contact d’activités seront créés une fois les règles d’activités configurées.

**Quel est le [!DNL Marketo Measure] nom de la campagne ?**

Puisque ces activités résultent en un point de contact, [!DNL Marketo Measure] doit savoir à quel canal et sous-canal ils appartiennent. Pour chaque règle, vous devez fournir un nom de campagne [!DNL Marketo Measure]. Une fois cela créé, utilisez le fichier CSV Canaux en ligne pour mapper ce nom de campagne [!DNL Marketo Measure] à son canal approprié. Le nom de la campagne [!DNL Marketo Measure] apparaît également sur le point de contact lui-même dans le champ [!UICONTROL Nom de la campagne publicitaire] .

**Quels autres champs de point de contact sont renseignés ?**

| **Champ de point de contact** | **Valeur** |
|---|---|
| Prospérité/Contact | Toutes les activités sont liées à un prospect ou à un contact |
| Campagne | Channel.Subchannel [[!DNL Marketo Measure]] |
| Source du point de contact | Activité CRM |
| Support | Activity.Type |
| Type de point de contact | Activity.Type |
| Nom de la campagne publicitaire | [!DNL Marketo Measure] Nom de la campagne |
| Contenu publicitaire | Objet de l’activité |
| Identifiant de publicité | Activity External Id |
| Date du point de contact | [custom - set in apps] |

**Que faire si je dois créer une règle différente pour chaque représentant commercial ? Dois-je créer une campagne [!DNL Marketo Measure] différente pour chacune ?**

Non, non. Les &quot;Noms de campagne dynamiques&quot; vous permettent de remplir une partie (ou la totalité) du nom de campagne [!DNL Marketo Measure] à l’aide d’un &quot;paramètre de remplacement&quot; qui référence un champ de l’objet d’activité. Par exemple, si vous avez un nom de campagne [!DNL Marketo Measure] intitulé &quot;Appel sortant&quot; mais que vous souhaitez que le représentant commercial soit à la fin, prenez le nom du champ CRM et appelez le nom de campagne [!DNL Marketo Measure] &quot;Appel sortant {AssignedTo}&quot; ou &quot;Appel sortant {CreatedBy}&quot;.

**Comment configurer des activités dans l’application [!DNL Marketo Measure] ?**

Vous trouverez des instructions sur la configuration des activités dans l’application de mesure [!UICONTROL Marketo] dans l’article de prise en charge des activités [!DNL Marketo Measure] .

**Que signifient les différents opérateurs ?**

* est égal à : correspondance exacte avec la valeur (alias : social)
* contient : le texte se trouve au milieu (alias : &#42;social&#42;)
* commence par : la valeur commence par le texte (alias : social&#42;)
* se termine par : la valeur se termine par le texte (alias : &#42;social)
* correspond à n’importe quel : plusieurs valeurs peuvent être ajoutées séparées par des virgules. Si [!UICONTROL commence par], [!UICONTROL  se termine par] ou si des opérateurs doivent être appliqués, utilisez le caractère générique (&#42;)
* supérieur à : utilisé pour les champs numériques ou les champs de date/heure
* inférieur à : utilisé pour les champs numériques ou les champs de date/heure

**Sous quel canal se trouvent ces activités ?**

Lorsque la règle d’activité et son nom de campagne [!DNL Marketo Measure] correspondant sont créés, utilisez les définitions de canaux en ligne pour placer ces campagnes sous le canal marketing approprié. [!DNL Marketo Measure] peut définir des canaux à l’aide non seulement de supports et de sources, mais aussi de campagnes.

Dans l’exemple ci-dessus, pour affecter la campagne &quot;Appel sortant {Affecté à}&quot; au canal BDR, insérez une ligne dans votre fichier CSV Canaux en ligne pour le canal BDR avec une définition de campagne de &quot;Appel sortant&#42;&quot;. L’astérisque indique une valeur de caractère générique, de sorte que toutes les campagnes commençant par &quot;Appel sortant&quot; tomberont sous le canal BDR, plutôt que de devoir créer une ligne distincte pour chaque nom de campagne.
