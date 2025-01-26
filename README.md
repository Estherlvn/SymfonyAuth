# Système de Login et Register sécurisé avec Symfony 7

Etapes pour configurer un système de login et register sécurisé avec Symfony 7, MySQL et Twig

## Prérequis

- Installer PHP, Composer, Symfony CLI, MySQL et HeidiSQL.
- Avoir un éditeur de texte (ex : VSCode).

## Étapes

1. **Initialisation du projet :**
   - Créez un projet Symfony :
     ```bash
     symfony new SymfonyAuth --webapp
     ```
   - Ou clonez un projet existant :
     ```bash
     git clone https://github.com/Estherlvn/SymfonyAuth.git
     cd SymfonyAuth
     ```

2. **Installation des dépendances :**
   ```bash
   composer install


3. **Configuration de la base de données :**
   - Configurez la connexion dans le fichier `.env` :
     ```
     DATABASE_URL="mysql://root@127.0.0.1:3306/nom_de_la_base"
     ```

4. **Création de l'entité utilisateur :**
   - Générez l'entité `User` :
     ```bash
     symfony console make:user
     ```
     Suivez les instructions pour configurer l'entité avec les champs nécessaires, comme `email` et `password`.

5. **Migration de la base de données :**
   - Créez les fichiers de migration :
     ```bash
     symfony console make:migration
     ```
   - Appliquez les migrations pour mettre à jour la base :
     ```bash
     symfony console doctrine:migrations:migrate
     ```

6. **Création de la partie register :**
   - Générez le formulaire d'inscription :
     ```bash
     symfony console make:registration-form
     ```
   - Modifiez et personnalisez le fichier généré dans le dossier `src/Form`.

7. **Création de la partie login :**
   - Générez le formulaire de connexion avec la commande adaptée à Symfony 7 :
     ```bash
     symfony console make:security:form-login
     ```
   - Cette commande configure automatiquement la partie login et met à jour le fichier `security.yaml` pour inclure les routes de connexion et déconnexion.

8. **Configuration de la sécurité :**
   - Vérifiez ou modifiez le fichier `config/packages/security.yaml` pour correspondre à vos besoins

9. **Personnalisation des templates :**
   - Modifiez les fichiers Twig générés dans le dossier `/templates` :
     - `register.html.twig` : page d'inscription.
     - `login.html.twig` : page de connexion.

10. **Test et lancement du serveur :**
    - Démarrez le serveur Symfony :
      ```bash
      symfony serve -d
      ```
    - Accédez aux pages suivantes pour tester votre système :
      - `/register` : Inscription.
      - `/login` : Connexion.
      - `/logout` : Déconnexion.

11. **Test des redirections :**
    - Les redirections après connexion ou échec sont configurées dans `security.yaml` via :
      - `default_target_path` : route après une connexion réussie.
      - `failure_path` : route après un échec.

12. **Déploiement :**
    - Assurez-vous que les dépendances sont installées sur le serveur.
    - Configurez la base de données de production dans le fichier `.env`.

## Résultat final

Votre système de login et register sécurisé avec Symfony 7 est opérationnel. Vous pouvez désormais personnaliser davantage les fonctionnalités ou ajouter des rôles utilisateurs pour gérer les autorisations.
