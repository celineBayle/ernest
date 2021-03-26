# Modèle d'installation de WordPress avec Composer
## Prérequis
* Composer (https://getcomposer.org/)
* WP-CLI (https://wp-cli.org/fr/)
## Préparation du projet
* Cloner ce repo
* Renommer le dossier cloné
* Supprimer le répertoire .git du dossier (sudo rm -R .git) pour supprimer le repo local

Si on souhaite "reconnecter" l'install avec un repo distant

* Réinitialiser un repo local (git init)
* Pousser sur un repo distant (git add . + git commit -m "installation de WP" + git remote add origin git@github.com:....git + git push -u origin master)
* On a un repo local connecté à un repo distant
## Installation à partir de ce modèle cloné
1. Télécharger WordPress, ses plugins, ses thèmes avec composer install

2. Créer une base de données avec un user dédié

3. Compléter le fichier wp-config.php (copie de wp-config-sample.php)

- les infos de connexion à la BDD (constantes préfixées par DB_)
- les clefs de salage (https://api.wordpress.org/secret-key/1.1/salt/)
- l'URL de la page d'accueil (constante WP_HOME)
- activer le debug (passer WP_DEBUG à true) si souhaité
- choisir l'environnement avec la constante ENVIRONMENT

4. Modifier les droits des dossiers et fichiers avec les commandes

* sudo chown -R $USER:www-data .
* sudo find . -type f -exec chmod 664 {} +
* sudo find . -type d -exec chmod 775 {} +
* sudo chmod g-w .htaccess

5. Installer WordPress avec la commande wp core install --prompt

Répondre aux questions

* url => url du site (la même chose que WP_HOME)
* site-title => nom du site (modifiable par la suite)
* username => super administrateur (utilisé pour la connexion au back-office)
* password => mot de passe du super administrateur
* email => email du super administrateur
* skip-email => souhaitez-vous zapper l'email de création d'user ?

6. 🎉