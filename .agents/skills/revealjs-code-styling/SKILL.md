---
name: revealjs-code-styling
description: Reveal.js styling for code demonstrations with syntax highlighting and themes. Use when creating slide presentations with code blocks, applying syntax highlighting, customizing themes, or building step-by-step code demonstrations with line highlighting and animations.
---

# Reveal.js Code & Styling

Presentation framework for creating slides with code demonstrations and custom styling.

## When to Apply

- Creating slide presentations with syntax-highlighted code blocks
- Building step-by-step code walkthroughs with line highlighting
- Customizing presentation themes and visual styling
- Implementing animated code transitions between slides

## Critical Rules

**Highlight.js Plugin Required**: Always include RevealHighlight plugin and CSS theme for syntax highlighting

```html
<!-- WRONG - no syntax highlighting -->
<pre><code>
let a = 1;
</code></pre>

<!-- RIGHT - with highlight.js integration -->
<link rel="stylesheet" href="plugin/highlight/monokai.css" />
<script src="plugin/highlight/highlight.js"></script>
<script>
  Reveal.initialize({
    plugins: [RevealHighlight]
  });
</script>
```

**Step Highlighting Syntax**: Use pipe `|` separator for sequential code highlighting

```html
<!-- WRONG - shows all highlights at once -->
<pre><code data-line-numbers="1-3,5-7">

<!-- RIGHT - shows highlights in steps -->
<pre><code data-line-numbers="1-3|5-7|9">
```

## Key Patterns

### Code Block Setup

```html
<pre><code data-trim data-noescape class="language-python">
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
</code></pre>
```

### Step-by-Step Line Highlighting

```html
<pre><code data-line-numbers="1|2-4|6-8" data-trim>
function processData(items) {
    const filtered = items.filter(item => item.active);
    const mapped = filtered.map(item => ({
        id: item.id,
        name: item.name
    }));
    
    return mapped.sort((a, b) => a.name.localeCompare(b.name));
}
</code></pre>
```

### Animated Code Transitions

```html
<section data-auto-animate>
  <pre data-id="code"><code data-trim data-line-numbers>
    let items = [];
  </code></pre>
</section>
<section data-auto-animate>
  <pre data-id="code"><code data-trim data-line-numbers>
    let items = [
        { id: 1, name: 'Apple' },
        { id: 2, name: 'Banana' }
    ];
  </code></pre>
</section>
```

### Theme Application

```html
<!-- Built-in themes: black, white, league, beige, sky, night, serif, simple, solarized, blood, moon -->
<link rel="stylesheet" href="dist/theme/night.css" />

<!-- With highlight.js themes -->
<link rel="stylesheet" href="plugin/highlight/github-dark.css" />
```

### Custom Fragment Effects

```css
.fragment.highlight-current-red {
    opacity: 1;
    visibility: inherit;
}
.fragment.highlight-current-red.current-fragment {
    color: #ff2c2d;
}
```

```html
<section>
    <p class="fragment highlight-current-red">First point</p>
    <p class="fragment highlight-current-red">Second point</p>
    <p class="fragment highlight-current-red">Third point</p>
</section>
```

### State-Based Styling

```html
<section data-state="custom-slide">
    <h1>Special Slide</h1>
</section>
```

```css
.custom-slide .reveal {
    background: linear-gradient(45deg, #1e3c72, #2a5298);
}
.custom-slide h1 {
    color: white;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
}
```

## Common Mistakes

- **Missing data-trim**: Code blocks retain leading whitespace without `data-trim`
- **Wrong line number syntax**: Use ranges `1-5` and steps `1-3|5-7`, not `1,2,3,4,5`
- **Missing language class**: Specify `class="language-javascript"` for proper syntax highlighting
- **Forgetting auto-animate IDs**: Use `data-id` on `<pre>` elements for smooth code transitions