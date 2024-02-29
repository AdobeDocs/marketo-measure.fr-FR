---
unique-page-id: 27656745
description: FAQ (multidevise) - [!DNL Marketo Measure] - Documentation du produit
title: Questions fréquentes sur la gestion de plusieurs devises
exl-id: 1d0936fb-4e66-4877-98d2-32c678a7ef3e
feature: Multi-Currency
source-git-commit: cc786cb3af08fa36af91ef22f4dba3072c9617eb
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Questions fréquentes sur la gestion de plusieurs devises {#faq-multi-currency}

**Comment savoir quelle fonctionnalité activer ?**

Gardez à l’esprit qu’il existe deux bits de fonctionnalités différents pour cette fonctionnalité. Tous deux se trouvent dans la variable [!UICONTROL Général] de la section CRM dans Paramètres : plusieurs devises et devises avancées. Plusieurs devises doivent être activées si le client utilise plus d’une seule devise, tandis que la fonctionnalité supplémentaire en bits Devises avancées peut être activée si le client utilise [!DNL Salesforce]Fonctionnalité de &quot;gestion de devise avancée&quot; dans laquelle l’utilisateur peut définir une plage temporelle pour les taux de conversion.

Malheureusement, nous ne savons pas quand un client passe de Simple à Avancé si Avancé a déjà été activé. Pour cette raison, le client doit conserver le paramètre Devises avancées aligné manuellement sur son paramètre CRM. Cela devrait être visible pour le client si les conversions sont incorrectes, ce qui signifie que nous ne savions pas quel niveau de conversion appliquer.

**Pourquoi mon compte publicitaire me donne-t-il un message d’avertissement ?**

Un message d’avertissement s’affiche en regard de votre compte publicitaire. Il se peut que des devises soient entrées dans une devise non prise en charge. Si cela se produit, vos tableaux de bord contiendront des mosaïques avec un message &quot;Devises mixtes&quot;. Nous vous conseillons de travailler avec votre administrateur CRM pour vous assurer que cette devise inconnue contient une conversion dans votre CRM.

**Que signifie &quot;Devises mixtes&quot; sur la mosaïque de mon tableau de bord ?**

Si une mosaïque comporte un message &quot;Devises mixtes&quot; en bas, cela signifie que nous avons importé des coûts associés à une devise que nous ne reconnaissons pas. Comme toutes nos conversions doivent provenir du CRM avec un taux de conversion réel, cela signifie que votre CRM manque de cette devise. Nous vous conseillons de travailler avec votre administrateur CRM pour vous assurer que cette devise inconnue contient une conversion dans votre CRM.

**Comment ajouter une nouvelle devise ou un nouveau taux de conversion ?**

La déclaration d’une nouvelle devise ou d’un nouveau taux de conversion ne peut être effectuée que dans [!DNL Salesforce] ou [!DNL Dynamics] pour qu&#39;il n&#39;y ait qu&#39;une seule source de vérité pour ces valeurs. Une fois qu’une nouvelle devise ou un nouveau taux de conversion est détecté, [!DNL Marketo Measure] téléchargera cela et le mettra à votre disposition. Nous n&#39;avons pas de zone pour entrer ces tarifs.

**La devise ne s’affiche pas dans le bon format. Comment puis-je changer ceci ?**

Nous comprenons que certains pays ont une manière différente de mettre en forme les montants (par exemple, 1 234,00, 1 234, 1 234). Mais nous introduisons un autre niveau de complexité si nous devons non seulement déterminer la devise d&#39;un utilisateur, mais aussi son pays d&#39;origine, puisque différents pays et devises peuvent être gérés différemment. Le format cohérent que nous avons choisi est 1 234,00. Cela ne peut pas être modifié.

**Pourquoi ne pouvez-vous pas afficher le symbole monétaire de la devise que j’ai sélectionnée ?**

[!DNL Salesforce] et [!DNL Dynamics] afficher leurs montants avec le code de conversion à 3 lettres. Par souci de cohérence, les montants convertis s’affichent également avec le code de conversion à 3 lettres et non le symbole.

**Que verra mon client s’il n’a pas activé le multidevise ?**

Si le client ne dispose pas de la fonctionnalité à plusieurs devises, les paramètres régionaux de sa devise sont définis par défaut dans le CRM et modifiez tous les codes ISO qui indiquent leurs dépenses et recettes dans la devise de l’entreprise. Si ce n’est pas le cas et que le client utilise une devise de manière mixte, la solution consiste à effectuer une mise à niveau pour obtenir la fonctionnalité de plusieurs devises.

**Comment cette fonction affecte-t-elle les rapports basés sur les points de contact dans le CRM ?**

Pour [!DNL Dynamics] et [!DNL Salesforce] les clients qui utilisent uniquement la gestion de devise de base (non avancée), les recettes des points de contact doivent être correctement converties, de sorte que les rapports CRM fonctionnent comme prévu.

Malheureusement, il y a quelques nuances à la façon dont cela fonctionne pour les utilisateurs de [!DNL Salesforce] Gestion avancée des devises, en raison d’une limitation de longue date de [!DNL Salesforce]. La réponse courte à &quot;ce que nous faisons dans ce cas&quot; est que nous convertissons les recettes à l’aide des taux plats définis dans l’onglet de base (c’est-à-dire non avancé) &quot;Gestion des devises&quot;. En d&#39;autres termes, nous ignorons complètement les taux de change datés malgré le fait que le client ait défini des taux de change datés.

Pour le lecteur intéressé, voici pourquoi ça marche ainsi. Nos points de contact utilisent des champs de formule pour calculer le chiffre d’affaires (dérivé du montant d’opportunité associé). [!DNL Salesforce] prend en charge la conversion de devise en mode natif pour ces calculs de formule, mais uniquement pour leur version de base de la prise en charge de la devise. Il nous est impossible de définir un champ de formule qui référence les taux de change datés. [!DNL Salesforce] Comme nous ne supportons pas cette capacité, nous n&#39;avons aucun moyen de faire référence aux taux dépassés dans nos calculs de revenus, même si ces taux dépassés existent dans les [!DNL Salesforce] (ça a l&#39;air fou mais c&#39;est comme ça que ça marche.)

**Si mon client a utilisé un workflow pour renseigner un champ converti, comment doit-il utiliser ce champ à partir de maintenant ?**

Puisque notre offre va maintenant gérer les conversions pour le client, nous vous recommandons de supprimer les workflows et le champ personnalisé et de nous permettre d’importer leur valeur brute Montant .

>[!MORELIKETHIS]
>
>[Notifications d’erreur](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
