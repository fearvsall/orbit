# ORBIT Architecture

## System Overview

```
┌─────────────────────────────────────────────────────────────┐
│                     Frontend (Next.js)                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Search    │  │    Proxy     │  │   Hub Pages  │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│  ┌──────────────────────────────────────────────────────┐   │
│  │         Orbit AI Assistant (Right Sidebar)          │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                            ↓ API
┌─────────────────────────────────────────────────────────────┐
│                   Backend (Go / REST API)                    │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐              │
│  │   Search   │ │   Proxy    │ │   AI API   │              │
│  │  Service   │ │  Service   │ │  Service   │              │
│  └────────────┘ └────────────┘ └────────────┘              │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐              │
│  │   Apps     │ │   Games    │ │  User      │              │
│  │  Service   │ │  Service   │ │  Service   │              │
│  └────────────┘ └────────────┘ └────────────┘              │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                   Data Layer                                │
│  ┌────────────────────┐  ┌──────────────────────┐          │
│  │   PostgreSQL DB    │  │   Redis Cache        │          │
│  │  - Users           │  │  - Sessions          │          │
│  │  - History         │  │  - Search Cache      │          │
│  │  - Bookmarks       │  │  - Rate Limits       │          │
│  │  - Preferences     │  │  - AI Context        │          │
│  └────────────────────┘  └──────────────────────┘          │
└─────────────────────────────────────────────────────────────┘
```

## Component Breakdown

### Frontend Services

#### 1. Search Module
- Universal search bar component
- Query parsing & formatting
- Results aggregation
- Suggestion engine
- Tab routing (Web, Apps, Games, AI)

#### 2. Proxy Browser
- Iframe sandbox for websites
- Tab manager
- Session handler
- History tracker
- Bookmark manager

#### 3. Apps Hub
- App discovery interface
- Launch mechanism
- Favorites system
- Recent apps tracking

#### 4. Games Hub
- Game library view
- Category filtering
- Featured section
- Fullscreen launcher

#### 5. Orbit AI
- Chat interface
- Context awareness
- Code highlighting
- Response streaming

### Backend Services

#### 1. Search Service
- Web search API integration
- Search suggestions
- Result ranking
- Caching layer

#### 2. Proxy Service
- Request interception
- Response modification
- CORS handling
- Session management
- Security headers

#### 3. AI Service
- LLM integration (OpenAI/Claude)
- Context building
- Code generation
- Content summarization

#### 4. Apps Service
- App registry
- Metadata management
- Launch tracking
- Usage analytics

#### 5. Games Service
- Game catalog
- Category management
- Score tracking
- Play history

#### 6. User Service
- Authentication & authorization
- Profile management
- Preferences
- Account settings

## Data Flow

### Search Flow
```
User Input
  ↓
Search Bar Component
  ↓
Backend Search Service
  ↓
Web APIs + Cache
  ↓
Result Processing
  ↓
Frontend Display
```

### Proxy Flow
```
User URL
  ↓
Proxy Browser Component
  ↓
Backend Proxy Service
  ↓
Remote Website
  ↓
Response Modification
  ↓
Iframe Rendering
```

### AI Flow
```
User Query
  ↓
Orbit AI Component
  ↓
Context Collection (Page, History)
  ↓
Backend AI Service
  ↓
LLM API
  ↓
Response Stream
  ↓
Markdown Rendering
```

## API Endpoints

### Search API
```
GET  /api/search/web?q=query
GET  /api/search/suggestions?q=query
GET  /api/search/history
POST /api/search/history (save)
```

### Proxy API
```
POST   /api/proxy/request
GET    /api/proxy/sessions
POST   /api/proxy/sessions/:id
DELETE /api/proxy/sessions/:id
```

### AI API
```
POST /api/ai/chat
POST /api/ai/generate-code
POST /api/ai/summarize
POST /api/ai/explain
```

### Apps API
```
GET /api/apps/catalog
GET /api/apps/favorites
POST /api/apps/launch
```

### Games API
```
GET /api/games/catalog
GET /api/games/categories
GET /api/games/:id/play
POST /api/games/scores
```

### User API
```
POST   /api/auth/login
POST   /api/auth/register
POST   /api/auth/logout
GET    /api/user/profile
PUT    /api/user/profile
GET    /api/user/preferences
PUT    /api/user/preferences
```

## Database Schema

### Users Table
```sql
users (
  id UUID PRIMARY KEY,
  email VARCHAR UNIQUE,
  username VARCHAR UNIQUE,
  password_hash VARCHAR,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

### Search History
```sql
search_history (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users,
  query VARCHAR,
  results_count INT,
  created_at TIMESTAMP
)
```

### Bookmarks
```sql
bookmarks (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users,
  url VARCHAR,
  title VARCHAR,
  favicon VARCHAR,
  created_at TIMESTAMP
)
```

### User Preferences
```sql
user_preferences (
  user_id UUID PRIMARY KEY REFERENCES users,
  theme VARCHAR DEFAULT 'dark',
  search_engine VARCHAR,
  ai_model VARCHAR,
  notifications_enabled BOOLEAN,
  updated_at TIMESTAMP
)
```

### Apps
```sql
apps (
  id UUID PRIMARY KEY,
  name VARCHAR,
  description TEXT,
  url VARCHAR,
  icon VARCHAR,
  category VARCHAR,
  rating FLOAT,
  created_at TIMESTAMP
)
```

### Games
```sql
games (
  id UUID PRIMARY KEY,
  title VARCHAR,
  description TEXT,
  url VARCHAR,
  thumbnail VARCHAR,
  category VARCHAR,
  rating FLOAT,
  play_count INT,
  created_at TIMESTAMP
)
```

### Game Scores
```sql
game_scores (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users,
  game_id UUID REFERENCES games,
  score INT,
  played_at TIMESTAMP
)
```

## Caching Strategy

- **Redis TTL**: 24 hours for search results
- **Redis TTL**: 1 hour for suggestions
- **Redis TTL**: Session data until logout
- **CDN**: Static assets (images, fonts)
- **Browser Cache**: UI components, icons

## Security Measures

- HTTPS only
- CORS configuration
- Rate limiting (100 req/min per IP)
- SQL injection prevention (prepared statements)
- XSS protection (CSP headers)
- CSRF tokens for state-changing operations
- Input validation & sanitization
- Secure session management

## Scalability

- Horizontal scaling via Docker containers
- Load balancing (nginx)
- Database replication
- Redis cluster for distributed caching
- CDN for static content
- Microservices architecture for independent scaling
