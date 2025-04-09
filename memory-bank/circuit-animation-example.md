# Detailed Circuit Animation Implementation Example

This document provides a comprehensive example of how to implement the animated circuit lines for the Cyborg Dev landing page, focusing on the Hero section as a demonstration.

## Complete HTML Structure Example

```html
<!-- Add this at the end of the <head> section -->
<style>
  /* Circuit animation CSS (see CSS section below) */
</style>

<!-- Add this right after the opening <body> tag -->
<div class="circuit-container">
  <!-- Hero Section Circuits (Orange-Red) -->
  <svg class="circuit-svg hero-circuits" viewBox="0 0 1200 800" preserveAspectRatio="none">
    <!-- Left side circuits connecting to hero content -->
    <path 
      class="circuit-line circuit-orange-red delay-1" 
      d="M120,150 L220,150 L220,250 L350,250" 
    />
    
    <!-- Right side circuits connecting to form -->
    <path 
      class="circuit-line circuit-orange-red delay-2" 
      d="M850,180 L950,180 L950,300 L1050,300" 
    />
    
    <!-- Bottom circuits connecting sections -->
    <path 
      class="circuit-line circuit-orange-red delay-3" 
      d="M400,650 L400,700 L600,700 L600,750" 
    />
    
    <!-- Central circuits connecting hero sections -->
    <path 
      class="circuit-line circuit-orange-red delay-1" 
      d="M600,200 L600,300 L700,300 L700,350" 
    />
    
    <!-- Diagonal accent circuit -->
    <path 
      class="circuit-line circuit-orange-red delay-2" 
      d="M300,400 L450,400 L500,450 L650,450" 
    />
  </svg>
  
  <!-- Défis Section Circuits (Blue) would go here -->
  <!-- Témoignages Section Circuits (Purple) would go here -->
  <!-- Vision Section Circuits (Green) would go here -->
</div>
```

## Detailed CSS Implementation

```css
/* Circuit container positioning */
.circuit-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  pointer-events: none; /* Allow clicks to pass through */
  overflow: hidden;
}

/* SVG base styling */
.circuit-svg {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}

/* Section-specific positioning */
.hero-circuits {
  height: 100vh; /* Full height for hero section */
}

/* Circuit line base styling */
.circuit-line {
  stroke-width: 1px;
  fill: none;
  stroke-dasharray: 5, 15; /* Create dashed line effect */
  opacity: 0.15; /* Very subtle base opacity */
  filter: drop-shadow(0 0 1px currentColor); /* Subtle glow */
}

/* Color variations - using the current brand colors but with reduced opacity */
.circuit-orange-red {
  stroke: rgba(255, 73, 49, 0.7);
}

.circuit-purple {
  stroke: rgba(158, 87, 179, 0.7);
}

.circuit-green {
  stroke: rgba(26, 251, 111, 0.7);
}

.circuit-blue {
  stroke: rgba(38, 122, 210, 0.7);
}

/* Flow animation for circuit lines */
@keyframes flowAnimation {
  0% {
    stroke-dashoffset: 100;
    opacity: 0.15;
  }
  50% {
    opacity: 0.4; /* Peak brightness */
  }
  100% {
    stroke-dashoffset: 0;
    opacity: 0.15;
  }
}

/* Apply animation to all circuit lines */
.circuit-line {
  animation: flowAnimation 15s linear infinite;
}

/* Create staggered animation effect with different delay classes */
.delay-1 {
  animation-delay: -2s;
  animation-duration: 12s; /* Slightly faster */
}

.delay-2 {
  animation-delay: -5s;
  animation-duration: 16s; /* Slightly slower */
}

.delay-3 {
  animation-delay: -9s;
  animation-duration: 20s; /* Even slower */
}

/* Responsive adjustments */
@media (max-width: 768px) {
  /* Simplified circuit paths for mobile */
  .circuit-svg {
    display: none; /* Optional: hide on very small screens */
  }
  
  /* Alternative: keep some strategic paths */
  .circuit-line.mobile-hidden {
    display: none;
  }
  
  /* Reduce animation complexity on mobile */
  .circuit-line {
    animation-duration: 25s; /* Slower animation to reduce GPU load */
  }
}

/* Animation reduction for users who prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
  .circuit-line {
    animation: none;
    opacity: 0.2;
  }
}
```

