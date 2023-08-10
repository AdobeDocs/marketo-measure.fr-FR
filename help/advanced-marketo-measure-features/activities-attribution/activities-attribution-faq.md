---
unique-page-id: 18874704
description: FAQ sur l’attribution des activités - [!DNL Marketo Measure] - Documentation du produit
title: Questions fréquentes sur l’attribution des activités
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 3%

---

# Questions fréquentes sur l’attribution des activités {#activities-attribution-faq}

La variable [!DNL Marketo Measure] La fonctionnalité Activités nous permet d’importer tous vos enregistrements d’activité et de générer des points de contact pour eux, ce qui permet à ces activités de recevoir un crédit d’attribution. Le cas d’utilisation le plus courant consiste à effectuer le suivi des activités de l’équipe de vente, dans la mesure où elles créent généralement un enregistrement des appels téléphoniques ou des emails envoyés aux prospects. Les interactions de contenu, telles que les téléchargements de ressources ou les affichages de vidéos, peuvent également faire l’objet d’un suivi unique.

**En quoi cela diffère-t-il des campagnes hors ligne ?**

La principale différence réside dans le fait que les campagnes ne peuvent fournir qu’un seul point de contact, car elles ne permettent qu’un seul membre de campagne pour chaque prospect ou contact. Cela signifie que vous ne pouvez pas suivre les événements récurrents tels que les appels sortants ou les démonstrations ou les participants au webinaire, sauf si vous créez des campagnes individuelles pour chaque groupe. Les activités vous permettront de mesurer chaque événement.

**Y a-t-il une différence entre la tâche, les événements et les activités ?**

L’objet Activities agit comme un parapluie, ou parent, sur les objets Task et Event. Les activités couvrent essentiellement les tâches et les événements. Les tâches sont généralement utilisées pour enregistrer des éléments ponctuels rapides, tels qu’un appel téléphonique ou un courrier électronique. Les événements sont généralement utilisés pour des éléments qui peuvent avoir une date de début ou de fin, comme des réunions ou des conférences.

**Si je dispose d’un prospect ou d’un contact avec la même tâche récurrente, telle qu’un email ou un appel, les points de contact de l’acheteur s’afficheront-ils pour tous ?**

Oui. Il y aura une relation 1:1 entre vos activités synchronisées et les points de contact créés.

**Comment savoir quels enregistrements vont entraîner la création de points de contact ?**

Il est conseillé de configurer d’abord vos filtres à l’aide de l’objet Activité dans votre CRM. En fonction des règles de filtrage, cela vous donnera une bonne idée du nombre d’enregistrements qui tombent sous ce critère, puis vous pourrez l’affiner au besoin. Cela n’est pas obligatoire, mais un moyen utile pour les utilisateurs de comprendre combien de points de contact d’activités seront créés une fois les règles d’activités configurées.

**Qu’est-ce que la variable [!DNL Marketo Measure] Nom de la campagne ?**

Puisque ces activités auront pour résultat un point de contact, [!DNL Marketo Measure] doit savoir à quel canal et sous-canal ils appartiennent. Pour chaque règle, vous devrez fournir un [!DNL Marketo Measure] Nom de la campagne. Une fois créé, vous pouvez utiliser le fichier CSV Canaux en ligne pour mapper ce [!DNL Marketo Measure] Nom de la campagne sur son canal approprié. La variable [!DNL Marketo Measure] Le nom de la campagne s’affiche également sur le point de contact lui-même dans la variable [!UICONTROL Nom de la campagne publicitaire] champ .

**Quels autres champs de point de contact sont renseignés ?**

| **Champ de point de contact** | **Valeur** |
|---|---|
| Prospect/contact | Toutes les activités sont liées à un prospect ou à un contact |
| Campagne | Channel.Subchannel [[!DNL Marketo Measure]] |
| Source du point de contact | Activité CRM |
| Support | Activity.Type |
| Type de Touchpoint | Activity.Type |
| Nom de la campagne publicitaire | [!DNL Marketo Measure] Nom de campagne |
| Contenu publicitaire | Objet de l’activité |
| Identifiant de publicité | Activity External Id |
| Date du Touchpoint | [custom - défini dans les applications] |

**Que faire si je dois créer une règle différente pour chaque représentant commercial ? Dois-je créer des [!DNL Marketo Measure] Campagnes pour chacune ?**

Non, non. Nous avons introduit un concept de &quot;noms de campagne dynamique&quot;. Cela vous permet de remplir une partie (ou la totalité) de la variable [!DNL Marketo Measure] Nom de la campagne à l’aide d’un &quot;paramètre de remplacement&quot; qui fait référence à un champ de l’objet d’activité. Par exemple, si vous avez une [!DNL Marketo Measure] Nom de la campagne intitulé &quot;Appel sortant&quot; mais que vous souhaitez que le représentant commercial soit à la fin, prenez le nom du champ CRM et appelez le [!DNL Marketo Measure] Nom de la campagne &quot;Appel sortant {AssignedTo}&quot; ou &quot;Appel sortant {CreatedBy}.&quot;

**Comment configurer des activités dans le [!DNL Marketo Measure] application ?**

Instructions sur la configuration des activités dans [!UICONTROL Marketo] L’application de mesure se trouve dans la variable [!DNL Marketo Measure] Article relatif à la prise en charge des activités.

**Que signifient les différents opérateurs ?**

* est égal à : correspondance exacte avec la valeur (alias : social)
* contient : le texte se trouve au milieu (c’est-à-dire : &#42;social&#42;)
* commence par : la valeur commence par le texte (alias : social&#42;)
* se termine par : la valeur se termine par le texte (alias : &#42;social)
* correspond à n’importe quel : plusieurs valeurs peuvent être ajoutées séparées par des virgules. If [!UICONTROL commence par], [!UICONTROL se termine par], ou contient des opérateurs qui doivent être appliqués, utilisez le caractère générique (&#42;)
* supérieur à : utilisé pour les champs numériques ou les champs de date/heure
* inférieur à : utilisé pour les champs numériques ou les champs de date/heure

**À quel canal ces activités se trouveront-elles ?**

Une fois la règle d’activité et sa [!DNL Marketo Measure] Nom de la campagne, sont créées. Utilisez les définitions des canaux en ligne pour placer ces campagnes sous le canal marketing approprié. [!DNL Marketo Measure] permet de définir des canaux à l’aide non seulement de supports et de sources, mais aussi de campagnes.

Dans l’exemple ci-dessus, pour affecter la campagne &quot;Appel sortant {Affecté à}&quot; au canal BDR, vous souhaiterez insérer une ligne dans votre fichier CSV Canaux en ligne pour le canal BDR avec une définition de campagne de &quot;Appel sortant&quot;.&#42;&quot; : l’astérisque indique une valeur de caractère générique, de sorte que toutes les campagnes commençant par &quot;Appel sortant&quot; tombent sous le canal BDR, plutôt que d’avoir à créer une ligne distincte pour chaque nom de campagne.
