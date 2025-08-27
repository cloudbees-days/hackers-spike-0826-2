# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Vue.js-based clone of Hacker News designed as a demo application. It's intentionally kept as a client-side rendered app (no SSR) with relatively simple architecture to make it useful for testing various tools and deployment scenarios.

**Tech Stack:**
- Vue.js 2.6 with Vue Router and Vuex
- Bulma/Buefy for UI components
- Jest for testing
- Docker with Kubernetes deployment configs
- CloudBees CI/CD pipeline integration

## Development Commands

```bash
# Install dependencies
npm install

# Development server with hot reload
npm run serve

# Production build
npm run build

# Run all tests
npm run test:unit

# Run tests with coverage
npm run test:coverage

# Lint code
npm run lint
```

## Architecture

**Frontend Structure:**
- `src/App.vue` - Main app component with Nav and Footer
- `src/views/` - Page components (Hot, Ask, Show, About, Login)
- `src/components/` - Reusable components (Nav, Footer, ListItem)
- `src/store.js` - Vuex store for authentication state
- `src/router.js` - Vue Router configuration
- `src/utils/` - Utility functions (user management, feature flags)

**Key Components:**
- Authentication system uses local mock users defined in `src/utils/users.js`
- Vuex store manages login/logout state with localStorage persistence
- Feature flagging integration via CloudBees Rollout (`rox-browser` package)
- HackerNews API integration for content display

**Testing:**
- Jest configuration in `jest.config.js`
- Unit tests in `tests/unit/` directory
- Uses Vue Test Utils and Testing Library
- Test coverage reporting enabled

**Deployment:**
- Docker containerization with nginx
- Kubernetes manifests in `k8s/` with base and overlay configs
- Helm chart in `chart/` directory
- CloudBees CI/CD pipeline defined in "DOW Demo YAML" file

## Environment Setup

Set `VUE_APP_ROLLOUT_KEY` environment variable for CloudBees SDK integration.

## Special Files

- `vulnerable-packages.sh` - Security audit script that copies high/critical vulnerability packages
- `DOW Demo YAML` - CloudBees workflow configuration for CI/CD pipeline
- `default.conf` - nginx configuration for Docker deployment