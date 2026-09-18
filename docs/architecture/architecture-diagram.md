# 🏛️ FitFlow Redesign — Architecture Diagram

## High-Level System Architecture

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                              CLIENT LAYER                                    │
│                                                                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                       │
│  │  Web Browser  │  │  Mobile App  │  │  PWA Client  │                       │
│  │  (React/TS)   │  │  (Future RN) │  │  (Offline)   │                       │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘                       │
│         │                  │                  │                               │
│         └──────────────────┼──────────────────┘                               │
│                            │                                                 │
│                    ┌───────▼────────┐                                        │
│                    │   API Gateway  │                                        │
│                    │   (Nginx)      │                                        │
│                    └───────┬────────┘                                        │
└────────────────────────────┼─────────────────────────────────────────────────┘
                             │
┌────────────────────────────┼─────────────────────────────────────────────────┐
│                     SERVICE LAYER                                            │
│                            │                                                 │
│         ┌──────────────────┼──────────────────┐                              │
│         │                  │                  │                               │
│  ┌──────▼───────┐  ┌──────▼───────┐  ┌──────▼───────┐                       │
│  │   Backend     │  │  AI Service   │  │  Auth Service│                       │
│  │   API         │  │  (FastAPI)    │  │  (JWT/OAuth) │                       │
│  │  (Express)    │  │               │  │              │                       │
│  │               │  │ • Workout Rec │  │ • Login      │                       │
│  │ • Workouts    │  │ • Form Check  │  │ • Register   │                       │
│  │ • Users       │  │ • Analytics   │  │ • OAuth 2.0  │                       │
│  │ • Progress    │  │ • Predictions │  │ • Token Mgmt │                       │
│  │ • Nutrition   │  │               │  │              │                       │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘                       │
│         │                  │                  │                               │
└─────────┼──────────────────┼──────────────────┼──────────────────────────────┘
          │                  │                  │
┌─────────┼──────────────────┼──────────────────┼──────────────────────────────┐
│         │           DATA LAYER                │                              │
│         │                  │                  │                               │
│  ┌──────▼───────┐  ┌──────▼───────┐  ┌──────▼───────┐                       │
│  │   MongoDB     │  │    Redis     │  │  File Store  │                       │
│  │               │  │              │  │  (S3/Local)  │                       │
│  │ • Users       │  │ • Sessions   │  │              │                       │
│  │ • Workouts    │  │ • Cache      │  │ • Profile    │                       │
│  │ • Exercises   │  │ • Leaderboard│  │   Images     │                       │
│  │ • Meals       │  │ • Rate Limit │  │ • ML Models  │                       │
│  │ • Progress    │  │              │  │ • Exports    │                       │
│  └──────────────┘  └──────────────┘  └──────────────┘                       │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## Component Architecture (Frontend)

```
App
├── Layout
│   ├── Navbar
│   │   ├── Logo
│   │   ├── NavLinks
│   │   ├── SearchBar
│   │   └── UserMenu
│   ├── Sidebar
│   │   ├── SideNavLinks
│   │   └── QuickActions
│   └── Footer
│
├── Pages
│   ├── Dashboard
│   │   ├── StatsOverview (calories, steps, workouts)
│   │   ├── WeeklyChart
│   │   ├── RecentWorkouts
│   │   ├── AIRecommendations
│   │   └── ProgressRing
│   │
│   ├── Workouts
│   │   ├── WorkoutList
│   │   ├── WorkoutCard
│   │   ├── WorkoutDetail
│   │   ├── ExerciseLibrary
│   │   └── WorkoutBuilder
│   │
│   ├── Progress
│   │   ├── ProgressCharts
│   │   ├── BodyMetrics
│   │   ├── GoalTracker
│   │   └── HistoryTimeline
│   │
│   ├── Nutrition
│   │   ├── MealLogger
│   │   ├── NutritionSummary
│   │   ├── MealSuggestions (AI)
│   │   └── CalorieTracker
│   │
│   ├── Profile
│   │   ├── UserInfo
│   │   ├── FitnessGoals
│   │   ├── Preferences
│   │   └── AccountSettings
│   │
│   └── Auth
│       ├── LoginForm
│       ├── RegisterForm
│       ├── ForgotPassword
│       └── OAuthButtons
│
└── Shared Components
    ├── Button
    ├── Card
    ├── Modal
    ├── Toast
    ├── LoadingSpinner
    ├── EmptyState
    └── ErrorBoundary
```

