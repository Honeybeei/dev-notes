# 🌈 Color Tokens

- [🌈 Color Tokens](#-color-tokens)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🏛️ Global/Base Color Tokens](#️-globalbase-color-tokens)
    - [🌑 Neutral Colors (Gray Scale)](#-neutral-colors-gray-scale)
    - [🎨 Brand Colors](#-brand-colors)
    - [🚦 Semantic Colors](#-semantic-colors)
    - [📊 TailwindCSS Color Scale Reference](#-tailwindcss-color-scale-reference)
  - [🏷️ Semantic/Alias Tokens](#️-semanticalias-tokens)
    - [🎯 Primary \& Secondary Colors](#-primary--secondary-colors)
    - [⚠️ Status Colors](#️-status-colors)
    - [🖼️ Surface \& Background Colors](#️-surface--background-colors)
    - [📝 Text Colors](#-text-colors)
    - [🔗 Border Colors](#-border-colors)
  - [🧩 Component-Specific Tokens](#-component-specific-tokens)
    - [🔘 Button Colors](#-button-colors)
    - [📄 Card Colors](#-card-colors)
    - [📝 Input Colors](#-input-colors)
    - [🏷️ Badge Colors](#️-badge-colors)
  - [🌓 Dark Mode Support](#-dark-mode-support)
  - [♿ Accessibility Guidelines](#-accessibility-guidelines)
    - [Contrast Ratios (WCAG 2.1 AA)](#contrast-ratios-wcag-21-aa)
    - [Color Usage Best Practices](#color-usage-best-practices)
    - [Focus Indicators](#focus-indicators)
  - [💡 Best Practices](#-best-practices)
    - [1. Token Usage Hierarchy](#1-token-usage-hierarchy)
    - [2. HSL vs RGB](#2-hsl-vs-rgb)
    - [3. Naming Conventions](#3-naming-conventions)
    - [4. Documentation](#4-documentation)

## 👀 Fast Lookup

- **Color Scale**: 50 (lightest) to 950 (darkest) following TailwindCSS convention
- **Neutral Colors**: Gray scale for backgrounds, text, and borders
- **Brand Colors**: Primary (blue), secondary (gray), accent colors
- **Semantic Colors**: Success (green), destructive/error (red), warning (yellow), info (blue)
- **ShadCN-UI Pattern**: Uses CSS custom properties with HSL values
- **Token Hierarchy**: Global scales → Semantic meanings → Component applications
- **Dark Mode**: Automatic theme switching using CSS custom properties
- **Accessibility**: WCAG 2.1 AA contrast ratios (4.5:1 text, 3:1 UI)
- **Format**: `--color-{category}-{scale}` for global, `--{semantic-name}` for aliases
- **Components**: Button, card, input, badge variations with state-specific tokens

## 🏛️ Global/Base Color Tokens

Global color tokens follow the TailwindCSS scale system (50-950) and serve as the foundation for all other color tokens. These are the raw color values that should not be used directly in components.

### 🌑 Neutral Colors (Gray Scale)

Neutral colors are essential for creating hierarchy, backgrounds, text, and borders. Based on TailwindCSS `slate` and `gray` palettes:

```css
:root {
  /* Slate - Primary neutral palette */
  --color-slate-50: #f8fafc;
  --color-slate-100: #f1f5f9;
  --color-slate-200: #e2e8f0;
  --color-slate-300: #cbd5e1;
  --color-slate-400: #94a3b8;
  --color-slate-500: #64748b;
  --color-slate-600: #475569;
  --color-slate-700: #334155;
  --color-slate-800: #1e293b;
  --color-slate-900: #0f172a;
  --color-slate-950: #020617;

  /* Gray - Alternative neutral palette */
  --color-gray-50: #f9fafb;
  --color-gray-100: #f3f4f6;
  --color-gray-200: #e5e7eb;
  --color-gray-300: #d1d5db;
  --color-gray-400: #9ca3af;
  --color-gray-500: #6b7280;
  --color-gray-600: #4b5563;
  --color-gray-700: #374151;
  --color-gray-800: #1f2937;
  --color-gray-900: #111827;
  --color-gray-950: #030712;
}
```

### 🎨 Brand Colors

Brand colors define the visual identity. Following ShadCN-UI's primary color approach:

```css
:root {
  /* Blue - Primary brand color */
  --color-blue-50: #eff6ff;
  --color-blue-100: #dbeafe;
  --color-blue-200: #bfdbfe;
  --color-blue-300: #93c5fd;
  --color-blue-400: #60a5fa;
  --color-blue-500: #3b82f6;  /* Primary brand color */
  --color-blue-600: #2563eb;
  --color-blue-700: #1d4ed8;
  --color-blue-800: #1e40af;
  --color-blue-900: #1e3a8a;
  --color-blue-950: #172554;

  /* Violet - Secondary/Accent brand color */
  --color-violet-50: #f5f3ff;
  --color-violet-100: #ede9fe;
  --color-violet-200: #ddd6fe;
  --color-violet-300: #c4b5fd;
  --color-violet-400: #a78bfa;
  --color-violet-500: #8b5cf6;
  --color-violet-600: #7c3aed;
  --color-violet-700: #6d28d9;
  --color-violet-800: #5b21b6;
  --color-violet-900: #4c1d95;
  --color-violet-950: #2e1065;
}
```

### 🚦 Semantic Colors

Colors that convey meaning and status:

```css
:root {
  /* Green - Success/Positive */
  --color-green-50: #f0fdf4;
  --color-green-100: #dcfce7;
  --color-green-200: #bbf7d0;
  --color-green-300: #86efac;
  --color-green-400: #4ade80;
  --color-green-500: #22c55e;  /* Success base */
  --color-green-600: #16a34a;
  --color-green-700: #15803d;
  --color-green-800: #166534;
  --color-green-900: #14532d;
  --color-green-950: #052e16;

  /* Red - Error/Destructive */
  --color-red-50: #fef2f2;
  --color-red-100: #fee2e2;
  --color-red-200: #fecaca;
  --color-red-300: #fca5a5;
  --color-red-400: #f87171;
  --color-red-500: #ef4444;  /* Error base */
  --color-red-600: #dc2626;
  --color-red-700: #b91c1c;
  --color-red-800: #991b1b;
  --color-red-900: #7f1d1d;
  --color-red-950: #450a0a;

  /* Yellow - Warning */
  --color-yellow-50: #fefce8;
  --color-yellow-100: #fef3c7;
  --color-yellow-200: #fde68a;
  --color-yellow-300: #fcd34d;
  --color-yellow-400: #fbbf24;
  --color-yellow-500: #f59e0b;  /* Warning base */
  --color-yellow-600: #d97706;
  --color-yellow-700: #b45309;
  --color-yellow-800: #92400e;
  --color-yellow-900: #78350f;
  --color-yellow-950: #451a03;
}
```

### 📊 TailwindCSS Color Scale Reference

| Scale | Usage | Light Mode | Dark Mode |
|-------|-------|------------|-----------|
| 50    | Subtle backgrounds | Very light tints | Dark surface highlights |
| 100   | Hover states for subtle elements | Light backgrounds | Subtle dark backgrounds |
| 200   | Borders, dividers | Soft borders | Medium dark borders |
| 300   | Disabled text, placeholder | Light gray text | Dark gray text |
| 400   | Secondary text | Medium gray text | Light gray text |
| 500   | **Primary color** | Base brand color | Base brand color |
| 600   | Primary hover states | Darker interactions | Lighter interactions |
| 700   | Primary pressed states | Dark interactions | Medium interactions |
| 800   | High contrast text | Very dark text | Light text |
| 900   | Highest contrast | Near black | Near white |
| 950   | Maximum contrast | Darkest possible | Lightest possible |

## 🏷️ Semantic/Alias Tokens

Semantic tokens provide meaning and context. Following ShadCN-UI's HSL-based approach:

### 🎯 Primary & Secondary Colors

```css
:root {
  /* ShadCN-UI style semantic tokens */
  --primary: 221.2 83.2% 53.3%;        /* blue-600 in HSL */
  --primary-foreground: 210 40% 98%;    /* white/near-white text on primary */
  
  --secondary: 210 40% 96%;             /* slate-100 background */
  --secondary-foreground: 222.2 84% 4.9%; /* slate-900 text */
  
  --accent: 210 40% 96%;                /* Same as secondary */
  --accent-foreground: 222.2 84% 4.9%; /* Dark text on accent */
}

/* Traditional approach (alternative) */
:root {
  --color-primary: var(--color-blue-600);
  --color-primary-hover: var(--color-blue-700);
  --color-primary-active: var(--color-blue-800);
  --color-primary-disabled: var(--color-blue-300);
  
  --color-secondary: var(--color-slate-600);
  --color-secondary-hover: var(--color-slate-700);
  --color-secondary-active: var(--color-slate-800);
}
```

### ⚠️ Status Colors

```css
:root {
  /* ShadCN-UI status colors */
  --destructive: 0 84.2% 60.2%;           /* red-500 */
  --destructive-foreground: 210 40% 98%;   /* white text */
  
  --success: 142.1 76.2% 36.3%;           /* green-600 */
  --success-foreground: 210 40% 98%;      /* white text */
  
  --warning: 47.9 95.8% 53.1%;            /* yellow-500 */
  --warning-foreground: 222.2 84% 4.9%;   /* dark text */
  
  --info: 221.2 83.2% 53.3%;              /* blue-600 */
  --info-foreground: 210 40% 98%;         /* white text */
}
```

### 🖼️ Surface & Background Colors

```css
:root {
  /* ShadCN-UI background system */
  --background: 0 0% 100%;                 /* white */
  --foreground: 222.2 84% 4.9%;           /* slate-900 */
  
  --card: 0 0% 100%;                       /* white */
  --card-foreground: 222.2 84% 4.9%;      /* slate-900 */
  
  --popover: 0 0% 100%;                    /* white */
  --popover-foreground: 222.2 84% 4.9%;   /* slate-900 */
  
  --muted: 210 40% 96%;                    /* slate-100 */
  --muted-foreground: 215.4 16.3% 46.9%;  /* slate-500 */
}
```

### 📝 Text Colors

```css
:root {
  /* Text hierarchy */
  --text-primary: var(--color-slate-900);      /* High contrast */
  --text-secondary: var(--color-slate-600);    /* Medium contrast */
  --text-tertiary: var(--color-slate-500);     /* Low contrast */
  --text-disabled: var(--color-slate-400);     /* Disabled state */
  --text-inverse: var(--color-white);          /* Text on dark backgrounds */
  --text-link: var(--color-blue-600);          /* Link color */
  --text-link-hover: var(--color-blue-700);    /* Link hover */
}
```

### 🔗 Border Colors

```css
:root {
  /* ShadCN-UI border system */
  --border: 214.3 31.8% 91.4%;            /* slate-200 */
  --input: 214.3 31.8% 91.4%;             /* slate-200 */
  --ring: 221.2 83.2% 53.3%;              /* blue-600 for focus rings */
  
  /* Traditional border hierarchy */
  --border-subtle: var(--color-slate-200);     /* Light borders */
  --border-default: var(--color-slate-300);    /* Default borders */
  --border-strong: var(--color-slate-400);     /* Emphasized borders */
  --border-interactive: var(--color-blue-500); /* Interactive elements */
}
```

## 🧩 Component-Specific Tokens

Component tokens reference semantic tokens and provide specific styling for UI elements:

### 🔘 Button Colors

```css
:root {
  /* Primary Button */
  --button-primary-bg: hsl(var(--primary));
  --button-primary-fg: hsl(var(--primary-foreground));
  --button-primary-hover: hsl(var(--primary)) / 0.9;
  --button-primary-active: hsl(var(--primary)) / 0.8;
  --button-primary-disabled: hsl(var(--muted));
  
  /* Secondary Button */
  --button-secondary-bg: hsl(var(--secondary));
  --button-secondary-fg: hsl(var(--secondary-foreground));
  --button-secondary-hover: hsl(var(--secondary)) / 0.8;
  --button-secondary-border: hsl(var(--border));
  
  /* Destructive Button */
  --button-destructive-bg: hsl(var(--destructive));
  --button-destructive-fg: hsl(var(--destructive-foreground));
  --button-destructive-hover: hsl(var(--destructive)) / 0.9;
  
  /* Ghost Button */
  --button-ghost-bg: transparent;
  --button-ghost-fg: hsl(var(--foreground));
  --button-ghost-hover: hsl(var(--accent));
  
  /* Outline Button */
  --button-outline-bg: hsl(var(--background));
  --button-outline-fg: hsl(var(--foreground));
  --button-outline-border: hsl(var(--border));
  --button-outline-hover: hsl(var(--accent));
}
```

### 📄 Card Colors

```css
:root {
  --card-bg: hsl(var(--card));
  --card-fg: hsl(var(--card-foreground));
  --card-border: hsl(var(--border));
  --card-shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1);
  
  --card-header-bg: transparent;
  --card-footer-bg: hsl(var(--muted)) / 0.5;
}
```

### 📝 Input Colors

```css
:root {
  --input-bg: hsl(var(--background));
  --input-fg: hsl(var(--foreground));
  --input-border: hsl(var(--input));
  --input-border-focus: hsl(var(--ring));
  --input-placeholder: hsl(var(--muted-foreground));
  
  /* Input states */
  --input-invalid-border: hsl(var(--destructive));
  --input-disabled-bg: hsl(var(--muted));
  --input-disabled-fg: hsl(var(--muted-foreground));
}
```

### 🏷️ Badge Colors

```css
:root {
  /* Default Badge */
  --badge-default-bg: hsl(var(--primary));
  --badge-default-fg: hsl(var(--primary-foreground));
  
  /* Secondary Badge */
  --badge-secondary-bg: hsl(var(--secondary));
  --badge-secondary-fg: hsl(var(--secondary-foreground));
  
  /* Status Badges */
  --badge-success-bg: hsl(var(--success));
  --badge-success-fg: hsl(var(--success-foreground));
  
  --badge-destructive-bg: hsl(var(--destructive));
  --badge-destructive-fg: hsl(var(--destructive-foreground));
  
  --badge-warning-bg: hsl(var(--warning));
  --badge-warning-fg: hsl(var(--warning-foreground));
  
  /* Outline Badge */
  --badge-outline-bg: transparent;
  --badge-outline-fg: hsl(var(--foreground));
  --badge-outline-border: hsl(var(--border));
}
```

## 🌓 Dark Mode Support

ShadCN-UI uses CSS custom properties for automatic dark mode switching:

```css
:root {
  /* Light mode (default) */
  --background: 0 0% 100%;
  --foreground: 222.2 84% 4.9%;
  --primary: 221.2 83.2% 53.3%;
  --primary-foreground: 210 40% 98%;
  /* ... other light mode colors */
}

.dark {
  /* Dark mode overrides */
  --background: 222.2 84% 4.9%;
  --foreground: 210 40% 98%;
  --primary: 217.2 91.2% 59.8%;
  --primary-foreground: 222.2 84% 4.9%;
  --card: 222.2 84% 4.9%;
  --card-foreground: 210 40% 98%;
  --popover: 222.2 84% 4.9%;
  --popover-foreground: 210 40% 98%;
  --secondary: 217.2 32.6% 17.5%;
  --secondary-foreground: 210 40% 98%;
  --muted: 217.2 32.6% 17.5%;
  --muted-foreground: 215 20.2% 65.1%;
  --accent: 217.2 32.6% 17.5%;
  --accent-foreground: 210 40% 98%;
  --destructive: 0 62.8% 30.6%;
  --destructive-foreground: 210 40% 98%;
  --border: 217.2 32.6% 17.5%;
  --input: 217.2 32.6% 17.5%;
  --ring: 224.3 76.3% 94.1%;
}
```

## ♿ Accessibility Guidelines

### Contrast Ratios (WCAG 2.1 AA)

- **Normal text**: Minimum 4.5:1 contrast ratio
- **Large text** (18pt+ or 14pt+ bold): Minimum 3:1 contrast ratio
- **UI components**: Minimum 3:1 contrast ratio for borders and focus indicators

### Color Usage Best Practices

```css
/* ✅ Good: Sufficient contrast */
.text-primary {
  color: var(--color-slate-900);  /* High contrast on white */
}

.text-secondary {
  color: var(--color-slate-600);  /* Medium contrast, still accessible */
}

/* ❌ Bad: Insufficient contrast */
.text-bad {
  color: var(--color-slate-400);  /* Too light for body text */
}
```

### Focus Indicators

```css
.focus-visible {
  outline: 2px solid hsl(var(--ring));
  outline-offset: 2px;
}
```

## 💡 Best Practices

### 1. Token Usage Hierarchy

```css
/* ✅ Use semantic tokens in components */
.my-component {
  background-color: hsl(var(--card));
  color: hsl(var(--card-foreground));
  border: 1px solid hsl(var(--border));
}

/* ❌ Don't use global tokens directly */
.my-component-bad {
  background-color: var(--color-slate-100);  /* Too specific */
}
```

### 2. HSL vs RGB

```css
/* ✅ ShadCN-UI approach: HSL with alpha */
.element {
  background-color: hsl(var(--primary) / 0.1);  /* 10% opacity */
}

/* ✅ Traditional approach: RGB with alpha */
.element-alt {
  background-color: rgb(from var(--color-blue-600) r g b / 0.1);
}
```

### 3. Naming Conventions

- **Global tokens**: `--color-{palette}-{scale}` (e.g., `--color-blue-500`)
- **Semantic tokens**: `--{purpose}` (e.g., `--primary`, `--destructive`)
- **Component tokens**: `--{component}-{element}-{state}` (e.g., `--button-primary-hover`)

### 4. Documentation

Always document:

- Token purpose and usage context
- Accessibility considerations
- Dark mode behavior
- Component-specific implementations
