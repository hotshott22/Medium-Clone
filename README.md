# 📝 Modern Blogging Platform (Next.js 13)

A **production-grade, SEO-friendly blogging platform** built with **Next.js 13 App Router**, designed for performance, scalability, and an excellent developer experience.

---

## 🎯 Core Features

### 📚 Content Management

- **Rich Text Editor**  
  React Quill integration with a custom formatting toolbar.

- **Image Upload System**  
  Direct uploads to Firebase Storage with automatic optimization.

- **SEO-Optimized URLs**  
  Automatic slug generation from titles for better search rankings.

- **Category System**  
  Visual tag-based content organization.

- **View Analytics**  
  Real-time post view counter using atomic increments.

- **Draft & Publish Workflow**  
  Seamless creation, editing, drafting, and publishing of content.

---

### 🎨 User Experience

- **Server-Side Rendering (SSR)**  
  Fast initial page loads with full SEO support.

- **Dark / Light Themes**  
  Context API-based theme switching with `localStorage` persistence.

- **Responsive Design**  
  Mobile-first layout with 6 breakpoints (475px → 1536px).

- **Pagination (Infinite Scroll Alternative)**  
  URL-based pagination with state management.

- **Real-Time Comments**  
  SWR-powered commenting with optimistic UI updates.

---

### 🔐 Authentication & Security

- **Multi-Provider OAuth**  
  Google & GitHub login via NextAuth.js.

- **Server-Side Session Management**  
  Secure HTTP-only cookies for XSS protection.

- **Protected API Routes**  
  Server-side authentication on all write operations.

- **Role-Based Access Control (RBAC)**  
  User-specific permissions for content creation.

- **CSRF Protection**  
  Built-in NextAuth.js security mechanisms.

---

### 🛠️ Developer Experience

- **Type-Safe Database Queries**  
  Prisma ORM with auto-generated TypeScript types.

- **API Route Handlers**  
  RESTful APIs using Next.js 13 Route Handlers.

- **Modular Component Architecture**  
  Reusable components with scoped CSS Modules.

- **Error Boundaries**  
  Graceful error handling with fallback UI.

- **Hot Module Replacement**  
  Fast development cycle using Next.js dev server.

---

## 🏗️ Technical Architecture & Stack

### 📐 System Architecture Overview

```text
┌─────────────────────────────────────────────────────────────┐
│                         CLIENT LAYER                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Browser    │  │   Mobile     │  │   Tablet     │      │
│  │  (Desktop)   │  │   Device     │  │   Device     │      │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘      │
│         └──────────────────┴──────────────────┘              │
└─────────────────────────┬───────────────────────────────────┘
                          │ HTTPS
┌─────────────────────────▼───────────────────────────────────┐
│                    FRONTEND (Vercel CDN)                     │
│  ┌────────────────────────────────────────────────────────┐ │
│  │            Next.js 13 App Router (SSR/CSR)             │ │
│  │  ┌──────────────┐  ┌──────────────┐  ┌─────────────┐  │ │
│  │  │   Server     │  │    Client    │  │    Static   │  │ │
│  │  │  Components  │  │  Components  │  │    Assets   │  │ │
│  │  └──────────────┘  └──────────────┘  └─────────────┘  │ │
│  └────────────────────────────────────────────────────────┘ │
│  │  React 18 + Context API + SWR                             │
│  │  CSS Modules + CSS Variables (Theming)                    │
│  └────────────────────────────────────────────────────────── │
└─────────────────────────┬───────────────────────────────────┘
                          │ API Calls
┌─────────────────────────▼───────────────────────────────────┐
│              BACKEND API (Next.js API Routes)                │
│  ┌────────────────────────────────────────────────────────┐ │
│  │  /api/posts         - CRUD operations                  │ │
│  │  /api/posts/[slug]  - Single post fetch                │ │
│  │  /api/comments      - Comment management               │ │
│  │  /api/categories    - Category listing                 │ │
│  │  /api/auth/[...]    - Authentication (NextAuth)        │ │
│  └────────────────────────────────────────────────────────┘ │
│  │  Authentication Middleware (getServerSession)             │
│  │  Request Validation & Error Handling                      │
│  └────────────────────────────────────────────────────────── │
└────────┬─────────────────────────┬─────────────────┬─────────┘
         │                         │                 │
         │ Prisma ORM              │ NextAuth        │ REST API
         ▼                         ▼                 ▼
┌─────────────────┐    ┌─────────────────┐   ┌─────────────────┐
│   MongoDB Atlas │    │ OAuth Providers │   │Firebase Storage │
│  Users          │    │ Google          │   │ Images / Files  │
│  Posts          │    │ GitHub          │   │ CDN Delivery    │
│  Comments       │    └─────────────────┘   └─────────────────┘
│  Categories     │
│  Sessions       │
└─────────────────┘
