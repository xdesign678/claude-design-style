# UI States Reference

Empty states, skeleton loading, toast notifications, and error pages for the Anthropic/Claude design style.

## Empty States

### Anatomy

Every empty state has three layers: illustration (optional) + heading + description + CTA (optional). Keep tone calm and helpful, not apologetic.

```css
.empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 64px 32px;
  gap: 12px;
}

.empty-state-icon {
  width: 48px;
  height: 48px;
  color: var(--text-tertiary);
  margin-bottom: 8px;
}

.empty-state-title {
  font-family: var(--font-sans);
  font-size: 16px;
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
}

.empty-state-desc {
  font-family: var(--font-sans);
  font-size: 14px;
  color: var(--text-secondary);
  max-width: 320px;
  line-height: 1.6;
  margin: 0;
}

.empty-state .btn-primary {
  margin-top: 8px;
}
```

### Three Empty State Types

```html
<!-- 1. Onboarding / First use -->
<div class="empty-state">
  <svg class="empty-state-icon"><!-- inbox icon --></svg>
  <h3 class="empty-state-title">No conversations yet</h3>
  <p class="empty-state-desc">Start a new conversation to begin exploring.</p>
  <button class="btn-primary">New Conversation</button>
</div>

<!-- 2. No results (after search/filter) -->
<div class="empty-state">
  <svg class="empty-state-icon"><!-- search icon --></svg>
  <h3 class="empty-state-title">No results found</h3>
  <p class="empty-state-desc">Try adjusting your search or filters.</p>
</div>

<!-- 3. Error / Failed to load -->
<div class="empty-state">
  <svg class="empty-state-icon"><!-- alert icon --></svg>
  <h3 class="empty-state-title">Something went wrong</h3>
  <p class="empty-state-desc">We couldn't load this content. Please try again.</p>
  <button class="btn-secondary">Retry</button>
</div>
```

---

## Skeleton Loading

### Design Principles

- Background: `var(--bg-hover)` — slightly darker than page
- Animation: gentle pulse (opacity 1 → 0.5 → 1), 2s duration
- Shimmer effect: subtle left-to-right gradient sweep (optional, more polished)
- Border-radius: match the actual content it represents

```css
@keyframes skeleton-pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.45; }
}

@keyframes skeleton-shimmer {
  0% { background-position: -200% 0; }
  100% { background-position: 200% 0; }
}

/* Base skeleton */
.skeleton {
  background: var(--bg-hover);
  border-radius: 4px;
  animation: skeleton-pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

/* Shimmer variant (more polished) */
.skeleton-shimmer {
  background: linear-gradient(
    90deg,
    var(--bg-hover) 25%,
    var(--bg-muted) 50%,
    var(--bg-hover) 75%
  );
  background-size: 200% 100%;
  animation: skeleton-shimmer 1.8s linear infinite;
}
```

### Common Skeleton Variants

```css
.skeleton-text      { height: 14px; border-radius: 3px; }
.skeleton-text-lg   { height: 18px; border-radius: 3px; }
.skeleton-heading   { height: 24px; border-radius: 4px; width: 60%; }
.skeleton-avatar    { width: 32px; height: 32px; border-radius: 8px; flex-shrink: 0; }
.skeleton-avatar-lg { width: 48px; height: 48px; border-radius: 12px; }
.skeleton-badge     { height: 20px; width: 60px; border-radius: 4px; }
.skeleton-button    { height: 36px; width: 100px; border-radius: 7.5px; }
.skeleton-card      { height: 120px; border-radius: 8px; }
.skeleton-image     { border-radius: 8px; } /* set width/height inline */
```

### Card Skeleton Pattern

```html
<div class="card" aria-busy="true" aria-label="Loading...">
  <div style="display:flex; gap:12px; align-items:center; margin-bottom:16px;">
    <div class="skeleton skeleton-avatar"></div>
    <div style="flex:1; display:flex; flex-direction:column; gap:6px;">
      <div class="skeleton skeleton-text" style="width:70%;"></div>
      <div class="skeleton skeleton-text" style="width:40%;"></div>
    </div>
  </div>
  <div style="display:flex; flex-direction:column; gap:8px;">
    <div class="skeleton skeleton-text" style="width:100%;"></div>
    <div class="skeleton skeleton-text" style="width:90%;"></div>
    <div class="skeleton skeleton-text" style="width:60%;"></div>
  </div>
</div>
```

### Dark Mode Skeletons

```css
.dark .skeleton {
  background: var(--bg-hover);  /* #2a2a27 — already appropriate */
}
.dark .skeleton-shimmer {
  background: linear-gradient(
    90deg,
    var(--bg-hover) 25%,
    #333330 50%,
    var(--bg-hover) 75%
  );
  background-size: 200% 100%;
}
```

---

## Toast / Notifications

### Placement and Stack

- Default position: **bottom-center** (matches claude.ai) or bottom-right
- Max width: 380px
- Stack top-to-bottom, newest at bottom
- Auto-dismiss: 4000ms (success/info), 6000ms (error — user needs to read)

