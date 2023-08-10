---
unique-page-id: 18874660
description: FAQ - [!DNL Marketo Measure] - Documentation du produit
title: Questions fréquentes
exl-id: f1896bf8-2216-427e-ac3e-98d87efede76
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---

# Questions fréquentes {#faq}

[!DNL Marketo Measure Discover]: Questions fréquentes.

**Comment enregistrer les filtres sur un rapport ?**

Comme aujourd’hui, les résultats de la requête sont enregistrés dans l’URL et peuvent être enregistrés ou partagés avec l’URL copiée.

**Comment utiliser des périodes prédéfinies comme l’année dernière ou le trimestre en cours ?**

Plutôt que d’utiliser des périodes prédéfinies, nous avons désormais ajouté une flexibilité de date. Vous pouvez toujours définir l’année dernière, mais vous avez la possibilité de sélectionner 1 an dernier , qui correspond aux 365 derniers jours à partir d’aujourd’hui ou 1 année complète la plus récente année complète, du 1/1 au 12/31. Le nouveau sélecteur de date permet également de définir une plage de dates relative, ce qui aura tendance à donner une fenêtre de temps variable pour une date mobile.

**Comment obtenir des données CPL ou CPC ?**

Ces mesures sont disponibles uniquement sur la carte Média payant .

**Pourquoi n’affichez-vous pas Pages vues sur le Forum de croissance ?**

L’une des fonctionnalités du tableau Croissance est que vous ne pouvez pas regrouper les graphiques de tendance par dimension, comme Canal ou Campagne. Ces données ne sont pas disponibles au niveau des pages vues, car les pages vues n’ont pas toujours de source telle que Canal ou Campagne, car elles se produisent au milieu des visites web. Utilisez des médias payants ou du trafic web pour afficher les données de pages vues.

**Lorsque je modifie le groupement, les totaux ne correspondent pas toujours au même montant. Pourquoi ?**

Les valeurs n’existent pas pour chaque hiérarchie de données, car la hiérarchie n’est pas toujours un flux de découpe clair. Par exemple, que les coûts soient auto-déclarés ou importés d&#39;un fournisseur d&#39;annonces, le coût total du canal 1 peut être de 10 000 euros, mais par campagne individuelle, seul un total de 5 500 euros a été réellement reporté. Ainsi, lorsque le regroupement change entre les canaux et Campaign, les totaux varient.

**Qu’est-ce que &quot;correspond à un attribut utilisateur&quot; dans les opérateurs de filtre ?**

Les attributs utilisateur sont appliqués aux utilisateurs tels que l’identifiant de l’entreprise, le prénom ou le nom, mais comme nos utilisateurs sont vous (nos clients), et non vos clients, les attributs utilisateur ne peuvent pas être utilisés dans la variable [!DNL Marketo Measure Discover] expérience. N&#39;hésitez pas à ignorer cette option. Nous travaillons à une meilleure expérience de filtrage personnalisé qui supprimera les filtres qui ne s’appliquent pas à nos clients.

**Comment se fait-il que certaines périodes par défaut passent par le premier du mois suivant ?**

Bien que la période ne soit pas toujours intuitive, l’interface utilisateur du filtre par défaut comporte le texte &quot;précédent&quot; utile qui correspond à la date de fin. Cela devrait vous rappeler que la date de fin que vous utilisez doit être d’un jour en dehors de la période souhaitée.

**Quel modèle d’attribution est utilisé pour les Leads et les contacts ?**

Les points de contact des acheteurs mappés aux pistes et aux contacts mesurent jusqu’à la touche Création de piste. Il est donc recommandé d’utiliser les modèles Première touche, Création de piste et En forme de U. Si vous remplacez le modèle d’attribution par le modèle en forme de W ou chemin complet, nous appliquons automatiquement un modèle en forme de U pour les pistes et les contacts.

**Pourquoi mes mosaïques Visites, Visites uniques et Forms sont-elles vides sur le Forum de croissance ?**

Si ces mosaïques sont nulles ou vides dans votre vue, cela signifie que les mosaïques ne sont pas configurées pour votre compte. Contactez votre gestionnaire de succès si vous avez des questions à ce sujet.

**Pour Leads au fil du temps et Contacts au fil du temps, quel est le nombre qui fait référence ?**

