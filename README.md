# Portfolio Pro Documentation

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
   - [Project Structure](#project-structure)
3. [Core Features](#core-features)
   - [Responsive Design](#responsive-design)
   - [Dark/Light Mode](#darklight-mode)
   - [Smooth Animations](#smooth-animations)
   - [Interactive Background](#interactive-background)
4. [Components](#components)
   - [UI Components](#ui-components)
   - [Layout Components](#layout-components)
   - [Section Components](#section-components)
5. [Customization](#customization)
   - [Personal Information](#personal-information)
   - [Theme Customization](#theme-customization)
   - [Content Customization](#content-customization)
6. [Hooks and Utilities](#hooks-and-utilities)
   - [useToast](#usetoast)
   - [useTheme](#usetheme)
   - [Utility Functions](#utility-functions)
7. [Deployment](#deployment)
   - [Build Process](#build-process)
   - [Deployment Options](#deployment-options)
8. [Troubleshooting](#troubleshooting)
9. [FAQ](#faq)
10. [Credits](#credits)

## Introduction

Portfolio Pro is a modern, responsive portfolio template built with React, Vite, Tailwind CSS, and Framer Motion. It's designed for developers, designers, and creative professionals who want to showcase their work in a clean, professional manner.

The template features a sleek design with smooth animations, interactive elements, and a fully responsive layout that works on all devices. It includes sections for showcasing your skills, projects, services, and contact information.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- Node.js (v14.0.0 or later)
- npm or yarn

### Installation

1. Clone or download the template:

```bash
Download file from themeforest and extract on your computer
Go to portfolio-pro folder
```

2. Install dependencies:

```bash
npm install
# or
yarn install
```

3. Start the development server:

```bash
npm run dev
# or
yarn dev
```

4. Open [http://localhost:5173](http://localhost:5173) in your browser to see the result.

### Project Structure

```
portfolio-pro/
├── public/                # Static assets
│   ├── images/            # Image assets
│   ├── resume.pdf         # Your resume file
│   └── ...
├── src/                   # Source code
│   ├── components/        # React components
│   │   ├── sections/      # Page sections (hero, about, etc.)
│   │   ├── ui/            # UI components
│   │   ├── navbar.jsx     # Navigation component
│   │   ├── footer.jsx     # Footer component
│   │   └── ...
│   ├── hooks/             # Custom React hooks
│   ├── lib/               # Utility functions
│   ├── App.jsx            # Main App component
│   ├── main.jsx           # Entry point
│   └── index.css          # Global styles
├── package.json           # Project dependencies
├── vite.config.js         # Vite configuration
├── tailwind.config.js     # Tailwind CSS configuration
└── README.md              # Project documentation
```

## Core Features

### Responsive Design

Portfolio Pro is built with a mobile-first approach, ensuring that your portfolio looks great on all devices, from mobile phones to large desktop screens. The layout adapts intelligently to different screen sizes using Tailwind CSS's responsive utilities.

Key responsive features:
- Flexible grid layouts
- Responsive typography
- Mobile navigation menu
- Optimized images

### Dark/Light Mode

The template includes a built-in theme switcher that allows visitors to toggle between dark and light modes. The theme preference is saved in local storage and respects the user's system preferences by default.

The theme implementation uses CSS variables for seamless transitions between themes. You can customize the color scheme for both light and dark modes in the `src/index.css` file.

```jsx
// Example of the theme toggle component
import { useTheme } from './components/theme-provider';

function ThemeToggle() {
  const { theme, setTheme } = useTheme();
  
  return (
    <button onClick={() => setTheme(theme === 'dark' ? 'light' : 'dark')}>
      Toggle Theme
    </button>
  );
}
```

### Smooth Animations

Using Framer Motion, the template includes smooth, subtle animations that enhance the user experience without being distracting. Elements fade in as they enter the viewport, creating an engaging scrolling experience.

Example of an animated component:

```jsx
import { motion } from 'framer-motion';

<motion.div
  initial={{ opacity: 0, y: 20 }}
  whileInView={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.5 }}
  viewport={{ once: true }}
>
  Your content here
</motion.div>
```

### Interactive Background

The template features an interactive 3D particle background created with Three.js that responds to mouse movements, adding a modern and dynamic feel to your portfolio.

The background is implemented in the `ParallaxBackground` component and can be customized to match your style preferences.

## Components

### UI Components

Portfolio Pro includes a comprehensive set of UI components built with Radix UI primitives and styled with Tailwind CSS. These components are located in the `src/components/ui` directory.

Key UI components:

- **Button**: Versatile button component with multiple variants
- **Card**: Container component for displaying content in a card format
- **Dialog**: Modal dialog for displaying additional content
- **Form**: Form components with validation support
- **Toast**: Notification component for displaying messages
- **Tabs**: Tabbed interface for organizing content
- **Carousel**: Slideshow component for displaying multiple items
- **Progress**: Progress bar for visualizing data
- **Badge**: Label component for displaying metadata
- **Avatar**: User avatar component

Example usage:

```jsx
import { Button } from './components/ui/button';
import { Card, CardContent, CardHeader, CardTitle } from './components/ui/card';

function ExampleComponent() {
  return (
    <Card>
      <CardHeader>
        <CardTitle>Card Title</CardTitle>
      </CardHeader>
      <CardContent>
        <p>Card content goes here</p>
        <Button>Click Me</Button>
      </CardContent>
    </Card>
  );
}
```

### Layout Components

Layout components help structure the overall page layout and provide consistent styling across the portfolio.

Key layout components:

- **Navbar**: Navigation bar with responsive mobile menu
- **Footer**: Page footer with contact information and links
- **ParallaxBackground**: Interactive background component
- **SectionHeading**: Consistent heading style for all sections

### Section Components

Section components represent the main content sections of the portfolio. These are located in the `src/components/sections` directory.

Available sections:

- **Hero**: The first section visitors see, featuring your name, profession, and call-to-action buttons
- **About**: Detailed information about you and your background
- **Services**: Showcase of services you offer
- **Portfolio**: Gallery of your projects with filtering options
- **Skills**: Display of your technical skills with progress bars
- **Contact**: Contact form and contact information

Each section is designed to be modular and can be easily customized or removed based on your needs.

## Customization

### Personal Information

To customize the portfolio with your personal information, you'll need to modify several files:

#### Update Hero Section

Open `src/components/sections/hero.jsx` and update the text content:

```jsx
<h1 className="text-4xl md:text-5xl lg:text-6xl font-bold mb-4">
  Hi, I'm <span className="text-primary">Your Name</span>
</h1>

<h2 className="text-2xl md:text-3xl font-semibold mb-6">
  <span className="inline-block">
    Your Profession
  </span>
</h2>

<p className="text-muted-foreground text-lg mb-8 max-w-xl">
  Your brief description here.
</p>
```

#### Update About Section

Open `src/components/sections/about.jsx` and update your personal information:

```jsx
<h3 className="text-2xl font-bold mb-4">
  I'm a passionate [Your Profession] based in [Your Location]
</h3>

// Update personal details
<div>
  <p className="font-medium">Name:</p>
  <p className="text-muted-foreground">Your Name</p>
</div>
<div>
  <p className="font-medium">Email:</p>
  <p className="text-muted-foreground">your.email@example.com</p>
</div>
```

#### Update Contact Information

Open `src/components/sections/contact.jsx` and update your contact details:

```jsx
// Update location
<p className="text-muted-foreground">Your City, Country</p>

// Update email
<p className="text-muted-foreground">your.email@example.com</p>

// Update phone
<p className="text-muted-foreground">+1 (123) 456-7890</p>
```

#### Update Navbar

Open `src/components/navbar.jsx` and update your name:

```jsx
<ScrollLink
  to="hero"
  spy={true}
  smooth={true}
  offset={-100}
  duration={500}
  className="text-2xl font-bold cursor-pointer"
>
  Your<span className="text-primary">Name</span>
</ScrollLink>
```

#### Update Footer

Open `src/components/footer.jsx` and update your information:

```jsx
<h3 className="text-2xl font-bold mb-4">Your<span className="text-primary">Name</span></h3>

<p className="text-muted-foreground mb-6 max-w-md">
  Your brief description here.
</p>

// Update social links
<Button variant="ghost" size="icon" asChild>
  <a href="https://github.com/yourusername" target="_blank" rel="noopener noreferrer">
    <Github className="h-5 w-5" />
  </a>
</Button>
```

### Theme Customization

#### Color Scheme

Portfolio Pro uses a CSS variables-based theming system that supports both light and dark modes. The color scheme is defined in `src/index.css`:

```css
@layer base {
  :root {
    --background: 0 0% 100%;
    --foreground: 0 0% 3.9%;
    --card: 0 0% 100%;
    --card-foreground: 0 0% 3.9%;
    --popover: 0 0% 100%;
    --popover-foreground: 0 0% 3.9%;
    --primary: 0 0% 9%;
    --primary-foreground: 0 0% 98%;
    /* ... other variables ... */
  }
  .dark {
    --background: 0 0% 3.9%;
    --foreground: 0 0% 98%;
    /* ... other dark mode variables ... */
  }
}
```

To customize the color scheme, modify these CSS variables. The values are in the format of `H S L` (Hue, Saturation, Lightness).

For example, to change the primary color to blue:

```css
:root {
  /* Change primary color to blue */
  --primary: 210 100% 50%; /* Blue */
  --primary-foreground: 0 0% 98%;
  /* ... other variables ... */
}
.dark {
  /* Change primary color to a lighter blue in dark mode */
  --primary: 210 100% 60%; /* Lighter blue */
  --primary-foreground: 0 0% 98%;
  /* ... other variables ... */
}
```

#### Typography

The template uses system fonts by default. To change the font, you can update the `tailwind.config.js` file:

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['Your Font Name', 'sans-serif'],
      },
    },
  },
};
```

Then, add the font link to the `index.html` file:

```html
<link href="https://fonts.googleapis.com/css2?family=Your+Font+Name:wght@400;500;700&display=swap" rel="stylesheet">
```

### Content Customization

#### Portfolio Projects

To update the portfolio projects, open `src/components/sections/portfolio.jsx` and modify the `projects` array:

```jsx
const projects = [
  {
    id: 1,
    title: 'Your Project Title',
    category: 'web', // or 'mobile', etc.
    image: '/images/project-image.jpg',
    description: 'Brief description of your project',
    technologies: ['React', 'Node.js', 'MongoDB'],
    demoLink: 'https://example.com',
    githubLink: 'https://github.com/yourusername/project',
    detailedDescription: 'Detailed description of your project...'
  },
  // Add more projects...
];
```

#### Skills

To update your skills, open `src/components/sections/skills.jsx` and modify the skills arrays:

```jsx
const frontendSkills = [
  { name: 'HTML/CSS', level: 95 },
  { name: 'JavaScript', level: 90 },
  // Add more skills...
];

const backendSkills = [
  { name: 'Node.js', level: 85 },
  { name: 'Express', level: 80 },
  // Add more skills...
];
```

#### Services

To update the services you offer, open `src/components/sections/services.jsx` and modify the `services` array:

```jsx
const services = [
  {
    id: 1,
    icon: <Layout className="h-10 w-10 text-primary" />,
    title: 'Your Service',
    description: 'Description of your service...',
  },
  // Add more services...
];
```

#### Images

To update images, replace the image files in the `public/images` directory with your own images, or update the image paths in the respective components.

## Hooks and Utilities

### useToast

The `useToast` hook provides a simple way to display toast notifications in your application. It's implemented in `src/hooks/use-toast.js`.

Example usage:

```jsx
import { useToast } from '../hooks/use-toast';

function ExampleComponent() {
  const { toast } = useToast();
  
  const showToast = () => {
    toast({
      title: "Success!",
      description: "Your action was completed successfully.",
      variant: "default", // or "destructive"
    });
  };
  
  return (
    <button onClick={showToast}>Show Toast</button>
  );
}
```

### useTheme

The `useTheme` hook provides access to the current theme and allows you to change it. It's implemented in `src/components/theme-provider.jsx`.

Example usage:

```jsx
import { useTheme } from '../components/theme-provider';

function ExampleComponent() {
  const { theme, setTheme } = useTheme();
  
  return (
    <div>
      <p>Current theme: {theme}</p>
      <button onClick={() => setTheme('light')}>Light</button>
      <button onClick={() => setTheme('dark')}>Dark</button>
      <button onClick={() => setTheme('system')}>System</button>
    </div>
  );
}
```

### Utility Functions

The template includes utility functions in the `src/lib/utils.js` file:

```js
import { clsx } from 'clsx';
import { twMerge } from 'tailwind-merge';

export function cn(...inputs) {
  return twMerge(clsx(inputs));
}
```

The `cn` function is used to merge Tailwind CSS classes and conditional classes throughout the template.

Example usage:

```jsx
import { cn } from '../lib/utils';

function ExampleComponent({ className }) {
  return (
    <div className={cn(
      "base-class",
      className,
      condition && "conditional-class"
    )}>
      Content
    </div>
  );
}
```

## Deployment

### Build Process

To build the portfolio for production, run:

```bash
npm run build
# or
yarn build
```

This will create a `dist` directory with the production-ready files.

To preview the production build locally, run:

```bash
npm run preview
# or
yarn preview
```

### Deployment Options

#### Netlify

To deploy to Netlify:

1. Create an account on [Netlify](https://netlify.com)
2. Click "New site from Git" and connect your repository
3. Set the build command to `npm run build`
4. Set the publish directory to `dist`

#### Vercel

To deploy to Vercel:

1. Create an account on [Vercel](https://vercel.com)
2. Install the Vercel CLI: `npm install -g vercel`
3. Run `vercel` in your project directory and follow the prompts
4. Or connect your GitHub repository to Vercel for automatic deployments

#### GitHub Pages

To deploy to GitHub Pages:

1. Update `vite.config.js` with your repository name:

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import path from 'path'

export default defineConfig({
  plugins: [react()],
  base: '/your-repo-name/',
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src'),
    },
  },
})
```

2. Add a `.github/workflows/deploy.yml` file for GitHub Actions:

```yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
        
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16
          
      - name: Install dependencies
        run: npm ci
        
      - name: Build
        run: npm run build
        
      - name: Deploy
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: dist
          branch: gh-pages
```

## Troubleshooting

### Common Issues

#### Images Not Loading

If images are not loading, check the following:

1. Ensure the image paths are correct
2. Make sure the images are in the `public` directory
3. Check for any console errors related to image loading

#### Styling Issues

If you're experiencing styling issues:

1. Make sure Tailwind CSS is properly configured
2. Check for any conflicting styles
3. Verify that the theme variables are correctly defined

#### Build Errors

If you encounter build errors:

1. Check the console for specific error messages
2. Ensure all dependencies are installed
3. Verify that your code doesn't contain any syntax errors

## FAQ

### How do I add a new section to the portfolio?

To add a new section:

1. Create a new component in `src/components/sections/`
2. Import and add the component to `src/App.jsx`
3. Add a navigation link in `src/components/navbar.jsx`

### How do I change the profile picture?

Replace the image URLs in the Hero and About sections with your own image URLs. For example:

```jsx
<img 
  src="/images/your-profile-picture.jpg" 
  alt="Your Name" 
  className="w-full h-full object-cover"
/>
```

### How do I add more portfolio projects?

Add more objects to the `projects` array in `src/components/sections/portfolio.jsx`:

```jsx
const projects = [
  // Existing projects...
  {
    id: 7, // Make sure to use a unique ID
    title: 'New Project',
    category: 'web',
    image: '/images/project-image.jpg',
    description: 'Project description...',
    technologies: ['React', 'Node.js'],
    demoLink: 'https://example.com',
    githubLink: 'https://github.com/yourusername/project',
    detailedDescription: 'Detailed description...'
  },
];
```

### How do I make the contact form functional?

The contact form in the template is set up for demonstration purposes. To make it functional, you need to implement a backend service to handle form submissions. Here's a simple example using a service like Formspree:

```jsx
function onSubmit(values) {
  setIsSubmitting(true);
  
  // Send form data to Formspree
  fetch('https://formspree.io/f/your-form-id', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(values),
  })
    .then(response => {
      if (response.ok) {
        toast({
          title: "Message sent!",
          description: "Thank you for your message. I'll get back to you soon.",
        });
        form.reset();
      } else {
        toast({
          title: "Error",
          description: "There was a problem sending your message. Please try again.",
          variant: "destructive",
        });
      }
    })
    .catch(error => {
      toast({
        title: "Error",
        description: "There was a problem sending your message. Please try again.",
        variant: "destructive",
      });
    })
    .finally(() => {
      setIsSubmitting(false);
    });
}
```

### How do I add a blog section?

To add a blog section, you would need to create new components and pages. Here's a simplified approach:

1. Create a `src/components/sections/blog.jsx` component to display blog post previews
2. Create a blog post component for individual blog posts
3. Add a link to the blog in the navigation
4. Update your routing if you're using a router

### How do I change the fonts?

To change the fonts, you can add a Google Font or any other web font to your project. Here's how to do it with Google Fonts:

1. Add the font link to the `index.html` file:

```html
<link href="https://fonts.googleapis.com/css2?family=Your+Font+Name:wght@400;500;700&display=swap" rel="stylesheet">
```

2. Update the font family in the Tailwind configuration:

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['"Your Font Name"', 'sans-serif'],
      },
    },
  },
};
```

### How do I add animations to other elements?

You can add animations to any element using Framer Motion. Here's a simple example:

```jsx
import { motion } from 'framer-motion';

// Simple fade-in animation
<motion.div
  initial={{ opacity: 0 }}
  animate={{ opacity: 1 }}
  transition={{ duration: 0.5 }}
>
  Your content here
</motion.div>

// Animation when element enters viewport
<motion.div
  initial={{ opacity: 0, y: 50 }}
  whileInView={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.5 }}
  viewport={{ once: true }}
>
  Your content here
</motion.div>
```

## Credits

Portfolio Pro uses the following open-source libraries and resources:

- [React](https://reactjs.org/) - JavaScript library for building user interfaces
- [Vite](https://vitejs.dev/) - Next generation frontend tooling
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework
- [Framer Motion](https://www.framer.com/motion/) - Animation library
- [Three.js](https://threejs.org/) - 3D library
- [Radix UI](https://www.radix-ui.com/) - UI component primitives
- [React Hook Form](https://react-hook-form.com/) - Form validation
- [Lucide](https://lucide.dev/) - Icon library
