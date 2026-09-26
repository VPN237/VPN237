# VPN237 v0.3

Version de développement connectée à Supabase.

Project URL intégré : https://apeugjrypzbdkpjorzep.supabase.co

La Publishable key n'est pas stockée dans le code source. Au build Flutter, fournir :

flutter build apk --release --dart-define=SUPABASE_PUBLISHABLE_KEY=VOTRE_PUBLISHABLE_KEY

Fonctions :
- inscription / connexion Supabase
- récupération réelle des forfaits depuis `products`
- création réelle de commandes dans `orders`
- historique `Mes achats`
- base de paiement sélectionnée, sans prétendre à un paiement automatique
- préparation du stockage privé `connection-files`

Important : le schéma Supabase actuel doit utiliser les noms de colonnes de la version configurée dans le projet : `profiles.role`, `products.data_label`, `products.duration_label`, `orders.requested_file_name`, etc.


## V4 - Espace admin fichiers
La table `connection_files` utilisée par cette version contient : `id`, `order_id`, `file_name`, `storage_path`, `uploaded_by`, `created_at`. L'admin peut choisir un fichier depuis son téléphone, l'envoyer dans le bucket privé `connection-files`, créer/mettre à jour la ligne `connection_files`, puis passer automatiquement la commande à `file_available`. Le client voit ensuite le fichier dans Mes achats et peut ouvrir son lien signé temporaire.
