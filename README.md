# 🛒 IB-Shop — Application Web E-commerce

Une application web complète de gestion e-commerce avec React.js (front-end) et Laravel (back-end API REST), avec authentification multi-rôles.

---

## Technologies utilisées

### Back-end
- **Laravel 11** — Framework PHP
- **Laravel Sanctum** — Authentification API par token
- **MySQL** — Base de données relationnelle
- **PHP 8.2+**

### Front-end
- **React.js** (Vite) — Interface utilisateur
- **Tailwind CSS** — Design moderne et responsive
- **Axios** — Communication avec l'API
- **React Router DOM** — Navigation entre les pages

---

## Fonctionnalités

### Côté Client (User)
-  Inscription et connexion sécurisée
-  Catalogue de produits avec recherche, filtres et tri
-  Filtrage par catégorie et par prix
-  Page détail produit avec gestion des quantités
- Panier d'achat (ajout, modification, suppression)
- Passage de commande
-  Historique des commandes avec statuts
- Notifications en temps réel (confirmation, livraison...)

### Côté Admin
-  Dashboard avec statistiques (produits, commandes, CA)
-  Gestion des produits (CRUD + upload d'images)
-  Gestion des catégories (CRUD)
-  Gestion des commandes (changement de statut)
-  Gestion des utilisateurs

### Sécurité
-  Authentification par token (Laravel Sanctum)
- Protection des routes par rôle (Admin / User)
-  Validation des données côté serveur
-  Middleware de vérification des rôles

---

##  Structure du projet

```
prjoet-ib-shop/
├── backend/          # API Laravel
│   ├── app/
│   │   ├── Http/
│   │   │   ├── Controllers/
│   │   │   │   ├── AuthController.php
│   │   │   │   ├── CategoryController.php
│   │   │   │   ├── ProductController.php
│   │   │   │   ├── OrderController.php
│   │   │   │   ├── UserController.php
│   │   │   │   └── NotificationController.php
│   │   │   └── Middleware/
│   │   │       └── CheckRole.php
│   │   └── Models/
│   │       ├── User.php
│   │       ├── Category.php
│   │       ├── Product.php
│   │       ├── Order.php
│   │       ├── OrderItem.php
│   │       └── Notification.php
│   ├── database/
│   │   ├── migrations/
│   │   └── seeders/
│   └── routes/
│       └── api.php
│
└── frontend/         # Application React
    └── src/
        ├── api/
        │   └── axios.js
        ├── components/
        │   ├── Navbar.jsx
        │   ├── Footer.jsx
        │   ├── SkeletonCard.jsx
        │   ├── PrivateRoute.jsx
        │   └── AdminStats.jsx
        ├── context/
        │   └── AuthContext.jsx
        └── pages/
            ├── Home.jsx
            ├── Login.jsx
            ├── Register.jsx
            ├── ProductDetail.jsx
            ├── NotFound.jsx
            ├── admin/
            │   ├── Dashboard.jsx
            │   ├── ManageProducts.jsx
            │   ├── ManageCategories.jsx
            │   ├── ManageOrders.jsx
            │   └── ManageUsers.jsx
            └── user/
                ├── Cart.jsx
                └── MyOrders.jsx
```

---

##  Installation et lancement

### Prérequis
- PHP 8.2+
- Composer
- Node.js 18+
- MySQL

---

### 1. Cloner le repository

```bash
git clone https://github.com/votre-username/ma-boutique.git
cd ma-boutique
```

---

### 2. Installer et configurer le Back-end (Laravel)

```bash
cd backend

# Installer les dépendances
composer install

# Copier le fichier d'environnement
cp .env.example .env

# Générer la clé d'application
php artisan key:generate
```

Modifier le fichier `.env` avec vos informations de base de données :

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=ecommerce_db
DB_USERNAME=root
DB_PASSWORD=
```

```bash
# Créer la base de données (via phpMyAdmin ou MySQL CLI)
# Puis lancer les migrations
php artisan migrate

# Créer le lien de stockage pour les images
php artisan storage:link

# (Optionnel) Insérer des données de test
php artisan db:seed

# Lancer le serveur
php artisan serve
```

Le back-end sera disponible sur : `http://127.0.0.1:8000`

---

### 3. Installer et configurer le Front-end (React)

```bash
cd frontend

# Installer les dépendances
npm install

# Lancer le serveur de développement
npm run dev
```

Le front-end sera disponible sur : `http://localhost:5173`

---

### 4. Créer un compte Admin

Après inscription, aller dans phpMyAdmin et exécuter :

```sql
UPDATE users SET role = 'admin' WHERE email = 'votre@email.com';
```

---

## 🗄️ Base de données

| Table | Description |
|---|---|
| `users` | Comptes utilisateurs avec rôles (admin/user) |
| `categories` | Catégories de produits |
| `products` | Produits avec prix, stock et images |
| `orders` | Commandes des utilisateurs |
| `order_items` | Détail des produits dans chaque commande |
| `notifications` | Notifications pour les utilisateurs |

---

## 🔗 API Endpoints principaux

| Méthode | Route | Accès |
|---|---|---|
| POST | /api/register | Public |
| POST | /api/login | Public |
| GET | /api/products | Public |
| GET | /api/categories | Public |
| POST | /api/orders | Auth |
| GET | /api/orders/my | Auth |
| GET | /api/notifications | Auth |
| POST | /api/products | Admin |
| PUT | /api/orders/{id}/status | Admin |
| GET | /api/users | Admin |

---

## 👥 Équipe

Projet réalisé dans le cadre du cours de Développement Web par SABA GOULWINDIN NAYIM ISAACK ET MOUSSA IDE IBRAHIM assiste par Claude dans la correction des erreurs et l'optimisation du code, encadré par Mr Rahhal ERRATTAHI
Université Chouaib Doukkali  ENSA El Jadida  

---

## 📄 Licence

Projet académique — Tous droits réservés © 2025
