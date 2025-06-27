# replit.md

## Overview

FitAI is a cross-platform mobile fitness application with a sleek, dark, WHOOP-inspired UI built with React Native and Expo. The app generates custom workout & nutrition plans via an AI assistant, tracks macros & supplements, and allows users to continually refine everything through chat-style AI prompts. The system provides personalized fitness experiences with real-time AI coaching and data-driven insights.

## System Architecture

### Mobile Frontend Architecture
- **Framework**: React Native with Expo SDK 51
- **Navigation**: React Navigation v6 with bottom tabs and stack navigation
- **UI Design**: WHOOP-inspired dark theme with custom components
- **Colors**: Dark gradient backgrounds (#101518 → #283339) with teal (#00F19F) accents
- **Interactions**: Expo Haptics for tactile feedback
- **Icons**: Expo Vector Icons (Ionicons)
- **Platform**: Cross-platform iOS/Android with web support

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL storage
- **API Design**: RESTful endpoints with standardized error handling
- **Development**: Hot reload with tsx

### Database Layer
- **ORM**: Drizzle ORM with PostgreSQL dialect
- **Database**: PostgreSQL (Neon serverless for production)
- **Schema Management**: Drizzle Kit for migrations
- **Connection**: Connection pooling with @neondatabase/serverless

## Key Components

### Authentication System
- **Provider**: Replit Auth integration with mandatory user and session tables
- **Strategy**: OpenID Connect with Passport.js
- **Session Storage**: PostgreSQL-backed sessions with connect-pg-simple
- **Protection**: Route-level authentication middleware

### AI Services
- **OpenAI Integration**: GPT-4o model for workout generation and nutrition advice
- **Capabilities**: 
  - Personalized workout plan generation
  - Nutrition analysis and recommendations
  - Supplement analysis and guidance
  - Conversational AI chat support

### Data Models
- **Users**: Profile management with fitness goals and preferences
- **Workouts**: Plans, scheduled sessions, and exercise logging
- **Nutrition**: Food database, meal logging, and macro tracking
- **Supplements**: User supplements and intake tracking
- **AI Chat**: Message history and conversation context

### UI Component System
- **Design System**: shadcn/ui with Radix UI primitives
- **Styling**: CSS variables for theming with Tailwind utilities
- **Icons**: FontAwesome and Lucide React
- **Responsive**: Mobile-first design with desktop adaptations
- **Accessibility**: ARIA compliant components

## Data Flow

### Authentication Flow
1. User accesses protected route
2. Middleware checks session validity
3. If unauthenticated, redirect to Replit Auth
4. On successful auth, create/update user record
5. Establish session and redirect to application

### Data Fetching Pattern
1. React Query manages all server state
2. Automatic caching and background refetching
3. Optimistic updates for better UX
4. Error boundaries for graceful degradation

### AI Integration Flow
1. User requests AI assistance (workout, nutrition, chat)
2. Backend validates request and user context
3. OpenAI API called with user profile context
4. Response processed and stored in database
5. Frontend updates with new data via React Query

## External Dependencies

### Core Infrastructure
- **Database**: PostgreSQL (provisioned via Replit)
- **Authentication**: Replit Auth service
- **AI Services**: OpenAI API (GPT-4o model)
- **Nutrition Data**: Edamam Food Database API (optional)

### Development Tools
- **Package Manager**: npm with lockfile v3
- **TypeScript**: Strict mode with path mapping
- **Build Tools**: Vite for frontend, esbuild for backend
- **Code Quality**: Built-in TypeScript checking

### Runtime Environment
- **Node.js**: Version 20 (specified in .replit)
- **Environment**: Replit container with PostgreSQL module
- **Deployment**: Autoscale deployment target

## Deployment Strategy

### Development Environment
- **Command**: `npm run dev` (runs tsx server with hot reload)
- **Port**: 5000 (mapped to external port 80)
- **Database**: Local PostgreSQL instance
- **Environment Variables**: SESSION_SECRET, DATABASE_URL, OPENAI_API_KEY

### Production Deployment
- **Build Process**: 
  1. Frontend: Vite builds to dist/public
  2. Backend: esbuild bundles server to dist/index.js
- **Start Command**: `npm run start` (runs built server)
- **Database**: Neon serverless PostgreSQL
- **Session Storage**: PostgreSQL with automatic cleanup

### Environment Configuration
- **Required Variables**: 
  - DATABASE_URL (auto-provisioned by Replit)
  - SESSION_SECRET (for session encryption)
  - OPENAI_API_KEY (for AI features)
  - REPL_ID (provided by Replit)
- **Optional Variables**:
  - EDAMAM_APP_ID, EDAMAM_APP_KEY (nutrition API)
  - ISSUER_URL (OpenID Connect issuer)

## User Preferences

Preferred communication style: Simple, everyday language.

## Product Requirements Update

User has provided updated PRD for VITRA AI Fitness Companion with enhanced features:
- Widget-based customizable homepage with add/remove/reorder functionality
- AI Coach integration for workout and meal plan generation
- Supplement tracking with AI analysis and deficiency warnings
- Water intake tracking with activity-based recommendations
- Barcode scanning for nutrition input (future enhancement)
- Recovery status tracking and HRV monitoring capabilities
- Mobile-first design with WHOOP/Apple Fitness aesthetic
- Target audience: 18-55 years, all fitness levels, muscle gain/strength/endurance goals

## Mobile App Features

### Core Screens
1. **Onboarding Flow**: Paginated single-question setup with AI plan generation
2. **Today Dashboard**: Recovery metrics, workout preview, macro progress
3. **Workouts**: Weekly calendar with drag-and-drop, AI generation
4. **Nutrition**: Macro tracking with pie charts, barcode scanning
5. **Supplements**: Progress tracking with AI analysis
6. **AI Coach**: Chat interface with quick actions and suggestions

### Design System
- **WHOOP-inspired Dark Theme**: Gradient backgrounds (#101518 → #283339)
- **Accent Colors**: Teal (#00F19F), Blue (#0093E7), status indicators
- **Interactions**: Haptic feedback on all major actions
- **Typography**: System fonts with proper weight hierarchy
- **Components**: Custom cards, rings, progress bars, chat bubbles

### Mobile-Specific Features
- Bottom tab navigation with stack navigation for onboarding
- Haptic feedback using Expo Haptics
- Barcode scanner integration for nutrition logging
- Cross-platform iOS/Android support with web fallback
- Optimized for 60fps performance

## Deployment Instructions

### Development
1. Backend: `npm run dev` (continues to run Express server on port 5000)
2. Mobile: `cd mobile && npx expo start` (starts Expo development server)
3. Access mobile app via Expo Go app or simulator

### Production
- Backend: Deploy to Replit with existing configuration
- Mobile: Build with EAS (Expo Application Services) for app stores
- Environment: Configure API endpoints for production backend

## Changelog

- June 22, 2025: Initial web application setup
- June 22, 2025: Complete transformation to React Native mobile app with WHOOP-inspired design
  - Added cross-platform mobile frontend with Expo
  - Implemented 5 core screens with dark theme
  - Added haptic feedback and mobile-optimized interactions
  - Integrated with existing backend API
  - Added onboarding flow with AI plan generation
  - Created comprehensive mobile documentation
- June 23, 2025: PRD Implementation - RepLift features
  - Created PRD-compliant single-question onboarding with animated progress dots
  - Added barcode scanning functionality to nutrition tracker
  - Implemented "Add to Plan" one-tap adoption flow for AI-generated workouts
  - Built plan editor with drag-and-drop reordering and AI "Tweak" buttons
  - Enhanced mobile app with authentic data integrity for recovery metrics
  - Updated both web and mobile UI to show device connection prompts instead of mock data
- June 23, 2025: UI Consistency Updates
  - Standardized headers across all tabs with consistent aesthetic fonts
  - Updated Profile tab with WHOOP-inspired dark gradient theme
  - Fixed Nutrition tab styling to match other tabs with glass-morphism design
  - Implemented consistent "FitAI" branding with gradient text and tab-specific icons
  - All tabs now feature centered FitAI logo with descriptive subtitle (Dashboard, Workouts, Nutrition, Profile)
- June 23, 2025: Header Modernization
  - Redesigned all tab headers with modern uppercase aesthetic fonts
  - Home tab: "FIT AI" in bold gradient uppercase with tracking-wider
  - Other tabs: Individual tab names (WORKOUTS, NUTRITION, PROFILE, COACH) in same style
  - Removed user greeting and simplified header layout for cleaner appearance
  - Applied consistent 2xl font size and teal-to-blue gradient across all headers
- June 23, 2025: WHOOP-Inspired AI Chat Interface
  - Redesigned chat window with modern gradient background matching WHOOP aesthetics
  - Added sophisticated header with AI avatar, status indicator, and GPT-4o branding
  - Implemented message bubbles with rounded corners and avatar system
  - Enhanced typing indicators with animated dots and professional styling
  - Added smooth scrolling chat area with custom scrollbar styling
  - Improved accessibility with proper dialog descriptions and ARIA labels
- June 23, 2025: Homepage Widget Navigation
  - Made all homepage widgets clickable with hover effects and cursor pointers
  - Today's Calories widget navigates to Nutrition page
  - Workouts widget navigates to Workouts page
  - Today's Macros section navigates to Nutrition page
  - Today's Workout section navigates to Workouts page (general) or specific workout (when clicking workout cards)
  - Added proper event handling with stopPropagation for nested clickable elements
- June 23, 2025: WHOOP-Inspired Complete Redesign - "Vitra" Branding
  - Rebranded app from "FitAI" to "Vitra" with modern aesthetic
  - Completely redesigned homepage with integrated WHOOP-style layout
  - Added profile circle in top-left corner for navigation to profile page
  - Centered "VITRA" branding with clean typography
  - Added date navigation (TODAY) with chevron controls
  - Implemented pure black background for authentic WHOOP aesthetic
  - Redesigned bottom navigation with 4 tabs: Home, Coaching, Community, More
  - Removed separate Profile tab and integrated into header profile circle
  - Added chevron right arrows to all widgets as visual navigation indicators
  - Updated all cards to dark gray styling with green accent progress bars
  - Simplified typography with uppercase tracking for section headers
- June 23, 2025: Header and Navigation Refinements
  - Changed background from pure black to gradient (gray-900 to black) for better visual depth
  - Made header sticky with subtle backdrop blur and translucent background
  - Centered "VITRA" branding and removed "TODAY" text for cleaner layout
  - Replaced bottom navigation text labels with modern outline icons only
  - Updated navigation icons using Lucide React: Home, Dumbbell, Apple, MessageCircle
  - Reduced header profile circle size for more subtle appearance
- June 23, 2025: Universal WHOOP-Inspired Styling Implementation
  - Applied consistent WHOOP-inspired design across all tabs (Workouts, Nutrition, Coach, Profile)
  - Updated all pages with gradient backgrounds, sticky headers, and centered branding
  - Created comprehensive Profile page with three tabs: Account, Profile Details, and Fitness Metrics
  - Added editable fitness goals, activity levels, calorie targets, and macro adjustments
  - Profile changes automatically update nutrition targets and home page displays
  - Implemented dark glass-morphism cards with proper spacing and modern form controls
- June 23, 2025: AI-Focused Profile Streamlining with Photo Upload
  - Streamlined Profile page to focus only on AI-relevant metrics for personalized recommendations
  - Added profile photo upload functionality with DiceBear avatar generation
  - Consolidated profile forms into two tabs: Account (with photo) and AI Profile (training data)
  - Removed non-AI metrics (height, weight, fiber targets) to focus on data that informs AI decisions
  - AI Profile includes: age, gender, activity level, fitness goals, dietary preferences, and macro targets
  - Profile photo upload generates unique avatars using user ID as seed for consistency
  - All AI-relevant data directly feeds into OpenAI service for personalized workout and nutrition recommendations
- June 23, 2025: Workout Display Simplification
  - Simplified "Today's Workout" widget to show only essential overview (name, day, duration, exercise count)
  - Added "Show All/Show Less" toggle functionality for exercise lists in Workouts page
  - Removed all exercise tips, notes, weight information, and rest time details for cleaner display
  - Exercise lists now show only exercise name and sets/reps with minimal layout
  - Maintained navigation from home widget to detailed workout view in Workouts tab
- June 24, 2025: Enhanced Workout Completion & Navigation
  - Implemented toggle functionality for workout completion/incompletion with teal checkmarks
  - Added uncomplete API endpoint for reversing workout completion status
  - Fixed context menu prevention across all home page widgets to eliminate unwanted popups
  - Updated toast notifications to match WHOOP-inspired design with dark backgrounds and teal accents
  - Redesigned Nutrition page with three swipeable tabs: Food, Supplements, and Water tracking
  - Applied consistent WHOOP-inspired styling across all nutrition tab content with dark theme
  - Standardized header design across all pages with centered "VITRA" branding for seamless navigation
  - Created equanimity between all tab headers to feel like one continuous screen experience
  - Completely redesigned Nutrition page with DIARY-style layout featuring three clickable widgets:
    * Calories widget with large number display and target comparison
    * Macros widget with circular progress rings for protein, carbs, and fats
    * Meals widget with meal categories and "Add" buttons for food logging
  - Updated floating action button styling with custom teal background color
  - Enhanced Nutrition page with comprehensive tab system and functional editing:
    * Added three-tab navigation (Food, Supplements, Water) with consistent styling
    * Implemented chevron arrows on clickable widgets for better UX
    * Built functional calorie and macro target editing modals with form inputs
    * Added breakfast to meals widget (now includes breakfast, lunch, dinner)
    * Created "Today's Diary" widget to display logged food items with nutritional breakdown
    * Integrated water tracking tab with intake buttons and progress visualization
    * Connected edit modals to backend API with proper mutation handling
  - Unified design consistency across home, workouts, and nutrition pages:
    * Applied home page background colors (bg-gray-900, border-gray-800) to all widgets
    * Updated all cards and containers to match home page styling for visual cohesion
    * Standardized hover effects and border treatments across all pages
  - Redesigned calorie and macro edit modals with WHOOP-inspired compact widgets:
    * Created smaller, focused modal dialogs matching app aesthetic
    * Used same color scheme (bg-gray-900, border-gray-800) as main widgets
    * Implemented clean input styling with transparent backgrounds and large text
    * Added grid layout for macro inputs with centered styling and unit labels
    * Maintained teal accent color for save buttons consistent with app branding
- June 24, 2025: Created dedicated Calories page for comprehensive calorie management:
  - Built full-screen calorie tracking page accessible from nutrition widget
  - Added manual calorie entry with large input field and quick-add buttons (+100, +200, +300, +500 cal)
  - Implemented calorie goal management with preset options (1800, 2000, 2400, 2800 cal)
  - Integrated progress visualization with percentage completion and progress bar
  - Connected to backend API for real-time calorie logging and goal updates
  - Applied consistent WHOOP-inspired styling with proper navigation and back button
- June 24, 2025: Resolved calorie tracking system and achieved full functionality:
  - Fixed API endpoint authentication and payload structure issues
  - Verified database integration with proper food log storage and aggregation
  - Confirmed real-time calorie updates across all pages (Home, Nutrition, Calories)
  - System now accurately tracks and displays calorie intake with immediate UI updates
  - Added comprehensive debugging logs for monitoring food log operations
- June 24, 2025: Implemented advanced widget system with customization features:
  - Created modular widget architecture with WidgetManager for add/remove/reorder functionality
  - Built WaterTracker widget with intake logging and progress visualization
  - Added WorkoutStreakWidget showing current streak, weekly completion, and total workouts
  - Implemented RecoveryWidget with manual logging of recovery score, sleep, and stress levels
  - Integrated localStorage persistence for widget configuration across sessions
  - Added backend API endpoints for water tracking, workout streaks, and recovery data
  - Enhanced homepage with dynamic widget rendering based on user preferences
- June 24, 2025: iPhone-Style Widget Management System:
  - Replaced settings icon with plus button for widget management
  - Created iPhone-inspired widget gallery with live previews and descriptions
  - Implemented tap-and-hold drag functionality for widget reordering
  - Added haptic feedback and visual drag states (opacity, scale, rotation effects)
  - Built comprehensive widget preview system showing actual widget appearance
  - Enhanced widget manager with current widgets section and removal functionality
  - Integrated touch event handling for mobile-first drag interactions
- June 24, 2025: Implemented Widget Sizing System with Full and Half-Width Options:
  - Added widget size property ('full' or 'half') to widget configuration system
  - Created compact versions of Calories and Macros widgets for half-width display
  - Implemented intelligent grid layout that groups half-width widgets side by side
  - Enhanced widget manager with size selection (Full/Half buttons for applicable widgets)
  - Added size toggle functionality for existing widgets in current widgets section
  - Visual previews show both full and half-width versions for applicable widgets
  - Automatic localStorage migration includes size property for all widgets
- June 24, 2025: Added AI Assistant Widget with Quick Actions:
  - Created AIAssistantWidget with quick coaching suggestions (workout, nutrition, recovery)
  - Integrated with existing AI chat system and OpenAI service
  - Added preview component for widget manager with live chat history
  - Implemented quick action buttons for instant AI recommendations
  - Connected to Coach page for full chat experience
  - Widget shows recent chat messages and provides tap-to-expand functionality
- June 24, 2025: Enhanced Physical Drag-and-Drop System:
  - Implemented true visual dragging where widgets follow finger/mouse movement
  - Added support for both touch and mouse interactions for cross-platform compatibility
  - Created fixed positioning system for dragged widgets with proper offset calculations
  - Added visual feedback for drop targets with scaling and opacity effects
  - Enhanced drag state management with position tracking and collision detection
  - Improved bottom padding (pb-32) for better scrolling past last widget
  - Refined drag logic with reliable event handling and 400ms hold timer
  - Fixed widget reordering with proper state management and localStorage persistence
- June 24, 2025: Real-Time Widget Reordering and UI Consistency Improvements:
  - Implemented live widget repositioning where dragged widgets automatically push others aside
  - Removed drop target highlighting in favor of smooth real-time reordering
  - Added proper bottom padding (pb-28) across all pages to prevent bottom navigation overlap
  - Standardized header typography across all tabs with consistent VITRA gradient styling
  - Applied consistent "VITRA" branding across all tab headers with thin white font and uppercase tracking
  - Enhanced drag experience with 300ms smooth transitions when widgets reposition during drag
  - Fixed scrolling issues where widgets would cover bottom tab navigation
  - Enhanced bottom navigation z-index (z-50) to ensure it stays above all content
  - Increased bottom padding to pb-32 across all pages for proper content visibility