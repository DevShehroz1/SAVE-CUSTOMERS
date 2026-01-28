# SaveCustomer Header - Complete Design & Implementation Instructions

## Overview
The SaveCustomer header is a fixed, pill-shaped navigation bar that floats above the website content. It features a gradient background, logo, navigation links, and a CTA button.

---

## Desktop Design (Viewport Width > 640px)

### Container & Positioning
- **Wrapper (`.sc-header-outer`)**:
  - Position: Fixed at the top of the viewport
  - Top offset: 24px from the top edge
  - Horizontal: Centered using `left: 50%` and `transform: translateX(-50%)`
  - Width: 100% of viewport
  - Side padding: 24px on left and right
  - Z-index: 1000 (ensures it stays above all content)
  - Pointer events: Disabled on wrapper (only the pill itself is interactive)

### Header Pill (`.sc-header`)
- **Dimensions**:
  - Max width: 960px (centered within viewport)
  - Height: 72px
  - Horizontal padding: 32px left and right
  - Border radius: 999px (fully rounded pill shape)

- **Visual Design**:
  - Background: Linear gradient (120deg) with three colors:
    - Start: `#004734` (dark green)
    - Middle: `#47bf5d` (medium green)
    - End: `#81d490` (light green)
  - Box shadow: `0 18px 40px rgba(0, 0, 0, 0.22)` (elevated appearance)
  - Backdrop filter: `blur(16px)` (glassmorphism effect)
  - Text color: `#ffffff` (white)

- **Layout**:
  - Display: Flexbox
  - Alignment: Items centered vertically
  - Justification: Space between (logo left, nav center, CTA right)

### Logo (`.sc-logo`)
- **Size**: Height 28px, width auto (maintains aspect ratio)
- **Position**: Left side of header
- **File**: `assets/Logo_Wide_-_SaveCustomer_-_2.png`

### Navigation Links (`.sc-nav`)
- **Layout**:
  - Display: Flexbox, horizontally aligned
  - Gap between links: 32px
  - Font size: 16px
  - Font weight: 500 (medium)

- **Links** (in order):
  1. "Home" (links to `#home`)
  2. "Cs Tools" (links to `#cs-tools`)
  3. "Helpfull Content" (links to `#helpful-content`)

- **Link Styling**:
  - Default opacity: 0.9
  - Hover opacity: 1.0
  - Text color: Inherits white from header
  - Underline animation: On hover, a white underline (2px height) animates from 0 to 100% width
  - Transition: 0.2s ease-out

### CTA Button (`.sc-cta`)
- **Text**: "Book a Meeting"
- **Size**:
  - Padding: 6px vertical, 12px horizontal
  - Border radius: 14px
  - Font size: 14px
  - Font weight: 600 (semi-bold)

- **Visual Design**:
  - Background: Linear gradient (135deg):
    - Start: `#003023` (very dark green)
    - Middle: `#20572a` (dark green)
    - End: `#285741` (medium-dark green)
  - Text color: `#ffffff` (white)
  - Box shadow: `0 8px 18px rgba(0, 71, 46, 0.25)`

- **Interactions**:
  - Hover: 
    - Lifts up 1px (`transform: translateY(-1px)`)
    - Shadow increases: `0 10px 24px rgba(0, 71, 46, 0.3)`
    - Brightness: Increases by 3%
  - Active (click):
    - Returns to original position
    - Shadow reduces: `0 6px 12px rgba(0, 71, 46, 0.25)`
  - Transitions: 0.15s ease-out for all properties

### Content Spacing
- **Page content** (`.sc-content`):
  - Top margin: 80px (prevents content from being hidden behind fixed header)

---

## Mobile Design (Viewport Width ≤ 640px)

### Container & Positioning
- **Wrapper (`.sc-header-outer`)**:
  - Top offset: Reduced to 16px (from 24px)
  - Side padding: Removed (0px) for edge-to-edge placement

### Header Pill (`.sc-header`)
- **Dimensions**:
  - Max width: 340px (narrower for mobile)
  - Height: 46px (reduced from 72px)
  - Horizontal padding: 18px (reduced from 32px)

- **Visual Design**: Same gradient, shadow, and backdrop filter as desktop

### Logo (`.sc-logo`)
- **Size**: Height 16px (reduced from 28px)

### Navigation Links (`.sc-nav`)
- **Gap**: Reduced to 12px (from 32px)
- **Font size**: 14px (reduced from 16px)
- **Visibility**:
  - **Hidden**: "Home" and "Helpfull Content" links are hidden (`display: none`)
  - **Visible**: Only "Cs Tools" (second link) is shown (`display: inline-block`)
  - This creates a simplified mobile navigation

### CTA Button (`.sc-cta`)
- **Padding**: Same as desktop (6px vertical, 12px horizontal)
- **Font size**: 13px (slightly smaller than desktop 14px)
- **Box shadow**: Reduced to `0 6px 14px rgba(0, 71, 46, 0.25)`
- **Interactions**: Same hover/active states as desktop

