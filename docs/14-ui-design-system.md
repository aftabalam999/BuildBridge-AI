# 14 - UI Design System

# BuildBridge AI

## Design System Documentation

---

# 1. Overview

BuildBridge AI follows a clean, modern, and minimal design language focused on readability, professionalism, and usability.

The UI is inspired by educational platforms, productivity software, and enterprise dashboards.

### Design Principles

- Clean & Minimal
- Consistent
- Professional
- Accessible
- Responsive
- Reusable Components
- Soft Color Palette
- Spacious Layout

---

# 2. Brand Color Palette

## Primary Color

Used for:

- Primary Buttons
- Links
- Active Navigation
- Icons
- Focus States
- Charts

| Token | Hex |
|---------|---------|
| Primary | #5C8DC5 |
| Primary Hover | #4A7CB5 |
| Primary Light | #DCE9F6 |

---

## Secondary Color

Used for:

- Cards
- Timeline
- Tags
- Sections

| Token | Hex |
|---------|---------|
| Secondary | #AD9E90 |
| Secondary Hover | #998B7E |
| Secondary Light | #EEE8E3 |

---

## Accent Color

Used for:

- Sidebar Icons
- Badges
- Labels
- Statistics

| Token | Hex |
|---------|---------|
| Accent | #736F60 |
| Accent Light | #D6D2CB |

---

## Neutral Color

Used for:

- Borders
- Placeholder Text
- Disabled Buttons
- Dividers

| Token | Hex |
|---------|---------|
| Neutral | #909EAE |
| Neutral Light | #E8EDF2 |

---

# 3. Semantic Colors

## Success

| Color | Hex |
|---------|---------|
| Success | #43A047 |

---

## Warning

| Color | Hex |
|---------|---------|
| Warning | #F9A825 |

---

## Error

| Color | Hex |
|---------|---------|
| Error | #D32F2F |

---

## Info

Uses Primary Blue

```
#5C8DC5
```

---

# 4. Background Colors

| Area | Color |
|---------|---------|
| Application | #F8F9FA |
| Section | #F3F5F7 |
| Card | #FFFFFF |
| Sidebar | #FFFFFF |
| Navbar | #FFFFFF |
| Modal | #FFFFFF |

---

# 5. Text Colors

| Usage | Color |
|---------|---------|
| Heading | #1F2937 |
| Body | #374151 |
| Secondary Text | #736F60 |
| Muted Text | #909EAE |
| White Text | #FFFFFF |

---

# 6. Typography

## Font Family

Primary

```
Inter
```

Fallback

```
sans-serif
```

---

## Font Sizes

| Element | Size |
|---------|---------|
| Hero Title | 56px |
| Page Title | 40px |
| Section Title | 32px |
| Card Title | 22px |
| Heading | 20px |
| Body | 16px |
| Small | 14px |
| Caption | 12px |

---

## Font Weight

| Weight | Usage |
|---------|---------|
| 700 | Hero |
| 600 | Titles |
| 500 | Buttons |
| 400 | Body |

---

# 7. Spacing System

Base Unit

```
4px
```

Spacing Scale

| Value | Tailwind |
|---------|---------|
|4px|1|
|8px|2|
|12px|3|
|16px|4|
|20px|5|
|24px|6|
|32px|8|
|40px|10|
|48px|12|
|64px|16|

---

# 8. Border Radius

| Component | Radius |
|---------|---------|
| Button | 10px |
| Card | 18px |
| Input | 12px |
| Badge | 9999px |
| Modal | 20px |

Tailwind

```
rounded-lg

rounded-xl

rounded-2xl

rounded-full
```

---

# 9. Shadows

Cards

```
shadow-md
```

Hover

```
shadow-lg
```

Modal

```
shadow-2xl
```

Buttons

```
shadow-sm
```

---

# 10. Buttons

## Primary Button

Background

```
#5C8DC5
```

Text

```
White
```

Hover

```
#4A7CB5
```

---

## Secondary Button

Background

```
#AD9E90
```

Text

```
White
```

Hover

```
#998B7E
```

---

## Outline Button

Border

```
#5C8DC5
```

Text

```
#5C8DC5
```

Hover

```
Background:
#DCE9F6
```

---

## Ghost Button

Background

```
Transparent
```

Hover

```
#F3F5F7
```

---

# 11. Inputs

Background

```
White
```

Border

```
#E5E7EB
```

Focus Border

```
#5C8DC5
```

Placeholder

```
#909EAE
```

Error

```
#D32F2F
```

---

# 12. Cards

Background

```
White
```

Border

```
1px solid #E5E7EB
```

Radius

```
18px
```

Padding

```
24px
```

Hover

```
Translate Y -2px

Shadow-lg
```

---

# 13. Dashboard Colors

Roadmap

```
#5C8DC5
```

Resume

```
#909EAE
```

Projects

```
#AD9E90
```

Interview

```
#736F60
```

This color coding helps users quickly distinguish between different modules.

---

# 14. Icons

Library

```
Lucide React
```

Default Color

```
#736F60
```

Active Color

```
#5C8DC5
```

---

# 15. Layout

Container

```
max-w-7xl
mx-auto
```

Section Padding

Desktop

```
py-20
```

Tablet

```
py-16
```

Mobile

```
py-12
```

---

# 16. Responsive Breakpoints

| Device | Width |
|---------|---------|
| Mobile | <640px |
| Tablet | ≥640px |
| Laptop | ≥1024px |
| Desktop | ≥1280px |

---

# 17. Reusable Components

Common Components

- Button
- Input
- Select
- TextArea
- Modal
- Card
- Badge
- Avatar
- Loader
- Spinner
- Toast
- Empty State
- Skeleton Loader

Feature Components

- Sidebar
- Navbar
- Dashboard Cards
- Timeline
- Resume Card
- Project Card
- Interview Card

---

# 18. Animation Guidelines

Library

```
Framer Motion
```

Recommended Animations

- Fade In
- Slide Up
- Scale Hover
- Card Hover
- Sidebar Transition
- Modal Transition

Animation Duration

```
200ms–300ms
```

---

# 19. Accessibility

- Minimum WCAG AA contrast ratio
- Keyboard navigation
- Focus indicators
- Semantic HTML
- Proper form labels
- Screen reader friendly

---

# 20. Tailwind Theme

```javascript
colors: {
  primary: "#5C8DC5",
  secondary: "#AD9E90",
  accent: "#736F60",
  neutral: "#909EAE",

  background: "#F8F9FA",
  surface: "#FFFFFF",

  text: "#1F2937",
  muted: "#6B7280",

  success: "#43A047",
  warning: "#F9A825",
  error: "#D32F2F",
}
```

---

# 21. Design Principles

- Consistency over complexity
- Soft colors reduce visual fatigue
- Clear visual hierarchy
- High readability
- Reusable UI components
- Mobile-first responsive design
- Use whitespace generously
- Keep interactions simple and predictable

---

# 22. Summary

BuildBridge AI uses a calm and professional design system centered around a muted blue (`#5C8DC5`), warm beige (`#AD9E90`), neutral blue-gray (`#909EAE`), and olive-gray (`#736F60`). Combined with clean typography, spacious layouts, and reusable components, this system creates a trustworthy and modern experience that aligns with an AI-powered career guidance platform.