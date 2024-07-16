---
unique-page-id: 27656745
description: FAQ (multidevise) - [!DNL Marketo Measure]
title: Questions fréquentes sur la gestion de plusieurs devises
exl-id: 1d0936fb-4e66-4877-98d2-32c678a7ef3e
feature: Multi-Currency
source-git-commit: 3b14e758e81f237406da4e0fe1682a02b7a841fd
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Questions fréquentes sur la gestion de plusieurs devises {#faq-multi-currency}

**Comment puis-je savoir quelle fonctionnalité activer ?**

Gardez à l’esprit qu’il existe deux bits de fonctionnalités différents pour cette fonctionnalité. Tous deux se trouvent dans l&#39;onglet [!UICONTROL Général] de la section CRM dans Paramètres : plusieurs devises et devises avancées. Plusieurs devises doivent être activées si le client utilise plus d’une seule devise, tandis que la fonctionnalité supplémentaire en bits Devises avancées peut être activée si le client utilise la fonction &quot;Advanced Currency Management&quot; (Gestion avancée des devises) de [!DNL Salesforce], où l’utilisateur peut définir une plage temporelle pour les taux de conversion.

Marketo Measure extrait automatiquement le paramètre de devise du CRM du client. La configuration manuelle dans Marketo Measure pour correspondre au CRM n’est plus nécessaire. Le paramètre de devise se trouve dans la page &quot;Général&quot; sous &quot;CRM&quot;.

**Pourquoi mon compte publicitaire me donne-t-il un message d’avertissement ?**

Un message d’avertissement s’affiche en regard de votre compte publicitaire. Il se peut que des devises soient entrées dans une devise non prise en charge. Si cela se produit, vos tableaux de bord contiendront des mosaïques avec un message &quot;Devises mixtes&quot;. Nous vous conseillons de travailler avec votre administrateur CRM pour vous assurer que cette devise inconnue contient une conversion dans votre CRM.

**Que signifie &quot;Devises mixtes&quot; sur ma mosaïque de tableau de bord ?**

Si une mosaïque comporte un message &quot;Devises mixtes&quot; en bas, cela signifie que nous avons importé des coûts associés à une devise que nous ne reconnaissons pas. Comme toutes nos conversions doivent provenir du CRM avec un taux de conversion réel, cela signifie que votre CRM manque de cette devise. Nous vous conseillons de travailler avec votre administrateur CRM pour vous assurer que cette devise inconnue contient une conversion dans votre CRM.

**Comment puis-je corriger l’erreur &quot;Mixed Currencies&quot; provoquée par des devises non valides ?**

Notre système met à jour les devises non reconnues vers &quot;XXX&quot;. Pour exclure les opportunités avec des devises non valides, créez une règle de suppression sur la page Paramètres des points de contact afin d’empêcher les points de contact pour les opportunités avec la devise &quot;XXX&quot;. Une fois le traitement effectué, nous ne créerons de rapports que sur les devises connues.

**Comment ajouter une nouvelle devise ou un nouveau taux de conversion ?**

La déclaration d’une nouvelle devise ou d’un nouveau taux de conversion ne peut être effectuée que dans [!DNL Salesforce] ou [!DNL Dynamics], de sorte qu’il n’existe qu’une seule source de vérité pour ces valeurs. Une fois qu’une nouvelle devise ou un nouveau taux de conversion est détecté, [!DNL Marketo Measure] le télécharge et vous le rend disponible. Nous n&#39;avons pas de zone pour entrer ces tarifs.

**La devise ne s’affiche pas dans le format correct. Comment puis-je changer cela ?**

Nous comprenons que certains pays ont une manière différente de mettre en forme les montants (par exemple, 1 234,00, 1 234, 1 234). Mais nous introduisons un autre niveau de complexité si nous devons non seulement déterminer la devise d&#39;un utilisateur, mais aussi son pays d&#39;origine, puisque différents pays et devises peuvent être gérés différemment. Le format cohérent que nous avons choisi est 1 234,00. Cela ne peut pas être modifié.

**Pourquoi ne pouvez-vous pas afficher le symbole de devise pour ma devise sélectionnée ?**

[!DNL Salesforce] et [!DNL Dynamics] affichent leurs montants avec le code de conversion de 3 lettres. Par souci de cohérence, les montants convertis s’affichent également avec le code de conversion à 3 lettres et non le symbole.

**Que verra mon client s’il n’a pas activé le multi-devise ?**

Si le client ne dispose pas de la fonctionnalité à plusieurs devises, les paramètres régionaux de sa devise sont définis par défaut dans le CRM et modifiez tous les codes ISO qui indiquent leurs dépenses et recettes dans la devise de l’entreprise. Si ce n’est pas le cas et que le client utilise une devise de manière mixte, la solution consiste à effectuer une mise à niveau pour obtenir la fonctionnalité de plusieurs devises.

**Comment cette fonctionnalité affecte-t-elle les rapports basés sur les points de contact dans le CRM ?**

Pour les clients [!DNL Dynamics] et [!DNL Salesforce] qui utilisent uniquement la gestion de devise de base (non avancée), les montants de recettes des points de contact doivent être correctement convertis, de sorte que les rapports de gestion de la relation client fonctionnent comme prévu.

Il existe malheureusement une certaine nuance à la façon dont cela fonctionne pour les utilisateurs de la gestion avancée des devises [!DNL Salesforce], en raison d&#39;une limitation de [!DNL Salesforce] de longue date. La réponse courte à &quot;ce que nous faisons dans ce cas&quot; est que nous convertissons les recettes à l’aide des taux plats définis dans l’onglet de base (c’est-à-dire non avancé) &quot;Gestion des devises&quot;. En d’autres termes, nous ignorons complètement les taux d’exchange datés bien que le client ait défini des taux d’exchange datés.

Pour le lecteur intéressé, voici pourquoi ça marche ainsi. Nos points de contact utilisent des champs de formule pour calculer le chiffre d’affaires (dérivé du montant d’opportunité associé). [!DNL Salesforce] prend en charge la conversion de devise en mode natif pour ces calculs de formule, mais uniquement pour leur version de base de la prise en charge de la devise. Il nous est impossible de définir un champ de formule qui référence les tarifs exchanges datés. [!DNL Salesforce] ne prend tout simplement pas en charge cette fonctionnalité. Nous n’avons donc aucun moyen de référencer les taux dépassés dans nos calculs de recettes malgré le fait que ces taux dépassés existent dans [!DNL Salesforce] (ça a l’air fou mais c’est comme ça que ça marche).

**Si mon client a utilisé un workflow pour renseigner un champ converti, comment doit-il utiliser ce champ à partir de maintenant ?**

Puisque notre offre va maintenant gérer les conversions pour le client, nous vous recommandons de supprimer les workflows et le champ personnalisé et de nous permettre d’importer leur valeur brute Montant .

>[!MORELIKETHIS]
>
>[Notifications d’erreur](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
