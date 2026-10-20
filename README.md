# TP 6 : Spring Boot et Swagger (student-management)

Application de gestion des étudiants avec Spring Boot, MySQL, Spring Data JPA et Swagger (springdoc-openapi).

## Prérequis

- JDK 21
- MySQL ou MariaDB démarré sur le port 3306 (XAMPP, WAMP, ...)
- phpMyAdmin, MySQL Workbench ou DBeaver
- IntelliJ IDEA (Maven est intégré) ou Maven installé

## Structure

```
student-management/
├─ pom.xml
└─ src/
   ├─ main/
   │  ├─ java/com/example/studentmanagement/
   │  │  ├─ StudentManagementApplication.java
   │  │  ├─ entity/Student.java
   │  │  ├─ repository/StudentRepository.java
   │  │  ├─ service/StudentService.java
   │  │  └─ controller/StudentController.java
   │  └─ resources/application.properties
   └─ test/java/com/example/studentmanagement/
      └─ StudentControllerTest.java
```

## Configuration

### 1. Créer la base de données

Dans phpMyAdmin (onglet SQL) :

```sql
CREATE DATABASE studentdb;
```

## Tester avec Swagger

Ouvrir http://localhost:8080/swagger-ui.html

Pour chaque endpoint : Try it out, puis Execute.

| Méthode | URL | Code attendu | Description |
|---|---|---|---|
| POST | /students/save | 201 | Enregistrer un étudiant |
| GET | /students/all | 200 | Liste de tous les étudiants |
| GET | /students/count | 200 | Nombre d'étudiants |
| GET | /students/byYear | 200 | Nombre d'étudiants par année de naissance |
| DELETE | /students/delete/{id} | 204 (404 si absent) | Supprimer un étudiant |

## Les screens

<img width="796" height="179" alt="TP6_1" src="https://github.com/user-attachments/assets/212fa385-94ec-47d5-929a-28fe1ee59739" />

<img width="461" height="133" alt="TP6_2" src="https://github.com/user-attachments/assets/9c138041-8911-4f66-94ea-7e37414197ed" />

<img width="944" height="352" alt="TP6_3" src="https://github.com/user-attachments/assets/c65d6d6a-bf9e-4b93-8a83-1a8c9b71a8fd" />

<img width="795" height="362" alt="TP6_4" src="https://github.com/user-attachments/assets/5ac7f6ad-0b2c-479d-8f32-1ba29c98f167" />

<img width="928" height="383" alt="TP6_5" src="https://github.com/user-attachments/assets/e2f776c3-db49-4fe9-b971-f08d7cc174b0" />

<img width="512" height="200" alt="TP6_TEST" src="https://github.com/user-attachments/assets/cc52177d-ba06-4bc0-927a-e95e6437b447" />


