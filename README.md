# OAuth2 Client - Spring Boot Application

Application Spring Boot avec authentification Google OAuth2.

## 🚀 Démarrage rapide

### Prérequis
- Java 21
- Maven 3.9+
- Google OAuth2 Client ID et Secret

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

#### Avec Docker
```bash
# Build
docker build -t oauth2-client .

# Run
docker run -p 8080:8080 oauth2-client
```

#### Avec Docker Compose
```bash
docker-compose up --build
```

## 📝 Endpoints

- `http://localhost:8080/` - Page d'accueil
- `http://localhost:8080/profile` - Profil utilisateur (nécessite authentification)

## 🔐 Authentification

L'application utilise Spring Security OAuth2 pour l'authentification Google. Lors de l'accès à `/profile`, vous serez automatiquement redirigé vers Google pour vous connecter.

