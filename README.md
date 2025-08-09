# 💝 Mama's Website - Astro + shadcn-vue

A beautiful, modern website built with love using **Astro.js** and **shadcn-vue** components. This project serves as both a heartfelt tribute and a comprehensive showcase of modern web development technologies.

![Mama's Website](https://img.shields.io/badge/Made%20with-Love-red?style=for-the-badge&logo=heart&logoColor=white)
![Astro](https://img.shields.io/badge/Astro-0C1222?style=for-the-badge&logo=astro&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vue.js&logoColor=4FC08D)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

## 🌟 Live Demo

Visit the live website: [Mama's Website](https://your-deployment-url.com) (Update with your actual deployment URL)

## 📸 Screenshots

| Desktop | Mobile |
|---------|--------|
| ![Desktop Homepage](./docs/screenshots/desktop-home.png) | ![Mobile Menu](./docs/screenshots/mobile-menu.png) |
| ![About Page](./docs/screenshots/desktop-about.png) | ![Mobile About](./docs/screenshots/mobile-about.png) |

## 🚀 Features

### ✨ Modern Design
- **Beautiful UI**: Clean, modern design using shadcn-vue components
- **Responsive Layout**: Perfect experience across all devices and screen sizes
- **Dark/Light Mode**: Automatic theme support with CSS variables
- **Accessibility**: WCAG compliant with proper semantic HTML and ARIA labels

### 🛠️ Technical Excellence
- **Astro.js Framework**: Lightning-fast static site generation with islands architecture
- **Vue.js Integration**: Interactive components where needed
- **shadcn-vue Components**: High-quality, accessible UI components
- **Tailwind CSS**: Utility-first CSS framework for rapid development
- **TypeScript Support**: Type-safe development environment

### 📱 Pages & Features
- **Homepage**: Hero section, features grid, technology showcase
- **About Page**: Personal content, interests, inspirational quotes
- **Contact Page**: Contact form, contact information, FAQ section
- **Navigation**: Responsive navigation with mobile hamburger menu
- **Footer**: Site links, technology credits, copyright information

## 🏗️ Tech Stack

| Technology | Purpose | Version |
|------------|---------|---------|
| [Astro.js](https://astro.build/) | Static Site Generator | ^5.1.5 |
| [Vue.js](https://vuejs.org/) | Interactive Components | ^3.5.13 |
| [shadcn-vue](https://shadcn-vue.com/) | UI Components | Latest |
| [Tailwind CSS](https://tailwindcss.com/) | Styling | ^3.4.17 |
| [Lucide Vue Next](https://lucide.dev/) | Icons | ^0.471.0 |
| [Radix Vue](https://radix-vue.com/) | Primitive Components | ^1.9.12 |

## 🚀 Quick Start

### Prerequisites

- **Node.js** (version 18.0 or higher)
- **npm** or **pnpm** or **yarn**
- **Git**

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Nefnief-tech/mama-web-astro-shadcnui.git
   cd mama-web-astro-shadcnui
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   pnpm install
   # or
   yarn install
   ```

3. **Start development server**
   ```bash
   npm run dev
   # or
   pnpm dev
   # or
   yarn dev
   ```

4. **Open in browser**
   ```
   http://localhost:4321
   ```

## 📁 Project Structure

```
mama-web-astro-shadcnui/
├── public/                     # Static assets
│   └── favicon.svg
├── src/
│   ├── components/            # Vue components
│   │   ├── ui/               # shadcn-vue components
│   │   ├── Navigation.vue    # Main navigation
│   │   └── Footer.vue        # Site footer
│   ├── layouts/              # Astro layouts
│   │   └── Layout.astro      # Main layout
│   ├── pages/                # Astro pages (auto-routing)
│   │   ├── index.astro       # Homepage
│   │   ├── about.astro       # About page
│   │   └── contact.astro     # Contact page
│   ├── styles/               # Global styles
│   │   └── globals.css       # Tailwind & CSS variables
│   └── lib/                  # Utilities
│       └── utils.js          # Utility functions
├── components/               # Legacy component location
├── astro.config.mjs         # Astro configuration
├── tailwind.config.mjs      # Tailwind configuration
├── tsconfig.json           # TypeScript configuration
├── components.json         # shadcn-vue configuration
└── package.json            # Dependencies and scripts
```

## 🎨 Customization

### Adding New Components

1. **Add shadcn-vue components**:
   ```bash
   npx shadcn-vue@latest add button
   npx shadcn-vue@latest add card
   # Components will be added to src/components/ui/
   ```

2. **Create custom Vue components**:
   ```vue
   <!-- src/components/MyComponent.vue -->
   <script setup>
   import { Button } from '@/components/ui/button'
   </script>

   <template>
     <Button>Click me</Button>
   </template>
   ```

3. **Use in Astro pages**:
   ```astro
   ---
   import MyComponent from '@/components/MyComponent.vue'
   ---
   <MyComponent client:load />
   ```

### Styling

- **Global styles**: Edit `src/styles/globals.css`
- **Component styles**: Use Tailwind classes or scoped CSS
- **Theme colors**: Modify CSS variables in `globals.css`
- **Tailwind config**: Update `tailwind.config.mjs`

### Content Updates

- **Homepage content**: Edit `src/pages/index.astro`
- **About page**: Edit `src/pages/about.astro`
- **Contact info**: Update `src/pages/contact.astro`
- **Navigation**: Modify `src/components/Navigation.vue`

## 🚀 Deployment

### Static Hosting (Recommended)

1. **Build the project**:
   ```bash
   npm run build
   ```

2. **Deploy the `dist/` folder** to your preferred hosting:
   - [Netlify](https://netlify.com)
   - [Vercel](https://vercel.com)
   - [GitHub Pages](https://pages.github.com)
   - [Cloudflare Pages](https://pages.cloudflare.com)

### Netlify Deployment

1. Connect your GitHub repository to Netlify
2. Set build command: `npm run build`
3. Set publish directory: `dist`
4. Deploy!

### Vercel Deployment

1. Install Vercel CLI: `npm i -g vercel`
2. Run: `vercel --prod`
3. Follow the prompts

## 🛠️ Development

### Available Scripts

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run astro        # Run Astro CLI commands
```

### Adding New Pages

1. Create a new `.astro` file in `src/pages/`
2. Use the Layout component:
   ```astro
   ---
   import Layout from '@/layouts/Layout.astro'
   ---
   <Layout title="Page Title">
     <h1>Your content here</h1>
   </Layout>
   ```

### Development Tips

- **Hot reloading**: Astro automatically reloads on file changes
- **Vue components**: Use `client:load` directive for interactivity
- **CSS classes**: Use Tailwind utility classes for styling
- **Icons**: Import from `lucide-vue-next`
- **Components**: Import shadcn-vue components from `@/components/ui/`

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Make your changes**
4. **Commit your changes**: `git commit -m 'Add amazing feature'`
5. **Push to the branch**: `git push origin feature/amazing-feature`
6. **Open a Pull Request**

### Development Guidelines

- Follow existing code style and conventions
- Add comments for complex logic
- Test your changes on both desktop and mobile
- Update documentation if needed
- Ensure all builds pass before submitting

## 🐛 Troubleshooting

### Common Issues

1. **Build errors with components**:
   - Check import paths are correct
   - Ensure all dependencies are installed
   - Verify component syntax

2. **Mobile menu not working**:
   - Ensure Vue components have `client:load` directive
   - Check console for JavaScript errors

3. **Styling issues**:
   - Verify Tailwind classes are spelled correctly
   - Check if custom CSS is conflicting
   - Ensure CSS variables are properly defined

4. **Development server issues**:
   - Clear `node_modules` and reinstall: `rm -rf node_modules && npm install`
   - Clear Astro cache: `rm -rf .astro`
   - Check Node.js version compatibility

### Getting Help

- **Issues**: [GitHub Issues](https://github.com/Nefnief-tech/mama-web-astro-shadcnui/issues)
- **Discussions**: [GitHub Discussions](https://github.com/Nefnief-tech/mama-web-astro-shadcnui/discussions)
- **Astro Docs**: [astro.build/docs](https://docs.astro.build/)
- **shadcn-vue Docs**: [shadcn-vue.com](https://www.shadcn-vue.com/)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 💝 Acknowledgments

- **Mama** - The inspiration behind this project
- **Astro Team** - For the amazing framework
- **shadcn** - For the beautiful component system
- **Vue.js Team** - For the reactive framework
- **Tailwind CSS** - For the utility-first CSS framework

---

<div align="center">

**Made with ❤️ for Mama**

*A project that combines technical excellence with heartfelt intention*

</div>