### Content Spacing
- **Page content** (`.sc-content`):
  - Top margin: 72px (reduced from 80px to account for smaller header)

---

## Responsive Breakpoint

- **Breakpoint**: `@media (max-width: 640px)`
- **Behavior**: All mobile styles apply at 640px and below
- **Above 640px**: Desktop styles apply

---

## Technical Implementation Details

### HTML Structure
```html
<div class="sc-header-outer">
  <header class="sc-header">
    <div class="sc-header-left">
      <img src="assets/Logo_Wide_-_SaveCustomer_-_2.png" alt="SaveCustomer" class="sc-logo" />
    </div>
    <nav class="sc-nav" aria-label="Main navigation">
      <a href="#home">Home</a>
      <a href="#cs-tools">Cs Tools</a>
      <a href="#helpful-content">Helpfull Content</a>
    </nav>
    <div class="sc-header-right">
      <button class="sc-cta" type="button">Book a Meeting</button>
    </div>
  </header>
</div>
```

### Key CSS Classes
- `.sc-header-outer` - Fixed positioning wrapper
- `.sc-header` - The pill-shaped header container
- `.sc-header-left` - Logo container
- `.sc-logo` - Logo image styling
- `.sc-nav` - Navigation links container
- `.sc-header-right` - CTA button container
- `.sc-cta` - CTA button styling
- `.sc-content` - Main content area (needs top margin)

### Accessibility
- Navigation has `aria-label="Main navigation"` for screen readers
- Button has proper `type="button"` attribute
- Logo has descriptive `alt="SaveCustomer"` text

### Browser Compatibility
- Uses modern CSS features:
  - Flexbox (widely supported)
  - CSS Grid (not used, but available)
  - Backdrop filter (may need fallback for older browsers)
  - CSS transforms (widely supported)
  - Media queries (widely supported)

---

## Visual Summary

### Desktop Header
```
┌─────────────────────────────────────────────────────────────┐
│  [Logo]    Home  Cs Tools  Helpfull Content    [Book Meeting] │
└─────────────────────────────────────────────────────────────┘
     ↑                                                      ↑
  28px height                                          14px font
  960px max width                                       CTA button
  72px height
```

### Mobile Header
```
┌──────────────────────┐
│ [Logo]  Cs Tools  [B]│
└──────────────────────┘
     ↑              ↑
  16px height   13px font
  340px width    CTA button
  46px height
```

---

## Color Palette

### Header Background Gradient
- `#004734` - Dark green (start)
- `#47bf5d` - Medium green (middle)
- `#81d490` - Light green (end)

### CTA Button Gradient
- `#003023` - Very dark green (start)
- `#20572a` - Dark green (middle)
- `#285741` - Medium-dark green (end)

### Text & Accents
- `#ffffff` - White (all text and underlines)
- `rgba(255, 255, 255, 0.9)` - White at 90% opacity (link underlines)

### Shadows
- Header shadow: `rgba(0, 0, 0, 0.22)` - Black at 22% opacity
- CTA shadow: `rgba(0, 71, 46, 0.25)` - Dark green at 25% opacity

---

## Animation & Transitions

1. **Navigation Link Hover**:
   - Underline expands from 0 to 100% width
   - Duration: 0.2s
   - Easing: ease-out

2. **CTA Button Hover**:
   - Lifts 1px upward
   - Shadow increases
   - Brightness increases 3%
   - Duration: 0.15s
   - Easing: ease-out

3. **CTA Button Active**:
   - Returns to original position
   - Shadow decreases
   - Duration: 0.15s
   - Easing: ease-out

---

## Notes for Developers

- The header is **fixed**, meaning it stays at the top when scrolling
- Content below must have sufficient top margin/padding to avoid being hidden
- The wrapper uses `pointer-events: none` so clicks pass through to content, except the pill itself
- Mobile breakpoint is at 640px - test thoroughly at this exact width
- Logo should maintain aspect ratio (width: auto)
- All measurements are in pixels for precision
- The gradient uses 120deg angle for desktop header, 135deg for CTA button

---

## Testing Checklist

- [ ] Desktop: Header appears centered, 24px from top
- [ ] Desktop: All three nav links visible and clickable
- [ ] Desktop: Logo displays correctly at 28px height
- [ ] Desktop: CTA button has hover and active states
- [ ] Mobile (≤640px): Header reduces to 340px width
- [ ] Mobile: Only "Cs Tools" link visible
- [ ] Mobile: Logo reduces to 16px height
- [ ] Mobile: Header positioned 16px from top
- [ ] Content spacing: 80px desktop, 72px mobile
- [ ] Header stays fixed when scrolling
- [ ] Gradient displays correctly in all browsers
- [ ] Backdrop filter works (or has fallback)
- [ ] All links navigate correctly
- [ ] CTA button is functional