## JavaScript Enhancement (Optional)

```javascript
// Optional JavaScript to dynamically adjust circuit positions based on viewport
// This helps maintain proper positioning when the layout changes responsively

document.addEventListener('DOMContentLoaded', function() {
  // Get references to circuit SVGs
  const heroCircuits = document.querySelector('.hero-circuits');
  
  // Function to update SVG viewBox based on container dimensions
  function updateCircuitPositions() {
    // Get the hero section dimensions
    const heroSection = document.querySelector('.hero-section'); // Use your actual hero section selector
    if (heroSection && heroCircuits) {
      const rect = heroSection.getBoundingClientRect();
      
      // Update the viewBox to match the aspect ratio
      const viewBoxValue = `0 0 ${rect.width} ${rect.height}`;
      heroCircuits.setAttribute('viewBox', viewBoxValue);
      
      // Update SVG dimensions
      heroCircuits.style.width = `${rect.width}px`;
      heroCircuits.style.height = `${rect.height}px`;
    }
  }
  
  // Update on load and resize
  updateCircuitPositions();
  window.addEventListener('resize', updateCircuitPositions);
});
```

## Integration Instructions

1. Add the CSS to your page's `<style>` section or a separate CSS file
2. Insert the circuit container divs with SVGs directly after the opening `<body>` tag
3. Customize the SVG paths to match your page layout

## Creating SVG Paths

The most critical aspect of the implementation is creating appropriate SVG paths. Here's a step-by-step guide:

1. **Plan the Layout**: First, identify key UI elements you want to connect with circuit lines.

2. **Create a Grid**: Mentally overlay a grid on your design. Circuit paths should follow this grid with clean horizontal and vertical lines and 90° turns.

3. **Path Syntax**: SVG paths use the following commands:
   - `M x,y` - Move to coordinates (x,y)
   - `L x,y` - Draw a line to coordinates (x,y)
   - `H x` - Draw a horizontal line to x coordinate
   - `V y` - Draw a vertical line to y coordinate

4. **Example Path Construction**:
   ```
   "M100,100 L300,100 L300,300"
   ```
   This creates a path that:
   - Starts at position (100,100)
   - Draws a horizontal line to (300,100)
   - Draws a vertical line down to (300,300)

5. **Connect Strategic Elements**: Design paths that:
   - Connect related UI components
   - Lead the eye through the page's natural flow
   - Emphasize important content areas
   - Create visual structure and hierarchy

## Viewport Coordinates

When working with SVG in a responsive context, understand that:

1. The viewBox attribute (`viewBox="0 0 1200 800"`) defines the coordinate system
2. Path coordinates are relative to this viewBox, not actual pixels
3. Using a generous viewBox (like 1200×800) allows for precise positioning regardless of actual screen size

## Animation Refinement

You can adjust these properties to fine-tune the animation:

- `stroke-dasharray`: Adjusts the length of dashes and gaps (e.g., `5, 15` means 5px dash, 15px gap)
- `stroke-dashoffset`: Controls the starting position of the dash pattern
- `animation-duration`: Controls how fast the animation runs (longer = slower)
- `opacity` values: Adjust the min/max opacity in the keyframes for more or less subtlety

## Multiple Sections Approach

For a complete implementation:

1. Create separate SVG elements for each page section
2. Use the appropriate color class based on the section theme
3. Position each SVG absolutely within its section
4. Use z-index to ensure circuits appear behind content

## Performance Considerations

To maintain good performance:

1. Limit the total number of path elements (15-20 maximum)
2. Use `will-change: opacity, stroke-dashoffset` for paths that animate
3. Consider disabling animations on mobile devices
4. Test on lower-powered devices to ensure smooth rendering