```css
/* Toast container */
.toast-container {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 2000;
  display: flex;
  flex-direction: column;
  gap: 8px;
  pointer-events: none;
}

/* Toast base */
.toast {
  padding: 12px 16px;
  border-radius: 8px;
  font-family: var(--font-sans);
  font-size: 14px;
  line-height: 1.5;
  display: flex;
  align-items: center;
  gap: 10px;
  min-width: 280px;
  max-width: 380px;
  box-shadow: var(--shadow-md);
  pointer-events: all;
  animation: toast-in 300ms cubic-bezier(0, 0, 0.2, 1) forwards;
}

@keyframes toast-in {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes toast-out {
  from { opacity: 1; transform: translateY(0); }
  to   { opacity: 0; transform: translateY(8px); }
}

/* Default — neutral dark */
.toast {
  background: var(--bg-button);
  color: var(--text-on-button);
}

/* Success */
.toast.success {
  background: #1a3d2b;
  color: #d1fae5;
}

/* Error */
.toast.error {
  background: #3d1a1a;
  color: #fecaca;
}

/* Warning */
.toast.warning {
  background: #3d2e0a;
  color: #fef3c7;
}

.toast .icon {
  width: 16px;
  height: 16px;
  flex-shrink: 0;
}

.toast-close {
  margin-left: auto;
  background: none;
  border: none;
  color: inherit;
  opacity: 0.6;
  cursor: pointer;
  padding: 2px;
  line-height: 1;
  transition: opacity 150ms ease;
}
.toast-close:hover { opacity: 1; }
```

### Accessibility

```html
<!-- Toast region — screen readers announce changes -->
<div
  role="status"
  aria-live="polite"
  aria-atomic="true"
  class="toast-container"
  id="toast-container"
>
  <!-- Toasts injected here -->
</div>

<!-- For errors (higher urgency): aria-live="assertive" -->
```

---

## Progress Bar

```css
/* Linear progress */
.progress-bar {
  height: 4px;
  background: var(--bg-hover);
  border-radius: 2px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: var(--text-primary);
  border-radius: 2px;
  transition: width 300ms ease;
}

/* Indeterminate (unknown duration) */
@keyframes indeterminate {
  0%   { transform: translateX(-100%) scaleX(0.5); }
  50%  { transform: translateX(0%) scaleX(0.5); }
  100% { transform: translateX(200%) scaleX(0.5); }
}

.progress-bar.indeterminate .progress-fill {
  width: 50%;
  animation: indeterminate 1.5s ease-in-out infinite;
}

/* Page-level progress (NProgress-style top bar) */
.page-progress {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: var(--text-primary);
  z-index: 9999;
  transform-origin: left;
}
```

---

## Error Pages

### 404

```html
<div class="error-page">
  <p class="error-code">404</p>
  <h1 class="error-title">Page not found</h1>
  <p class="error-desc">The page you're looking for doesn't exist or has been moved.</p>
  <a href="/" class="btn-primary">Back to home</a>
</div>
```

```css
.error-page {
  min-height: calc(100vh - 68px);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 64px 32px;
  gap: 12px;
}

.error-code {
  font-family: var(--font-sans);
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-tertiary);
  margin: 0 0 8px;
}

.error-title {
  font-family: var(--font-sans);
  font-size: clamp(1.75rem, 1.52rem + 0.98vw, 2.5rem);
  font-weight: 600;
  color: var(--text-primary);
  letter-spacing: -0.01em;
  margin: 0;
}

.error-desc {
  font-size: 16px;
  color: var(--text-secondary);
  max-width: 400px;
  line-height: 1.6;
  margin: 0 0 16px;
}
```

### Offline Banner

```css
.offline-banner {
  position: fixed;
  top: 68px;  /* below nav */
  left: 50%;
  transform: translateX(-50%);
  padding: 10px 20px;
  background: var(--bg-button);
  color: var(--text-on-button);
  border-radius: 0 0 8px 8px;
  font-size: 13px;
  z-index: 500;
  display: flex;
  align-items: center;
  gap: 8px;
}
```

---

## Pagination

```css
.pagination {
  display: flex;
  align-items: center;
  gap: 4px;
}

.page-btn {
  min-width: 32px;
  height: 32px;
  border-radius: 7.5px;
  border: 1px solid transparent;
  background: transparent;
  color: var(--text-secondary);
  font-family: var(--font-sans);
  font-size: 14px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 150ms ease;
}

.page-btn:hover {
  background: var(--bg-hover);
  color: var(--text-primary);
}

.page-btn.active {
  background: var(--bg-button);
  color: var(--text-on-button);
  border-color: var(--bg-button);
}

.page-btn:disabled {
  opacity: 0.3;
  cursor: not-allowed;
}

.page-ellipsis {
  color: var(--text-tertiary);
  font-size: 14px;
  padding: 0 4px;
  line-height: 32px;
}

/* Page info label */
.pagination-info {
  font-size: 13px;
  color: var(--text-secondary);
  margin-left: 8px;
}
```
