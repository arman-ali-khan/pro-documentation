# Portfolio Pro Components Documentation

This document provides detailed information about the components used in the Portfolio Pro template, their props, and usage examples.

## Table of Contents

1. [UI Components](#ui-components)
   - [Button](#button)
   - [Card](#card)
   - [Dialog](#dialog)
   - [Form](#form)
   - [Toast](#toast)
   - [Tabs](#tabs)
   - [Carousel](#carousel)
   - [Progress](#progress)
   - [Badge](#badge)
   - [Avatar](#avatar)
2. [Layout Components](#layout-components)
   - [Navbar](#navbar)
   - [Footer](#footer)
   - [ParallaxBackground](#parallaxbackground)
   - [SectionHeading](#sectionheading)
3. [Section Components](#section-components)
   - [Hero](#hero)
   - [About](#about)
   - [Services](#services)
   - [Portfolio](#portfolio)
   - [Skills](#skills)
   - [Contact](#contact)
4. [Hooks and Context Providers](#hooks-and-context-providers)
   - [ThemeProvider](#themeprovider)
   - [ToastProvider](#toastprovider)

## UI Components

### Button

A versatile button component with multiple variants and sizes.

**Props:**
- `variant`: The button style variant (`default`, `destructive`, `outline`, `secondary`, `ghost`, `link`)
- `size`: The button size (`default`, `sm`, `lg`, `icon`)
- `asChild`: Boolean to render the button as a child component
- `className`: Additional CSS classes
- `disabled`: Boolean to disable the button
- `children`: Button content

**Example:**
```jsx
import { Button } from './components/ui/button';

<Button variant="default" size="default">
  Click Me
</Button>

<Button variant="outline" size="lg">
  Large Button
</Button>

<Button variant="ghost" size="icon">
  <Icon />
</Button>

<Button asChild>
  <a href="https://example.com">Link Button</a>
</Button>
```

### Card

A container component for displaying content in a card format.

**Components:**
- `Card`: The main card container
- `CardHeader`: The card header section
- `CardTitle`: The card title
- `CardDescription`: The card description
- `CardContent`: The card content section
- `CardFooter`: The card footer section

**Example:**
```jsx
import {
  Card,
  CardHeader,
  CardTitle,
  CardDescription,
  CardContent,
  CardFooter
} from './components/ui/card';

<Card>
  <CardHeader>
    <CardTitle>Card Title</CardTitle>
    <CardDescription>Card description</CardDescription>
  </CardHeader>
  <CardContent>
    <p>Card content goes here</p>
  </CardContent>
  <CardFooter>
    <Button>Action</Button>
  </CardFooter>
</Card>
```

### Dialog

A modal dialog component for displaying additional content.

**Components:**
- `Dialog`: The main dialog container
- `DialogTrigger`: The element that triggers the dialog
- `DialogContent`: The dialog content container
- `DialogHeader`: The dialog header section
- `DialogTitle`: The dialog title
- `DialogDescription`: The dialog description
- `DialogFooter`: The dialog footer section
- `DialogClose`: The dialog close button

**Example:**
```jsx
import {
  Dialog,
  DialogTrigger,
  DialogContent,
  DialogHeader,
  DialogTitle,
  DialogDescription,
  DialogFooter,
  DialogClose
} from './components/ui/dialog';

<Dialog>
  <DialogTrigger asChild>
    <Button>Open Dialog</Button>
  </DialogTrigger>
  <DialogContent>
    <DialogHeader>
      <DialogTitle>Dialog Title</DialogTitle>
      <DialogDescription>Dialog description</DialogDescription>
    </DialogHeader>
    <div>Dialog content goes here</div>
    <DialogFooter>
      <Button>Action</Button>
      <DialogClose asChild>
        <Button variant="outline">Cancel</Button>
      </DialogClose>
    </DialogFooter>
  </DialogContent>
</Dialog>
```

### Form

Form components with validation support using React Hook Form.

**Components:**
- `Form`: The main form container
- `FormField`: The form field container
- `FormItem`: The form item container
- `FormLabel`: The form label
- `FormControl`: The form control container
- `FormDescription`: The form field description
- `FormMessage`: The form field error message

**Example:**
```jsx
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import * as z from 'zod';
import {
  Form,
  FormField,
  FormItem,
  FormLabel,
  FormControl,
  FormDescription,
  FormMessage
} from './components/ui/form';
import { Input } from './components/ui/input';
import { Button } from './components/ui/button';

const formSchema = z.object({
  name: z.string().min(2, { message: 'Name must be at least 2 characters.' }),
  email: z.string().email({ message: 'Please enter a valid email address.' }),
});

function FormExample() {
  const form = useForm({
    resolver: zodResolver(formSchema),
    defaultValues: {
      name: '',
      email: '',
    },
  });

  function onSubmit(values) {
    console.log(values);
  }

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-6">
        <FormField
          control={form.control}
          name="name"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Name</FormLabel>
              <FormControl>
                <Input placeholder="Your name" {...field} />
              </FormControl>
              <FormDescription>Enter your full name.</FormDescription>
              <FormMessage />
            </FormItem>
          )}
        />
        <FormField
          control={form.control}
          name="email"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Email</FormLabel>
              <FormControl>
                <Input placeholder="Your email" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />
        <Button type="submit">Submit</Button>
      </form>
    </Form>
  );
}
```

### Toast

Notification component for displaying messages.

**Components:**
- `ToastProvider`: The toast provider component
- `ToastViewport`: The toast viewport container
- `Toast`: The toast component
- `ToastTitle`: The toast title
- `ToastDescription`: The toast description
- `ToastAction`: The toast action button
- `ToastClose`: The toast close button

**Example:**
```jsx
import { useToast } from '../hooks/use-toast';
import { Button } from './components/ui/button';

function ToastExample() {
  const { toast } = useToast();

  const showToast = () => {
    toast({
      title: "Success!",
      description: "Your action was completed successfully.",
      variant: "default", // or "destructive"
    });
  };

  return (
    <Button onClick={showToast}>Show Toast</Button>
  );
}
```

### Tabs

Tabbed interface component for organizing content.

**Components:**
- `Tabs`: The main tabs container
- `TabsList`: The tabs list container
- `TabsTrigger`: The tab trigger button
- `TabsContent`: The tab content container

**Example:**
```jsx
import { Tabs, TabsList, TabsTrigger, TabsContent } from './components/ui/tabs';

<Tabs defaultValue="tab1">
  <TabsList>
    <TabsTrigger value="tab1">Tab 1</TabsTrigger>
    <TabsTrigger value="tab2">Tab 2</TabsTrigger>
    <TabsTrigger value="tab3">Tab 3</TabsTrigger>
  </TabsList>
  <TabsContent value="tab1">
    <p>Content for Tab 1</p>
  </TabsContent>
  <TabsContent value="tab2">
    <p>Content for Tab 2</p>
  </TabsContent>
  <TabsContent value="tab3">
    <p>Content for Tab 3</p>
  </TabsContent>
</Tabs>
```

### Carousel

Slideshow component for displaying multiple items.

**Components:**
- `Carousel`: The main carousel container
- `CarouselContent`: The carousel content container
- `CarouselItem`: The carousel item container
- `CarouselPrevious`: The previous button
- `CarouselNext`: The next button

**Example:**
```jsx
import {
  Carousel,
  CarouselContent,
  CarouselItem,
  CarouselPrevious,
  CarouselNext
} from './components/ui/carousel';

<Carousel>
  <CarouselContent>
    <CarouselItem>
      <div>Slide 1</div>
    </CarouselItem>
    <CarouselItem>
      <div>Slide 2</div>
    </CarouselItem>
    <CarouselItem>
      <div>Slide 3</div>
    </CarouselItem>
  </CarouselContent>
  <CarouselPrevious />
  <CarouselNext />
</Carousel>
```

### Progress

Progress bar component for visualizing data.

**Props:**
- `value`: The progress value (0-100)
- `className`: Additional CSS classes

**Example:**
```jsx
import { Progress } from './components/ui/progress';

<Progress value={75} className="h-2" />
```

### Badge

Label component for displaying metadata.

**Props:**
- `variant`: The badge style variant (`default`, `secondary`, `destructive`, `outline`)
- `className`: Additional CSS classes
- `children`: Badge content

**Example:**
```jsx
import { Badge } from './components/ui/badge';

<Badge>Default</Badge>
<Badge variant="secondary">Secondary</Badge>
<Badge variant="destructive">Destructive</Badge>
<Badge variant="outline">Outline</Badge>
```

### Avatar

User avatar component.

**Components:**
- `Avatar`: The main avatar container
- `AvatarImage`: The avatar image
- `AvatarFallback`: The avatar fallback content

**Example:**
```jsx
import { Avatar, AvatarImage, AvatarFallback } from './components/ui/avatar';

<Avatar>
  <AvatarImage src="https://example.com/avatar.jpg" alt="User Name" />
  <AvatarFallback>UN</AvatarFallback>
</Avatar>
```

## Layout Components

### Navbar

Navigation bar component with responsive mobile menu.

**Props:**
- None (uses internal state for mobile menu and scroll behavior)

**Example:**
```jsx
import Navbar from './components/navbar';

<Navbar />
```

**Customization:**
- Update the `navLinks` array to customize the navigation links
- Modify the logo/brand name
- Adjust the mobile menu behavior

### Footer

Page footer component with contact information and links.

**Props:**
- None

**Example:**
```jsx
import Footer from './components/footer';

<Footer />
```

**Customization:**
- Update the contact information
- Modify the social media links
- Adjust the copyright text and year

### ParallaxBackground

Interactive background component with 3D particles.

**Props:**
- None (uses internal state for mouse movement)

**Example:**
```jsx
import ParallaxBackground from './components/parallax-background';

<ParallaxBackground />
```

**Customization:**
- Adjust the particle count, size, and color
- Modify the parallax effect intensity
- Change the animation behavior

### SectionHeading

Consistent heading style for all sections.

**Props:**
- `title`: The section title
- `subtitle`: The section subtitle (optional)
- `className`: Additional CSS classes

**Example:**
```jsx
import SectionHeading from './components/section-heading';

<SectionHeading 
  title="Section Title" 
  subtitle="Section subtitle text"
/>
```

## Section Components

### Hero

The first section visitors see, featuring your name, profession, and call-to-action buttons.

**Props:**
- None

**Example:**
```jsx
import Hero from './components/sections/hero';

<Hero />
```

**Customization:**
- Update the name, profession, and description
- Modify the call-to-action buttons
- Change the profile image
- Adjust the social media links

### About

Detailed information about you and your background.

**Props:**
- None

**Example:**
```jsx
import About from './components/sections/about';

<About />
```

**Customization:**
- Update the about text and personal details
- Modify the profile image
- Change the resume/CV download link
- Adjust the contact button

### Services

Showcase of services you offer.

**Props:**
- None

**Example:**
```jsx
import Services from './components/sections/services';

<Services />
```

**Customization:**
- Update the services array with your own services
- Modify the service icons
- Change the service descriptions
- Adjust the request service button

### Portfolio

Gallery of your projects with filtering options.

**Props:**
- None

**Example:**
```jsx
import Portfolio from './components/sections/portfolio';

<Portfolio />
```

**Customization:**
- Update the projects array with your own projects
- Modify the project categories and filters
- Change the project images
- Adjust the project details modal

### Skills

Display of your technical skills with progress bars.

**Props:**
- None

**Example:**
```jsx
import Skills from './components/sections/skills';

<Skills />
```

**Customization:**
- Update the skills arrays with your own skills
- Modify the skill categories and tabs
- Change the skill levels
- Adjust the progress bar appearance

### Contact

Contact form and contact information.

**Props:**
- None

**Example:**
```jsx
import Contact from './components/sections/contact';

<Contact />
```

**Customization:**
- Update the contact information
- Modify the form fields and validation
- Change the form submission behavior
- Adjust the success/error messages

## Hooks and Context Providers

### ThemeProvider

Theme context provider for managing the light/dark theme.

**Props:**
- `children`: The child components
- `defaultTheme`: The default theme (`light`, `dark`, `system`)
- `storageKey`: The local storage key for saving the theme preference

**Example:**
```jsx
import { ThemeProvider } from './components/theme-provider';

<ThemeProvider defaultTheme="system" storageKey="theme-preference">
  <App />
</ThemeProvider>
```

**Usage:**
```jsx
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

### ToastProvider

Toast context provider for managing toast notifications.

**Props:**
- `children`: The child components

**Example:**
```jsx
import { ToastProvider } from './components/ui/toast';
import { Toaster } from './components/ui/toaster';

<ToastProvider>
  <App />
  <Toaster />
</ToastProvider>
```

**Usage:**
```jsx
import { useToast } from '../hooks/use-toast';

function ToastExample() {
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

This completes the components documentation for Portfolio Pro. Each component is designed to be modular and customizable, allowing you to create a unique portfolio that showcases your work effectively.