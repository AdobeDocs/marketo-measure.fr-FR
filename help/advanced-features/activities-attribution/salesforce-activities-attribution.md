---
description: Attribution des activités Salesforce - [!DNL Marketo Measure]
title: Attribution des activités Salesforce
exl-id: 1dc6f15b-2a45-4ed3-9fa3-5267366d1f45
feature: Attribution, Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 1%

---


# Attribution des activités Salesforce {#salesforce-activities-attribution}

L’intégration des activités [!DNL Marketo Measure] Salesforce intègre des enregistrements de tâches et d’événements spécifiques à votre modèle d’attribution. Commencez à suivre des éléments tels que les e-mails de vente ou les appels téléphoniques de vente qui ne recevaient pas le crédit dû. Pour configurer votre règle d’activités, accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. De là, accédez à l’onglet **[!UICONTROL Paramètres]** et cliquez sur l’onglet **[!UICONTROL Activités]**.

![Onglet Paramètres affichant la page de configuration des activités pour les règles d’attribution](assets/1.png)

>[!AVAILABILITY]
>
>Cette fonctionnalité est activée uniquement pour les clients de niveau 2. Pour demander un niveau de compte supérieur, contactez l’équipe du compte Adobe (votre gestionnaire de compte).

Pour commencer, nous introduisons un nouveau concept appelé Campagne [!DNL Marketo Measure]. Pour chaque règle que vous définissez, vous allez regrouper les enregistrements dans une campagne [!DNL Marketo Measure] que vous pouvez nommer. Ajoutez plusieurs campagnes selon les besoins. Imaginez mesurer l’efficacité d’une campagne de ventes sortantes à côté d’une campagne de médias payants !

Vous allez utiliser ce nom de campagne [!DNL Marketo Measure] pour nous indiquer à quel canal il doit être mappé. Si vous pensez toujours aux ventes sortantes, peut-être que toutes les campagnes de ventes sortantes doivent se trouver dans un canal BDR.

Familiarisez-vous avec cette hiérarchie :

* Canal
   * Sous-canal
      * Campagne
      * Campagne
   * Sous-canal
      * Campagne

>[!TIP]
>Si vous souhaitez définir une campagne unique pour chaque représentant commercial, par exemple, utilisez des paramètres de remplacement dynamique pour renseigner le nom de la campagne [!DNL Marketo Measure]. Dans le même exemple, vous pouvez saisir `"Outbound Sales - {AssignedTo}"` et le remplacer par `"Outbound Sales - Jill"` ou `"Outbound Sales - Jack."`

![Exemple de paramètre de remplacement dynamique pour le champ Nom de la campagne pour les ventes sortantes](assets/2.png)

Une fois le nom de la campagne [!DNL Marketo Measure] défini, il est temps de configurer vos règles d’activité.

Les règles agissent comme un filtre pour nous indiquer les enregistrements éligibles à l’attribution. Imaginons que vous créiez un rapport dans votre CRM en suivant une logique similaire pour générer ce rapport. Vous avez la possibilité d’utiliser une combinaison d’instructions et/ou et de divers opérateurs tels que `matches any`, `contains`, `starts with`, `ends with`, `is equal to`. Définissez des instructions de `and` dans une règle ou un calque encadré `or` des instructions en dehors de la boîte.

![Interface de configuration des règles d’activité affichant les critères de filtre avec les options d’instruction et/ou](assets/3.png)

>[!NOTE]
>Les champs de formule ne peuvent pas être utilisés dans vos règles et n&#39;apparaîtront pas dans la liste de sélection. Étant donné que les formules calculent en arrière-plan et ne modifient pas un enregistrement, [!DNL Marketo Measure] ne pouvez pas détecter si un enregistrement correspond ou non à une règle.
>Veillez à utiliser des valeurs correctes pour les champs d’ID tels que CrmEvent.CreatedById. [!DNL Salesforce IDs] 18 caractères ( 0054H000007WmrfQAC).

Enfin, choisissez l’un de vos champs de date ou de date/heure à utiliser comme date Buyer Touchpoint. Les champs standard et personnalisés peuvent être sélectionnés.

>[!TIP]
>Avec l’installation de votre package, [!DNL Marketo Measure] inclut un champ de date Buyer Touchpoint personnalisé dans l’enregistrement d’activité. Si vous souhaitez utiliser une date dynamique, comme la date de modification d’un statut, il est possible d’utiliser un workflow CRM pour définir la « Date du Buyer Touchpoint », puis sélectionnez la Date du Buyer Touchpoint ici à cette étape.

![Sélection du champ de date Buyer Touchpoint affichant les options de champ de date standard et personnalisées](assets/4.png)

N’oubliez pas de définir des règles différentes pour les tâches ou les événements. Vous devez savoir quel objet votre équipe commerciale utilise pour enregistrer ses activités.

![Sélecteur de type d’objet affichant les options Tâches et Événements pour les règles d’activité](assets/5.png)

Vous souhaiterez probablement placer ces nouveaux points de contact dans leur [canal marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Channels.Online%20Channels){target="_blank"} approprié. Pour ce faire, définissez le canal avec son nouveau mapping de campagne qui vient d’être créé.

>[!TIP]
>Lors de l’ajout d’une définition de canal , utilisez des valeurs génériques, un moyen plus facile de définir des opérateurs tels que :
>commence par ( Sortant&#42; )
>contient ( &#42;Sortant&#42; )
>se termine par ( &#42;Sortant )
>Aucun caractère joker ne signifie fondamentalement « est égal à ». Veillez donc à les utiliser selon vos besoins.

| Opérateur | Exemple d’utilisation |
|---|---|
| Est égal à | Valeur unique - correspondance exacte |
| Contient | Valeur unique - contient la valeur |
| Correspond à l’un des | Valeurs multiples - Correspondance exacte |
| Correspond À N’Importe Quel (Contient) | Valeurs multiples : &#42;value&#42;, &#42;value, &#42;value&#42; |

![Page de configuration du canal marketing présentant le mappage de la campagne avec les options d’opérateur de caractères génériques](assets/6.png)

Enfin et surtout, vous avez la possibilité de saisir les coûts de vos nouveaux canaux. Le [&#x200B; Chargement des dépenses marketing &#x200B;](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Reporting.Marketing%20Spend){target="_blank"} vous permet de saisir vos dépenses au niveau du canal, du sous-canal ou de la campagne. Avec vos nouvelles campagnes [!DNL Marketo Measure], vous pouvez ajouter ces coûts associés par mois, puis afficher le retour sur investissement de chaque campagne.

![Interface de chargement des dépenses marketing pour saisir les coûts de canal par mois avec le suivi du retour sur investissement](assets/7.png)

>[!MORELIKETHIS]
>[FAQ sur l’attribution des activités](/help/advanced-features/activities-attribution/activities-attribution-faq.md)
