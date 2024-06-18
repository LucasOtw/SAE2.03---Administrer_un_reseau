# Documentation: Administration d'un Réseau

## Introduction

Ce guide fournit des instructions pour administrer un réseau informatique. Il couvre l'installation de services réseau, la configuration de serveurs web et bases de données, ainsi que la sécurisation de ces services.

## Table des Matières

1. [Installation de Services Réseau](#installation-de-services-réseau)
2. [Configuration du Serveur Web Apache](#configuration-du-serveur-web-apache)
3. [Gestion de MySQL](#gestion-de-mysql)
4. [Utilisation de PHP avec MySQL](#utilisation-de-php-avec-mysql)
5. [Sécurisation du Serveur](#sécurisation-du-serveur)

## Installation de Services Réseau

1. Vérifiez le statut d’exécution du service Web :
    ```bash
    systemctl status apache2
    ```

2. Trouvez le fichier de configuration avec la directive `DocumentRoot` :
    ```bash
    grep "DocumentRoot" /etc/apache2/apache2.conf
    ```

3. Repérez le chemin du binaire Apache :
    ```bash
    type -a apache2
    ```

4. Identifiez la version d'Apache :
    ```bash
    apache2 -v
    ```

5. Listez les modules Apache :
    ```bash
    apache2 -M
    ```

6. Vérifiez le rôle du module `mod_log_config.c`.

## Configuration du Serveur Web Apache

1. Modifiez les configurations nécessaires dans les fichiers `apache2.conf` ou `httpd.conf`.

## Gestion de MySQL

1. Sécurisez MySQL :
    ```bash
    mysql_secure_installation
    ```

2. Vérifiez le statut du service MySQL :
    ```bash
    systemctl status mysql
    ```

3. Identifiez la version de MySQL :
    ```bash
    mysql -V
    ```

4. Connectez-vous à MySQL :
    ```bash
    mysql -u root -p
    ```

5. Affichez les bases de données existantes :
    ```sql
    SHOW DATABASES;
    ```

6. Créez une base de données avec votre prénom :
    ```sql
    CREATE DATABASE [votre_prenom];
    ```

7. Créez une table `étudiants` et insérez des enregistrements :
    ```sql
    USE [votre_prenom];
    CREATE TABLE étudiants (
        id INT AUTO_INCREMENT PRIMARY KEY,
        nom VARCHAR(100),
        date_naissance DATE,
        classement INT
    );
    INSERT INTO étudiants (nom, date_naissance, classement) VALUES ('Alice Dupont', '2000-01-15', 1);
    INSERT INTO étudiants (nom, date_naissance, classement) VALUES ('Bob Martin', '1999-02-20', 2);
    INSERT INTO étudiants (nom, date_naissance, classement) VALUES ('Charlie Durant', '2001-03-30', 3);
    SELECT * FROM étudiants;
    ```

8. Supprimez un enregistrement :
    ```sql
    DELETE FROM étudiants WHERE id = 2;
    ```

9. Modifiez un enregistrement :
    ```sql
    UPDATE étudiants SET date_naissance = '1990-01-01' WHERE id = 1;
    ```

## Utilisation de PHP avec MySQL

1. Créez un script PHP pour gérer la base de données :

    ```php
    <?php
    $servername = "localhost";
    $username = "root";
    $password = "lannion";
    $dbname = "[votre_prenom]";

    $conn = new mysqli($servername, $username, $password);
    if ($conn->connect_error) {
        die("La connexion a échoué : " . $conn->connect_error);
    }

    $sql
