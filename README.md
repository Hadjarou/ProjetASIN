# **ProjetASIN - Outil d'importation de fichiers Excel dans une base de données SQLite en ligne de commande**

## **Description**

Ce projet permet de créer, importer et administrer une base de données SQLite à partir d'un fichier Excel. Il propose également diverses commandes permettant de lister les tables, d'afficher leur contenu et d'exécuter d'autres opérations, le tout via une interface en ligne de commande (CLI).

## A - **Installation**

### **Installation de Python 3 et de pip**

#### **Mise à jour des paquets**
Avant toute installation, assurez-vous que votre système est à jour en exécutant la commande suivante :

```bash
sudo apt update
```

#### **Installation de Python 3**
Python 3 est généralement inclus dans les dépôts officiels des distributions Linux. Pour l'installer, utilisez la commande suivante :

```bash
sudo apt install python3
```

#### **Installation de pip pour Python 3**
Une fois Python installé, vous pouvez installer pip, le gestionnaire de paquets de Python, en exécutant la commande suivante :

```bash
sudo apt install python3-pip
```

#### **Vérification de l'installation**
Après l’installation, il est recommandé de vérifier que Python et pip sont correctement installés en affichant leurs versions respectives :

```bash
python3 --version
pip3 --version
```

Si l'installation a été effectuée avec succès, vous devriez obtenir un affichage similaire à celui-ci :

```bash
Python 3.x.x
pip 20.x.x
```

---

## **Clonage du dépôt**

```bash
git clone https://github.com/Hadjarou/ProjetASIN.git
```

### **Accès au répertoire du projet**
```bash
cd ProjetASIN
```

### **Création d'un environnement virtuel**
```bash
python3 -m venv venv
```
Cette commande génère un répertoire `venv` contenant toutes les dépendances isolées nécessaires au projet.

### **Activation de l'environnement virtuel**
Une fois l’environnement virtuel créé, il est impératif de l’activer avant d’installer les dépendances requises.

```bash
source venv/bin/activate
```

---

## **Installation des dépendances**
```bash
pip install -r requirements.txt
```
## Vérifier si le projet a bien été déployer
```bash
pyhton main.py
```
  ## Vous aurez une sortie comme suit : 
  ````bash
    Utilisation des commandes :
  
  1. Créer une table :
     create --db <nom_db> --table <nom_table> --columns <colonne1:type1> <colonne2:type2> ...
     Exemple : create --db personnes --table utilisateurs --columns matricule:TEXT nom:TEXT prenom:TEXT date_naissance:DATE status:TEXT
  
  2. Types de données valides :
     Les types valides pour les colonnes sont : TEXT, INTEGER, REAL, BLOB, DATE
  
  3. Importer un fichier Excel dans une table :
     import --db <nom_db> --table <nom_table> --file <chemin_fichier_excel>
     Exemple : import --db personnes --table utilisateurs --file /chemin/vers/fichier.xlsx
  
  4. Supprimer une table :
     delete --db <nom_db> --table <nom_table>
     Exemple : delete --db personnes --table utilisateurs
  
  5. Supprimer la base de données :
     delete-db --db <nom_db>
     Exemple : delete-db --db personnes
  
  6. Lister les tables :
     list-tables --db <nom_db>
     Exemple : list-tables --db personnes
  
  7. Voir le contenu d\'une table :
     view --db <nom_db> --table <nom_table>
     Exemple : view --db personnes --table utilisateurs
  
  8. Voir la structure d\'une table (DESCRIBE) :
     describe --db <nom_db> --table <nom_table>
     Exemple : describe --db personnes --table utilisateurs

  ````
---


## B - **Utilisation**

### 1 - **Exécution du script en ligne de commande (sans alias)**
Pour l'exécution sans alias vous devez soit être dans le dossier du projet soit avoir le chemain absolu du fichier main.py
## Dans notre cas on considère que nous sommes dans le dossier du projet
#### **Création d'une table**
```bash
python3 main.py create --db <nom_db> --table <nom_table> --columns <colonne1:type1> <colonne2:type2> ...
```
**Exemple :**
```bash
python3 main.py create --db personnes --table utilisateurs --columns matricule:TEXT nom:TEXT prenom:TEXT datedenaissance:DATE status:TEXT
```

#### **Types de données valides**
Les types de données acceptés pour les colonnes sont : `TEXT`, `INTEGER`, `REAL`, `BLOB`, `DATE`.

#### **Importation d’un fichier Excel dans une table**
```bash
python3 main.py import --db <nom_db> --table <nom_table> --file <chemin_fichier_excel>
```
**Exemple :**
```bash
python3 main.py import --db personnes --table utilisateurs --file people\ sample.xlsx
```

#### **Suppression d'une table**
```bash
python3 main.py delete --db <nom_db> --table <nom_table>
```
**Exemple :**
```bash
python3 main.py delete --db personnes --table utilisateurs
```

#### **Suppression de la base de données**
```bash
python3 main.py delete-db --db <nom_db>
```
**Exemple :**
```bash
python3 main.py delete-db --db personnes
```

#### **Affichage de la liste des tables**
```bash
python3 main.py list-tables --db <nom_db>
```
**Exemple :**
```bash
python3 main.py list-tables --db personnes
```

