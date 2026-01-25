# Design Guide: Ideal Customer Profile Site

This document provides comprehensive design specifications for the Ideal Customer Profile marketing site. Use this guide when creating new pages or components to maintain visual consistency.

---

## Table of Contents

1. [Brand Identity](#brand-identity)
2. [Colors](#colors)
3. [Typography](#typography)
4. [Layout & Spacing](#layout--spacing)
5. [Components](#components)
6. [Page Structure](#page-structure)
7. [Code Patterns](#code-patterns)

---

## Brand Identity

### Brand Voice
- **Professional yet approachable** - Written for B2B SaaS/AI founders
- **Data-driven** - Statistics, case studies, and frameworks
- **Action-oriented** - Clear CTAs, calculators, practical guides
- **Expert authority** - TK Kader's experience (Marketo, ToutApp)

### Logo
```html
<img src="https://www.tkkader.com/wp-content/uploads/TK_Abbreviated-Logo-on-Dark-BG-1.png"
     alt="TK Kader Logo"
     class="h-10 w-auto bg-slate-900 rounded-md p-2 shadow-sm" />
```

### Favicon
```html
<link rel="icon" href="https://www.tkkader.com/wp-content/uploads/cropped-TK-Kader-Brand-Favicon.png" sizes="32x32" />
```

---

## Colors

### Primary Palette

| Name | Tailwind Class | Hex | Usage |
|------|---------------|-----|-------|
| **Background** | `bg-[#FFFEFC]` | #FFFEFC | Page background (warm cream) |
| **Primary Red** | `bg-red-600` | #DC2626 | CTAs, accents, play buttons |
| **Primary Red Hover** | `bg-red-700` | #B91C1C | Button hover states |
| **Dark** | `bg-slate-900` | #0F172A | Calculators, dark boxes, footer |
| **Dark Secondary** | `bg-slate-800` | #1E293B | Input fields, secondary dark elements |

### Text Colors

| Name | Tailwind Class | Usage |
|------|---------------|-------|
| **Headings** | `text-slate-900` | H1, H2, H3, strong emphasis |
| **Body** | `text-slate-700` | Primary body text |
| **Secondary** | `text-slate-600` | Secondary body text, descriptions |
| **Muted** | `text-slate-500` | Labels, captions, breadcrumbs |
| **Light** | `text-slate-400` | Footer text, subtle labels |
| **Red Accent** | `text-red-600` | Links, highlights, part labels |

### Status/Accent Colors

| Purpose | Background | Border | Text |
|---------|------------|--------|------|
| **Key Takeaway** | `bg-yellow-50` | `border-yellow-400` | `text-yellow-800` |
| **Success/Green** | `bg-green-50` | `border-green-200` | `text-green-700` |
| **Info/Blue** | `bg-blue-50` | `border-blue-200` | `text-blue-700` |
| **Warning/Amber** | `bg-amber-50` | `border-amber-200` | `text-amber-700` |
| **Purple** | `bg-purple-50` | `border-purple-200` | `text-purple-700` |

### Selection
```css
selection:bg-yellow-200 selection:text-slate-900
```

---

## Typography

### Font Families

```html
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Crimson+Pro:ital,wght@0,400;0,600;0,800;1,400&family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
```

```css
/* Base styles */
body { font-family: 'Inter', sans-serif; }
h1, h2, h3, h4, h5, h6 { font-family: 'Crimson Pro', serif; }
```

### Heading Styles

| Element | Classes | Example |
|---------|---------|---------|
| **H1 (Hero)** | `text-5xl md:text-7xl font-serif font-bold text-slate-900 leading-[1.1] tracking-tight` | Page titles |
| **H1 (Main page)** | `text-6xl md:text-8xl font-serif font-bold text-slate-900 leading-[1.05] tracking-tight` | Main ICP Guide hero |
| **H2 (Section)** | `text-3xl md:text-4xl font-serif font-bold text-slate-900` | Part headers |
| **H2 (Large)** | `text-4xl md:text-5xl font-serif font-bold text-slate-900` | Main page sections |
| **H3 (Subsection)** | `text-2xl font-serif font-bold text-slate-900` | Within sections |
| **H3 (Card)** | `text-xl font-serif font-bold text-slate-900` | Card titles |

### Body Text

| Purpose | Classes |
|---------|---------|
| **Lead paragraph** | `text-xl md:text-2xl text-slate-500 font-sans font-light leading-relaxed` |
| **Body large** | `font-sans text-lg text-slate-700 leading-loose` |
| **Body regular** | `font-sans text-base text-slate-600 leading-relaxed` |
| **Body small** | `font-sans text-sm text-slate-600` |
| **Caption/Label** | `text-xs text-slate-500` |

### Special Text Styles

```html
<!-- Part Label -->
<span class="font-sans font-bold text-red-600 text-sm uppercase tracking-widest">Part 1</span>

<!-- Section Subheader -->
<h4 class="font-bold text-white uppercase tracking-wider text-xs mb-4">Section Title</h4>

<!-- Highlighted text -->
<strong class="text-slate-900 font-semibold bg-yellow-100 px-1">highlighted text</strong>

<!-- Italic quote -->
<p class="font-serif text-xl text-slate-900 leading-relaxed italic">"Quote text here"</p>

<!-- Monospace (definitions, formulas) -->
<span class="font-mono text-sm">CAC Payback = CAC / (ARPU × Margin)</span>
```

---

## Layout & Spacing

### Container Widths

| Class | Usage |
|-------|-------|
| `max-w-7xl` | Navigation, main content area with sidebar |
| `max-w-5xl` | Hero sections, footer |
| `max-w-4xl` | Article content, calculator pages |
| `max-w-3xl` | Hero text, CTA sections |
| `max-w-xl` | CTA box descriptions |

### Standard Spacing

| Size | Class | Usage |
|------|-------|-------|
| **Section gap** | `mb-16` | Between major sections |
| **Large gap** | `mb-12` | After videos, before subsections |
| **Medium gap** | `mb-8` | Between paragraphs, after headings |
| **Small gap** | `mb-6` | Within sections |
| **Tiny gap** | `mb-4` | Between related elements |

### Padding

| Context | Classes |
|---------|---------|
| **Page horizontal** | `px-4 md:px-6` |
| **Section vertical** | `py-8`, `py-12`, `py-16`, `py-20` |
| **Card padding** | `p-6`, `p-8`, `p-10` |
| **Navigation height** | `h-20` |

### Grid Layouts

```html
<!-- Two column stats -->
<div class="grid md:grid-cols-2 gap-6">

<!-- Three column footer -->
<div class="grid md:grid-cols-3 gap-10">

<!-- Two column calculator inputs -->
<div class="grid md:grid-cols-2 gap-6">
```

---

## Components

### Navigation (Sticky)

```html
<nav class="sticky top-0 z-50 bg-[#FFFEFC]/95 backdrop-blur border-b border-slate-100">
    <div class="max-w-7xl mx-auto px-6 h-20 flex items-center justify-between">
        <a href="/" class="font-black text-xl tracking-tighter flex items-center gap-2 font-sans hover:opacity-80 transition-opacity">
            <img src="..." alt="TK Kader Logo" class="h-10 w-auto bg-slate-900 rounded-md p-2 shadow-sm" />
            <span>Ideal Customer Profile<span class="text-red-600">.com</span></span>
        </a>
        <a href="..." class="hidden md:inline-flex bg-red-600 text-white px-6 py-2 rounded-full text-sm font-bold hover:bg-red-700 transition-all hover:scale-105">
            CTA Text &rarr;
        </a>
    </div>
</nav>
```

### Mobile Sticky Bottom Bar

```html
<div class="md:hidden fixed bottom-0 left-0 w-full bg-white border-t border-slate-200 p-4 z-50 flex items-center justify-between shadow-[0_-4px_10px_rgba(0,0,0,0.05)]">
    <div class="text-xs font-bold text-slate-500 font-sans">
        Short text with <span class="text-red-600">highlight</span>.
    </div>
    <a href="..." class="bg-red-600 text-white px-6 py-2 rounded-full text-sm font-bold text-center" target="_blank">
        CTA &rarr;
    </a>
</div>
```

### Breadcrumb

```html
<div class="max-w-4xl mx-auto px-6 pt-6">
    <nav class="text-sm font-sans text-slate-500">
        <a href="/" class="hover:text-red-600 transition-colors">ICP Guide</a>
        <span class="mx-2">/</span>
        <span class="text-slate-900">Current Page</span>
    </nav>
</div>
```

### Video Facade (Click-to-Load YouTube)

```html
<!-- CSS Required -->
<style>
.video-facade { cursor: pointer; position: relative; background-size: cover; background-position: center; display: flex; align-items: center; justify-content: center; overflow: hidden; border: 1px solid #e2e8f0; }
.video-facade::before { content: ''; position: absolute; inset: 0; background: rgba(0,0,0,0.1); transition: background 0.3s; pointer-events: none; }
.video-facade iframe { position: relative; z-index: 20; }
.video-facade:hover::before { background: rgba(0,0,0,0.0); }
.play-button { width: 72px; height: 72px; background: #DC2626; border-radius: 50%; display: flex; align-items: center; justify-content: center; position: relative; z-index: 10; transition: transform 0.2s; box-shadow: 0 10px 25px -5px rgba(220, 38, 38, 0.4); }
.video-facade:hover .play-button { transform: scale(1.05); }
.play-button svg { width: 32px; height: 32px; fill: white; margin-left: 4px; }
</style>

<!-- HTML -->
<div class="video-facade w-full aspect-video rounded-lg shadow-sm mb-8 bg-slate-100 group"
     style="background-image: url('https://img.youtube.com/vi/VIDEO_ID/maxresdefault.jpg');"
     onclick="this.onclick=null;this.innerHTML='<iframe class=\'w-full h-full\' src=\'https://www.youtube.com/embed/VIDEO_ID?autoplay=1\' frameborder=\'0\' allow=\'accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture\' allowfullscreen></iframe>'">
    <div class="play-button"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
</div>
```

### Key Takeaway Box (Yellow)

```html
<div class="bg-yellow-50 border-l-4 border-yellow-400 p-8 mb-16">
    <span class="font-sans font-bold text-yellow-800 text-xs uppercase tracking-widest mb-3 block">Key Takeaway</span>
    <p class="font-serif text-xl text-slate-900 leading-relaxed italic">
        "Quote or key insight goes here."
    </p>
    <p class="font-sans text-slate-600 mt-4 text-sm">— Attribution</p>
</div>
```

### Dark Info Box

```html
<div class="bg-slate-900 text-white p-6 rounded-lg">
    <p class="font-sans text-sm">
        <strong>Key insight:</strong> Supporting text goes here.
    </p>
</div>
```

### Dark Section Box (with decoration)

```html
<div class="bg-slate-900 text-white rounded-xl p-10 mb-16 shadow-2xl relative overflow-hidden">
    <div class="absolute top-0 right-0 -mr-16 -mt-16 w-64 h-64 bg-red-600 rounded-full opacity-20 blur-3xl"></div>
    <h2 class="font-serif text-2xl font-bold mb-2 relative z-10">Title</h2>
    <p class="text-slate-400 mb-8 font-sans text-sm relative z-10">Subtitle text.</p>
    <!-- Content -->
</div>
```

### Calculator Inputs

```html
<!-- CSS Required -->
<style>
.calc-input { width: 100%; padding: 12px; border: 2px solid #e2e8f0; border-radius: 8px; font-family: 'Inter', sans-serif; font-size: 16px; transition: border-color 0.2s; }
.calc-input:focus { outline: none; border-color: #DC2626; }
</style>

<!-- Dark theme input -->
<div>
    <label class="block text-xs uppercase tracking-widest font-bold text-slate-500 mb-2">Label Text</label>
    <input type="text" class="calc-input bg-slate-800 border-slate-700 text-white focus:border-red-500" placeholder="e.g. 500" value="500">
    <p class="text-xs text-slate-500 mt-1">Helper text</p>
</div>
```

### Stat Cards (Colored)

```html
<div class="grid md:grid-cols-2 gap-6">
    <div class="bg-green-50 border border-green-200 p-6 rounded-lg">
        <div class="text-4xl font-bold text-green-700 mb-2">68%</div>
        <div class="text-sm uppercase tracking-widest text-green-800 font-bold mb-2">Stat Label</div>
        <p class="text-slate-600 text-sm">Description text.</p>
    </div>
    <!-- Repeat with blue-50, amber-50, purple-50 -->
</div>
```

### Numbered Steps

```html
<div class="space-y-6">
    <div class="bg-white border border-slate-200 rounded-lg p-6">
        <div class="flex items-start gap-4">
            <span class="flex-shrink-0 w-8 h-8 bg-red-600 text-white rounded-full flex items-center justify-center font-bold text-sm">1</span>
            <div>
                <h3 class="font-serif text-xl font-bold text-slate-900 mb-2">Step Title</h3>
                <p class="font-sans text-slate-600">Step description.</p>
            </div>
        </div>
    </div>
</div>
```

### Large Numbered List

```html
<ul class="space-y-8">
    <li class="flex gap-6">
        <span class="font-serif text-4xl text-slate-200 font-bold">1</span>
        <div>
            <strong class="text-slate-900 block text-lg mb-1">Title</strong>
            <span class="text-base text-slate-600 block mt-2">Description text.</span>
        </div>
    </li>
</ul>
```

### Tables

```html
<div class="overflow-x-auto">
    <table class="w-full border-collapse font-sans text-base">
        <thead>
            <tr class="bg-slate-900 text-white">
                <th class="p-4 text-left font-bold">Column 1</th>
                <th class="p-4 text-left font-bold">Column 2</th>
            </tr>
        </thead>
        <tbody>
            <tr class="border-b border-slate-200">
                <td class="p-4 font-semibold text-slate-900">Row label</td>
                <td class="p-4 text-slate-600">Value</td>
            </tr>
            <tr class="border-b border-slate-200 bg-slate-50">
                <td class="p-4 font-semibold text-slate-900">Alternating row</td>
                <td class="p-4 text-slate-600">Value</td>
            </tr>
        </tbody>
    </table>
</div>
```

### CTA Box (Bordered)

```html
<div class="border-2 border-slate-900 p-10 text-center bg-white rounded-lg mb-16">
    <h2 class="font-serif text-3xl font-bold mb-4">CTA Headline</h2>
    <p class="font-sans text-slate-600 mb-8 max-w-xl mx-auto text-lg leading-relaxed">
        Supporting text for the CTA.
    </p>
    <a href="..." class="inline-block bg-red-600 text-white px-8 py-4 rounded-full font-bold hover:bg-red-700 transition-transform hover:-translate-y-1 shadow-lg shadow-red-200">
        Button Text &rarr;
    </a>
</div>
```

### Primary CTA Button

```html
<a href="..." class="inline-block bg-red-600 text-white px-8 py-4 rounded-full font-bold hover:bg-red-700 transition-transform hover:-translate-y-1 shadow-lg shadow-red-200">
    Button Text &rarr;
</a>
```

### Secondary Button (Dark)

```html
<a href="..." class="block text-center w-full bg-slate-900 text-white py-2 rounded-full text-xs font-bold hover:bg-black transition-colors">
    Button Text
</a>
```

### Inline Link

```html
<a href="..." class="text-red-600 hover:underline">Link text</a>
<!-- With font-semibold for emphasis -->
<a href="..." class="text-red-600 hover:underline font-semibold">Link text</a>
```

### Glossary Items

```html
<dl class="grid md:grid-cols-2 gap-6 font-sans">
    <div class="bg-slate-50 p-5 rounded-lg">
        <dt class="font-bold text-slate-900">Term</dt>
        <dd class="text-slate-600 mt-1 text-sm">Definition text.</dd>
    </div>
</dl>
```

### FAQ Section

```html
<dl class="space-y-8 font-sans">
    <div>
        <dt class="font-bold text-slate-900 text-lg">Question text?</dt>
        <dd class="text-slate-600 mt-2 leading-relaxed text-lg">Answer text.</dd>
    </div>
</dl>
```

### Part Divider

```html
<div class="flex items-center gap-4 mb-6">
    <span class="font-sans font-bold text-red-600 text-sm uppercase tracking-widest">Part 1</span>
    <div class="h-px bg-red-100 flex-1"></div>
</div>
```

### Channel/Feature Box (Colored Border)

```html
<div class="bg-white border-2 border-blue-200 rounded-lg p-8 mb-8">
    <div class="flex items-center gap-3 mb-4">
        <span class="flex-shrink-0 w-10 h-10 bg-blue-600 text-white rounded-full flex items-center justify-center font-bold">1</span>
        <h3 class="font-serif text-2xl font-bold text-slate-900">Title</h3>
    </div>
    <p class="font-sans text-slate-700 leading-relaxed mb-6">Content...</p>
</div>
```

### Footer CTA Section (Red)

```html
<div class="bg-red-600 py-20 px-4 text-center relative overflow-hidden">
    <div class="relative z-10 max-w-3xl mx-auto">
        <h2 class="text-4xl md:text-5xl font-serif font-bold text-white mb-6">Headline</h2>
        <p class="text-xl text-white/90 mb-10 font-sans font-medium">Supporting text.</p>
        <a href="..." target="_blank" class="inline-flex items-center gap-2 bg-white text-red-700 px-10 py-4 rounded-full font-bold text-lg hover:scale-105 transition-transform shadow-2xl">
            Button Text
        </a>
    </div>
</div>
```

### Footer

```html
<footer class="py-16 text-center text-slate-500 text-sm bg-slate-900 font-sans">
    <div class="max-w-5xl mx-auto px-6 grid md:grid-cols-3 gap-10 text-left">
        <!-- Column 1: Logo & Bio -->
        <div>
            <img src="..." alt="TK Kader Logo" class="h-12 w-auto mb-6" />
            <p class="leading-relaxed text-slate-400">Bio text with <a href="..." class="hover:text-white transition-colors underline">links</a>.</p>
        </div>
        <!-- Column 2: Links -->
        <div>
            <h4 class="font-bold text-white uppercase tracking-wider text-xs mb-4">Section Title</h4>
            <ul class="space-y-3">
                <li><a href="..." class="hover:text-white transition-colors">Link</a></li>
            </ul>
        </div>
        <!-- Column 3: Legal -->
        <div>
            <h4 class="font-bold text-white uppercase tracking-wider text-xs mb-4">Legal</h4>
            <ul class="space-y-3">
                <li><a href="..." target="_blank" class="hover:text-white transition-colors">Privacy Policy</a></li>
                <li><a href="..." target="_blank" class="hover:text-white transition-colors">Terms of Service</a></li>
            </ul>
            <p class="mt-6 text-xs opacity-40">&copy; 2026 Ideal Customer Profile, LLC.</p>
        </div>
    </div>
</footer>
```

---

## Page Structure

### Standard Page Template

```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <!-- Meta tags -->
    <!-- Favicon -->
    <!-- Canonical -->
    <!-- Open Graph -->
    <!-- Twitter -->
    <!-- Preconnect hints -->
    <!-- Google Analytics -->
    <!-- Tailwind CSS -->
    <!-- Google Fonts -->
    <!-- Schema markup -->
    <!-- Custom styles -->
</head>
<body class="text-slate-800 bg-[#FFFEFC] selection:bg-yellow-200 selection:text-slate-900 pb-20 md:pb-0">
    <!-- Navigation -->
    <!-- Mobile sticky bottom bar -->
    <!-- Breadcrumb -->
    <!-- Hero section -->
    <!-- Main content -->
    <!-- Footer CTA (red) -->
    <!-- Footer -->
</body>
</html>
```

### Section Scroll Targeting

```html
<section id="section-id" class="mb-28 scroll-mt-28">
```

---

## Code Patterns

### Preconnect Hints (Performance)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="preconnect" href="https://www.youtube.com">
<link rel="preconnect" href="https://img.youtube.com">
<link rel="preconnect" href="https://www.tkkader.com">
<link rel="preconnect" href="https://cdn.tailwindcss.com">
```

### Schema Markup Types

Always include relevant schema types:
- `BreadcrumbList` - For navigation breadcrumbs
- `Article` - For content pages
- `VideoObject` - For each embedded video
- `HowTo` - For step-by-step guides
- `FAQPage` - For FAQ sections
- `WebApplication` - For calculators

### UTM Parameters

Use consistent UTM parameters for tracking:
```
?utm_source=icp&utm_medium=organic
```

### Mobile-First Responsive

- Hide on mobile: `hidden md:block` or `hidden md:inline-flex`
- Show only on mobile: `md:hidden`
- Responsive text: `text-3xl md:text-4xl`
- Responsive grid: `grid md:grid-cols-2`
- Bottom padding for mobile bar: `pb-20 md:pb-0`

---

## Quick Reference: Common Tailwind Classes

### Borders
- `rounded-lg` - Standard radius
- `rounded-xl` - Larger radius (calculators, modals)
- `rounded-full` - Buttons, pills
- `rounded-2xl` - Modals
- `border border-slate-200` - Light border
- `border-2 border-slate-900` - Strong border (CTA boxes)

### Shadows
- `shadow-sm` - Subtle (videos, cards)
- `shadow-lg` - Medium (buttons)
- `shadow-2xl` - Strong (calculators, modals)
- `shadow-red-200` - Colored shadow for red buttons

### Transitions
- `transition-colors` - For color changes
- `transition-transform` - For scale/translate
- `transition-all` - For multiple properties
- `hover:scale-105` - Standard hover scale
- `hover:-translate-y-1` - Button lift effect

### Z-Index Layers
- `z-10` - Above content (play buttons)
- `z-20` - Video iframes
- `z-50` - Navigation, mobile bar
- `z-[60]` - Modals
