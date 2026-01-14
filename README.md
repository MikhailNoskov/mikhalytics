# Go Developer Test Project

This project is designed to test Go developers' skills in building a backend service that consumes external APIs.

## 📚 Documentation

- **[Getting Started](./GETTING_STARTED.md)** - Start here! Setup guide for candidates
- **[Test Requirements](./TEST_REQUIREMENTS.md)** - Complete test requirements and evaluation criteria
- **[Test Summary](./TEST_SUMMARY.md)** - Quick overview of required tasks
- **[Candidate Checklist](./CANDIDATE_CHECKLIST.md)** - Track your progress

## Project Structure

```
.
├── node-backend/     # Node.js Express API server (calls Go backend)
├── go-backend/        # Go HTTP server (data source)
└── react-frontend/    # React frontend (calls Node.js backend)
```

## Architecture Flow

```
React Frontend (port 5173)
    ↓
Node.js Backend (port 3000)
    ↓
Go Backend (port 8080)
```

## Quick Start

**Important:** Start services in this order:

### 1. Start Go Backend (Data Source)

```bash
cd go-backend
go mod tidy
go run .
```

The Go backend will run on `http://localhost:8080` and serves as the data source.

### 2. Start Node.js Backend (API Gateway)

In a new terminal:

```bash
cd node-backend
npm install
npm start
```

The Node.js backend will run on `http://localhost:3000` and proxies requests to the Go backend.

### 3. Start React Frontend

In a new terminal:

```bash
cd react-frontend
npm install
npm run dev
```

The React frontend will run on `http://localhost:5173` and calls the Node.js backend.

## Project Overview

### Go Backend (Data Source)
A Go HTTP server that:
- Serves as the primary data source
- Stores users and tasks in-memory
- Exposes REST endpoints (`/api/users`, `/api/tasks`, `/api/stats`)
- Demonstrates Go HTTP server implementation
- Handles JSON requests/responses
- Implements thread-safe data access with mutexes

### Node.js Backend (API Gateway)
A RESTful API server built with Express that:
- Acts as a proxy/gateway between React and Go
- Calls the Go backend for all data operations
- Provides the same API interface to the frontend
- Demonstrates HTTP client usage in Node.js
- Handles error propagation and status codes

### React Frontend
A modern React application that:
- Consumes the Node.js backend API
- Displays users and tasks
- Provides filtering and search capabilities
- Shows real-time statistics
- Features a modern, responsive UI

## Test Requirements

**📋 See [TEST_REQUIREMENTS.md](./TEST_REQUIREMENTS.md) for detailed test requirements and evaluation criteria.**

The test includes:
- **Phase 1**: Setup and understanding (30 min)
- **Phase 2**: Core requirements - Add POST/PUT endpoints, logging (2-3 hours)
- **Phase 3**: Advanced features - Persistence, caching, middleware (2-3 hours)
- **Phase 4**: Code quality - Testing, documentation, best practices
- **Phase 5**: Bonus tasks - Authentication, rate limiting, metrics

## Requirements

- Node.js 16+ and npm
- Go 1.21+
