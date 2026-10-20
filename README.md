# TP 6 : Spring Boot et Swagger (student-management)

## Prérequis

- JDK 21 (ou modifier `<java.version>` dans `pom.xml`)
- MySQL démarré sur le port 3306 (MySQL Workbench, XAMPP, WAMP...)
- IntelliJ IDEA (Maven est intégré) ou Maven installé

## 1. Créer la base MySQL

```sql
CREATE DATABASE studentdb;
```

## 2. Vérifier `src/main/resources/application.properties`

```
spring.datasource.username=root
spring.datasource.password=
```

Adapter le mot de passe si votre MySQL en a un. Les tables sont créées automatiquement (`ddl-auto=update`).

## 3. Ouvrir le projet

IntelliJ : **File > Open**, choisir le dossier `student-management` (celui qui contient `pom.xml`), puis **Trust Project**. Attendre la fin du téléchargement des dépendances Maven.

## 4. Lancer

- IntelliJ : ouvrir `StudentManagementApplication` puis cliquer sur la flèche verte.
- Terminal, à la racine du projet :

```
mvn spring-boot:run
```

Démarrage réussi quand la console affiche `Started StudentManagementApplication`.

## 5. Tester

Swagger UI : http://localhost:8080/swagger-ui.html

| Méthode | URL | Code attendu |
|---|---|---|
| POST | /students/save | 201 |
| GET | /students/all | 200 |
| DELETE | /students/delete/{id} | 204 (404 si absent) |
| GET | /students/count | 200 |
| GET | /students/byYear | 200 |

Corps du POST :

```json
{ "nom": "LACHGAR", "prenom": "Mohamed", "dateNaissance": "1985-09-01" }
```

## 6. Tests unitaires

```
mvn test
```

ou clic droit sur `StudentControllerTest` puis **Run**. Ces tests n'ont pas besoin de MySQL.

## Remarques

- Spring Data REST expose aussi les repositories sous `/api` (réglé par `spring.data.rest.base-path=/api`) pour éviter un conflit avec le contrôleur sur `/students`.
- Le package utilisé partout est `com.example.studentmanagement` (l'énoncé mélange `demo` et `studentmanagement`).
- La version de springdoc est adaptée à Spring Boot 3.5 (l'énoncé indique `2.0.2`, trop ancienne).

## Erreurs fréquentes

- `Communications link failure` : MySQL n'est pas démarré ou le port est différent.
- `Access denied for user 'root'` : corriger le mot de passe dans `application.properties`.
- `Unknown database 'studentdb'` : la base n'a pas été créée (étape 1).
- `Port 8080 was already in use` : ajouter `server.port=8081` dans `application.properties`.
