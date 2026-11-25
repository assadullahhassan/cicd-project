# 🌱 Plant Therapist

> *"Emotional support tips for people who keep killing their houseplants."*

**Plant Therapist** is a full-stack web application featuring a clean, minimalist landing page designed to collect email signups for an upcoming launch. It is built with a modern Node.js and Express backend, PostgreSQL database integration via Drizzle ORM, Docker containerization, and a complete GitHub Actions CI/CD pipeline deployed to Render.

🌐 **Live Demo:** [plant-therapist-web-hbph.onrender.com](https://plant-therapist-web-hbph.onrender.com)

📸 **Screenshot/Video:** [Click here](https://drive.google.com/drive/folders/1G_HxI-a1HKV6oQNscJe_CgqYXZgC8tDe?usp=sharing)

---

## ✨ Features

- **Minimalist Landing Page:** Clean, responsive UI with email validation and waitlist registration ("Notify Me").
- **Database Persistence:** Stores subscriber emails securely using PostgreSQL (Neon Serverless / `pg`) and Drizzle ORM.
- **Automated Testing:** Unit and integration tests powered by Jest and Supertest.
- **Code Quality & Formatting:** Enforced code standards using ESLint and Prettier.
- **Containerized Deployment:** Ready-to-run `Dockerfile` for consistent environments across development and production.
- **CI/CD Pipeline:** Automated formatting checks, linting, testing, and Docker image builds via GitHub Actions.

---

## 🛠️ Tech Stack

### Frontend
- **HTML5 & CSS3** (`public/index.html`, `public/styles.css`)
- **Vanilla JavaScript** (`public/scripts.js`)

### Backend & Database
- **Runtime:** Node.js (v24)
- **Framework:** Express (`^5.2.1`)
- **Database:** PostgreSQL (`pg`, `@neondatabase/serverless`)
- **ORM & Migrations:** Drizzle ORM (`^0.45.1`) & Drizzle Kit (`^0.31.10`)
- **Validation:** `validator` (`^13.15.26`)

### DevOps, Testing & Tooling
- **Testing:** Jest (`^30.4.2`), Supertest (`^7.2.2`)
- **Linting & Formatting:** ESLint (`^10.6.0`), Prettier (`^3.9.4`)
- **Containerization:** Docker
- **CI/CD & Hosting:** GitHub Actions & Render

---

## 📁 Project Structure

```text
plant-therapist-cicd-project/
├── .github/
│   └── workflows/
│       └── ci.yml           # GitHub Actions CI/CD workflow
├── drizzle/                 # Generated SQL migration files
├── public/                  # Static frontend assets
│   ├── index.html           # Landing page markup
│   ├── scripts.js           # Client-side form handling
│   └── styles.css           # Application styling
├── src/
│   ├── db/
│   │   ├── index.js         # Database connection setup
│   │   ├── migrate.js       # Database migration runner
│   │   └── schema.js        # Drizzle database schema definitions
│   ├── app.js               # Express app configuration & routes
│   ├── app.test.js          # API & integration tests
│   └── server.js            # Application entry point
├── .dockerignore
├── .env                     # Environment variables (not tracked in git)
├── .gitignore
├── .prettierignore
├── .prettierrc
├── Dockerfile               # Docker container instructions
├── drizzle.config.js        # Drizzle Kit configuration
├── eslint.config.mjs        # ESLint configuration
├── package.json
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v24 or higher recommended)
- [PostgreSQL](https://www.postgresql.org/) database (or a [Neon](https://neon.tech/) serverless Postgres instance)
- [Docker](https://www.docker.com/) *(optional, for containerized runs)*

### Installation

1. **Clone the repository:**
   ```bash
   git clone <your-repository-url>
   cd ci-project
   ```

2. **Install dependencies:**
   ```bash
   npm ci
   ```

3. **Configure environment variables:**
   Create a `.env` file in the root directory and add your database connection string and port configuration:
   ```env
   PORT=3000
   DATABASE_URL=postgresql://user:password@host:port/database
   ```

4. **Run database migrations:**
   ```bash
   npm run db:migrate
   ```

5. **Start the server:**
   ```bash
   npm start
   ```
   The application will be available at `http://localhost:3000`.

---

## 📜 Available Scripts

| Command | Description |
| :--- | :--- |
| `npm start` | Starts the production Node.js server (`src/server.js`) |
| `npm test` | Runs the test suite using Jest |
| `npm run db:generate` | Generates SQL migrations from your Drizzle schema |
| `npm run db:migrate` | Applies pending migrations to the PostgreSQL database |
| `npm run lint` | Checks code for linting errors with ESLint |
| `npm run lint:fix` | Automatically fixes ESLint issues |
| `npm run format` | Formats all files using Prettier |
| `npm run format:check` | Verifies that all files adhere to Prettier formatting rules |
| `npm run docker:build` | Builds the Docker image tagged as `cicd` |
| `npm run docker:run` | Runs the Docker container on port `3000` using `.env` |

---

## 🐳 Docker Support

To build and run the application inside a Docker container:

```bash
# Build the image
npm run docker:build

# Run the container
npm run docker:run
```

---

## 🔄 CI/CD Pipeline

Every push and pull request targeting the `main` branch triggers the GitHub Actions workflow (`.github/workflows/ci.yml`), which executes the following stages:

1. **Build and Test:**
   - Checks out the repository and sets up **Node.js 24**.
   - Installs clean dependencies via `npm ci`.
   - Validates code formatting (`npm run format:check`).
   - Runs static code analysis (`npm run lint`).
   - Executes automated tests (`npm test`).
2. **Build and Push:**
   - Runs automatically on pushes to `main` after passing all checks and tests to build and deploy the updated container.

---

