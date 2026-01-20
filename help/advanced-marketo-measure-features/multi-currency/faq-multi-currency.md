---
unique-page-id: 27656745
description: FAQ (multidevise) - [!DNL Marketo Measure]
title: Questions fréquentes sur la gestion de plusieurs devises
exl-id: 1d0936fb-4e66-4877-98d2-32c678a7ef3e
feature: Multi-Currency
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Questions fréquentes sur la gestion de plusieurs devises {#faq-multi-currency}

**Comment puis-je connaître le bit de fonctionnalité à activer ?**

Gardez à l’esprit qu’il existe deux bits de fonctionnalité différents pour cette fonctionnalité. Les deux se trouvent dans l’onglet [!UICONTROL Général] de la section CRM dans Paramètres : devises multiples et devises avancées. Plusieurs devises doivent être activées si le client utilise plusieurs devises, tandis que le bit de fonction supplémentaire Advanced Currencies peut être activé si le client utilise la fonction « Advanced Currency Management » de [!DNL Salesforce], dans laquelle l&#39;utilisateur peut définir une plage temporelle de taux de conversion.

Marketo Measure extrait automatiquement le paramètre monétaire du CRM du client. Il n’est plus nécessaire de configurer manuellement Marketo Measure pour qu’il corresponde au CRM. Le paramètre de devise se trouve dans la page « Général » sous « CRM ».

**Pourquoi mon compte publicitaire m’envoie-t-il un message d’avertissement ?**

Un message d’avertissement s’affichera à côté de votre compte publicitaire si des devises provenant d’une devise non prise en charge sont susceptibles d’être importées. Si cela se produit, vos tableaux de bord contiendront des vignettes avec un message « Devises mixtes ». Nous vous conseillons de travailler avec votre administrateur CRM pour vous assurer que cette devise inconnue contient une conversion dans votre CRM.

**Que signifie « Devises mixtes » sur la mosaïque de mon tableau de bord ?**

Si une mosaïque comporte un message « Devises mixtes » en bas, cela signifie que nous avons importé des coûts associés à une devise que nous ne reconnaissons pas. Comme toutes nos conversions doivent provenir du CRM avec un taux de conversion réel, cela signifie que votre CRM n&#39;a pas cette devise. Nous vous conseillons de travailler avec votre administrateur CRM pour vous assurer que cette devise inconnue contient une conversion dans votre CRM.

**Comment puis-je corriger l’erreur « Devises mixtes » causée par des devises non valides ?**

Notre système met à jour les devises non reconnues sur « XXX ». Pour exclure les opportunités avec des devises non valides, créez une règle de suppression dans la page Paramètres des points de contact afin d’empêcher les points de contact pour les opportunités avec la devise « XXX ». Une fois le traitement effectué, nous ne produirons des rapports que sur les devises connues.

**Comment ajouter une nouvelle devise ou un nouveau taux de conversion ?**

La déclaration d&#39;une nouvelle devise ou d&#39;un nouveau taux de conversion ne peut être effectuée qu&#39;en [!DNL Salesforce] ou [!DNL Dynamics] afin qu&#39;il n&#39;y ait qu&#39;une seule source de vérité pour ces valeurs. Une fois qu’une nouvelle devise ou un nouveau taux de conversion est détecté, [!DNL Marketo Measure] le télécharge et le met à votre disposition. Nous ne proposons pas de zone pour entrer ces tarifs.

**La devise ne s’affiche pas dans le bon format. Comment puis-je changer cela ?**

Nous comprenons que certains pays ont une façon différente de formater les montants (par exemple, 1 234,00, 1,234, 1 234). Mais nous introduisons un autre niveau de complexité si nous devons non seulement déterminer la devise d&#39;un utilisateur, mais aussi son pays d&#39;origine, car différents pays et devises peuvent être traités différemment. Le format que nous avons choisi est 1 234,00. Ceci ne peut pas être modifié.

**Pourquoi ne pouvez-vous pas afficher le symbole de la devise sélectionnée ?**

[!DNL Salesforce] et [!DNL Dynamics] affichent leurs montants avec le code de conversion à 3 lettres. Par souci de cohérence, nos montants convertis s’affichent également avec le code de conversion à 3 lettres et non avec le symbole.

**Que verra mon client s&#39;il n&#39;a pas activé la fonction multidevise ?**

Si le client ne dispose pas de la fonctionnalité multidevise, nous définirons par défaut ses paramètres régionaux dans le CRM et modifierons tous les codes ISO qui indiquent ses dépenses et ses revenus dans la devise de l’entreprise. Si cette valeur est incorrecte et que le client utilise plusieurs devises, la solution consiste à effectuer une mise à niveau pour obtenir la fonctionnalité multidevise.

**Comment cette fonctionnalité affecte-t-elle les rapports basés sur les points de contact dans le CRM ?**

Pour les clients [!DNL Dynamics] et [!DNL Salesforce] qui utilisent uniquement la gestion de devise de base (non avancée), les montants des revenus des points de contact doivent être correctement convertis, de sorte que les rapports de gestion de la relation client fonctionnent comme prévu.

Il y a malheureusement quelques nuances dans la façon dont cela fonctionne pour les utilisateurs de [!DNL Salesforce] Advanced Currency Management, en raison d&#39;une limitation de longue date de [!DNL Salesforce]. La réponse courte à la question « Que faisons-nous dans ce cas ? » est que nous convertissons les montants des revenus à l’aide des taux forfaitaires définis dans l’onglet « Gérer les devises » de base (c.-à-d. non avancé). En d&#39;autres termes, nous ignorons complètement les taux de change datés malgré le fait que le client a défini des taux de change datés.

Pour le lecteur intéressé, voici pourquoi il fonctionne de cette manière. Nos points de contact utilisent des champs de formule pour calculer le chiffre d’affaires (dérivé du montant de l’opportunité associé). [!DNL Salesforce] prend en charge de manière native la conversion de devise pour ces calculs de formule, mais uniquement pour leur version de base de la prise en charge de devise. Il nous est impossible de définir un champ de formule qui fait référence aux taux de change datés. [!DNL Salesforce] ne prend tout simplement pas en charge cette fonctionnalité, de sorte que nous n&#39;avons aucun moyen de faire référence aux taux datés dans nos calculs de revenus malgré le fait que ces taux datés existent en [!DNL Salesforce] (cela semble fou, mais c&#39;est comme ça que ça fonctionne.)

**Si mon client a utilisé un workflow pour remplir un champ converti, comment doit-il utiliser ce champ à l’avenir ?**

Puisque notre offre gère désormais les conversions pour le client, nous lui recommandons de supprimer les workflows et le champ personnalisé et de nous permettre d’importer leur valeur Quantité brute.

>[!MORELIKETHIS]
>
>[Notifications d’erreur](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