#### **Affichage du contenu d'une table**
```bash
python3 main.py view --db <nom_db> --table <nom_table>
```
**Exemple :**
```bash
python3 main.py view --db personnes --table utilisateurs
```

#### **Affichage de la structure d'une table (DESCRIBE)**
```bash
python3 main.py describe --db <nom_db> --table <nom_table>
```
**Exemple :**
```bash
python3 main.py describe --db personnes --table utilisateurs
```

---

## 2 - **Exécution du script avec un alias**

### **Rendre le script exécutable**
Avant de pouvoir utiliser un alias, il est nécessaire de rendre le script exécutable :

```bash
chmod +x main.py
```

### **Création d'un alias pour simplifier l’exécution du script**
Si vous souhaitez exécuter le script avec une commande plus concise, comme `PASIN`, vous pouvez définir un alias dans votre fichier de configuration Shell (`~/.bashrc` ou `~/.zshrc`).

Ouvrez le fichier de configuration avec un éditeur de texte :  
```bash
nano ~/.bashrc
```

Ajoutez la ligne suivante à la fin du fichier :  
```bash
alias PASIN="python3 /chemin/vers/votre/projet/ProjetASIN/main.py"
```

  ## Note : Le chemin doit être absolu, de la racine jusqu'au fichier main.py

Rechargez ensuite le fichier de configuration pour appliquer les modifications :  
```bash
source ~/.bashrc
```

---

### **Activation de l’environnement virtuel**
Avant d'exécuter toute commande, assurez-vous d'activer l'environnement virtuel :
### *Tout d'abord aller dans le répertoire de votre projet et taper cette commande :*
```bash
source venv/bin/activate
```

### **Exécution du script avec l’alias**
Une fois l’alias configuré, il est possible d’exécuter les commandes en utilisant `PASIN` directement.
Le proccessus sera le même, mais cette fois au lieu de taper pyhton main.py avant d'exécuter les commandes on utilise directement `PASIN`
### *Assurez-vous d'activer l'environnement au préalable*
**Exemple :**  
```bash
PASIN create --db <nom_db> --table <nom_table> --columns <colonne1:type1> <colonne2:type2> ...
```

---
### C - Activé l'environnement virtuel du projet depuis n'importe quel emplacement ( éviter d'aller à chaque fois dans le répertoire )
  Ouvrez le fichier de configuration avec un éditeur de texte :  
  ```bash
  nano ~/.bashrc
  ```
  Ajoutez la ligne suivante à la fin du fichier :  
  ```bash
  alias ENVASIN='cd /chemin/vers/votre/projet/ProjetASIN && source venv/bin/activate'
  ```
  ## Note : Le chemin doit être absolu, de la racine jusqu'au fichier main.py
  
  Rechargez ensuite le fichier de configuration pour appliquer les modifications :  
  ```bash
  source ~/.bashrc
  ```

  ### Note : Pour désactiver l'environnement virtuel taper la commande suivante 
  ````bash
    deactivate
  ````
## *TAPER `ENVASIN` peu importe où vous êtes pour activer l'environnement du projet*

---
## D - Ouvrir la base avec SQLite en ligne de commande
### Installer sqlite3
````bash
sudo apt update
sudo apt install sqlite3
````
### Ouvrir la base de données 
*Assurer vous que la base de données soit dans le même répertoire ou que vous ayez son chemin d'accès*
````bash
sqlite3 <nom_base>
````
## OU
````bash
sqlite3 /chemin/vers/votre/base_de_donnees/<nom_base>
````

**Exemple :**
```bash
sqlite3 personnes
```
### Puis, une fois dans SQLite :
  ### Lister les tables :
  ````bash
  .tables
  ````

  ### Voir la structure d'une table :
  ````bash
    .schema <nom_de_la_table>
  ````
  **Exemple :**
  ```bash
  .schema utilisateurs
  ```

  ### Afficher les données :
  ````bash
  SELECT * FROM <nom_de_la_table>;
  ````
  **Exemple : Affichage de 50 premières lignes**
  ```bash
  SELECT * FROM utilisateurs LIMIT 50;
  ```

  ### Quitter :
  ````bash
  .exit
  ````

---
## E - Exécution du test automatique avec l'affichage du temps d'exécution
  Avant d'exécuter toute commande, assurez-vous d'activer l'environnement virtuel :
  ```bash
  ENVASIN
  ```
  ### *Lister le contenu du dossier tests :*
  ````bash
    ls tests
  ````
  *Le résultat de cette commande sera dans le cas de notre fichier excel fournit:*
  ````bash
  'people sample.xlsx'   test_sqlite.py
  ````
  ## Note : *Assurer vous que le fichier excel soit bien présent dans le dossier*

  ## Installer pytest pour l'exécution des tests
  ````bash
  pip install pytest
  ````
  ## 1. Test sans affichage des données après l'importation 
  ````bash
  python -m pytest -v tests/test_sqlite.py
  ````
  ## 2 Test avec affichage des données après l'importation
  ````bash
    python -m pytest -v tests/test_sqlite.py
  ````
  *Après avoir exécuter l'une de ces commandes un fichier test_db.sqlite sera genéré dans votre repertoire de travail, 
      ce fichier correspond à la base de données sqlite avec les données du fichier excel importé*
      ## *Pour explorer ce fichier consulter le rubrique C*
  
