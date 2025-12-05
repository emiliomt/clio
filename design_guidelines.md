# Clio Notes App - Design Guidelines

## Design Approach
**Selected Approach**: Design System with Notion/Linear inspiration
**Justification**: Utility-focused productivity tool requiring clean, distraction-free interface optimizing for extended writing sessions and note organization.

## Core Design Principles
- **Distraction-Free Focus**: Minimal chrome, maximum content visibility
- **Efficient Hierarchy**: Clear visual distinction between navigation, list, and editor zones
- **Smooth Transitions**: Subtle animations only for state changes (note selection, theme toggle)

## Typography System

**Font Family**: System font stack for optimal performance
- Primary: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`

**Hierarchy**:
- Note titles in editor: `text-2xl font-semibold` (24px)
- Note list items: `text-base font-medium` (16px)
- Body content: `text-base leading-relaxed` (16px, 1.75 line-height)
- UI labels/buttons: `text-sm font-medium` (14px)
- Timestamps/metadata: `text-xs text-gray-500` (12px)

## Layout System

**Spacing Primitives**: Tailwind units of `2, 4, 6, 8` primarily
- Component padding: `p-4` to `p-6`
- Section gaps: `gap-4` to `gap-6`
- Generous editor padding: `p-8` for writing comfort

**Layout Structure**:
- Fixed left sidebar: `w-72` (288px)
- Remaining space: Fluid editor area with `max-w-3xl mx-auto` for optimal reading width
- Three-zone layout: Auth/Sidebar/Editor with clear visual separation

## Component Library

### Authentication Screen
- Centered card layout `max-w-md mx-auto mt-24`
- Clean form with stacked inputs (`space-y-4`)
- Toggle between Login/Register modes with subtle tab-style switcher
- Primary CTA button fills width

### Left Sidebar (Navigation Zone)
- **Header section** (`p-6 border-b`):
  - App title "Clio" with icon
  - Theme toggle icon button (top-right)
  
- **Search bar** (`px-4 py-3`):
  - Input with search icon prefix
  - Subtle border, no heavy styling
  
- **New Note button** (`mx-4 mb-4`):
  - Full-width primary button
  - Clear "+" icon with "New Note" label
  
- **Notes list** (scrollable area):
  - Each item: `px-4 py-3` with `border-l-4` accent when selected
  - Title truncation with ellipsis
  - Small timestamp below title
  - Hover state: subtle background change

### Editor Panel (Content Zone)
- **Title input**:
  - Large, borderless input mimicking heading style
  - `border-b` separator only
  - Placeholder: "Untitled"
  
- **Content textarea**:
  - Borderless, auto-expanding
  - Generous padding `p-8`
  - Wiki links `[[Note Title]]` render with distinct styling: `text-blue-600 underline decoration-dotted`
  
- **Footer toolbar** (`border-t p-4 flex justify-between`):
  - Left: Delete button (text, destructive color)
  - Center: Auto-save status ("Saved" with checkmark icon)
  - Right: Export/Import buttons

### Backlinks Panel
- Collapsible section at bottom of editor
- Header: "Backlinks (count)" with chevron toggle
- List of linked notes as clickable chips/pills
- Shows when 1+ backlinks exist

### Theme Implementation
- **Dark theme** (default): Deep charcoal backgrounds `bg-gray-900`, light text `text-gray-100`
- **Light theme**: Clean whites `bg-white`, dark text `text-gray-900`
- Consistent contrast ratios (WCAG AA)
- Border colors adapt: `border-gray-800` (dark) / `border-gray-200` (light)

## Interaction Patterns

**Auto-save indicator**: Small, unobtrusive checkmark icon with "Saved" text in footer
**Loading states**: Subtle skeleton screens for notes list during initial fetch
**Empty states**: 
- No notes: Centered illustration with "Create your first note" prompt
- No search results: "No notes found" message with clear search term

**Buttons**:
- Primary: Solid background, white text, slight rounded corners `rounded-lg`
- Secondary: Outlined style with hover fill
- Destructive: Red text/outline, confirmation modal before delete
- Icon buttons: Square `p-2`, hover background circle

**Forms**:
- Input fields: `border rounded-lg px-4 py-2.5`
- Focus state: Blue ring `focus:ring-2 focus:ring-blue-500`
- Labels above inputs, `text-sm font-medium mb-2`

## Visual Refinements

- Subtle box shadows for depth: `shadow-sm` on cards
- Smooth transitions: `transition-colors duration-200` for hover states
- No heavy animations - focus on content, not motion
- Consistent border radius: `rounded-lg` for containers, `rounded-md` for inputs/buttons

## Accessibility
- Clear focus indicators on all interactive elements
- Semantic HTML structure (main, aside, nav)
- Proper ARIA labels for icon-only buttons
- Keyboard navigation support (tab through notes list, Cmd/Ctrl+N for new note)

---

**Result**: A clean, professional notes application prioritizing readability and efficient note management with a modern, minimal aesthetic suitable for extended writing sessions.