---
unique-page-id: 18874604
description: Segmentation personnalisée - [!DNL Marketo Measure] - Documentation du produit
title: Segmentation personnalisée
exl-id: c20a2add-250e-45ff-97a6-1b1c03351b6a
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Segmentation personnalisée {#custom-segmentation}

Les segments permettent de filtrer les données dans la variable [!DNL Marketo Measure] Tableau de bord du ROI afin d’approfondir l’analyse d’un jeu de données spécifique. Par exemple, un segment peut être défini par un territoire géographique ou un système de classement.

**Pourquoi la segmentation personnalisée ?**

La fonction Segmentation personnalisée vous permet de filtrer les points de contact par catégorie et par cinq segments au maximum. Selon l’objet vers lequel pointe votre tiret de retour sur investissement (prospect ou contact), vous pouvez créer des segments en fonction des champs figurant dans l’objet de piste/contact. Vous pourrez également créer des segments en fonction de n’importe quel champ de l’objet d’opportunité.

**Quand la fonction Segmentation personnalisée est-elle utile ?**

La segmentation personnalisée peut être utilisée pour afficher les données d’un type d’enregistrement particulier. Une fois que vous avez mappé la logique de filtre, vous devriez être en mesure de voir dans le [!DNL Marketo Measure] Vue de la cascade de la demande du tableau de bord : les mêmes données que celles affichées dans votre gestion de la relation client.

**Comment puis-je le configurer ?**

Étape 1 - Déterminer les informations que vous souhaitez voir.

Avant d’utiliser cette fonction, déterminez les informations de point de contact que vous souhaitez filtrer. N’oubliez pas d’utiliser les valeurs exactes dans votre CRM pour vos types d’enregistrements. La configuration va filtrer les points de contact du haut vers le bas de l’entonnoir marketing.

Étape 2 - Connectez-vous et recherchez la fonction Segments .

* Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et se connecter
* Sous , [!UICONTROL Mon compte] onglet, sélectionnez [!UICONTROL Paramètres]
* Sélectionner [!UICONTROL Segments] des options de la barre latérale gauche, sous la [!UICONTROL Reporting] section

Étape 3 - Comprendre les composants.

* Utilisez cette légende pour comprendre les différentes icônes de cette page.

![](assets/1.png)

Étape 4 - Ajout de règles de filtrage.

* Saisissez tout d’abord le nom de la catégorie. Business Type est un exemple. Cliquez sur la coche lorsque vous avez terminé. Vous devez saisir un nom de catégorie avant d’ajouter des segments.
* Cliquez sur le signe plus pour ajouter un segment.
* Saisissez un Nom de segment. Par exemple, vous pouvez avoir un segment pour Nouvelle entreprise, Partenaires, Renouvellement ou Mise à niveau.

![](assets/2.png)

* Cliquez sur l’icône plus pour afficher les champs de saisie de règle. Les options de la liste de sélection de champs extrait directement les champs de votre CRM.

![](assets/3.png)

>[!NOTE]
>
>Les champs de formule ne peuvent pas être utilisés dans vos règles et n’apparaîtront pas dans la liste de sélection. Parce que les formules sont calculées en arrière-plan et ne modifient pas d&#39;enregistrement, [!DNL Marketo Measure] ne peut pas détecter si un enregistrement correspond à une règle ou non.

* L’option Valeur n’est pas une liste déroulante et sa valeur doit être saisie manuellement. Veillez à vérifier les valeurs de votre organisation Salesforce.
* Répétez ce processus pour les règles de segment Opportunités .
* La catégorie &quot;Autre&quot; est un segment par défaut qui capture tous les points de contact non définis. Vous pouvez modifier le nom du segment par défaut.
* Cliquez sur l’icône de corbeille pour supprimer une catégorie entière ou une règle individuelle dans une catégorie. Vous pouvez également cliquer sur l’icône en forme de crayon pour modifier la catégorie ou la règle.
* Vous remarquerez que vous avez un bouton &quot;Enregistrer&quot; et un bouton &quot;Enregistrer et traiter&quot;. Utilisez le bouton Enregistrer pour enregistrer votre travail et vos modifications au fil du temps. Utilisez le bouton Enregistrer et traiter UNIQUEMENT une fois que vous avez vérifié que :

   * Votre mappage est précis
   * Vous avez ajouté tous les segments dont vous souhaitez effectuer le suivi dans une catégorie.
   * Le bouton Save and Process se déclenche. [!DNL Marketo Measure] pour synchroniser tous vos points de contact et appliquer les nouvelles informations que vous avez ajoutées. Ce processus prend 7 jours et les règles ne peuvent pas être modifiées pendant cette période.

**_Remarques supplémentaires :_**

Si les règles ne sont pas configurées pour les pistes/contacts et les opportunités, seules une partie de vos données s’affiche. Pour plus d’informations, si vous ne configurez pas les règles d’opportunités, vous verrez uniquement les données de piste/contact sans les opportunités qui y sont associées. Il en va de même si vous ne définissez pas de règles pour les Leads/Contacts, vous ne verrez que les opportunités sans les Leads/Contacts associés.

Lorsque vous avez terminé, cliquez sur [!UICONTROL Enregistrer] d’abord, double-vérifiez tout, puis cliquez sur [!UICONTROL Enregistrement et traitement]. N’oubliez pas que vous ne pourrez pas modifier vos paramètres pendant les sept jours qui suivent l’enregistrement et le traitement, comme suit : [!DNL Marketo Measure] reformate vos données pendant cette période.

**Comment enregistrer les rapports générés ?**

Vous ne pouvez pas enregistrer les rapports générés directement dans l’interface utilisateur. Cependant, [!DNL Marketo Measure] enregistre les noms des segments dans l’URL afin que vous puissiez conserver un enregistrement de chaque rapport en marquant la page.
