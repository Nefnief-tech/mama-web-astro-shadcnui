# Mama Web Astro ShadCN UI

This is an Astro.js web application that uses Vue 3 components with ShadCN UI components and Tailwind CSS. It's a personal website project designed to test out Astro.js and ShadCN Vue integration.

**CRITICAL**: Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the information here.

## Working Effectively

### Bootstrap and Build
- Install dependencies: `npm install` -- takes 1-2 minutes. NEVER CANCEL. Set timeout to 5+ minutes.
- Build the project: `npm run build` -- takes 2-3 seconds. Fast build process.
- Fix security vulnerabilities: `npm audit fix` -- takes 1-2 minutes. Run this after `npm install`.

### Development Workflow
- Start development server: `npm run dev` -- runs on http://localhost:4321/
- Preview production build: `npm run preview` -- runs on http://localhost:4322/ (or next available port)
- Stop servers: Use Ctrl+C or appropriate stop commands

### Build Times and Timeouts
- **npm install**: 1-2 minutes. NEVER CANCEL. Set timeout to 5+ minutes.
- **npm audit fix**: 1-2 minutes. NEVER CANCEL. Set timeout to 5+ minutes.
- **npm run build**: 2-3 seconds. Very fast.
- **npm run dev**: Starts in under 1 second.
- **npm run preview**: Starts immediately.

## Validation and Testing

### Manual Validation Requirements
- ALWAYS test the application by starting the development server with `npm run dev`
- Verify the server responds with HTTP 200: `curl -s -o /dev/null -w "%{http_code}" http://localhost:4321/`
- ALWAYS check that the main page loads and displays a "Hello World" button
- Verify that Tailwind CSS styles are applied correctly
- Test build process completes without errors before making code changes

### End-to-End Validation Scenarios
- Build the project: `npm run build` should complete successfully
- Start dev server: `npm run dev` should serve the application on port 4321
- Load the homepage: Should display a styled button with "Hello World" text
- Verify responsive design: The page should use Tailwind CSS and be responsive

## Common Issues and Troubleshooting

### Import Path Issues
- **CRITICAL**: The project has a mixed path resolution setup. Components in the root `/components` directory must use relative paths.
- For imports from `/components/ui/*` to `/lib/utils`: Use relative paths like `../../../lib/utils`
- For imports from `/src/pages/*` to `/components/*`: Use relative paths like `../../components/ui/button`
- Do NOT use `@/` aliases for cross-directory imports as they are not properly configured

### Security Vulnerabilities
- Always run `npm audit fix` after `npm install` to address known vulnerabilities
- The project may report 6-7 moderate vulnerabilities initially, which are automatically fixed

### Build Failures
- If build fails with "Rollup failed to resolve import" errors, check that all import paths use relative paths instead of aliases
- Ensure all Vue components in `/components/ui/*` import utilities using relative paths

## Project Structure

### Key Directories
```
/
├── src/
│   ├── pages/           # Astro pages (index.astro)
│   ├── styles/          # Global CSS (globals.css with Tailwind)
│   ├── components/      # Source components (if any)
│   ├── layouts/         # Layout components
│   └── assets/          # Static assets
├── components/          # ShadCN UI components (root level)
│   └── ui/              # Individual UI components
├── lib/                 # Utilities (utils.js with cn function)
├── public/              # Static public assets
└── dist/                # Build output (generated)
```

### Important Files
- `astro.config.mjs` - Astro configuration with Vue and Tailwind integration
- `tailwind.config.mjs` - Tailwind CSS configuration
- `components.json` - ShadCN UI component configuration
- `package.json` - Project dependencies and scripts
- `tsconfig.json` - TypeScript configuration (with path aliases)
- `jsconfig.json` - JavaScript configuration

## Technology Stack

### Core Technologies
- **Astro.js 5.1.5** - Static site generator and framework
- **Vue 3.5.13** - Component framework for interactive elements
- **Tailwind CSS 3.4.17** - Utility-first CSS framework
- **ShadCN UI (Vue)** - Pre-built component library
- **Vite** - Build tool and development server

### Key Dependencies
- `@astrojs/vue` - Vue integration for Astro
- `@astrojs/tailwind` - Tailwind integration for Astro
- `radix-vue` - Headless UI components
- `class-variance-authority` - Component variant management
- `tailwind-merge` - Tailwind class merging utility

### Development Dependencies
- Node.js 20.19.4+
- npm 10.8.2+

## Available Commands

### npm Scripts
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run astro` - Run Astro CLI commands

### Astro CLI Commands
- `npx astro --help` - Show available commands
- `npx astro check` - Type check (requires @astrojs/check package)
- `npx astro add` - Add integrations
- `npx astro info` - Show project info

## Best Practices

### When Making Changes
- Always run `npm run build` to verify changes don't break the build
- Test the development server with `npm run dev` after making changes
- Use relative import paths instead of aliases for cross-directory imports
- Follow the existing Vue + Astro component patterns

### Code Style
- Use Tailwind CSS classes for styling
- Follow ShadCN UI component patterns for new components
- Use TypeScript types when possible (project supports both JS and TS)
- Keep components in appropriate directories (`/src/components/` for custom, `/components/ui/` for ShadCN)

### Performance Notes
- Build process is very fast (2-3 seconds)
- Development server starts quickly (under 1 second)
- Static site generation produces optimized output
- Astro only hydrates Vue components that need interactivity

## Quick Reference

### Repository Root Contents
```
ls -la /
.git/                    # Git repository
.gitignore              # Git ignore rules
.vscode/                # VSCode settings
README.md               # Project description
astro.config.mjs        # Astro configuration
components/             # ShadCN UI components
components.json         # ShadCN configuration
jsconfig.json           # JavaScript configuration
lib/                    # Utility functions
package-lock.json       # Dependency lock file
package.json            # Project configuration
public/                 # Static assets
src/                    # Source code
tailwind.config.mjs     # Tailwind configuration
tsconfig.json           # TypeScript configuration
```

### Working with ShadCN Components
- Components are located in `/components/ui/`
- Each component has its own directory with index.js and Component.vue files
- Import using relative paths: `import { Button } from "../../components/ui/button"`
- Available components: accordion, alert, button, card, input, and many more

### Testing Your Changes
1. Build: `npm run build` (should complete in 2-3 seconds)
2. Start dev server: `npm run dev`
3. Verify response: `curl -s -o /dev/null -w "%{http_code}" http://localhost:4321/` (should return 200)
4. Check in browser: Open http://localhost:4321/ and verify the page loads with styled content