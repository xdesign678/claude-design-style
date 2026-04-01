# Component Library Reference

Extended component styles beyond the basics in SKILL.md. Covers code blocks, modals, dropdowns, badges, tables, blockquotes, and more.

## Code Blocks

```css
/* Container */
.code-block {
  position: relative;
  margin: 16px 0;
  border-radius: 8px;
  border: 1px solid var(--border-light);
  background: var(--bg-muted);
  overflow: hidden;
}

/* Header bar (language label + copy button) */
.code-block-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px 16px;
  border-bottom: 1px solid var(--border-light);
  background: var(--bg-secondary);
}

.code-block-lang {
  font-family: var(--font-sans);
  font-size: 12px;
  font-weight: 500;
  color: var(--text-tertiary);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.code-block-copy {
  padding: 4px 10px;
  border-radius: 4px;
  border: 1px solid var(--border-default);
  background: transparent;
  color: var(--text-secondary);
  font-size: 12px;
  cursor: pointer;
  transition: all 150ms ease;
}
.code-block-copy:hover {
  background: var(--bg-hover);
  color: var(--text-primary);
}

/* Code content */
.code-block pre {
  padding: 16px;
  margin: 0;
  overflow-x: auto;
}

.code-block code {
  font-family: var(--font-mono);
  font-size: 0.875rem;       /* 14px */
  line-height: 1.5;
  color: var(--text-primary);
}

/* Inline code */
code:not(pre code) {
  background: var(--bg-muted);
  padding: 2px 6px;
  border-radius: 4px;
  font-size: 0.9em;
  font-family: var(--font-mono);
}

/* Dark mode code blocks */
.dark .code-block {
  background: #1e1e1e;
  border-color: rgba(236,233,225,0.08);
}
.dark .code-block-header { background: #2a2a27; }
.dark .code-block code { color: #e5e5e5; }
```

### Syntax Highlighting (Warm Palette)

```css
/* Token colors (matches Anthropic's warm aesthetic) */
.token-keyword   { color: #8b6bb0; }  /* muted purple */
.token-string    { color: #7a9e5d; }  /* muted green */
.token-function  { color: #5d8ab0; }  /* muted blue */
.token-comment   { color: var(--text-tertiary); font-style: italic; }
.token-number    { color: #c47d52; }  /* warm orange */
.token-operator  { color: var(--text-secondary); }
.token-type      { color: #8b6bb0; }  /* same as keyword */
.token-variable  { color: var(--text-primary); }
```

## Dropdown / Select

```css
/* Trigger button */
.dropdown-trigger {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 12px;
  border-radius: 7.5px;
  border: 1px solid var(--border-default);
  background: var(--bg-card);
  color: var(--text-primary);
  font-size: 14px;
  cursor: pointer;
  transition: all 200ms ease;
}
.dropdown-trigger:hover {
  background: var(--bg-hover);
  border-color: var(--text-tertiary);
}

/* Dropdown panel */
.dropdown-panel {
  position: absolute;
  top: calc(100% + 4px);
  left: 0;
  min-width: 200px;
  padding: 4px;
  border-radius: 8px;
  background: var(--bg-card);
  border: 1px solid var(--border-light);
  box-shadow: var(--shadow-md);
  z-index: 100;
}

/* Dropdown item */
.dropdown-item {
  padding: 8px 12px;
  border-radius: 4px;
  font-size: 14px;
  color: var(--text-primary);
  cursor: pointer;
  transition: background 150ms ease;
}
.dropdown-item:hover { background: var(--bg-hover); }
.dropdown-item.selected {
  background: var(--bg-muted);
  font-weight: 500;
}
```

## Modal / Dialog

```css
/* Overlay */
.modal-overlay {
  position: fixed;
  inset: 0;
  background: var(--bg-overlay);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: fade-in 200ms ease;
}

/* Modal container */
.modal {
  background: var(--bg-card);
  border: 1px solid var(--border-light);
  border-radius: 12px;
  box-shadow: var(--shadow-lg);
  width: min(90vw, 480px);
  max-height: 85vh;
  overflow-y: auto;
}

/* Modal sections */
.modal-header {
  padding: 24px 24px 0;
  font-size: 18px;
  font-weight: 600;
  font-family: var(--font-sans);
  color: var(--text-primary);
}
.modal-body { padding: 16px 24px; }
.modal-footer {
  padding: 0 24px 24px;
  display: flex;
  gap: 8px;
  justify-content: flex-end;
}
```

