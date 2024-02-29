---
unique-page-id: 18874708
description: Attribution des activités Salesforce - [!DNL Marketo Measure]
title: Attribution des activités Salesforce
exl-id: 1dc6f15b-2a45-4ed3-9fa3-5267366d1f45
feature: Attribution, Salesforce
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%

---

# Attribution des activités Salesforce {#salesforce-activities-attribution}

La variable [!DNL Marketo Measure] L’intégration des activités Salesforce intègre des enregistrements de tâches et d’événements spécifiques à votre modèle d’attribution. Commencez à effectuer le suivi d’éléments tels que les e-mails de vente ou les appels téléphoniques de vente qui n’étaient pas crédités. Pour configurer votre règle d’activités, accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. À partir de là, accédez au **[!UICONTROL Paramètres]** et cliquez sur l’onglet **[!UICONTROL Activités]** .

![](assets/1.png)

Pour commencer, nous introduisons un nouveau concept appelé un [!DNL Marketo Measure] Campagne. Pour chaque règle que vous définissez, vous allez regrouper les enregistrements dans une [!DNL Marketo Measure] Campagne que vous pouvez nommer. Ajoutez plusieurs campagnes selon vos besoins. Imaginez mesurer l’efficacité d’une campagne de ventes sortantes à côté d’une campagne de médias payants !

Vous allez utiliser ceci. [!DNL Marketo Measure] Nom de la campagne pour indiquer à quel canal il doit être mappé. Si vous pensez toujours aux ventes sortantes, peut-être que toutes les campagnes de ventes sortantes doivent être placées dans un canal BDR.

Familiarisez-vous avec cette hiérarchie :

* Canal
   * Sous-canal
      * Campagne
      * Campagne
   * Sous-canal
      * Campagne

>[!TIP]
>
>Si vous souhaitez définir une campagne unique pour chaque représentant commercial, par exemple, utilisez des paramètres de remplacement dynamiques pour renseigner la variable [!DNL Marketo Measure] Nom de la campagne. Dans le même exemple, vous pouvez saisir `"Outbound Sales - {AssignedTo}"` et il le transforme en quelque chose comme `"Outbound Sales - Jill"` ou `"Outbound Sales - Jack."`

![](assets/2.png)

Une fois votre [!DNL Marketo Measure] Nom de la campagne est défini. Il est temps de configurer vos règles d’activité.

Les règles agissent comme un filtre pour nous indiquer les enregistrements éligibles à l’attribution. Imaginez que vous créez un rapport dans votre CRM en utilisant une logique similaire pour générer ce rapport. Vous avez la possibilité d’utiliser une combinaison d’instructions et/ou et divers opérateurs tels que `matches any`, `contains`, `starts with`, `ends with`, `is equal to`. Définir `and` instructions dans une règle ou un calque encadré `or` à l’extérieur de la zone.

![](assets/3.png)

>[!NOTE]
>
>Les champs de formule ne peuvent pas être utilisés dans vos règles et n’apparaîtront pas dans la liste de sélection. Parce que les formules sont calculées en arrière-plan et ne modifient pas d&#39;enregistrement, [!DNL Marketo Measure] ne peut pas détecter si un enregistrement correspond à une règle ou non.
>
>Veillez à utiliser les valeurs correctes pour les champs d’ID tels que CrmEvent.CreatedById. [!DNL Salesforce IDs] comportent 18 caractères ( 0054H000007WmrfQAC).

Enfin, choisissez l’un de vos champs Date ou Date/Heure à utiliser comme Date de point de contact de l’acheteur. Les champs standard et personnalisés peuvent être sélectionnés.

>[!TIP]
>
>Avec l’installation de votre package, [!DNL Marketo Measure] inclut un champ Date de point de contact d’achat personnalisé dans l’enregistrement d’activité. Si vous souhaitez utiliser une date dynamique, comme la date de changement d’état, il est possible d’utiliser un workflow CRM pour définir la &quot;Date du point de contact de l’achat&quot; puis sélectionnez la Date du point de contact de l’achat ici à cette étape.

![](assets/4.png)

N’oubliez pas de définir des règles différentes pour les tâches ou les événements. Vous devez connaître l’objet utilisé par votre équipe de vente pour enregistrer leurs activités.

![](assets/5.png)

Vous souhaiterez probablement placer ces nouveaux points de contact dans les [Canal marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Channels.Online%20Channels){target="_blank"}. Pour ce faire, définissez le canal avec son nouveau mapping Campaign qui vient d&#39;être créé.

>[!TIP]
>
>Lors de l’ajout d’une définition de canal, utilisez des valeurs génériques, un moyen plus facile d’afficher les opérateurs tels que :
>
>commence par ( sortant&#42; )
>
contient ( &#42;Sortant&#42; )
>
se termine par ( &#42;Sortant )
>
Aucun caractère générique ne signifie en fait &quot;est égal à&quot;. Veillez donc à les utiliser selon vos besoins.

| **Opérateur** | **Cas d’utilisation** |
|---|---|
| Est égal à | Valeur unique : correspondance exacte |
| Contient | Valeur unique : contient la valeur |
| Correspond à n’importe quel | Plusieurs valeurs - Correspondance exacte |
| Correspond à n’importe quel (contient) | Plusieurs valeurs - &#42;value&#42;, &#42;value, &#42;value&#42; |

![](assets/6.png)

Enfin et surtout, vous avez la possibilité de saisir les coûts de vos nouveaux canaux. La variable [Chargement des dépenses marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Reporting.Marketing%20Spend){target="_blank"} vous permet de saisir vos dépenses au niveau du canal, du sous-canal ou de la campagne. Avec votre nouvelle [!DNL Marketo Measure] Pour les campagnes, vous pouvez ajouter ces coûts par mois, puis consulter le retour sur investissement de chaque campagne.

![](assets/7.png)

>[!MORELIKETHIS]
>
[FAQ sur l’attribution d’activités](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
