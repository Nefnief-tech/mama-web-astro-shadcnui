# 🤝 Contributing to Mama's Website

Thank you for your interest in contributing to Mama's Website! This project is built with love, and we welcome contributions that maintain the same spirit of care and quality.

## 💡 How to Contribute

### Types of Contributions

We welcome several types of contributions:

- 🐛 **Bug reports and fixes**
- ✨ **New features and enhancements**
- 📝 **Documentation improvements**
- 🎨 **Design and UX improvements**
- 🧪 **Tests and quality improvements**
- 🔧 **Performance optimizations**
- 🌐 **Accessibility improvements**

## 🚀 Getting Started

### Prerequisites

Before contributing, ensure you have:

- **Node.js** (v18.0 or higher)
- **npm** or **pnpm** or **yarn**
- **Git**
- **Code editor** (VS Code recommended)

### Setup Development Environment

1. **Fork the repository** on GitHub
2. **Clone your fork**:
   ```bash
   git clone https://github.com/YOUR_USERNAME/mama-web-astro-shadcnui.git
   cd mama-web-astro-shadcnui
   ```

3. **Add upstream remote**:
   ```bash
   git remote add upstream https://github.com/Nefnief-tech/mama-web-astro-shadcnui.git
   ```

4. **Install dependencies**:
   ```bash
   npm install
   ```

5. **Start development server**:
   ```bash
   npm run dev
   ```

6. **Verify setup**: Open `http://localhost:4321` and ensure the site loads correctly

## 🔄 Development Workflow

### Creating a Feature Branch

1. **Sync with upstream**:
   ```bash
   git checkout main
   git pull upstream main
   ```

2. **Create feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   # or
   git checkout -b docs/your-documentation-update
   ```

### Making Changes

1. **Follow coding standards** (see below)
2. **Test your changes** thoroughly
3. **Write meaningful commit messages**
4. **Update documentation** if needed

### Testing Changes

Before submitting your contribution:

1. **Run the build**:
   ```bash
   npm run build
   ```

2. **Test the preview**:
   ```bash
   npm run preview
   ```

3. **Check different screen sizes**:
   - Desktop (1920x1080, 1366x768)
   - Tablet (768x1024)
   - Mobile (375x667, 414x896)

4. **Test functionality**:
   - Navigation works on all pages
   - Mobile menu functions properly
   - Contact form behaves correctly
   - All links work as expected

## 📝 Coding Standards

### General Guidelines

- **Write clean, readable code** with meaningful names
- **Follow existing code style** and patterns
- **Add comments** for complex logic
- **Keep functions small** and focused
- **Use semantic HTML** for accessibility
- **Follow responsive design** principles

### File Naming Conventions

- **Astro pages**: `kebab-case.astro` (e.g., `about-us.astro`)
- **Vue components**: `PascalCase.vue` (e.g., `NavigationMenu.vue`)
- **Utilities**: `camelCase.js` (e.g., `formatDate.js`)
- **Styles**: `kebab-case.css` (e.g., `custom-styles.css`)

### Code Style

#### Astro Files
```astro
---
// Imports at the top
import Layout from '@/layouts/Layout.astro'
import Component from '@/components/Component.vue'

// TypeScript interface if needed
interface Props {
  title: string
  description?: string
}

// Props destructuring
const { title, description = 'Default description' } = Astro.props
---

<Layout title={title} description={description}>
  <Component client:load />
</Layout>
```

#### Vue Components
```vue
<script setup>
// Imports
import { ref, computed } from 'vue'
import { Button } from '@/components/ui/button'

// Props
const props = defineProps({
  title: { type: String, required: true },
  subtitle: { type: String, required: false }
})

// Reactive state
const isVisible = ref(false)

// Computed properties
const displayTitle = computed(() => props.title.toUpperCase())

// Methods
const toggleVisibility = () => {
  isVisible.value = !isVisible.value
}
</script>

<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold">{{ displayTitle }}</h1>
    <Button @click="toggleVisibility">Toggle</Button>
  </div>
