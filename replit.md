# Sortify - AI-Powered Waste Classification App

## Overview

Sortify is a React-based web application that helps users properly sort waste using AI-powered image classification. The app uses a camera interface to scan items and provides sorting instructions based on local recycling guidelines, tracks environmental impact, and gamifies the waste sorting experience with achievements and streaks.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**React + TypeScript SPA**: Built with React 18, TypeScript, and Vite for modern development experience. The app uses a client-side routing approach with Wouter for navigation between main sections (Home, History, Stats, Profile).

**UI Framework**: Implements shadcn/ui component library with Radix UI primitives and Tailwind CSS for styling. The design system uses CSS custom properties for theming with support for light/dark modes.

**State Management**: Uses React Query (TanStack Query) for server state management and caching. Local component state is managed with React hooks, avoiding complex global state solutions.

**Responsive Design**: Mobile-first approach with dedicated bottom navigation for mobile devices and standard navigation for desktop. Components adapt to different screen sizes using Tailwind breakpoints.

### Backend Architecture

**Express.js API Server**: RESTful API built with Express.js and TypeScript, providing endpoints for user profiles, scan history, achievements, and local guidelines. The server uses middleware for request logging and error handling.

**Database Layer**: Uses Drizzle ORM with PostgreSQL as the primary database. The schema includes tables for users, scan history, local guidelines, and achievements. Database migrations are managed through Drizzle Kit.

**Storage Abstraction**: Implements an in-memory storage interface (`IStorage`) for development/testing, with the ability to swap to real database implementations. This allows for easy testing and development without database dependencies.

**Data Models**: Comprehensive TypeScript schemas using Drizzle-Zod for validation, covering user profiles, scan records, achievement tracking, and local recycling guidelines.

### AI Classification System

**Mock AI Service**: Currently implements a mock classification system that simulates AI-powered waste identification. The service returns structured data including item classification, sorting instructions, contamination detection, and carbon impact calculations.

**Offline Capability**: Supports offline mode with cached classifications and local processing capabilities for situations with limited connectivity.

**Batch Processing**: Designed to handle multiple item scanning in a single session for improved user efficiency.

### Camera Integration

**WebRTC Camera Access**: Direct browser camera integration using the MediaDevices API with support for both front and rear cameras on mobile devices. Implements proper camera permissions handling and error states.

**Image Processing**: Client-side image capture and processing with canvas-based frame extraction for sending to classification services.

**Real-time Preview**: Live camera feed with overlay UI for scanning guidance and visual feedback.

### Data Architecture

**Environmental Impact Tracking**: Calculates and tracks carbon savings, energy conservation, and waste diversion metrics based on proper sorting behavior.

**Achievement System**: Gamification layer with unlockable achievements based on user behavior patterns like sorting streaks, total items processed, and environmental impact milestones.

**Local Guidelines Integration**: Location-aware recycling guidelines that adapt sorting instructions based on user's geographic location and local waste management policies.

## External Dependencies

### Core Framework Dependencies
- **React 18** - Primary UI framework with hooks and modern features
- **TypeScript** - Type safety and enhanced development experience
- **Vite** - Fast build tool and development server with hot module replacement

### UI and Styling
- **Tailwind CSS** - Utility-first CSS framework for responsive design
- **Radix UI** - Headless component primitives for accessibility
- **shadcn/ui** - Pre-built component library built on Radix
- **Lucide React** - Icon library for consistent iconography

### Backend and Database
- **Express.js** - Web application framework for the API server
- **Drizzle ORM** - TypeScript-first ORM with PostgreSQL support
- **Neon Database** - Serverless PostgreSQL database provider
- **Zod** - Schema validation library for type-safe data handling

### State Management and Data Fetching
- **TanStack React Query** - Server state management and caching
- **React Hook Form** - Form handling with validation support

### Development and Build Tools
- **ESBuild** - Fast bundling for production builds
- **TSX** - TypeScript execution for development server
- **PostCSS** - CSS processing with Autoprefixer

### Location and Media Services
- **Browser Geolocation API** - For location-aware recycling guidelines
- **WebRTC MediaDevices API** - Camera access for waste scanning
- **BigDataCloud API** - Reverse geocoding for location names

### Potential Future Integrations
- **AI/ML Services** - Real computer vision APIs for actual waste classification
- **Local Government APIs** - Real-time recycling guideline updates
- **Environmental Data APIs** - Accurate carbon impact calculations
- **Social Features** - Community sharing and comparison features