Il utilise les nombres de points de contact, distribués par le modèle d’attribution que vous sélectionnez. Il s’agira du total des Pistes et des Comptabilisation distribués au fil du temps. Ce n&#39;est pas un nombre unique.

**Le graphique des URL de formulaire par canal dans Marketing du contenu indique-t-il les visites web ou les remplissages de formulaire ?**

Ils ne sont suivis que les remplissages de formulaires.

**Quel est l’avantage de Discover sur la mesure ?**

[!DNL Marketo Measure Discover] offre de meilleures fonctionnalités, telles que des analyses publicitaires et un meilleur filtrage, comme les sous-canaux et les canaux. Nous sommes aussi en train de coucher le soleil Mesure quelque temps en 2019.

**En mesure, j’ai pu filtrer par groupe publicitaire et par compte lorsqu’il était filtré dans des comptes publicitaires. Comment puis-je le voir dans Discover ?**

Cette option est disponible uniquement avec le panorama des médias payants.

**En quoi l’entonnoir de cohortes est-il différent de l’entonnoir de port ?**

L’entonnoir de cohortes vous permet d’examiner le taux de conversion de votre entonnoir de vente, en mesurant l’impact entre les étapes. Vous pouvez sélectionner l’étape à mesurer à partir des filtres, ce qui vous permettra d’afficher le taux de conversion de cette étape à toutes les étapes suivantes. Le tableau des passeports présente tous les Leads/contacts et opportunités qui ont passé par chaque étape de pipeline au cours d’une période donnée.

**Comment le contenu du panorama des médias payants est-il déterminé ?**

Sur chacune des mosaïques de panorama, nous avons ajouté un filtre pour inclure uniquement les données pour lesquelles nous disposons d’un fournisseur d’annonces connu de Facebook, Google, Bing, LinkedIn ou Doubleclick, car notre intégration nous permet d’extraire les données d’annonces de ces sources. En outre, nous avons ajouté un nom approximatif correspondant aux canaux et sous-canaux pour l’affichage, la recherche payante, les réseaux sociaux payants, PPC, SEM, mobile payant, le Twitter payant, l’appel, l’arrêt, Madison Logic, Madisonlogic et Demandbase.

**Quelle est la différence entre les visites et les visites uniques ?**

Les visites uniques sont un sous-ensemble de visites. Alors que les visites sont un comptage de chaque visite du site, les visites uniques sont des cookies uniques de ces visites. Une personne peut comptabiliser plusieurs visites uniques si elle revient avec un autre identifiant de cookie.

**Les points de contact sont-ils comptabilisés dans le nombre de points de contact des acheteurs ou de points de contact d’attribution des acheteurs ?**

Il s’agit d’un comptage de ce que nous considérons comme des points de contact &quot;bruts&quot;, ou &quot;points de contact utilisateur&quot;, où il s’agit d’un agrégat des deux, plus des touches qui n’ont pas entraîné de point de contact sur le prospect/contact ou l’opportunité.

**Lorsque je filtre par URL, pourquoi le coût par mosaïque n’affiche-t-il que 0,00 $ ?**

Il s’agit du comportement attendu en raison du fait que nous n’avons pas de coûts segmentés par URL. Il n’est donc pas applicable dans ce scénario.

**Pourquoi toutes les options de Segment ne s’affichent-elles pas pour mes filtres de catégorie ?**

Seuls les segments auxquels des enregistrements valides sont associés s’affichent dans le filtre Segments . Par exemple, s’il n’existe aucun enregistrement avec le segment &quot;Autre&quot;, &quot;Autre&quot; ne s’affiche pas comme option.

**Does [!DNL Marketo Measure Discover] prendre en charge le jeu de caractères GB18030 ?**

Discover utilise des outils tiers et ne prend actuellement pas en charge le jeu de caractères GB18030.

**Lors du chargement de Discover, pourquoi une erreur 401 s’affiche-t-elle indiquant &quot;Vous n’êtes pas authentifié pour afficher cette page&quot; ?**

[!DNL Marketo Measure Discover] nécessite l’affichage correct des cookies tiers. Pour utiliser Discover, activez les cookies tiers dans votre navigateur et actualisez la page.

>[!NOTE]
>
>Certains navigateurs, y compris Chrome dans Incognito, désactivent par défaut les cookies tiers.

![](assets/faq-1.png)