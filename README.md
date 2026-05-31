# 🚀 Java Platform v2.0 - Enterprise Edition

A **highly scalable, production-ready Java platform** for collaborative learning, real-time code compilation, and communication. Built with modern enterprise technologies to support unlimited users with collaborative features.

---

## 👥 Team

1. **Devank Kashyap**
   - [GitHub Repository](https://github.com/devank26/CODECONNECT)

2. **Aadarsh Dimri**
   - [GitHub Repository](https://github.com/OpEx-Experiment001/CODECONNECT)

3. **Prince Badola**
   - [GitHub Repository](https://github.com/Prince20251337/Jarvis-IDE)

4. **Vaibhav Kathait**
   - [GitHub Profile](https://github.com/Vaibhav27-az)

---

## 📋 Table of Contents

- [Overview](#overview)
- [🎯 Key Features](#key-features)
- [🏗️ Architecture](#architecture)
- [💻 Technology Stack](#technology-stack)
- [📦 System Requirements](#system-requirements)
- [🛠️ Installation & Setup](#installation--setup)
- [📁 Project Structure](#project-structure)
- [🚀 Building & Running](#building--running)
- [🔌 Core Components](#core-components)
- [📚 API Documentation](#api-documentation)
- [🚀 Deployment](#deployment)
- [📝 Contributing](#contributing)

---

## Overview

Java Platform v2.0 is a **complete transformation** from a monolithic JavaFX desktop application to an **enterprise-grade microservices architecture**. It provides:

- **Real-time collaboration** for multiple users
- **Instant Java code compilation** in sandboxed environments
- **AI-powered assistance** with code analysis and suggestions
- **WebRTC video calling** for live communication
- **Complete user management** with authentication and sessions
- **Production-ready deployment** with Docker and cloud support

### Evolution from v1.0 → v2.0

| Feature | v1.0 | v2.0 |
|---------|------|------|
| **Architecture** | Monolithic JavaFX | Microservices + API |
| **Scalability** | Single Machine | Multi-Node Cluster |
| **Users** | Single User | ∞ Concurrent Users |
| **Data Persistence** | None | PostgreSQL + MongoDB |
| **Authentication** | None | JWT + OAuth2-ready |
| **Code Execution** | JVM Sandboxing | Docker Containers |
| **Real-time Chat** | Basic TCP | WebSocket with History |
| **Video Calls** | MJPEG Frames | WebRTC P2P |
| **Deployment** | Manual | Docker + Compose |
| **Monitoring** | None | Logging & Health Checks |

---

## 🎯 Key Features

### ✅ Real-Time Collaboration
- **WebSocket-based communication** for instant messaging
- **Live code sharing** with real-time updates
- **User presence detection** - see who's online
- **Message history** persistence with MongoDB
- **Typing indicators** for better UX

### ✅ Java Code Compiler
- **In-sandbox compilation** - compile and run Java code securely
- **Timeout & memory limits** - prevents resource exhaustion
- **Real-time output** streaming
- **Error reporting** with detailed diagnostics
- **Multi-file support** for complex projects
- **Docker containerization** for production-grade isolation

### ✅ AI-Powered Assistant
- **Intelligent error analysis** - explains compilation errors
- **Code suggestions** - context-aware recommendations
- **Java documentation** - instant API references
- **Learning support** - helps users understand code concepts
- **Integration with multiple AI providers** (OpenAI, Google Gemini)

### ✅ Video Calling
- **WebRTC peer-to-peer** video communication
- **HD quality video streaming**
- **Multiple user support** for group calls
- **Automatic fallback** if direct connection unavailable
- **Screen sharing ready** architecture

### ✅ User Management
- **JWT token-based authentication** - secure, stateless
- **Session management** - track active users
- **User profiles** - manage personal information
- **Activity tracking** - log user actions
- **Role-based access control (RBAC)** ready

### ✅ Enterprise Features
- **Health monitoring** - system status endpoints
- **Comprehensive logging** - audit trails for all operations
- **Error handling** - graceful degradation
- **CORS support** - cross-origin requests
- **Pagination & filtering** - efficient data retrieval
- **Rate limiting ready** - prevent abuse

---

## 🏗️ Architecture

### High-Level System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                   CLIENT LAYER                           │
│  (Web Frontend: React/Vue OR JavaFX Desktop)             │
│  - Code Editor Interface                                 │
│  - Chat UI with Real-time Updates                        │
│  - Video Call Interface                                  │
│  - AI Assistant Chat                                     │
└─────────────────────┬─────────────────────────────────┘
                      │ HTTP/HTTPS + WebSocket + WebRTC
              ┌───────▼────────────┐
              │ API GATEWAY         │
              │ (nginx / HA Proxy)  │
              └───────┬────────────┘
                      │
    ┌─────────────────┼─────────────────┐
    │                 │                  │
    ▼                 ▼                  ▼
┌──────────┐  ┌──────────┐  ┌────────────────┐
│Auth      │  │Compiler  │  │Real-time       │
│Service   │  │Service   │  │Services        │
├──────────┤  ├──────────┤  ├────────────────┤
│- JWT     │  │- Java    │  │- Chat Server   │
│- OAuth2  │  │  Compile │  │  (WebSocket)   │
│- Sessions│  │- Sandbox │  │- Video Relay   │
│- Profiles│  │- Docker  │  │- Notifications│
└──────────┘  └──────────┘  └────────────────┘
    │                 │                  │
    └─────────────────┼──────────────────┘
                      │
            ┌─────────▼──────────┐
            │ Spring Boot Core   │
            │ (REST API Layer)   │
            └─────────┬──────────┘
                      │
    ┌─────────────────┼──────────────────┐
    │                 │                  │
    ▼                 ▼                  ▼
┌──────────┐  ┌──────────┐  ┌────────────┐
│PostgreSQL│  │MongoDB   │  │Redis Cache │
│(RDBMS)   │  │(Documents│  │(Sessions & │
│- Users   │  │- Messages│  │Pub/Sub)    │
│- Sessions│  │- Code    │  └────────────┘
│- History │  │- Logs)   │
└──────────┘  └──────────┘
```

### Layered Architecture

```
┌─────────────────────────────────────────┐
│    PRESENTATION LAYER (Controllers)      │
│  - REST Endpoints (/api/v1/...)         │
│  - WebSocket Handlers                   │
│  - Error Handling & Responses            │
├─────────────────────────────────────────┤
│     BUSINESS LOGIC LAYER (Services)      │
│  - AuthenticationService                │
│  - CompilerService                      │
│  - ChatService                          │
│  - AIAssistantService                   │
│  - VideoService                         │
│  - UserService                          │
├─────────────────────────────────────────┤
│    DATA ACCESS LAYER (Repositories)      │
│  - JPA Repositories (PostgreSQL)        │
│  - MongoDB Repositories                 │
│  - Redis Integration                    │
├─────────────────────────────────────────┤
│ DATABASE & EXTERNAL SERVICES             │
│  - PostgreSQL 15+                       │
│  - MongoDB 6.0+                         │
│  - Redis 7.0+                           │
│  - Docker Container Service             │
│  - AI API Services                      │
└─────────────────────────────────────────┘
```

---

## 💻 Technology Stack

### Backend Technologies

| Category | Technology | Version | Purpose |
|----------|-----------|---------|---------|
| **Language** | Java | 21 LTS | Modern, feature-rich, enterprise-proven |
| **Framework** | Spring Boot | 3.2+ | Rapid development, production-ready |
| **ORM** | Spring Data JPA / Hibernate | Latest | Object-relational mapping |
| **Web** | Spring Web / REST | Latest | RESTful API development |
| **Real-time** | Spring WebSocket | Latest | Real-time bidirectional communication |
| **Security** | Spring Security | Latest | Authentication & authorization |
| **Build** | Maven | 3.8+ | Dependency management & build |

### Database Technologies

| Database | Version | Purpose | Use Case |
|----------|---------|---------|----------|
| **PostgreSQL** | 15+ | Primary relational database | Users, sessions, auth, history |
| **MongoDB** | 6.0+ | Document store | Messages, code snippets, logs |
| **Redis** | 7.0+ | In-memory cache & message broker | Sessions, pub/sub, caching |

### Deployment & Container Technologies

| Technology | Purpose |
|-----------|---------|
| **Docker** | Containerization for deployment |
| **Docker Compose** | Multi-container orchestration (dev/test) |
| **Docker Containers** | Java code sandbox execution |

### Frontend Technologies (v2.0 Ready)

| Technology | Purpose |
|-----------|---------|
| **React 18+ / Vue 3** | Web UI framework (ready for integration) |
| **Vite** | Fast build tool & dev server |
| **WebSocket Client** | Real-time communication |
| **TensorFlow.js** | Browser-based ML (optional) |

---

## 📦 System Requirements

### Minimum Requirements

```
✓ CPU:        2 cores (4+ recommended)
✓ RAM:        4GB (8GB+ recommended)
✓ Storage:    10GB free space (20GB+ for Docker)
✓ Network:    Stable internet connection
```

### Required Software

```
✓ Java Runtime Environment (JRE) 21+
  - OpenJDK: https://adoptopenjdk.net/
  - Eclipse Adoptium recommended
  - Verify: java -version

✓ Maven 3.8+
  - Download: https://maven.apache.org/download.cgi
  - Verify: mvn -version

✓ Docker & Docker Compose (for containerized deployment)
  - Download: https://www.docker.com/products/docker-desktop
  - Verify: docker --version && docker-compose --version

✓ Git (for version control)
  - Download: https://git-scm.com/
  - Verify: git --version
```

### Optional Tools

```
◇ PostgreSQL 15+ (if running outside Docker)
◇ MongoDB 6.0+ (if running outside Docker)
◇ Redis 7.0+ (if running outside Docker)
◇ Node.js 18+ (for frontend development)
```

---

## 🛠️ Installation & Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd "java pbl"
```

### 2. Set Up Java Environment

**Windows (PowerShell):**
```powershell
# Set JAVA_HOME
$env:JAVA_HOME = "C:\Program Files\Eclipse Adoptium\jdk-21.0.2.13-hotspot"
# Verify
java -version
```

**Linux/Mac:**
```bash
export JAVA_HOME="/usr/libexec/java_home -v 21"
java -version
```

### 3. Verify Maven Installation

```bash
mvn --version
# Output should show:
# Apache Maven 3.8.6+
# Java version: 21.x.x
```

### 4. Option A: Local Setup (Requires PostgreSQL, MongoDB, Redis)

```bash
# Install PostgreSQL 15+
# Install MongoDB 6.0+
# Install Redis 7.0+

# Create required databases
psql -U postgres -c "CREATE DATABASE javaplatform_db;"
psql -U postgres -c "CREATE DATABASE javaplatform_cache;"
```

### 4. Option B: Docker Setup (Recommended)

```bash
# Navigate to project directory
cd java-platform-v2

# Start all services with docker-compose
docker-compose up -d

# Wait for services to start (~30 seconds)
docker-compose ps

# View logs
docker-compose logs -f
```

### 5. Build the Project

```bash
cd java-platform-v2/backend

# Clean build
mvn clean install

# Skip tests for faster build
mvn clean install -DskipTests

# Verify build
mvn clean compile
```

### 6. Run the Application

**Using Maven:**
```bash
cd java-platform-v2/backend
mvn spring-boot:run
```

**Using Executable JAR:**
```bash
# Build JAR
mvn clean package

# Run JAR
java -jar target/java-platform-backend.jar
```

**Verify Running Application:**
```bash
# Check health endpoint
curl http://localhost:8080/api/v1/health

# Expected response:
# {"status":"UP","timestamp":"2024-12-20T10:30:00"}
```

---

## 📁 Project Structure

```
java pbl/
│
├── README.md (this file)
├── pom.xml (root POM for main application)
├── config.properties (configuration settings)
│
├── java-platform-v2/                    # Modern Spring Boot Application
│   ├── backend/
│   │   ├── pom.xml (backend dependencies)
│   │   ├── src/main/java/com/javaplatform/
│   │   │   ├── JavaPlatformApplication.java
│   │   │   ├── api/                      # REST Controllers (6 endpoints)
│   │   │   │   ├── AuthenticationController.java
│   │   │   │   ├── CompilerController.java
│   │   │   │   ├── ChatController.java
│   │   │   │   ├── AIAssistantController.java
│   │   │   │   ├── VideoController.java
│   │   │   │   ├── HealthController.java
│   │   │   │   └── UserController.java (ready)
│   │   │   │
│   │   │   ├── config/                  # Configuration Beans
│   │   │   │   ├── AsyncConfig.java        (async task processing)
│   │   │   │   ├── CacheConfig.java        (Redis caching)
│   │   │   │   ├── CorsConfig.java         (cross-origin requests)
│   │   │   │   ├── JpaConfig.java          (ORM configuration)
│   │   │   │   └── WebSocketConfig.java    (real-time communication)
│   │   │   │
│   │   │   ├── core/                    # Core Data Models
│   │   │   │   ├── CompileResult.java
│   │   │   │   ├── ExecutionResult.java
│   │   │   │   └── ApiResponse.java
│   │   │   │
│   │   │   ├── dto/                     # Data Transfer Objects
│   │   │   │   ├── AuthDTOs.java
│   │   │   │   ├── CompilerDTOs.java
│   │   │   │   ├── ChatDTOs.java
│   │   │   │   └── UserDTOs.java
│   │   │   │
│   │   │   ├── model/                   # JPA Entity Classes
│   │   │   │   ├── User.java
│   │   │   │   ├── Session.java
│   │   │   │   ├── CodeSnippet.java
│   │   │   │   └── Message.java
│   │   │   │
│   │   │   ├── realtime/                # WebSocket Handlers
│   │   │   │   ├── ChatWebSocketHandler.java
│   │   │   │   ├── VideoWebSocketHandler.java
│   │   │   │   └── NotificationHandler.java
│   │   │   │
│   │   │   ├── repository/              # Data Access Layer
│   │   │   │   ├── UserRepository.java
│   │   │   │   ├── SessionRepository.java
│   │   │   │   └── CodeSnippetRepository.java
│   │   │   │
│   │   │   ├── service/                 # Business Logic
│   │   │   │   ├── AuthenticationService.java
│   │   │   │   ├── CompilerService.java
│   │   │   │   ├── ChatService.java
│   │   │   │   ├── AIAssistantService.java
│   │   │   │   ├── VideoService.java
│   │   │   │   └── UserService.java
│   │   │   │
│   │   │   └── util/                    # Utility Classes
│   │   │       ├── JwtTokenProvider.java
│   │   │       ├── DockerExecutor.java
│   │   │       ├── ErrorAnalyzer.java
│   │   │       └── CloudServiceClient.java
│   │   │
│   │   ├── src/main/resources/
│   │   │   ├── application.yml           # Spring Boot configuration
│   │   │   ├── application-dev.yml       # Development config
│   │   │   ├── application-prod.yml      # Production config
│   │   │   └── schema.sql                # Database initialization
│   │   │
│   │   └── target/                       # Build output
│   │       ├── classes/                  # Compiled classes
│   │       ├── java-platform-backend.jar # Executable JAR
│   │       └── generated-sources/        # Generated code
│   │
│   ├── frontend/                        # Web UI (React/Vue ready)
│   │   ├── index.html
│   │   ├── js/
│   │   │   ├── app.js
│   │   │   ├── components/
│   │   │   ├── services/
│   │   │   └── utils/
│   │   └── css/
│   │
│   ├── docker-compose.yml               # Container orchestration
│   ├── Dockerfile                       # Backend container
│   ├── schema.sql                       # Database initialization
│   ├── README.md                        # Backend documentation
│   └── QUICKSTART.md                    # Quick start guide
│
├── src/                                 # Original JavaFX Application (v1.0)
│   └── main/java/com/javaplatform/
│       ├── MainApp.java                 # Desktop application entry
│       ├── SessionState.java            # Session management
│       ├── server/                      # Network servers
│       │   ├── AppServer.java           # Main TCP server
│       │   ├── ChatServer.java          # Chat functionality
│       │   └── VideoRelayServer.java    # Video streaming
│       ├── service/                     # Business logic
│       │   ├── CompilerService.java
│       │   ├── CompilerResult.java
│       │   ├── AIService.java
│       │   ├── ErrorAnalyser.java
│       │   └── VideoService.java
│       └── view/                        # UI components
│           ├── MainWindow.java
│           ├── LoginView.java
│           ├── ChatTab.java
│           ├── CompilerTab.java
│           ├── AIAssistantTab.java
│           └── VideoTab.java
│
├── target/                              # v1.0 Build output
│   ├── classes/
│   ├── java-platform-1.0-SNAPSHOT.jar
│   └── generated-sources/
│
└── Documentation Files/
    ├── EXECUTIVE_SUMMARY.md             # High-level overview
    ├── SYSTEM_DESIGN_DOCUMENT.md        # Architecture & design
    ├── IMPLEMENTATION_DECISIONS.md      # Key decisions matrix
    ├── IMPLEMENTATION_ROADMAP.md        # Detailed timeline
    ├── DEPLOYMENT_GUIDE.md              # Production deployment
    ├── QUICK_REFERENCE_GUIDE.md         # Feature reference
    ├── ADVANCED_JAVA_IMPLEMENTATION.md  # Technical deep-dive
    ├── FINAL_AUDIT_REPORT.md            # Quality metrics
    └── CODE_TEMPLATES_READY_TO_USE.md   # Code examples
```

---

## 🚀 Building & Running

### Quick Start (Using Docker) - Recommended ⭐

```bash
# 1. Navigate to backend directory
cd java-platform-v2/backend

# 2. Build and start with Docker
docker-compose up --build -d

# 3. Check services are running
docker-compose ps
# All services should show "Up"

# 4. Verify application health
curl http://localhost:8080/api/v1/health

# 5. View logs
docker-compose logs -f backend
```

### Manual Build & Run (Without Docker)

```bash
# 1. Build project
mvn clean install

# 2. Run Spring Boot application
mvn spring-boot:run

# 3. Application starts on http://localhost:8080
# 4. View startup logs in terminal
```

### Build Phases

```bash
# Clean (removes previous build)
mvn clean

# Compile source code
mvn compile

# Run tests
mvn test

# Package into JAR
mvn package

# Install to local repository
mvn install

# All at once (recommended)
mvn clean package -DskipTests
```

---

## 🔌 Core Components

### 1. **Authentication Service** (`AuthenticationController`)
- JWT token generation and validation
- User registration and login
- Session management
- OAuth2 integration ready
- **Endpoints:**
  - `POST /api/v1/auth/register` - Register new user
  - `POST /api/v1/auth/login` - User login
  - `POST /api/v1/auth/refresh` - Refresh token
  - `POST /api/v1/auth/logout` - User logout

### 2. **Compiler Service** (`CompilerController`)
- Compile Java code in isolated Docker containers
- Execute with timeout and memory limits
- Real-time output streaming
- Error reporting and analysis
- **Endpoints:**
  - `POST /api/v1/compile/java` - Compile Java code
  - `POST /api/v1/compile/execute` - Execute compiled code
  - `GET /api/v1/compile/status/{id}` - Check compilation status
  - `GET /api/v1/compile/history` - Get compilation history

### 3. **Chat Service** (`ChatController`)
- Real-time WebSocket messaging
- Message persistence in MongoDB
- Message history retrieval
- User presence tracking
- **Endpoints:**
  - `GET /api/v1/chat/messages` - Get message history
  - `POST /api/v1/chat/send` - Send message
  - `GET /api/v1/chat/users` - Get online users
  - **WebSocket:** `/ws/chat/{userId}` - Real-time chat

### 4. **AI Assistant Service** (`AIAssistantController`)
- Error analysis and explanation
- Code suggestions and improvements
- Java documentation references
- Learning support
- **Endpoints:**
  - `POST /api/v1/ai/analyze-error` - Analyze compilation error
  - `POST /api/v1/ai/suggest-code` - Get code suggestions
  - `GET /api/v1/ai/documentation/{className}` - Get API docs
  - `POST /api/v1/ai/explain` - Explain code

### 5. **Video Service** (`VideoController`)
- WebRTC peer-to-peer video calling
- Video relay for unreliable networks
- Multiple user support
- **Endpoints:**
  - `POST /api/v1/video/initiate` - Start video call
  - `POST /api/v1/video/offer` - Send WebRTC offer
  - `POST /api/v1/video/answer` - Send answer
  - `POST /api/v1/video/ice-candidate` - Exchange ICE candidates

### 6. **Health Check** (`HealthController`)
- System health monitoring
- Component status verification
- **Endpoints:**
  - `GET /api/v1/health` - Overall system health
  - `GET /api/v1/health/detailed` - Detailed component status

---

## 📚 API Documentation

### Base URL
```
http://localhost:8080/api/v1
```

### Authentication Header (Required for protected endpoints)
```
Authorization: Bearer <JWT_TOKEN>
```

### Response Format
```json
{
  "status": "success|error",
  "data": { /* response payload */ },
  "message": "Human-readable message",
  "timestamp": "2024-12-20T10:30:00Z"
}
```

### Example: Compile and Execute Java Code

**Request:**
```bash
curl -X POST http://localhost:8080/api/v1/compile/java \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "code": "public class HelloWorld { public static void main(String[] args) { System.out.println(\"Hello, World!\"); } }",
    "mainClass": "HelloWorld",
    "timeout": 5000
  }'
```

**Response:**
```json
{
  "status": "success",
  "data": {
    "compilationId": "compile-12345",
    "compiled": true,
    "output": "Hello, World!",
    "executionTime": 142,
    "errors": []
  },
  "message": "Code compiled and executed successfully"
}
```

---

## 🚀 Deployment

### Production Deployment (Docker)

```bash
# 1. Build Docker image
docker build -t java-platform:latest .

# 2. Tag for registry (e.g., Docker Hub)
docker tag java-platform:latest your-registry/java-platform:latest

# 3. Push to registry
docker push your-registry/java-platform:latest

# 4. Deploy on target server
docker run -d \
  -p 8080:8080 \
  -e SPRING_PROFILES_ACTIVE=prod \
  -e DB_HOST=your-db-host \
  -e REDIS_HOST=your-redis-host \
  your-registry/java-platform:latest
```

### Cloud Deployment Options

- **AWS:** ECS, EKS, Elastic Beanstalk
- **Azure:** Container Instances, App Service, AKS
- **Google Cloud:** Cloud Run, GKE
- **DigitalOcean:** Droplets + Docker

### Database Migration

```bash
# Execute schema.sql on PostgreSQL
psql -U postgres -d javaplatform_db -f schema.sql

# MongoDB initialization (automatic via app)
# Collections created on first use
```

---

## 📝 Contributing

### Development Workflow

1. **Create feature branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make changes and commit:**
   ```bash
   git add .
   git commit -m "Add: description of your feature"
   ```

3. **Push and create pull request:**
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Code review and merge into main**

### Coding Standards

- **Language:** Java 21+
- **Framework:** Spring Boot 3.2+
- **Build Tool:** Maven 3.8+
- **Code Style:** Google Java Style Guide
- **Documentation:** JavaDoc for public APIs

### Running Tests

```bash
# Run all tests
mvn test

# Run specific test class
mvn test -Dtest=CompilerServiceTest

# Run with coverage
mvn test jacoco:report
```

---

## 📞 Support & Resources

### Documentation
- [System Design Document](SYSTEM_DESIGN_DOCUMENT.md) - Deep architecture
- [Implementation Roadmap](IMPLEMENTATION_ROADMAP.md) - Development timeline
- [Quick Reference Guide](QUICK_REFERENCE_GUIDE.md) - Feature quick lookup
- [Deployment Guide](DEPLOYMENT_GUIDE.md) - Production setup

### External Resources
- [Spring Boot Docs](https://spring.io/projects/spring-boot)
- [Java 21 Documentation](https://docs.oracle.com/en/java/javase/21/)
- [Docker Docs](https://docs.docker.com/)
- [PostgreSQL Docs](https://www.postgresql.org/docs/)

### Common Issues & Solutions

**Issue:** `JAVA_HOME not set`
```bash
# Solution: Set JAVA_HOME environment variable
export JAVA_HOME=/path/to/jdk-21
```

**Issue:** `Port 8080 already in use`
```bash
# Solution: Change port in application.yml
server.port=8081
```

**Issue:** `Database connection failed`
```bash
# Solution: Verify database is running and credentials are correct
docker-compose ps
```

---

## 📊 Project Statistics

- **Language:** Java (primary), HTML/CSS/JavaScript (frontend)
- **Total Files:** 50+
- **Core Modules:** 6 (Authentication, Compiler, Chat, AI, Video, Health)
- **Database Models:** 10+
- **API Endpoints:** 25+
- **Test Coverage:** 80%+ (planned)
- **Build Time:** ~30 seconds (clean build)
- **Container Size:** ~500MB (optimized)

---

## 📄 License & Version

- **Version:** 2.0.0 (Production)
- **Status:** Active Development
- **Last Updated:** December 2024

---

## 👥 Contact & Contributors

**Project Lead:** Java Platform Development Team

**Questions?** Check the documentation files or create an issue in the repository.

---

**Happy Coding! 🚀**

Built with ❤️ using Java, Spring Boot, and modern cloud technologies.
# java-pbl
# CODECONNECT
