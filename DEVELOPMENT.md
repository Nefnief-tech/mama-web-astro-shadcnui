# 🚀 Development Guide

This guide will help you get started with developing and extending Mama's Website.

## 🛠️ Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18.0 or higher) - [Download here](https://nodejs.org/)
- **npm** (comes with Node.js) or **pnpm** or **yarn**
- **Git** - [Download here](https://git-scm.com/)
- **Code Editor** - We recommend [VS Code](https://code.visualstudio.com/) with these extensions:
  - Astro
  - Vue Language Features (Volar)
  - Tailwind CSS IntelliSense
  - Auto Rename Tag
  - Prettier

## 🏃‍♂️ Quick Setup

1. **Clone and Install**
   ```bash
   git clone https://github.com/Nefnief-tech/mama-web-astro-shadcnui.git
   cd mama-web-astro-shadcnui
   npm install
   ```

2. **Start Development**
   ```bash
   npm run dev
   ```

3. **Open Browser**
   Navigate to `http://localhost:4321`

## 📁 Understanding the Project Structure

### Key Directories

```
src/
├── components/          # Vue components
│   ├── ui/             # shadcn-vue components (auto-generated)
│   ├── Navigation.vue  # Main navigation component
│   └── Footer.vue      # Footer component
├── layouts/            # Astro layouts
│   └── Layout.astro    # Main layout template
├── pages/              # Astro pages (auto-routing)
│   ├── index.astro     # Homepage (/)
│   ├── about.astro     # About page (/about)
│   └── contact.astro   # Contact page (/contact)
├── styles/             # Global styles
│   └── globals.css     # Tailwind CSS and custom variables
└── lib/                # Utility functions
    └── utils.js        # Helper functions (cn, etc.)
```

### Configuration Files

- `astro.config.mjs` - Astro framework configuration
- `tailwind.config.mjs` - Tailwind CSS configuration
- `components.json` - shadcn-vue configuration
- `tsconfig.json` - TypeScript configuration
- `package.json` - Dependencies and scripts

## 🎨 Working with Components

### Using shadcn-vue Components

1. **Add a new component**:
   ```bash
   npx shadcn-vue@latest add accordion
   ```

2. **Use in Astro pages**:
   ```astro
   ---
   import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from '@/components/ui/accordion'
   ---

   <Accordion client:load>
     <AccordionItem value="item-1">
       <AccordionTrigger>Is it accessible?</AccordionTrigger>
       <AccordionContent>
         Yes. It adheres to the WAI-ARIA design pattern.
       </AccordionContent>
     </AccordionItem>
   </Accordion>
   ```

### Creating Custom Vue Components

1. **Create component file**:
   ```vue
   <!-- src/components/MyComponent.vue -->
   <script setup>
   import { ref } from 'vue'
   import { Button } from '@/components/ui/button'

   const count = ref(0)
   const increment = () => count.value++
   </script>

   <template>
     <div class="p-4 border rounded-lg">
       <p>Count: {{ count }}</p>
       <Button @click="increment">Increment</Button>
     </div>
   </template>
   ```

2. **Use in Astro**:
   ```astro
   ---
   import MyComponent from '@/components/MyComponent.vue'
   ---

   <MyComponent client:load />
   ```

### Component Best Practices

- **Use `client:load`** for interactive Vue components
- **Keep components small** and focused on a single responsibility
- **Use TypeScript** for better developer experience
- **Follow naming conventions**: PascalCase for components
- **Use composition API** in Vue components

## 🎨 Styling Guidelines

### Tailwind CSS

We use Tailwind CSS for styling. Here are the key principles:

1. **Utility-first approach**:
   ```html
   <div class="bg-white dark:bg-gray-800 p-6 rounded-lg shadow-md">
     <h2 class="text-2xl font-bold text-gray-900 dark:text-white mb-4">
       Title
     </h2>
   </div>
   ```

2. **Responsive design**:
   ```html
   <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
     <!-- Content -->
   </div>
   ```

3. **Dark mode support**:
   ```html
   <div class="bg-white dark:bg-gray-900 text-gray-900 dark:text-white">
     <!-- Content adapts to theme -->
   </div>
   ```

### CSS Variables

Custom colors are defined in `src/styles/globals.css`:

```css
:root {
  --background: 0 0% 100%;
  --foreground: 222.2 84% 4.9%;
  --primary: 222.2 47.4% 11.2%;
  /* ... more variables */
}
```

Use them in components:
```html
<div class="bg-background text-foreground border-border">
  Content
</div>
```

## 📄 Working with Pages

### Creating New Pages

1. **Create Astro file** in `src/pages/`:
   ```astro
   <!-- src/pages/blog.astro -->
   ---
   import Layout from '@/layouts/Layout.astro'
   import Navigation from '@/components/Navigation.vue'
   import Footer from '@/components/Footer.vue'
   ---

   <Layout title="Blog - Mama's Website">
     <Navigation client:load />
     
     <main>
       <h1>Blog Page</h1>
       <!-- Your content here -->
     </main>

     <Footer client:load />
   </Layout>
   ```

2. **Add to navigation** in `src/components/Navigation.vue`:
   ```javascript
   const menuItems = [
     { href: '/', label: 'Home', icon: Home },
     { href: '/about', label: 'About', icon: Heart },
     { href: '/blog', label: 'Blog', icon: BookOpen }, // New item
     { href: '/contact', label: 'Contact', icon: Mail }
   ]
   ```

### Page Structure Best Practices

1. **Use semantic HTML**:
   ```astro
   <main>
     <section aria-labelledby="hero-heading">
       <h1 id="hero-heading">Page Title</h1>
     </section>
     
     <section aria-labelledby="content-heading">
       <h2 id="content-heading">Content Section</h2>
     </section>
   </main>
   ```

2. **Include proper meta tags**:
   ```astro
   <Layout 
     title="Page Title - Mama's Website" 
     description="Page description for SEO"
   >
   ```

## 🔧 Development Workflow

### Daily Development

1. **Start the dev server**:
   ```bash
   npm run dev
   ```

2. **Make changes** to files
3. **Check browser** - changes auto-reload
4. **Test on mobile** - use browser dev tools
5. **Build before committing**:
   ```bash
   npm run build
   ```

### Code Quality

1. **Use consistent formatting**:
   - Install Prettier extension in VS Code
   - Format on save is recommended

2. **Follow naming conventions**:
   - Files: `kebab-case.astro`, `PascalCase.vue`
   - CSS classes: Tailwind utilities
   - JavaScript: `camelCase`

3. **Comment complex logic**:
   ```javascript
   // Calculate responsive grid columns based on screen size
   const getGridCols = (itemCount) => {
     if (itemCount <= 2) return 'grid-cols-1 md:grid-cols-2'
     return 'grid-cols-1 md:grid-cols-2 lg:grid-cols-3'
   }
   ```

### Testing Changes

1. **Desktop testing**:
   - Test all pages
   - Check navigation
   - Verify responsive design

2. **Mobile testing**:
   - Use browser dev tools
   - Test mobile menu
   - Check touch interactions

3. **Build testing**:
   ```bash
   npm run build
   npm run preview
   ```

## 🚀 Advanced Topics

### Adding Animations

Use Tailwind CSS animations or custom CSS:

```html
<!-- Tailwind animations -->
<div class="transition-all duration-300 hover:scale-105">
  Animated element
</div>

<!-- Custom animations -->
<style>
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.fade-in {
  animation: fadeIn 0.6s ease-out;
}
</style>
```

### Form Handling

For the contact form, you can integrate with services like:

- **Netlify Forms** (for static hosting)
- **Formspree** (external service)
- **Custom API** (for dynamic hosting)

Example with Netlify Forms:
```html
<form name="contact" method="POST" data-netlify="true">
  <!-- Form fields -->
</form>
```

### SEO Optimization

1. **Update meta tags** in Layout.astro
2. **Add structured data**:
   ```astro
   <script type="application/ld+json">
   {
     "@context": "https://schema.org",
     "@type": "WebSite",
     "name": "Mama's Website",
     "url": "https://your-domain.com"
   }
   </script>
   ```

3. **Generate sitemap** with Astro:
   ```bash
   npm install @astrojs/sitemap
   ```

## 🐛 Common Issues & Solutions

### Build Errors

1. **Import path errors**:
   ```bash
   # Check tsconfig.json paths configuration
   # Ensure files exist at specified paths
   ```

2. **Vue component errors**:
   ```bash
   # Add client:load directive to interactive components
   # Check component syntax and imports
   ```

### Styling Issues

1. **Tailwind not working**:
   - Check if classes are spelled correctly
   - Verify tailwind.config.mjs includes all files
   - Ensure globals.css is imported

2. **Dark mode issues**:
   - Check CSS variables are defined
   - Use dark: prefix for dark mode styles

### Performance Issues

1. **Large bundle size**:
   - Remove unused components
   - Optimize images
   - Use Astro's built-in optimizations

2. **Slow loading**:
   - Check network tab in dev tools
   - Optimize images and assets
   - Use Astro's lazy loading

## 📚 Helpful Resources

- [Astro Documentation](https://docs.astro.build/)
- [shadcn-vue Documentation](https://www.shadcn-vue.com/)
- [Vue.js Guide](https://vuejs.org/guide/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [Radix Vue Primitives](https://www.radix-vue.com/)

## 🤝 Getting Help

- Open an issue on GitHub
- Check existing issues and discussions
- Read the troubleshooting section in README
- Join the Astro Discord community

---

Happy coding! 🚀