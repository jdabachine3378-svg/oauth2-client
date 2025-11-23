# OAuth2 Client - Spring Boot Application

# 🔐 TP — Spring Security OAuth2 & OpenID Connect (Google Login)

Ce projet a pour objectif d’implémenter une authentification moderne dans une application **Spring Boot** en utilisant **OAuth2** et **OpenID Connect (OIDC)** avec **Google** comme fournisseur d’identité (Identity Provider).

L’utilisateur n’a plus besoin d’un compte interne :  
➡ l’authentification est entièrement déléguée à Google.  
➡ Spring Security récupère automatiquement les informations (nom, email, photo) via l’ID Token.

---
## 🎯 Objectifs du TP

- Comprendre les principes du protocole **OAuth2**.  
- Différencier OAuth2 (autorisation) et OIDC (authentification).  
- Configurer Spring Boot comme **client OAuth2**.  
- Mettre en place une **authentification Google**.  
- Extraire les informations utilisateur à partir du **ID Token (JWT)**.  
- Protéger les routes et gérer la redirection automatique.  

---

## 🧩 Architecture utilisée

```text
Navigateur → Spring Boot (client OAuth2) → Google OAuth2 Server
                    ↑                   ↓
         ID Token + Access Token  ←  Auth Code
 ```
## 🚀 Démarrage rapide

### Prérequis
- Java 21
- Maven 3.9+
- Google OAuth2 Client ID et Secret
###   📁 Structure du projet 
<img width="556" height="846" alt="image" src="https://github.com/user-attachments/assets/bb318f3a-a07f-40ba-bafd-50d9fa250ce7" />


### Configuration

1. **Configurer Google OAuth2** :
   - Aller sur [Google Cloud Console](https://console.cloud.google.com)
   - Créer un projet
   - Activer l'API "Google Identity Services"
   - Créer OAuth2 Client ID (Web Application)
   - Ajouter redirect URI : `http://localhost:8080/login/oauth2/code/google`

2. **Configurer les credentials OAuth2** :

   **Option 1 : Variables d'environnement (recommandé)**
   ```bash
   export GOOGLE_CLIENT_ID=votre_client_id
   export GOOGLE_CLIENT_SECRET=votre_secret
   ```
   
   **Option 2 : Fichier application-local.yml** (non versionné)
   ```yaml
   spring:
     security:
       oauth2:
         client:
           registration:
             google:
               client-id: VOTRE_CLIENT_ID
               client-secret: VOTRE_SECRET
   ```
   
   Le fichier `application.yml` utilise des variables d'environnement par défaut pour la sécurité.

### Lancer l'application

#### Avec Maven
```bash
mvn spring-boot:run
```


#### Avec Docker Compose
```bash
docker-compose up --build
```

## 📝 Endpoints

- `http://localhost:8080/` - Page d'accueil
- `http://localhost:8080/profile` - Profil utilisateur (nécessite authentification)
- 


https://github.com/user-attachments/assets/8df89850-167a-4f86-86c7-117372baa3a5


## 🔐 Authentification

L'application utilise Spring Security OAuth2 pour l'authentification Google. Lors de l'accès à `/profile`, vous serez automatiquement redirigé vers Google pour vous connecter.
🧑‍🏫 Auteur

## Jamila DABACHINE — ENS Marrakech
Master : Technologies Émergentes en Éducation
TP Spring Security — OAuth2 & OpenID Connect
