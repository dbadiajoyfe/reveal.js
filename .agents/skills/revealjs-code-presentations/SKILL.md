---
name: revealjs-code-presentations
description: Create reveal.js presentations with code demos and syntax highlighting. Use when building slide decks with live code examples, configuring navigation controls, setting up transitions, or styling presentation themes for technical content.
---

# Reveal.js Code Presentations

Interactive HTML presentations with syntax highlighting and smooth transitions.

## When to Apply

- Building slide decks with live code demonstrations
- Presenting technical content with step-by-step code reveals
- Creating presentations with custom navigation flows
- Styling presentations with themes and animations

## Critical Rules

**Plugin Registration**: Load RevealHighlight plugin for syntax highlighting

```html
<!-- WRONG - missing highlight plugin -->
<script>
  Reveal.initialize();
</script>

<!-- RIGHT - includes syntax highlighting -->
<link rel="stylesheet" href="plugin/highlight/monokai.css" />
<script src="plugin/highlight/highlight.js"></script>
<script>
  Reveal.initialize({
    plugins: [RevealHighlight]
  });
</script>
```

**Line Highlighting**: Use bracket syntax `[1-2|3|4]` for sequential code reveals

```html
<!-- WRONG - no line highlighting -->
```js
let a = 1;
let b = 2;
let c = x => 1 + 2 + x;
```

<!-- RIGHT - progressive line highlighting -->
```js [1-2|3|4]
let a = 1;
let b = 2;
let c = x => 1 + 2 + x;
c(3);
```
```

## Key Patterns

### Basic Slide Structure

```html
<div class="reveal">
  <div class="slides">
    <section>
      <h2>Horizontal Slide</h2>
    </section>
    <section>
      <section>Vertical Stack 1</section>
      <section>Vertical Stack 2</section>
    </section>
  </div>
</div>
```

### Code Block with Highlighting

```html
<section>
  <pre><code data-trim data-noescape data-line-numbers="1-3|5-7|9">
function example() {
  let data = fetch('/api');
  let result = await data.json();
  
  if (result.status === 'ok') {
    return result.data;
  }
  
  throw new Error('Failed');
}
  </code></pre>
</section>
```

### Auto-Animate Code Changes

```html
<section data-auto-animate>
  <pre data-id="code"><code data-trim>
    let planets = [
      { name: 'mars', diameter: 6779 }
    ]
  </code></pre>
</section>
<section data-auto-animate>
  <pre data-id="code"><code data-trim>
    let planets = [
      { name: 'mars', diameter: 6779 },
      { name: 'earth', diameter: 12742 }
    ]
  </code></pre>
</section>
```

### Navigation Configuration

```javascript
Reveal.initialize({
  // Navigation controls
  controls: true,
  controlsLayout: 'bottom-right',
  controlsBackArrows: 'faded',
  
  // Progress and numbering
  progress: true,
  slideNumber: 'c/t',
  
  // Navigation mode
  navigationMode: 'default', // 'linear' | 'grid'
  
  // Keyboard and touch
  keyboard: true,
  touch: true,
  
  plugins: [RevealHighlight]
});
```

### Slide Transitions

```html
<!-- Per-slide transitions -->
<section data-transition="slide">Default slide</section>
<section data-transition="zoom" data-transition-speed="fast">
  Zoom transition
</section>
<section data-transition="slide-in fade-out">
  Different in/out effects
</section>
```

```javascript
// Global transition settings
Reveal.initialize({
  transition: 'slide',
  transitionSpeed: 'default',
  backgroundTransition: 'fade'
});
```

### Custom Styling with States

```html
<section data-state="make-it-pop">
  <h2>Custom styled slide</h2>
</section>
```

```css
.make-it-pop {
  filter: drop-shadow(0 0 10px purple);
}

.make-it-pop h2 {
  color: #ff6b6b;
}
```

### Fragment Animations

```html
<section>
  <p class="fragment fade-in">Appears first</p>
  <p class="fragment highlight-blue">Highlights blue</p>
  <p class="fragment fade-in-then-out">Shows then hides</p>
</section>
```

## Common Mistakes

- **Missing `data-trim`**: Code blocks show unwanted indentation
- **Wrong bracket syntax**: Use `[1-2|3]` not `(1-2|3)` for line highlights
- **Auto-animate without `data-id`**: Elements won't animate between slides
- **Plugin not registered**: Syntax highlighting fails silently
- **Navigation mode confusion**: `linear` removes up/down arrows entirely