## Badges / Tags

```css
.badge {
  display: inline-flex;
  align-items: center;
  padding: 2px 8px;
  border-radius: 4px;
  background: var(--bg-muted);
  color: var(--text-secondary);
  font-size: 12px;
  font-weight: 500;
  font-family: var(--font-sans);
  letter-spacing: 0.02em;
}

/* Category label (uppercase) */
.badge-category {
  font-size: 10px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--text-tertiary);
}
```

## Tables

```css
table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
  font-family: var(--font-sans);
}

th {
  text-align: left;
  padding: 12px 16px;
  font-weight: 600;
  color: var(--text-primary);
  border-bottom: 1px solid var(--border-default);
  background: var(--bg-secondary);
}

td {
  padding: 12px 16px;
  color: var(--text-primary);
  border-bottom: 1px solid var(--border-light);
}

tr:last-child td { border-bottom: none; }
tr:hover td { background: var(--bg-hover); }
```

## Blockquotes

```css
blockquote {
  margin: 16px 0;
  padding: 12px 24px;
  border-left: 2px solid rgba(20,20,19,0.15);
  color: var(--text-secondary);
  font-style: normal;              /* NOT italic — Anthropic convention */
}

.dark blockquote {
  border-left-color: rgba(236,233,225,0.15);
}
```

## Dividers

```css
hr {
  border: none;
  border-top: 1px solid var(--border-section);
  margin: 24px 0;
}

/* Subtle section divider */
.divider-subtle {
  border-top: 1px solid var(--border-light);
  margin: 48px 0;
}
```

## Toast / Notification

```css
.toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  padding: 12px 20px;
  border-radius: 8px;
  background: var(--bg-button);
  color: var(--text-on-button);
  font-size: 14px;
  box-shadow: var(--shadow-md);
  z-index: 2000;
  animation: fade-in-up 300ms cubic-bezier(0, 0, 0.2, 1) forwards;
}
```

## Tooltip

```css
.tooltip {
  position: absolute;
  padding: 4px 8px;
  border-radius: 4px;
  background: var(--bg-button);
  color: var(--text-on-button);
  font-size: 12px;
  white-space: nowrap;
  z-index: 100;
  pointer-events: none;
  animation: fade-in 150ms ease;
}
```

## Avatar

```css
.avatar {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  background: var(--bg-muted);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  font-weight: 500;
  color: var(--text-secondary);
  overflow: hidden;
}
.avatar img { width: 100%; height: 100%; object-fit: cover; }
```

## Tabs

```css
.tabs {
  display: flex;
  gap: 0;
  border-bottom: 1px solid var(--border-section);
}

.tab {
  padding: 8px 16px;
  font-size: 14px;
  font-weight: 400;
  color: var(--text-secondary);
  background: none;
  border: none;
  border-bottom: 2px solid transparent;
  cursor: pointer;
  transition: all 150ms ease;
  margin-bottom: -1px;
}
.tab:hover { color: var(--text-primary); }
.tab.active {
  color: var(--text-primary);
  font-weight: 500;
  border-bottom-color: var(--text-primary);
}
```

## Accordion / Collapsible

```css
.accordion-trigger {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  padding: 12px 0;
  background: none;
  border: none;
  border-bottom: 1px solid var(--border-light);
  font-size: 15px;
  font-weight: 500;
  color: var(--text-primary);
  cursor: pointer;
}

.accordion-content {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 300ms cubic-bezier(0.4, 0, 0.2, 1);
}
.accordion-content.open { grid-template-rows: 1fr; }
.accordion-content > * { overflow: hidden; }
```

## List Styles

```css
/* Unordered list */
ul {
  padding-left: 24px;
  margin: 12px 0;
}
ul li {
  margin-bottom: 4px;
  line-height: 1.6;
}
ul li::marker { color: var(--text-tertiary); }

/* Ordered list */
ol {
  padding-left: 24px;
  margin: 12px 0;
}
ol li {
  margin-bottom: 4px;
  line-height: 1.6;
}
```

