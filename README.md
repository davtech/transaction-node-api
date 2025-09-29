# API REST Node Fastify

A simple RESTful API for managing financial transactions, built with [Fastify](https://www.fastify.io/), [Knex.js](https://knexjs.org/), and [SQLite](https://www.sqlite.org/). This project demonstrates session-based transaction management, environment configuration, and automated testing.

---

## 🚀 Online Production

**[View the API in production](https://transaction-node-api-unlu.onrender.com)**

---

## Features

- Create, list, and retrieve transactions
- Session-based transaction isolation using cookies
- Transaction summary endpoint
- SQLite database with migrations via Knex.js
- Environment variable management with dotenv and zod validation
- Automated tests with Vitest and Supertest
- Linting and formatting with ESLint and Prettier

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18+ recommended)
- [npm](https://www.npmjs.com/)

### Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/your-username/api_rest_node_fastfy.git
   cd api_rest_node_fastfy
   ```

2. Install dependencies:

   ```sh
   npm install
   ```

3. Copy the example environment file and configure as needed:

   ```sh
   cp .env.example .env
   ```

   Edit `.env` to set your `DATABASE_URL` and other variables.

### Database Setup

Run the database migrations:

```sh
npm run knex migrate:latest
```

### Running the Server

Start the development server:

```sh
npm run dev
```

The server will run at [http://localhost:3333](http://localhost:3333) by default.

### Running Tests

To run the test suite:

```sh
npm test
```

## API Endpoints

All endpoints are prefixed with `/transactions`.

### Create Transaction

- **POST** `/transactions`
- **Body:**
  ```json
  {
    "title": "New transaction",
    "amount": 5000,
    "type": "credit" // or "debit"
  }
  ```
- **Response:** `201 Created`

### List Transactions

- **GET** `/transactions`
- **Response:**
  ```json
  {
    "transactions": [
      {
        "id": "...",
        "title": "...",
        "amount": 5000,
        "created_at": "...",
        "session_id": "..."
      }
    ]
  }
  ```

### Get Transaction by ID

- **GET** `/transactions/:id`
- **Response:**
  ```json
  {
    "transaction": {
      "id": "...",
      "title": "...",
      "amount": 5000,
      "created_at": "...",
      "session_id": "..."
    }
  }
  ```

### Get Transaction Summary

- **GET** `/transactions/summary`
- **Response:**
  ```json
  {
    "summary": {
      "amount": 3000
    }
  }
  ```

## Project Structure

```
.
├── src/
│   ├── app.ts
│   ├── server.ts
│   ├── database.ts
│   ├── routes/
│   │   └── transactions.ts
│   ├── middlewares/
│   │   └── check-session-id-exists.ts
│   ├── env/
│   │   └── index.ts
│   ├── test/
│   │   └── transactions.spec.ts
│   └── @types/
│       └── knex.d.ts
├── db/
│   ├── migrations/
│   └── app.db
├── .env.example
├── .env.test.example
├── package.json
├── tsconfig.json
└── README.md
```

## Scripts

- `npm run dev` — Start the server in development mode
- `npm run build` — Build the project
- `npm run knex` — Run Knex CLI commands (e.g., migrations)
- `npm run lint` — Lint and fix code
- `npm test` — Run tests

## License

This project is licensed under the ISC License.

---

Made with ❤️ using Fastify, Knex, and SQLite.
