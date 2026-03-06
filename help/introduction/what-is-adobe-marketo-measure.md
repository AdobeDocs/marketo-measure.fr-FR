---
description: Qu’est-ce que Adobe Marketo Measure ?
title: Qu’est-ce que Adobe Marketo Measure ?
hide: true
hidefromtoc: true
source-git-commit: 7c3f586e308ba885d10f3f9b8925af93277ad2e0
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---

# Qu’est-ce que Adobe Marketo Measure ? {#what-is-adobe-marketo-measure}

Adobe Marketo Measure (anciennement Bizible) est une plateforme d’attribution multipoint de premier plan.

Il consolide les données provenant de sources de données disparates (CRM, automatisation du marketing, site web, etc.). Lorsque ces données se trouvent à un seul emplacement, une série temporelle d’événements (les points de contact susmentionnés) est créée pour chaque personne, identifiée par son adresse e-mail unique.

Ces points de contact sont ensuite associés aux opportunités par le biais des méthodologies basées sur le compte ou sur le rôle du contact d’opportunité, afin que nous puissions réattribuer les opportunités aux différents points de contact qui ont joué un rôle dans le parcours de chaque opportunité.

À l’aide de divers modèles d’attribution basés sur des règles et sur la position (que nous allons examiner plus en détail plus loin), chaque point de contact associé à une opportunité se voit attribuer un poids, qui attribue ensuite une valeur monétaire à chaque point de contact.

Comme chaque point de contact est un canal, un sous-canal, une campagne et d’autres segments définis, il vous permet de déterminer les activités marketing les plus fortement corrélées aux opportunités et aux succès.

Parlons un peu plus de la façon dont cela fonctionne
Fonctionnement de Marketo Measure
Marketo Measure s’intègre à de nombreux outils de votre tech stack. Il s’intègre également directement aux plateformes publicitaires répertoriées ci-dessous.

●    Google Ads
●    Bing Ads
●    Facebook/Meta
●    LinkedIn

Ces intégrations permettent de résoudre le trafic des campagnes multimédias payantes en campagne publicitaire exacte à partir de ces plateformes, lorsque le balisage automatique est activé.

Ces intégrations ingèrent également automatiquement toutes les dépenses publicitaires et de campagne publicitaire de ces plateformes, directement dans la plateforme Marketo Measure.

Remarque : ces intégrations ne peuvent pas importer de points de contact dans les jardins murés de médias payants, à l’exception de l’intégration du formulaire de génération de leads LinkedIn. Cela signifie que vous n&#39;obtenez pas de points de contact pour des choses comme des commentaires, des partages et des likes... ou toute autre interaction qui se produit uniquement à l&#39;intérieur de ces plateformes.
Marketo Measure dispose également d’un javascript qui est placé sur votre site web et qui crée des points de contact à partir des interactions web. Ces points de contact sont ensuite classés en canaux et sous-canaux en fonction des règles qui utilisent les paramètres UTM, les informations de campagne, les pages de destination et/ou les URL de référence. Vous trouverez plus d’informations sur cette fonctionnalité ultérieurement.

Il s’intègre également à votre CRM pour importer des opportunités, des comptes, des contacts, des leads, des rôles de contact d’opportunité, des campagnes, des membres de campagne et des activités (tâches et événements). Cette intégration vous permet de configurer des règles qui créent des points de contact à partir de l’appartenance à Campaign ainsi que des activités consignées pour une personne (appels téléphoniques, e-mails, réunions, etc.). Pour plus d’informations sur ces paramètres, reportez-vous à la section suivante.

Marketo Measure peut également s’intégrer directement à Marketo Engage. Cette intégration vous permet de créer des règles qui créent des points de contact à partir de l’appartenance au programme ainsi que du journal d’activité de Marketo. Nous allons également explorer plus en détail cette fonctionnalité.

Avec toutes ces données, vous créez maintenant des points de contact à partir d&#39;une pléthore de sources de données différentes. Un canal et, dans certains cas, un sous-canal sont ensuite attribués à ces points de contact. Les points de contact sont ainsi classés en fonction de leur origine.

Un poste est également attribué aux points de contact. Cette position est basée sur l’endroit où se trouve le point de contact dans le processus d’achat et le parcours. Il existe quatre postes standard, et vous avez la possibilité de créer des postes personnalisés. Les positions standard sont les suivantes...

●    Premier contact (FT) - Premier point de contact (peut être anonyme)
●    Création de piste (LC) : premier point de contact où nous capturons une adresse e-mail
●    Création d’une opportunité (OC) - Dernière touche avant la création d’une opportunité
●    Fermé - Dernier contact avant la fermeture (fermé, gagné ou fermé, perdu) d’une opportunité

Les positions déterminent ensuite le poids en fonction des différents modèles d’attribution.

Les opportunités ont ensuite leur valeur répartie entre tous les points de contact qui les ont influencées, comme les secteurs, afin de donner une valeur à chaque point de contact.

Par exemple, si un point de contact a un poids de 30 % et qu’il est lié à une opportunité avec une valeur de 10 000 $, alors ce point de contact est évalué à 3 000 $.
