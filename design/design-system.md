# 🧑‍🎨 Design system

- [🧑‍🎨 Design system](#-design-system)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📝 Overview](#-overview)
  - [🎨 Style Guide](#-style-guide)
    - [🗼 Hierarchy of design tokens](#-hierarchy-of-design-tokens)
    - [🌈 Colors](#-colors)
    - [🔤 Typography](#-typography)
    - [🫂 Spacing](#-spacing)
    - [Shadow, Borders, Radius, and etc](#shadow-borders-radius-and-etc)
  - [🧱 Component library](#-component-library)
    - [🧐 Why do we need a component library?](#-why-do-we-need-a-component-library)
    - [Key Elements of a Component Library](#key-elements-of-a-component-library)
    - [Component Categories](#component-categories)
  - [📚 Documentation](#-documentation)
  - [That's it for now 😇](#thats-it-for-now-)

## 👀 Fast Lookup

- **Design System**: Collection of reusable components, guidelines, and best practices for consistent UI/UX
- **Design Tokens**: Variables storing design values (colors, spacing, typography) organized in 3-level hierarchy
- **Token Hierarchy**: Global/Base → Semantic/Alias → Component-Specific
- **Style Guide**: Visual identifiers defining look and feel (colors, typography, spacing, shadows, etc.)
- **Component Library**: Reusable UI components for consistent development
- **Color Categories**: Global scales → Semantic meanings → Component-specific applications
- **Typography Tokens**: Font family, size, weight, line height, letter spacing
- **Spacing System**: Consistent distances, margins, and padding using scale values
- **Documentation**: Comprehensive guide explaining usage, best practices, and implementation
- **Benefits**: Consistency, efficiency, collaboration, scalability, maintainability

## 📝 Overview

**What is a design system?:**

The foundation of the project's Look and Feel

A design system is a collection of reusable components, guidelines, and best practices that help teams create consistent and cohesive UI/UX for products. It is like a coding convention (naming, structure, etc.) but for design.

It includes:

- **Style guide**: A document that outlines the visual and interaction design principles, including typography, color palette, spacing, shadows, radius, and etc. Design tokens are often used to define these elements in a consistent way.
- **Component library**: A collection of pre-built UI components that can be used to build applications quickly and consistently.
- **Documentation**: A comprehensive guide that explains why design decisions were made, how to use the components, and best practices for implementing the design system.

**Why do we need a design system?**

- **Consistency**: A design system ensures that all components and patterns are consistent across the product, which helps create a cohesive user experience.
- **Efficiency**: By reusing components and patterns, teams can save time and effort in the design and development process.
- **Collaboration**: A design system provides a common language and framework for designers and developers to work together, reducing misunderstandings and improving communication.
- **Scalability**: As products grow and evolve, a design system can help teams scale their design efforts and maintain consistency across multiple platforms and devices.

## 🎨 Style Guide

A **style guide** is a collection of **visual identifiers** that define the **look and feel** of the product. Each identifier is extracted as a **design token**—a variable that stores a specific value (such as **color**, **font size**, or **spacing**) and can be **reused** throughout the design system.

### 🗼 Hierarchy of design tokens

Design tokens are typically organized into a hierarchy, which helps maintain consistency and scalability across the design system. The hierarchy can be broken down into three main levels:

```plaintext
┌────────────────────┐
│    GLOBAL/BASE     │   Raw design tokens. `variable name - raw value` pairs
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│   SEMANTIC/ALIAS   │   Purpose-based design tokens referencing global tokens
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ COMPONENT-SPECIFIC │   UI element design tokens referencing semantic tokens
└────────────────────┘
```

This hierarchy allows for a clear and maintainable structure, where updates at higher levels automatically propagate down to lower levels. For example, changing the `primary` semantic token will update all component tokens that reference it.

I will create separate documentation for each design token category. It will contain commonly used design tokens, their purpose, and examples of how to use them. I will use `tailwindcss` design token system as a reference. The following categories will be covered:

- [Color tokens](./design-tokens/color-tokens.md)
- [Typography tokens](./design-tokens/typography-tokens.md)
- [Spacing tokens](./design-tokens/spacing-tokens.md)
- [Shadow tokens](./design-tokens/shadow-tokens.md)
- [Border tokens](./design-tokens/border-tokens.md)
- [Radius tokens](./design-tokens/radius-tokens.md)
- [Z-index tokens](./design-tokens/z-index-tokens.md)
- [Opacity tokens](./design-tokens/opacity-tokens.md)
- [Animation & Transition tokens](./design-tokens/animation-transition-tokens.md)

### 🌈 Colors

Colors are one of the most important aspects of a design system. They help create a visual hierarchy, establish brand identity, and convey meaning. Color tokens are typically organized into three main categories:

- **Global/Base Colors** with **Color Scales**: These are the **foundational colors** that can be used throughout the design system. They are typically defined using a color scale, which includes multiple shades of a color (e.g., `blue-50` to `blue-950`).
- **Semantic/Alias Colors**: These are purpose-based tokens that reference global colors. They are used to convey meaning and context in the UI, such as indicating *success*, *error*, or *warning* states. Also, they are used to define the main colors of the UI, such as `primary`, `secondary`, and `accent`.
- **Component-Specific Colors**: These are tokens that are tied to specific UI elements and their states. They are used to define the colors of buttons, cards, forms, and other components. (e.g., `button-primary-background`, `card-border`, `input-text-disabled`)

> ```plaintext
> ┌────────────────────┐
> │    GLOBAL/BASE     │   Raw color values
> │                    │   (e.g., blue-500 -> #3b82f6)
> └─────────┬──────────┘
>           │
>           ▼
> ┌────────────────────┐
> │   SEMANTIC/ALIAS   │   Purpose-based references to global tokens
> │                    │   (e.g., primary → blue-500)
> └─────────┬──────────┘
>           │
>           ▼
> ┌────────────────────┐
> │ COMPONENT-SPECIFIC │   UI element tokens referencing semantic tokens
> │                    │   (e.g., button-background → primary)
> └────────────────────┘
> ```

```css
/* Example of color tokens in CSS */
:root {
  /* Global/Neutral Colors */
  --color-gray-50: #f9fafb;
  --color-gray-100: #f3f4f6;
  ... (other gray colors)
  --color-gray-900: #111827;

  /* Semantic/Alias Colors -> Global Colors */
  --color-primary: var(--color-blue-500);
  --color-secondary: var(--color-green-500);
  --color-success: var(--color-green-500);

  /* Component-Specific Colors -> Semantic Colors */
  --color-button-primary-background: var(--color-primary);
  --color-button-secondary-background: var(--color-secondary);
}
```

### 🔤 Typography

Typography defines the text styles used throughout the design system. Typography tokens typically include:

- **Font family**: The typeface used for text (e.g., `sans-serif`, `serif`)
- **Font size**: The size of the text (e.g., `12px`, `16px`, `24px`)
- **Font weight**: The thickness of the text (e.g., `normal`, `bold`, `light`)
- **Line height**: The vertical space between lines of text (e.g., `1.5`, `2`)
- **Letter spacing**: The space between characters (e.g., `0.5px`, `1px`)
- **Text transformations**: The style of text (e.g., `uppercase`, `lowercase`, `capitalize`)
- **Text decoration**: The style of text (e.g., `underline`, `line-through`, `none`)

Typography tokens can also be organized into a hierarchy, similar to color tokens. This hierarchy includes:

- **Global/Base Typography**: The foundational text styles that can be used throughout the design system. (e.g., `font-family-base : 'Arial, sans-serif'`, `font-size-100: 12px`, `font-weight-bold: 700`)
- **Semantic Typography**: Purpose-based typography tokens that reference global typography tokens. (e.g, `typography-heading-1: font-size-700, font-weight-bold`)
- **Component-Specific Typography**: Tailored typography tokens for individual UI elements and their unique states or contexts.

> ```plaintext
> ┌────────────────────┐
> │    GLOBAL/BASE     │   Raw typography properties
> │                    │   (e.g., text-xl -> 1.25rem, font-bold -> 700)
> └─────────┬──────────┘
>           │
>           ▼
> ┌────────────────────┐
> │      SEMANTIC      │   Purpose-based typography combinations
> │                    │   (e.g., heading-2 -> font-bold, text-2xl)
> └─────────┬──────────┘
>           │
>           ▼
> ┌────────────────────┐
> │ COMPONENT-SPECIFIC │   UI element typography referencing semantic tokens
> │                    │   (e.g., button-primary-text -> heading-2)
> └────────────────────┘
> ```

### 🫂 Spacing

Spacing is crucial for creating consistent layouts and component spacing. It defines the distances between elements, margins, and padding to ensure a harmonious design.

- **Global/Base Spacing**: The foundational spacing values that can be used throughout the design system. Spacing tokens are typically defined using a scale value like colors. (e.g., `spacing-0: 0rem`, `spacing-1: 0.25rem`, `spacing-2: 0.5rem`)
- **Semantic Spacing**: Purpose-based spacing tokens that reference global spacing tokens. (e.g., `spacing-section: spacing-4`, `spacing-element-gap-sm: spacing-2`)
- **Component-Specific Spacing**: Tailored spacing tokens for individual UI elements and their unique states or contexts. (e.g., `button-padding: spacing-2`, `card-margin: spacing-4`)

> There are some gray areas between semantic and component-specific tokens. Let's just be flexible during the design process and use our best judgment. The goal is to create a consistent and harmonious design system.

### Shadow, Borders, Radius, and etc

- **Shadows**: Shadow tokens define the **depth** and **elevation** of UI elements.
  - **Offset**: How far the shadow extends (x and y offsets)
  - **Blur radius**: How soft or diffuse the shadow appears
  - **Spread radius**: How much the shadow expands or contracts
  - **Color**: The color of the shadow

- **Borders**: Border tokens define the **thickness**, **style**, and **color** of borders around UI elements.
  - **Width**: The thickness of the border (e.g., `1px`, `2px`)
  - **Style**: The style of the border (e.g., `solid`, `dashed`)
  - **Color**: The color of the border

- **Radius**: Radius tokens define the **corner radius** of UI elements, which affects the roundness of corners.
- **Z-index**: Z-index tokens define the **stacking order** of UI elements. They are used to control which elements appear on top of others.
- **Opacity**: Opacity tokens define the **transparency** of UI elements. They are typically defined as a percentage (e.g., `0%`, `50%`, `100%`).
- **Animation & Transition**: Animation and transition tokens define the **timing**, **duration**, and **easing** of animations and transitions applied to UI elements.

```css
/* Shadow token examples ---------------------------------------------------- */

/* Global/Base shadows */
--shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.1);
--shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);
--shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1); 

/* Alias/Semantic && Component-specific shadows */
--shadow-button: var(--shadow-md);
--shadow-card: var(--shadow-lg);
--shadow-modal: var(--shadow-lg);

/* Border token examples ---------------------------------------------------- */

/* Global/Base borders */
--border-width-sm: 1px;
--border-width-md: 2px;
--border-style-solid: solid;
--border-style-dashed: dashed;

/* Alias/Semantic && Component-specific borders */
--border-button-primary: var(--border-width-md) var(--border-style-solid) var(--color-primary);
--border-card: var(--border-width-sm) var(--border-style-solid) var(--color-gray-300);
--border-input: var(--border-width-sm) var(--border-style-solid) var(--color-gray-400);

/* Radius token examples ---------------------------------------------------- */

/* Global/Base radius */
--radius-xs: 0.125rem; /* 2px */
--radius-sm: 0.25rem; /* 4px */
/* ... */
--radius-2xl: 1.5rem; /* 24px */
--radius-full: 9999px; /* Fully rounded */

/* Alias/Semantic && Component-specific radius */
--radius-button: var(--radius-sm);
--radius-card: var(--radius-md);
--radius-input: var(--radius-xs);

```

## 🧱 Component library

Component library is a **collection** of reusable **UI components** that can be used to build applications quickly and consistently.

### 🧐 Why do we need a component library?

- **Consistency**: A component library ensures that all components are consistent in design and behavior, which helps create a cohesive user experience.
- **Efficiency**: Developers don't need to rebuild common elements from scratch each time, dramatically speeding up development.
- **Collaboration**: They create a shared language between designers and developers, improving communication and workflow.
- **Maintenance**: When you need to update a component, you can do it in one place and the change propagates everywhere it's used.
- **Scalability**: As your product grows, having standardized components makes it easier to maintain quality across an expanding interface.

### Key Elements of a Component Library

A well-structured component library typically includes:

- **Core Components**: Basic building blocks like buttons, inputs, icons, typography, and color systems.
- **Composite Components**: More complex elements built from core components, like forms, navigation bars, modals, etc.
- **Documentation**: Clear guidelines on how and when to use each component.
- **State Variations**: Different states for components (hover, active, disabled, error, etc.).
- **Responsive Behavior**: How components adapt to different screen sizes.

### Component Categories

- **Basic/General**: These are the building blocks of the design system. (e.g., Button, Avatar, Badge)
- **Forms**: Components that are used to collect user input. (e.g., Input, Select, Checkbox)
- **Data Display**: Components that are used to display data. (e.g., Table, Card, Tag, Tooltip, Accordion)
- **Feedback/Status**: Components that provide feedback to the user. (e.g., Alert, Spinner, Progress Bar, Toast, Modal, Dialog)
- **Navigation**: Components that facilitate user navigation within the application. (e.g., Tabs, Breadcrumbs, Pagination, Header, Footer)
- **Layout**: Components that help structure the layout of the application. (e.g., Grid, Stack, Container, Spacer)

## 📚 Documentation

Documentation is a `man` page that explains how to use the design system.

In the documentation, I will cover the following topics:

- **Introduction and Getting Started**: An overview of the design system and how to get started using it.
- **Design Principles and Philosophy**
  - Core values & Brand identity
  - Overall design objectives (e.g., Consistency, Accessibility, Usability)
  - Accessibility guidelines
  - Content Guidelines (e.g., Tone of voice, Writing style)
- **Design Tokens**: A detailed explanation of design tokens, their hierarchy, and how to use them.
- **Component Library**: A detailed explanation of the component library, its structure, and how to use it.
  - Component library overview(What is it? How to browse/search?)
  - Component categories
  - `Specific component` documentation
    - Component description and purpose
    - Live demo and Examples
    - API (Props)
    - Usage guidelines
    - Best practices

And more...

## That's it for now 😇

This is a work in progress. I will add more details and examples as I go along.
