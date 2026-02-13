# GitHub Project Board - Astro SSR

## Project Overview
SSR Astro application for displaying GitHub issues, PRs, and discussions for any GitHub organization. Features a tabbed repository view, filtering capabilities, and a dedicated roadmap page with README viewer.

## Tech Stack
- **Framework**: Astro v5 with SSR enabled (@astrojs/node adapter)
- **Language**: TypeScript
- **APIs**: GitHub REST API + GraphQL for discussions
- **Styling**: Unified global CSS with CSS variables for theming
- **Markdown**: markdown-it with markdown-it-anchor for README rendering

## Architecture
- **Pages**: 
  - `/` - Main project board with tabbed repository view
  - `/roadmap` - Dedicated roadmap page showing discussions, issues, and PRs from roadmap repo
- **Components**:
  - `FilterBar.astro` - State/type filtering
  - `GitHubItem.astro` - Individual item card display
  - `ThemeSelector.astro` - Light/dark/auto theme switcher
  - `ThemeManager.astro` - Client-side theme management
- **Layout**: `BaseLayout.astro` - Main layout with header, nav, and footer
- **Styles**: `src/styles/global.css` - Centralized styles with CSS variables

## Key Features
- **Repository Tabs**: Alphabetically sorted repositories with configurable sort function
- **Filtering**: Filter by state (open/closed/all) and type (issues/PRs/discussions/all)
- **Theme System**: Light/dark/auto modes with persistent preference
- **Roadmap Page**: 
  - Three-column layout (Discussions, Issues, Pull Requests)
  - README viewer dialog with markdown rendering and anchor links
- **Configurable**: Extensive config options in `src/config.ts`
- **Caching**: 5-minute TTL cache for API responses
- **Read-only**: Display only, no write operations to GitHub

## Configuration (src/config.ts)
- `organization` - GitHub org name
- `githubToken` - Optional token for higher rate limits
- `allowedRepositories` - Filter specific repos or leave empty for all
- `maxItemsPerPage` - Pagination limit
- `enableDiscussions` - Toggle GraphQL discussions fetching
- `roadmapRepository` - Name of repo used for roadmap page
- `defaultRepository` - Default selected tab on index page
- `repositorySort` - Custom function to sort repositories

## Styling System
- **Global CSS**: All shared styles in `src/styles/global.css`
- **CSS Variables**: Comprehensive color system with light/dark theme support
- **Page-specific CSS**: Only unique styles remain in page components
- **Component CSS**: Minimal, only for component-specific needs

## API Integration
- **GitHub REST API**: Issues, PRs, releases, repositories
- **GitHub GraphQL**: Discussions (requires token)
- **Caching**: In-memory cache with 5-minute TTL
- **Rate Limiting**: Respects GitHub rate limits, token recommended

## Development Guidelines
1. Use GitHub MCP tools when available for API exploration
2. All shared styles go in `global.css`, use CSS variables
3. Keep components focused and reusable
4. Cache API responses appropriately
5. Follow Astro SSR best practices
6. Test both light and dark themes
7. Ensure markdown rendering is safe (use markdown-it's html: true carefully)

## Setup
1. Copy `.env.example` to `.env` and add your GitHub token (optional but recommended)
2. Update `src/config.ts` with your organization name and preferences
3. Configure repository sorting, default repo, and other options as needed
4. Run `pnpm install` to install dependencies
5. Run `pnpm dev` to start the development server
6. For production deployment, see README.md

## Recent Enhancements
- Unified CSS system with global variables
- Repository sorting and default selection
- README dialog on roadmap page with markdown rendering
- GitHub org link in navigation
- Repository links in tab content
- Single-column list view on index (removed kanban board)
- Improved badge contrast and styling
- Better dark mode color differentiation
