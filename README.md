# 🏋️ FitFlow Redesign

> A comprehensive redesign of the FitFlow fitness application, focused on improving user experience, performance, and AI-powered personalization.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-in%20development-orange.svg)
![Version](https://img.shields.io/badge/version-0.1.0-green.svg)

---

## 📖 Overview

**FitFlow** is a modern fitness tracking and workout planning application. This redesign aims to deliver:

- 🎨 **Enhanced UI/UX** — A cleaner, more intuitive interface based on HCI principles
- 🤖 **AI-Powered Recommendations** — Personalized workout and nutrition suggestions
- ⚡ **Improved Performance** — Faster load times and smoother interactions
- 📱 **Responsive Design** — Seamless experience across all devices
- 🔐 **Better Security** — Modern authentication and data protection

---

## 🏗️ Project Structure

```
fitflow-redesign/
├── frontend/              # React-based frontend application
│   ├── public/            # Static assets
│   ├── src/
│   │   ├── components/    # Reusable UI components
│   │   ├── pages/         # Page-level components
│   │   ├── hooks/         # Custom React hooks
│   │   ├── services/      # API service layer
│   │   ├── store/         # State management
│   │   ├── styles/        # Global styles and themes
│   │   └── utils/         # Utility functions
│   └── package.json
├── backend/               # Node.js/Express backend API
│   ├── src/
│   │   ├── controllers/   # Request handlers
│   │   ├── models/        # Database models
│   │   ├── routes/        # API route definitions
│   │   ├── middleware/     # Custom middleware
│   │   ├── services/      # Business logic
│   │   └── utils/         # Utility functions
│   └── package.json
├── ai-service/            # AI/ML microservice
│   ├── models/            # Trained ML models
│   ├── src/
│   │   ├── recommendation/# Workout recommendation engine
│   │   ├── analysis/      # User data analysis
│   │   └── training/      # Model training scripts
│   └── requirements.txt
├── docs/                  # Project documentation
│   ├── architecture/      # Architecture diagrams & decisions
│   ├── api/               # API documentation
│   ├── design/            # UI/UX design documents
│   └── research/          # HCI research & findings
├── .github/               # GitHub configuration
│   └── workflows/         # CI/CD workflows
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🛠️ Tech Stack

| Layer            | Technology                        | Purpose                          |
|------------------|-----------------------------------|----------------------------------|
| **Frontend**     | React 18 + TypeScript             | UI framework                     |
| **Styling**      | Tailwind CSS + Framer Motion      | Styling & animations             |
| **State Mgmt**   | Zustand                           | Lightweight state management     |
| **Backend**      | Node.js + Express                 | REST API server                  |
| **Database**     | MongoDB + Redis                   | Data persistence & caching       |
| **AI/ML**        | Python + TensorFlow/scikit-learn  | Recommendation engine            |
| **Auth**         | JWT + OAuth 2.0                   | Authentication & authorization   |
| **Deployment**   | Docker + GitHub Actions           | Containerization & CI/CD         |
| **Testing**      | Jest + Cypress + Pytest           | Unit, integration & E2E testing  |

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** >= 18.x
- **Python** >= 3.10
- **MongoDB** >= 6.0
- **Docker** (optional, for containerized development)

### Installation

```bash
# Clone the repository
git clone https://github.com/duwi2002/FitFlow-redesign.-.git
cd fitflow-redesign

# Install frontend dependencies
cd frontend && npm install

# Install backend dependencies
cd ../backend && npm install

# Install AI service dependencies
cd ../ai-service && pip install -r requirements.txt
```

### Running the Application

```bash
# Start the backend server
cd backend && npm run dev

# Start the frontend dev server
cd frontend && npm run dev

# Start the AI service
cd ai-service && python -m uvicorn main:app --reload
```

---

## 📊 Key Features

### Phase 1 — Core Redesign
- [ ] User authentication & onboarding flow
- [ ] Dashboard redesign with fitness metrics
- [ ] Workout plan creation & tracking
- [ ] Progress visualization (charts & graphs)

### Phase 2 — AI Integration
- [ ] AI-powered workout recommendations
- [ ] Adaptive difficulty adjustment
- [ ] Nutrition tracking with meal suggestions
- [ ] Recovery & rest day recommendations

### Phase 3 — Social & Gamification
- [ ] Community features & social feed
- [ ] Achievement badges & streaks
- [ ] Challenges & leaderboards
- [ ] Workout sharing & collaboration

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

- **Project Lead / Developer** — [@duwi2002](https://github.com/duwi2002)

---

<p align="center">
  Built with ❤️ for the HCI Lab
</p>