---

## API Architecture

```
Backend API Routes
│
├── /api/v1/auth
│   ├── POST   /register
│   ├── POST   /login
│   ├── POST   /logout
│   ├── POST   /refresh-token
│   └── GET    /oauth/:provider
│
├── /api/v1/users
│   ├── GET    /me
│   ├── PUT    /me
│   ├── PUT    /me/avatar
│   └── DELETE /me
│
├── /api/v1/workouts
│   ├── GET    /                    (list workouts)
│   ├── POST   /                    (create workout)
│   ├── GET    /:id                 (get workout)
│   ├── PUT    /:id                 (update workout)
│   ├── DELETE /:id                 (delete workout)
│   └── POST   /:id/complete        (mark complete)
│
├── /api/v1/exercises
│   ├── GET    /                    (exercise library)
│   ├── GET    /:id                 (exercise details)
│   └── GET    /search?q=           (search exercises)
│
├── /api/v1/progress
│   ├── GET    /                    (progress history)
│   ├── POST   /                    (log progress)
│   ├── GET    /stats               (aggregated stats)
│   └── GET    /chart/:metric       (chart data)
│
├── /api/v1/nutrition
│   ├── GET    /meals               (meal history)
│   ├── POST   /meals               (log meal)
│   ├── GET    /summary/:date       (daily summary)
│   └── GET    /suggestions         (AI suggestions)
│
└── /api/v1/ai
    ├── GET    /recommendations     (workout recs)
    ├── POST   /analyze             (analyze progress)
    └── GET    /insights            (AI insights)
```

---

## Data Flow Diagram

```
User Interaction Flow:

    ┌─────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐
    │User │────▶│ React UI │────▶│ Zustand  │────▶│ API Svc  │
    │     │◀────│          │◀────│  Store   │◀────│ (Axios)  │
    └─────┘     └──────────┘     └──────────┘     └─────┬────┘
                                                         │
                                                         ▼
                                                  ┌──────────┐
                                                  │ Express  │
                                                  │ Backend  │
                                                  └─────┬────┘
                                                        │
                                          ┌─────────────┼─────────────┐
                                          ▼             ▼             ▼
                                   ┌──────────┐ ┌──────────┐ ┌──────────┐
                                   │ MongoDB  │ │  Redis   │ │ AI Svc   │
                                   │          │ │  Cache   │ │ (Python) │
                                   └──────────┘ └──────────┘ └──────────┘
```

---

## Deployment Architecture

```
┌─────────────────────────────────────────────────┐
│                  GitHub Actions                  │
│            (CI/CD Pipeline)                      │
│                                                  │
│  ┌──────┐   ┌──────┐   ┌──────┐   ┌──────────┐ │
│  │ Lint │──▶│ Test │──▶│Build │──▶│  Deploy   │ │
│  └──────┘   └──────┘   └──────┘   └──────────┘ │
└─────────────────────────────────────────────────┘
                                          │
                                          ▼
                              ┌───────────────────┐
                              │  Docker Containers │
                              │                    │
                              │  ┌──────────────┐  │
                              │  │   Frontend   │  │
                              │  │  (Nginx+SPA) │  │
                              │  └──────────────┘  │
                              │  ┌──────────────┐  │
                              │  │   Backend    │  │
                              │  │  (Node.js)   │  │
                              │  └──────────────┘  │
                              │  ┌──────────────┐  │
                              │  │  AI Service  │  │
                              │  │  (Python)    │  │
                              │  └──────────────┘  │
                              │  ┌──────────────┐  │
                              │  │  MongoDB     │  │
                              │  └──────────────┘  │
                              │  ┌──────────────┐  │
                              │  │  Redis       │  │
                              │  └──────────────┘  │
                              └───────────────────┘
```

---

## Security Architecture

```
                    ┌─────────────────────┐
                    │    Rate Limiter      │
                    │   (Express Middleware)│
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │    CORS Policy       │
                    │  (Whitelist Origins) │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │  JWT Verification    │
                    │  (Auth Middleware)   │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │  Input Validation    │
                    │  (Joi Schemas)       │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │  Request Handler     │
                    │  (Controller Layer)  │
                    └─────────────────────┘
```

---

*Last updated: September 2026*