</template>
```

#### CSS/Tailwind Guidelines

1. **Use Tailwind utilities** whenever possible:
   ```html
   <div class="flex items-center justify-between p-4 bg-white dark:bg-gray-800">
   ```

2. **Group related classes**:
   ```html
   <!-- Layout classes first, then styling -->
   <div class="flex items-center justify-center p-4 bg-primary text-white rounded-lg shadow-md">
   ```

3. **Use responsive prefixes**:
   ```html
   <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
   ```

4. **Custom CSS sparingly**:
   ```css
   /* Only when Tailwind can't achieve the desired effect */
   .custom-animation {
     animation: fadeIn 0.3s ease-in-out;
   }
   ```

## 🎨 Design Guidelines

### Visual Consistency

- **Follow existing color scheme** defined in `globals.css`
- **Use consistent spacing** with Tailwind's spacing scale
- **Maintain typography hierarchy** with proper heading levels
- **Ensure accessibility** with proper color contrast

### Component Design

- **Keep components focused** on a single responsibility
- **Make components reusable** when possible
- **Follow shadcn-vue patterns** for consistency
- **Add proper props** with TypeScript types

### Responsive Design

- **Mobile-first approach**: Design for mobile, then enhance for larger screens
- **Test on real devices** when possible
- **Use semantic breakpoints**: `sm`, `md`, `lg`, `xl`
- **Ensure touch targets** are at least 44px on mobile

## 🐛 Bug Reports

When reporting bugs, please include:

### Bug Report Template

```markdown
## Bug Description
A clear and concise description of the bug.

## Steps to Reproduce
1. Go to '...'
2. Click on '...'
3. Scroll down to '...'
4. See error

## Expected Behavior
What you expected to happen.

## Actual Behavior
What actually happened.

## Screenshots
If applicable, add screenshots to help explain the problem.

## Environment
- OS: [e.g., macOS, Windows, Linux]
- Browser: [e.g., Chrome 91, Firefox 89, Safari 14]
- Screen size: [e.g., mobile, tablet, desktop]
- Node.js version: [e.g., 18.17.0]

## Additional Context
Any other context about the problem.
```

## ✨ Feature Requests

When suggesting new features:

### Feature Request Template

```markdown
## Feature Description
A clear and concise description of the feature.

## Problem Statement
What problem does this feature solve?

## Proposed Solution
How should this feature work?

## Alternatives Considered
What other solutions have you considered?

## Additional Context
Any other context, mockups, or examples.
```

## 📋 Pull Request Process

### Before Submitting

1. **Check existing issues** and PRs to avoid duplicates
2. **Test your changes** thoroughly
3. **Update documentation** if needed
4. **Follow the coding standards**
5. **Write clear commit messages**

### Pull Request Template

When creating a PR, please include:

```markdown
## Description
Brief description of changes.

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update

## Testing
- [ ] I have tested my changes locally
- [ ] I have tested on mobile devices
- [ ] I have tested the build process
- [ ] I have updated documentation (if applicable)

## Screenshots (if applicable)
Add screenshots to help reviewers understand your changes.

## Checklist
- [ ] My code follows the project's coding standards
- [ ] I have performed a self-review of my code
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] My changes generate no new warnings
- [ ] I have updated the documentation accordingly
```

### Review Process

1. **Automated checks** will run on your PR
2. **Maintainers will review** your code
3. **Feedback may be provided** for improvements
4. **Once approved**, your PR will be merged

## 🎯 Specific Contribution Areas

### Documentation

- **Improve README** with clearer instructions
- **Add code examples** to development guide
- **Create tutorials** for common tasks
- **Fix typos** and grammar issues
- **Add missing documentation** for components

### Design & UX

- **Improve accessibility** features
- **Enhance mobile experience**
- **Add animations** and micro-interactions
- **Optimize color schemes**
- **Improve typography** and spacing

### Performance

- **Optimize images** and assets
- **Reduce bundle size**
- **Improve Lighthouse scores**
- **Add lazy loading**
- **Optimize build process**

### Features

- **Add new pages** or sections
- **Enhance contact form** functionality
- **Add blog** or content management
- **Implement search** functionality
- **Add PWA** features

## 🤔 Questions?

If you have questions about contributing:

1. **Check existing issues** and discussions
2. **Read the documentation** thoroughly
3. **Open a discussion** on GitHub
4. **Ask in the issue** you're working on

## 🙏 Recognition

Contributors will be:

- **Listed in README** (if significant contribution)
- **Mentioned in release notes**
- **Given credit** in commit messages
- **Appreciated** with genuine gratitude! 💝

## 📜 Code of Conduct

This project is built with love for Mama, and we expect all contributors to:

- **Be respectful** and inclusive
- **Provide constructive feedback**
- **Help newcomers** learn and contribute
- **Maintain the project's** positive spirit
- **Focus on building** something beautiful together

Thank you for contributing to Mama's Website! Your efforts help make this project better for everyone. 🌟

---

*Made with ❤️ for Mama by the community*