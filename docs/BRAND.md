# ORBIT Brand Guide

Premium, modern visual identity for ORBIT - the AI-powered search portal.

## Logo & Identity

### Name
**ORBIT** - Capitalize all letters, clean sans-serif typography

### Tagline
"Your gateway to the internet, supercharged with AI"

### Brand Values
- **Fast** - Instant results and responses
- **Sleek** - Modern, minimalist design
- **Intelligent** - AI-powered assistance
- **Accessible** - Universal search & browsing
- **Private** - Proxy-based browsing

## Color Palette

### Primary Colors
- **Sky Blue**: `#0ea5e9` - Primary CTA, highlights
- **Purple**: `#8b5cf6` - Secondary actions, gradients
- **Amber**: `#f59e0b` - Warnings, accents

### Neutral Colors
- **Charcoal**: `#0f172a` - Darkest background
- **Dark Gray**: `#1f2937` - Primary surface
- **Medium Gray**: `#374151` - Secondary surface
- **Light Gray**: `#d1d5db` - Tertiary text
- **Off White**: `#f3f4f6` - Primary text

### Usage
- Dark backgrounds for OLED efficiency
- Sky blue for interactive elements
- Purple for secondary CTAs
- Amber for alerts/warnings
- Grays for hierarchy

## Typography

### Font Family
**Inter** (Google Fonts)
- Clean, modern sans-serif
- Excellent readability
- Open source

### Type Scale
```
Display: 3xl (30px) - Bold
Heading 1: 2xl (24px) - Bold
Heading 2: xl (20px) - Semibold
Body: base (16px) - Regular
Small: sm (14px) - Regular
Caption: xs (12px) - Medium
```

### Font Weights
- **Regular**: 400 - Body text
- **Medium**: 500 - Small text
- **Semibold**: 600 - Headings
- **Bold**: 700 - Titles

## Components

### Buttons
- **Primary**: Sky blue background, white text
- **Secondary**: Purple background, white text
- **Tertiary**: Gray outline, gray text
- **Danger**: Red background, white text

### Cards & Surfaces
- Glass-morphism effect
- Backdrop blur: 12px
- Border: 1px white/20%
- Rounded corners: 12px
- Shadow: subtle glow

### Input Fields
- Dark background with subtle border
- Focus: blue glow effect
- Placeholder: medium gray
- Rounded: 8px
- Padding: 12px

### Modals & Overlays
- Backdrop: dark with opacity
- Card: elevated with glass effect
- Border: subtle white border
- Shadow: pronounced

## Effects & Animations

### Glass-Morphism
```css
backdrop-filter: blur(12px);
background: rgba(255, 255, 255, 0.1);
border: 1px solid rgba(255, 255, 255, 0.2);
```

### Transitions
- Default duration: 300ms
- Easing: ease-out
- Properties: color, background, transform

### Animations
- Fade in: 0.3s
- Slide up: 0.3s
- Pulse: 2s infinite
- Glow: smooth pulsing

## Layout & Spacing

### Spacing Scale
```
xs: 4px
sm: 8px
md: 16px
lg: 24px
xl: 32px
2xl: 48px
```

### Grid
- 12-column responsive grid
- Breakpoints: sm, md, lg, xl, 2xl
- Gutter: 24px

### Shadows
- **Subtle**: 0 1px 2px rgba(0,0,0,0.05)
- **Base**: 0 4px 6px rgba(0,0,0,0.1)
- **Medium**: 0 10px 15px rgba(0,0,0,0.1)
- **Glass**: 0 8px 32px rgba(31, 38, 135, 0.37)

## UI Patterns

### Search Bar
- Icon + input + action button
- Glass background
- Sky blue accent on focus
- Rounded corners: 12px

### Navigation
- Left sidebar: 256px
- Right sidebar: 384px
- Icons + labels
- Active state: blue highlight

### Cards Grid
- 3-4 columns responsive
- Gap: 16px
- Hover: subtle scale
- Rounded: 12px

### Modals
- Centered on screen
- Dark overlay with blur
- Glass card
- Header + content + footer

## Icons

- **Set**: React Icons (Feather set)
- **Size**: 20px default, 24px large
- **Color**: Inherit from text color
- **Stroke**: 2px

## Dark Mode

- Primary background: `#0f172a`
- Gradient: 135deg from `#0f172a` to `#111827`
- No light mode needed (dark-first design)

## Accessibility

- Minimum contrast ratio: 4.5:1
- Focus indicators: 2px blue outline
- Interactive elements: 44x44px minimum
- Text sizes: 16px minimum
- Line height: 1.5+ for body text

## Motion

- Reduce motion: respect `prefers-reduced-motion`
- Duration: 200ms for quick interactions
- Duration: 300-400ms for medium transitions
- Duration: 500ms+ for complex animations
- Avoid: motion sickness triggers

## Voice & Tone

- **Professional yet approachable**
- **Clear and concise**
- **Encouraging without being pushy**
- **Helpful and knowledgeable**

### Copywriting Guidelines
- Use active voice
- Short sentences
- Action-oriented verbs
- Avoid jargon
- Be specific

## Examples

### CTA Button
"Search the web" → Clear, concise action

### Input Placeholder
"Ask Orbit..." → Personal, inviting tone

### Success Message
"Added to bookmarks" → Confirmatory, positive

### Error Message
"Search query too long. Please try again." → Helpful, not blaming

---

**ORBIT** - Where search meets intelligence.
