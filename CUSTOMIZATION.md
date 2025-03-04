# Portfolio Pro Customization Guide

This guide provides detailed instructions on how to customize various aspects of the Portfolio Pro template to make it your own.

## Table of Contents

1. [Personal Information](#personal-information)
2. [Theme and Styling](#theme-and-styling)
3. [Content Sections](#content-sections)
4. [Adding New Features](#adding-new-features)
5. [Advanced Customization](#advanced-customization)

## Personal Information

### Basic Information

Update your personal information in the following files:

#### Hero Section (`src/components/sections/hero.jsx`)

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
  Your brief introduction here. Describe what you do and what makes you unique.
</p>
```

#### About Section (`src/components/sections/about.jsx`)

```jsx
<h3 className="text-2xl font-bold mb-4">
  I'm a passionate [Your Profession] based in [Your Location]
</h3>

<p className="text-muted-foreground mb-4">
  Your detailed bio goes here. Talk about your background, experience, and what drives you.
</p>

// Personal details
<div>
  <p className="font-medium">Name:</p>
  <p className="text-muted-foreground">Your Name</p>
</div>
<div>
  <p className="font-medium">Email:</p>
  <p className="text-muted-foreground">your.email@example.com</p>
</div>
<div>
  <p className="font-medium">Location:</p>
  <p className="text-muted-foreground">Your City, Country</p>
</div>
<div>
  <p className="font-medium">Availability:</p>
  <p className="text-muted-foreground">Freelance & Full-time</p>
</div>
```

#### Contact Section (`src/components/sections/contact.jsx`)

```jsx
// Update location
<p className="text-muted-foreground">Your City, Country</p>

// Update email
<p className="text-muted-foreground">your.email@example.com</p>

// Update phone
<p className="text-muted-foreground">+1 (123) 456-7890</p>
```

#### Navbar (`src/components/navbar.jsx`)

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

#### Footer (`src/components/footer.jsx`)

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
<Button variant="ghost" size="icon" asChild>
  <a href="https://linkedin.com/in/yourusername" target="_blank" rel="noopener noreferrer">
    <Linkedin className="h-5 w-5" />
  </a>
</Button>
<Button variant="ghost" size="icon" asChild>
  <a href="https://twitter.com/yourusername" target="_blank" rel="noopener noreferrer">
    <Twitter className="h-5 w-5" />
  </a>
</Button>
```

### Profile Images

Replace the profile images in the `public/images` directory:

1. Replace `author.jpg` with your profile picture for the hero section
2. Replace `author-about.jpg` with your profile picture for the about section

Alternatively, you can update the image paths in the components:

```jsx
// In hero.jsx
<img 
  src="/images/your-profile-image.jpg" 
  alt="Your Name" 
  className="w-full h-full object-cover"
/>

// In about.jsx
<img 
  src="/images/your-about-image.jpg" 
  alt="About Your Name" 
  className="rounded-lg shadow-lg w-full h-auto"
/>
```

### Resume/CV

Replace the resume file in the `public` directory:

1. Save your resume as a PDF file
2. Replace `resume.pdf` with your own file, or update the path in the about section:

```jsx
// In about.jsx
<Button asChild>
  <a href="/your-resume.pdf" download>
    <Download className="mr-2 h-4 w-4" /> Download CV
  </a>
</Button>
```

## Theme and Styling

### Color Scheme

The color scheme is defined using CSS variables in `src/index.css`. You can customize the colors by modifying these variables:

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
    --secondary: 0 0% 96.1%;
    --secondary-foreground: 0 0% 9%;
    --muted: 0 0% 96.1%;
    --muted-foreground: 0 0% 45.1%;
    --accent: 0 0% 96.1%;
    --accent-foreground: 0 0% 9%;
    --destructive: 0 84.2% 60.2%;
    --destructive-foreground: 0 0% 98%;
    --border: 0 0% 89.8%;
    --input: 0 0% 89.8%;
    --ring: 0 0% 3.9%;
    --radius: 0.5rem;
  }
  .dark {
    --background: 0 0% 3.9%;
    --foreground: 0 0% 98%;
    --card: 0 0% 3.9%;
    --card-foreground: 0 0% 98%;
    --popover: 0 0% 3.9%;
    --popover-foreground: 0 0% 98%;
    --primary: 0 0% 98%;
    --primary-foreground: 0 0% 9%;
    --secondary: 0 0% 14.9%;
    --secondary-foreground: 0 0% 98%;
    --muted: 0 0% 14.9%;
    --muted-foreground: 0 0% 63.9%;
    --accent: 0 0% 14.9%;
    --accent-foreground: 0 0% 98%;
    --destructive: 0 62.8% 30.6%;
    --destructive-foreground: 0 0% 98%;
    --border: 0 0% 14.9%;
    --input: 0 0% 14.9%;
    --ring: 0 0% 83.1%;
  }
}
```

The values are in the format of `H S L` (Hue, Saturation, Lightness).

#### Example: Changing to a Blue Theme

```css
:root {
  --primary: 210 100% 50%; /* Blue */
  --primary-foreground: 0 0% 98%;
  /* ... other variables ... */
}
.dark {
  --primary: 210 100% 60%; /* Lighter blue */
  --primary-foreground: 0 0% 98%;
  /* ... other variables ... */
}
```

### Typography

To change the font, update the `tailwind.config.js` file:

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

### Border Radius

You can adjust the border radius of components by modifying the `--radius` variable in `src/index.css`:

```css
:root {
  --radius: 0.5rem; /* Default */
}
```

Change it to a smaller value for less rounded corners:

```css
:root {
  --radius: 0.25rem; /* Less rounded */
}
```

Or to a larger value for more rounded corners:

```css
:root {
  --radius: 1rem; /* More rounded */
}
```

## Content Sections

### Portfolio Projects

Update the portfolio projects in `src/components/sections/portfolio.jsx`:

```jsx
const projects = [
  {
    id: 1,
    title: 'Your Project Title',
    category: 'web', // or 'mobile', 'design', etc.
    image: '/images/your-project-image.jpg',
    description: 'Brief description of your project',
    technologies: ['React', 'Node.js', 'MongoDB'],
    demoLink: 'https://example.com',
    githubLink: 'https://github.com/yourusername/project',
    detailedDescription: 'Detailed description of your project...'
  },
  // Add more projects...
];
```

To add project images:

1. Add your project images to the `public/images` directory
2. Reference them in the `image` property of each project

To add or modify project categories:

1. Update the `category` property of each project
2. Modify the filter buttons in the portfolio section:

```jsx
<Button 
  variant={filter === 'all' ? 'default' : 'outline'} 
  onClick={() => setFilter('all')}
>
  All
</Button>
<Button 
  variant={filter === 'web' ? 'default' : 'outline'} 
  onClick={() => setFilter('web')}
>
  Web
</Button>
<Button 
  variant={filter === 'mobile' ? 'default' : 'outline'} 
  onClick={() => setFilter('mobile')}
>
  Mobile
</Button>
<Button 
  variant={filter === 'design' ? 'default' : 'outline'} 
  onClick={() => setFilter('design')}
>
  Design
</Button>
```

### Skills

Update your skills in `src/components/sections/skills.jsx`:

```jsx
const frontendSkills = [
  { name: 'HTML/CSS', level: 95 },
  { name: 'JavaScript', level: 90 },
  { name: 'React', level: 85 },
  { name: 'Next.js', level: 80 },
  { name: 'TypeScript', level: 75 },
  { name: 'Tailwind CSS', level: 90 },
];

const backendSkills = [
  { name: 'Node.js', level: 85 },
  { name: 'Express', level: 80 },
  { name: 'MongoDB', level: 75 },
  { name: 'PostgreSQL', level: 70 },
  { name: 'GraphQL', level: 65 },
  { name: 'REST API', level: 90 },
];

const otherSkills = [
  { name: 'Git/GitHub', level: 85 },
  { name: 'Docker', level: 70 },
  { name: 'AWS', level: 65 },
  { name: 'CI/CD', level: 75 },
  { name: 'Testing', level: 80 },
  { name: 'UI/UX Design', level: 70 },
];
```

To add a new skill category:

1. Create a new array for your skills:

```jsx
const designSkills = [
  { name: 'Figma', level: 90 },
  { name: 'Adobe XD', level: 85 },
  { name: 'Photoshop', level: 80 },
  { name: 'Illustrator', level: 75 },
];
```

2. Add a new tab in the skills section:

```jsx
<TabsList className="grid w-full grid-cols-4 mb-8">
  <TabsTrigger value="frontend">Frontend</TabsTrigger>
  <TabsTrigger value="backend">Backend</TabsTrigger>
  <TabsTrigger value="design">Design</TabsTrigger>
  <TabsTrigger value="other">Other</TabsTrigger>
</TabsList>

{/* Add a new TabsContent for the design skills */}
<TabsContent value="design">
  <Card>
    <CardContent className="pt-6">
      <div className="space-y-6">
        {designSkills.map((skill, index) => (
          <motion.div
            key={skill.name}
            initial={{ opacity: 0, x: -20 }}
            whileInView={{ opacity: 1, x: 0 }}
            transition={{ duration: 0.5, delay: index * 0.1 }}
            viewport={{ once: true }}
          >
            <div className="flex justify-between mb-1">
              <span className="font-medium">{skill.name}</span>
              <span className="text-muted-foreground">{skill.level}%</span>
            </div>
            <Progress value={skill.level} className="h-2" />
          </motion.div>
        ))}
      </div>
    </CardContent>
  </Card>
</TabsContent>
```

### Services

Update the services you offer in `src/components/sections/services.jsx`:

```jsx
const services = [
  {
    id: 1,
    icon: <Layout className="h-10 w-10 text-primary" />,
    title: 'Web Design',
    description: 'Creating beautiful, responsive websites that look great on all devices and provide an excellent user experience.',
  },
  {
    id: 2,
    icon: <Code className="h-10 w-10 text-primary" />,
    title: 'Frontend Development',
    description: 'Building interactive user interfaces with modern frameworks like React, Next.js, and Vue.js.',
  },
  // Add more services...
];
```

To change the icons, import different icons from the Lucide React library:

```jsx
import { Layout, Code, Database, Smartphone, Server, ArrowRight, Palette, Globe } from 'lucide-react';
```

Then use them in your services:

```jsx
{
  id: 7,
  icon: <Palette className="h-10 w-10 text-primary" />,
  title: 'UI/UX Design',
  description: 'Designing intuitive and engaging user interfaces and experiences that delight users and achieve business goals.',
}
```

## Adding New Features

### Adding a Blog Section

To add a blog section to your portfolio:

1. Create a new component in `src/components/sections/blog.jsx`:

```jsx
import React from 'react';
import { motion } from 'framer-motion';
import SectionHeading from '../section-heading';
import { Card, CardContent, CardFooter, CardHeader, CardTitle } from '../ui/card';
import { Button } from '../ui/button';
import { ArrowRight } from 'lucide-react';

const blogPosts = [
  {
    id: 1,
    title: 'Your Blog Post Title',
    excerpt: 'A brief excerpt from your blog post...',
    date: 'June 15, 2025',
    image: '/images/blog-1.jpg',
    url: 'https://yourblog.com/post-1',
  },
  // Add more blog posts...
];

export default function Blog() {
  return (
    <section id="blog" className="py-20">
      <div className="container px-4 mx-auto">
        <SectionHeading 
          title="My Blog" 
          subtitle="Latest articles and tutorials"
        />
        
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {blogPosts.map((post, index) => (
            <motion.div
              key={post.id}
              initial={{ opacity: 0, y: 20 }}
              whileInView={{ opacity: 1, y: 0 }}
              transition={{ duration: 0.5, delay: index * 0.1 }}
              viewport={{ once: true }}
            >
              <Card className="h-full overflow-hidden group">
                <div className="relative overflow-hidden h-48">
                  <img 
                    src={post.image} 
                    alt={post.title} 
                    className="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                  />
                </div>
                <CardHeader>
                  <div className="text-sm text-muted-foreground mb-2">{post.date}</div>
                  <CardTitle>{post.title}</CardTitle>
                </CardHeader>
                <CardContent>
                  <p className="text-muted-foreground">{post.excerpt}</p>
                </CardContent>
                <CardFooter>
                  <Button variant="ghost" className="p-0 h-auto" asChild>
                    <a href={post.url} target="_blank" rel="noopener noreferrer">
                      Read More <ArrowRight className="ml-2 h-4 w-4" />
                    </a>
                  </Button>
                </CardFooter>
              </Card>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
}
```

2. Add the blog section to `src/App.jsx`:

```jsx
import Blog from './components/sections/blog';

function App() {
  return (
    <main className="relative min-h-screen">
      <ParallaxBackground />
      <Navbar />
      <div className="relative z-10">
        <Hero />
        <About />
        <Services />
        <Portfolio />
        <Skills />
        <Blog /> {/* Add the blog section here */}
        <Contact />
        <Footer />
      </div>
    </main>
  );
}
```

3. Add a link to the blog section in the navbar:

```jsx
const navLinks = [
  { name: 'Home', to: 'hero', offset: -100 },
  { name: 'About', to: 'about', offset: -80 },
  { name: 'Services', to: 'services', offset: -80 },
  { name: 'Portfolio', to: 'portfolio', offset: -80 },
  { name: 'Blog', to: 'blog', offset: -80 }, // Add this line
  { name: 'Contact', to: 'contact', offset: -80 },
];
```

### Adding a Testimonials Section

If you want to add a testimonials section:

1. Create a new component in `src/components/sections/testimonials.jsx`:

```jsx
import React from 'react';
import { motion } from 'framer-motion';
import SectionHeading from '../section-heading';
import {
  Carousel,
  CarouselContent,
  CarouselItem,
  CarouselNext,
  CarouselPrevious,
} from "../ui/carousel";
import { Card, CardContent } from '../ui/card';
import { Avatar, AvatarFallback, AvatarImage } from '../ui/avatar';
import { Quote } from 'lucide-react';

const testimonials = [
  {
    id: 1,
    name: 'Client Name',
    position: 'Position, Company',
    avatar: 'https://example.com/avatar1.jpg',
    text: 'Testimonial text...',
  },
  // Add more testimonials...
];

export default function Testimonials() {
  return (
    <section id="testimonials" className="py-20">
      <div className="container px-4 mx-auto">
        <SectionHeading 
          title="Testimonials" 
          subtitle="What my clients say about me"
        />
        
        <motion.div
          initial={{ opacity: 0 }}
          whileInView={{ opacity: 1 }}
          transition={{ duration: 0.5 }}
          viewport={{ once: true }}
          className="max-w-5xl mx-auto"
        >
          <Carousel
            opts={{
              align: "start",
              loop: true,
            }}
            className="w-full"
          >
            <CarouselContent>
              {testimonials.map((testimonial) => (
                <CarouselItem key={testimonial.id} className="md:basis-1/2 lg:basis-1/3 pl-4">
                  <Card className="h-full">
                    <CardContent className="p-6 flex flex-col h-full">
                      <Quote className="h-8 w-8 text-primary mb-4" />
                      <p className="text-muted-foreground mb-6 flex-grow">"{testimonial.text}"</p>
                      <div className="flex items-center">
                        <Avatar className="h-12 w-12 mr-4">
                          <AvatarImage src={testimonial.avatar} alt={testimonial.name} />
                          <AvatarFallback>{testimonial.name.charAt(0)}</AvatarFallback>
                        </Avatar>
                        <div>
                          <p className="font-medium">{testimonial.name}</p>
                          <p className="text-sm text-muted-foreground">{testimonial.position}</p>
                        </div>
                      </div>
                    </CardContent>
                  </Card>
                </CarouselItem>
              ))}
            </CarouselContent>
            <div className="flex justify-center mt-8 gap-2">
              <CarouselPrevious className="relative static" />
              <CarouselNext className="relative static" />
            </div>
          </Carousel>
        </motion.div>
      </div>
    </section>
  );
}
```

2. Add the testimonials section to `src/App.jsx`:

```jsx
import Testimonials from './components/sections/testimonials';

function App() {
  return (
    <main className="relative min-h-screen">
      <ParallaxBackground />
      <Navbar />
      <div className="relative z-10">
        <Hero />
        <About />
        <Services />
        <Portfolio />
        <Skills />
        <Testimonials /> {/* Add the testimonials section here */}
        <Contact />
        <Footer />
      </div>
    </main>
  );
}
```

3. Add a link to the testimonials section in the navbar if desired.

## Advanced Customization

### Customizing the Interactive Background

The interactive background is implemented in `src/components/parallax-background.jsx`. You can customize it by modifying the following parameters:

```jsx
// Change the number of particles
function ParticleField({ count = 5000 }) {
  // ...
}

// Change the ```jsx
// Change the particle size and color
<PointMaterial
  transparent
  color={theme === 'dark' ? '#ffffff' : '#000000'}
  size={0.02} // Change this value to adjust particle size
  sizeAttenuation={true}
  depthWrite={false}
/>

// Change the parallax effect intensity
containerRef.current.style.transform = `translateX(${x * 20}px) translateY(${y * 20}px)`;
// Increase or decrease the multiplier (20) to adjust the intensity
```

### Creating Custom UI Components

You can create custom UI components to extend the template's functionality. Here's an example of creating a custom card component:

```jsx
// src/components/ui/custom-card.jsx
import React from 'react';
import { cn } from '../../lib/utils';

export function CustomCard({ className, children, ...props }) {
  return (
    <div
      className={cn(
        "bg-card text-card-foreground rounded-lg border shadow-sm hover:shadow-md transition-shadow duration-300",
        className
      )}
      {...props}
    >
      {children}
    </div>
  );
}

export function CustomCardHeader({ className, children, ...props }) {
  return (
    <div
      className={cn("p-6 flex flex-col space-y-1.5", className)}
      {...props}
    >
      {children}
    </div>
  );
}

export function CustomCardContent({ className, children, ...props }) {
  return (
    <div className={cn("p-6 pt-0", className)} {...props}>
      {children}
    </div>
  );
}

export function CustomCardFooter({ className, children, ...props }) {
  return (
    <div
      className={cn("p-6 pt-0 flex items-center", className)}
      {...props}
    >
      {children}
    </div>
  );
}
```

### Adding Page Transitions

You can enhance the user experience by adding page transitions between sections:

1. Create a custom hook for section transitions:

```jsx
// src/hooks/use-section-transition.js
import { useEffect } from 'react';
import { useLocation } from 'react-router-dom';
import { animate } from 'framer-motion';

export function useSectionTransition() {
  const { hash } = useLocation();
  
  useEffect(() => {
    if (hash) {
      const targetElement = document.querySelector(hash);
      if (targetElement) {
        // Scroll to the element with a smooth animation
        window.scrollTo({
          top: targetElement.offsetTop - 80,
          behavior: 'smooth'
        });
        
        // Add a highlight animation to the section
        animate(
          targetElement,
          { scale: [1, 1.02, 1] },
          { duration: 0.5 }
        );
      }
    }
  }, [hash]);
}
```

2. Use the hook in your App component:

```jsx
import { useSectionTransition } from './hooks/use-section-transition';

function App() {
  useSectionTransition();
  
  return (
    // ...
  );
}
```

### Implementing a Contact Form with Backend Integration

To make the contact form functional with a backend service:

1. Update the `onSubmit` function in `src/components/sections/contact.jsx`:

```jsx
function onSubmit(values) {
  setIsSubmitting(true);
  
  // Send form data to your backend API
  fetch('https://your-api-endpoint.com/contact', {
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
        throw new Error('Failed to send message');
      }
    })
    .catch(error => {
      console.error('Error sending message:', error);
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

2. Alternatively, use a form service like Formspree:

```jsx
function onSubmit(values) {
  setIsSubmitting(true);
  
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
        throw new Error('Failed to send message');
      }
    })
    .catch(error => {
      console.error('Error sending message:', error);
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

### Adding Analytics

To add Google Analytics to your portfolio:

1. Create a new file `src/lib/analytics.js`:

```js
// Initialize Google Analytics
export const initGA = (measurementId) => {
  if (typeof window !== 'undefined') {
    // Add Google Analytics script
    const script = document.createElement('script');
    script.src = `https://www.googletagmanager.com/gtag/js?id=${measurementId}`;
    script.async = true;
    document.head.appendChild(script);
    
    // Initialize Google Analytics
    window.dataLayer = window.dataLayer || [];
    function gtag() {
      window.dataLayer.push(arguments);
    }
    gtag('js', new Date());
    gtag('config', measurementId);
    
    // Make gtag available globally
    window.gtag = gtag;
  }
};

// Track page views
export const pageview = (url) => {
  if (typeof window !== 'undefined' && window.gtag) {
    window.gtag('config', 'G-XXXXXXXXXX', {
      page_path: url,
    });
  }
};

// Track events
export const event = ({ action, category, label, value }) => {
  if (typeof window !== 'undefined' && window.gtag) {
    window.gtag('event', action, {
      event_category: category,
      event_label: label,
      value: value,
    });
  }
};
```

2. Initialize Google Analytics in your main component:

```jsx
// src/main.jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App.jsx';
import './index.css';
import { ThemeProvider } from './components/theme-provider';
import { Toaster } from './components/ui/toaster';
import { initGA } from './lib/analytics';

// Initialize Google Analytics with your measurement ID
initGA('G-XXXXXXXXXX');

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <ThemeProvider
      attribute="class"
      defaultTheme="system"
      enableSystem
      disableTransitionOnChange
    >
      <App />
      <Toaster />
    </ThemeProvider>
  </React.StrictMode>,
);
```

3. Track events in your components:

```jsx
import { event } from '../lib/analytics';

// In a component
const handleContactSubmit = () => {
  // Track the contact form submission
  event({
    action: 'submit_form',
    category: 'Contact',
    label: 'Contact Form',
  });
  
  // Rest of your code...
};
```

This completes the customization guide for Portfolio Pro. By following these instructions, you can fully customize the template to match your personal brand and showcase your work effectively.