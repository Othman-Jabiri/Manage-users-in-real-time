#  Realtime Dashboard - User Management System

Système de gestion d'utilisateurs en temps réel avec Next.js, PostgreSQL et Prisma.

##  Fonctionnalités

-  Authentification sécurisée (JWT + bcrypt)
-  Gestion CRUD des utilisateurs (Admin)
-  Dashboard avec statistiques en temps réel
-  Graphique d'activités hebdomadaires
-  Base de données PostgreSQL avec Prisma
-  Interface moderne avec Tailwind CSS
-  Notifications toast
-  Filtres et recherche d'utilisateurs
-  Export de données (CSV/PDF)

##  Technologies

- **Frontend:** Next.js 14, React 18, TypeScript, Tailwind CSS
- **Backend:** Next.js API Routes
- **Database:** PostgreSQL avec Prisma ORM
- **Auth:** JWT + bcrypt
- **Styling:** Tailwind CSS

### Installation

### Prérequis

- Node.js 18+
- PostgreSQL (local ou Supabase)
- npm ou yarn




### 1. Cloner le projet
```bash
git clone https://github.com/TON-USERNAME/realtime-dashboard.git
cd realtime-dashboard
```

### 2. Installer les dépendances
```bash
npm install
```

### 3. Configurer la base de données

Crée un fichier `.env` à la racine :
```env
DATABASE_URL="postgresql://postgres:PASSWORD@localhost:5432/realtime_dashboard"
JWT_SECRET="votre-secret-jwt-unique"
NODE_ENV="development"
```

### 4. Créer les tables
```bash
npx prisma migrate dev --name init
npx prisma generate
```

### 5. Peupler la base de données
```bash
npx prisma db seed
```

Ceci crée 2 comptes de test :
- **Admin:** admin@example.com / admin123
- **User:** user@example.com / user123

### 6. Lancer l'application
```bash
npm run dev
```

Ouvre [http://localhost:3000]

## 📚 Scripts Disponibles
```bash
npm run dev          # Lancer en développement
npm run build        # Build pour production
npm start            # Lancer en production
npx prisma studio    # Interface graphique DB
npx prisma db seed   # Peupler la DB
```

##  Structure du Projet
```
realtime-dashboard/
├── app/
│   ├── api/              # API Routes
│   │   ├── auth/login/   # Authentification
│   │   └── users/        # CRUD utilisateurs
│   ├── dashboard/        # Page dashboard
│   └── page.tsx          # Page de login
├── components/           # Composants React
│   ├── ui/               # Composants UI de base
│   ├── users-table.tsx
│   ├── activity-chart.tsx
│   ├── user-modal.tsx
│   └── notification-provider.tsx
├── lib/
│   ├── db.ts             # Prisma client + helpers
│   ├── auth.ts           # JWT utilities
│   └── utils.ts          # Fonctions utilitaires
├── prisma/
│   ├── schema.prisma     # Schéma de la DB
│   └── seed.ts           # Données de test
└── package.json
```

##  Sécurité

-  Mots de passe hashés avec bcrypt
-  Authentification JWT
-  Protection des routes API
-  Validation des entrées
-  Variables d'environnement


### Variables d'environnement requises
```env
DATABASE_URL=postgresql://...
JWT_SECRET=your-secret-key
NODE_ENV=production
```

##  Schéma de Base de Données

### Table `users`
- id (String, PK)
- email (String, unique)
- password (String, hashed)
- name (String)
- role (String: admin/user)
- createdAt (DateTime)
- lastActive (DateTime)

### Table `activities`
- id (String, PK)
- userId (String, FK)
- action (String)
- timestamp (DateTime)
- metadata (JSON)


## License
MIT

