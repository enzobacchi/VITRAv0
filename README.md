# VITRA AI Fitness Companion

A comprehensive cross-platform fitness application with AI-powered workout generation, nutrition tracking, and personalized coaching.

## Features

### 🏠 Smart Dashboard
- Customizable widget-based homepage
- iPhone-style drag-and-drop widget management
- Real-time fitness metrics and progress tracking

### 💪 AI-Powered Workouts
- Personalized workout generation using OpenAI GPT-4
- Weekly workout scheduling and tracking
- Exercise completion monitoring with progress streaks

### 🍎 Nutrition Tracking
- Comprehensive calorie and macro tracking
- Food logging with nutritional breakdown
- Customizable nutrition targets and goals

### 💊 Supplement Management
- Supplement tracking with AI analysis
- Deficiency warnings and recommendations
- Daily intake monitoring

### 🤖 AI Fitness Coach
- Conversational AI assistant for fitness guidance
- Real-time workout and nutrition advice
- Personalized recommendations based on user data

### 💧 Hydration Tracking
- Water intake monitoring
- Activity-based hydration recommendations
- Daily progress visualization

## Tech Stack

### Frontend
- **React** with TypeScript
- **Tailwind CSS** for styling
- **shadcn/ui** component library
- **Wouter** for routing
- **TanStack Query** for state management
- **Framer Motion** for animations

### Backend
- **Node.js** with Express
- **TypeScript** with ES modules
- **Drizzle ORM** with PostgreSQL
- **Replit Auth** for authentication
- **OpenAI API** for AI features

### Database
- **PostgreSQL** (Neon serverless)
- **Session storage** with connect-pg-simple
- **Schema management** with Drizzle Kit

## Design System

### WHOOP-Inspired Aesthetic
- Dark gradient backgrounds (#101518 → #283339)
- Teal accent color (#00F19F) for primary actions
- Glass-morphism effects with backdrop blur
- Smooth animations and haptic feedback

### Responsive Design
- Mobile-first approach
- Cross-platform iOS/Android compatibility
- Desktop-optimized layouts

## Getting Started

### Prerequisites
- Node.js 20+
- PostgreSQL database
- OpenAI API key

### Environment Variables
```env
DATABASE_URL=your_postgresql_connection_string
SESSION_SECRET=your_session_secret
OPENAI_API_KEY=your_openai_api_key
REPL_ID=your_replit_id
```

### Installation
```bash
npm install
```

### Development
```bash
npm run dev
```

### Database Setup
```bash
npm run db:push
```

## Project Structure

```
├── client/              # React frontend
│   ├── src/
│   │   ├── components/  # Reusable UI components
│   │   ├── pages/       # Main application pages
│   │   ├── hooks/       # Custom React hooks
│   │   └── lib/         # Utility functions
├── server/              # Express backend
│   ├── services/        # Business logic services
│   ├── routes.ts        # API route definitions
│   └── storage.ts       # Database abstraction layer
├── shared/              # Shared types and schemas
│   └── schema.ts        # Drizzle database schema
└── mobile/              # React Native app (future)
```

## Key Features Implementation

### Widget System
- Modular, reusable widget architecture
- localStorage persistence for user preferences
- Drag-and-drop reordering with real-time feedback
- Add/remove widgets with live preview gallery

### AI Integration
- OpenAI GPT-4 for workout and nutrition planning
- Context-aware responses using user profile data
- Structured output parsing for workout plans
- Chat-based interaction with quick actions

### Authentication
- Replit Auth integration with OpenID Connect
- Secure session management with PostgreSQL storage
- Protected routes with automatic redirects

### Real-time Updates
- TanStack Query for efficient data fetching
- Optimistic updates for better UX
- Background refetching with smart caching
- Error handling with user-friendly messages

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

MIT License - see LICENSE file for details

## Deployment

The application is designed for deployment on Replit with automatic scaling and built-in PostgreSQL support.

### Production Build
```bash
npm run build
npm run start
```

## Roadmap

- [ ] Barcode scanning for nutrition input
- [ ] HRV monitoring integration
- [ ] Social features and community
- [ ] Wearable device synchronization
- [ ] Advanced analytics and insights
- [ ] Mobile app store deployment

---

Built with ❤️ using React, Node.js, and AI