## Carousel / Slider

```css
.carousel {
  position: relative;
  overflow: hidden;
}

.carousel-track {
  display: flex;
  transition: transform 400ms cubic-bezier(0.4, 0, 0.2, 1);
}

.carousel-slide {
  flex: 0 0 100%;
  padding: 0 16px;
}

/* Pagination dots */
.carousel-dots {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin-top: 24px;
}

.carousel-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--border-default);
  border: none;
  cursor: pointer;
  transition: background 200ms ease;
}
.carousel-dot.active { background: var(--text-primary); }

/* Auto-rotation: 3 second interval (match Anthropic) */
```

## Expandable / See More

```css
.expandable {
  position: relative;
}

.expandable-content {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 400ms cubic-bezier(0.4, 0, 0.2, 1);
}
.expandable-content.open { grid-template-rows: 1fr; }
.expandable-content > * { overflow: hidden; }

.expandable-trigger {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 8px 0;
  font-size: 15px;
  font-weight: 500;
  color: var(--text-secondary);
  background: none;
  border: none;
  cursor: pointer;
  transition: color 150ms ease;
}
.expandable-trigger:hover { color: var(--text-primary); }

.expandable-trigger .icon {
  width: 16px;
  height: 16px;
  transition: transform 200ms ease;
}
.expandable-trigger.open .icon { transform: rotate(180deg); }
```

## Card Grid with Hover Dimming

```css
/* Sibling dimming pattern — very Anthropic */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 24px;
}

.card-grid .card {
  transition: opacity 300ms ease, transform 300ms ease, box-shadow 300ms ease;
}

.card-grid:has(.card:hover) .card:not(:hover) {
  opacity: 0.6;
}

.card-grid .card:hover {
  transform: scale(1.02);
  box-shadow: var(--shadow-md);
}
```

## Testimonial Card

```css
.testimonial {
  background: var(--bg-secondary);
  border-radius: 12px;
  padding: 32px;
}

.testimonial-logo {
  height: 24px;
  margin-bottom: 16px;
  opacity: 0.7;
}

.testimonial-quote {
  font-family: var(--font-serif);
  font-size: 17px;
  line-height: 1.6;
  color: var(--text-primary);
  margin-bottom: 24px;
}

.testimonial-author {
  font-family: var(--font-sans);
  font-size: 14px;
  color: var(--text-secondary);
}
.testimonial-author-name {
  font-weight: 500;
  color: var(--text-primary);
}
```

## Tooltip (Hover-Intent)

```css
.tooltip-trigger {
  position: relative;
  text-decoration-style: dotted;
  text-decoration-color: var(--text-tertiary);
  text-underline-offset: 0.2em;
  cursor: help;
}

.tooltip-content {
  position: absolute;
  bottom: calc(100% + 8px);
  left: 50%;
  transform: translateX(-50%);
  min-width: 200px;
  max-width: 320px;
  padding: 12px 16px;
  border-radius: 8px;
  background: var(--bg-button);
  color: var(--text-on-button);
  font-size: 13px;
  line-height: 1.5;
  box-shadow: var(--shadow-md);
  opacity: 0;
  visibility: hidden;
  transition: opacity 150ms ease, visibility 150ms ease;
  z-index: 100;
  pointer-events: none;
}

/* Hover-intent: 120ms close delay (prevents flicker) */
.tooltip-trigger:hover .tooltip-content,
.tooltip-trigger:focus-visible .tooltip-content {
  opacity: 1;
  visibility: visible;
  transition-delay: 0ms;
}
```

## Auto-Growing Textarea

```css
.auto-grow-wrap {
  display: grid;
}
.auto-grow-wrap::after {
  content: attr(data-replicated-value) " ";
  white-space: pre-wrap;
  visibility: hidden;
  grid-area: 1 / 1 / 2 / 2;
  padding: 16px;
  font: inherit;
}
.auto-grow-wrap textarea {
  resize: none;
  overflow: hidden;
  grid-area: 1 / 1 / 2 / 2;
  padding: 16px;
  font: inherit;
}
```
