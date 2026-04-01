# Form System Reference

Form validation states, field groups, and special inputs for the Anthropic/Claude design style.

## Form Validation States

### Color Tokens for Validation

```css
:root {
  /* Validation state colors */
  --state-error: #dc2626;          /* red — field error */
  --state-error-bg: rgba(220,38,38,0.06);
  --state-error-border: rgba(220,38,38,0.4);
  --state-warning: #d97706;        /* amber — caution */
  --state-warning-bg: rgba(217,119,6,0.06);
  --state-success: #16a34a;        /* green — valid */
  --state-success-bg: rgba(22,163,74,0.06);
  --state-success-border: rgba(22,163,74,0.3);
}
```

### Field with Validation

```css
/* Base field */
.field {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin-bottom: 20px;
}

.field-label {
  font-family: var(--font-sans);
  font-size: 14px;
  font-weight: 500;
  color: var(--text-primary);
  line-height: 1.4;
}

.field-label .required {
  color: var(--state-error);
  margin-left: 3px;
}

/* Input — default */
.field-input {
  border: 1px solid var(--border-default);
  border-radius: 7.5px;
  padding: 9px 14px;
  font-size: 15px;
  font-family: var(--font-sans);
  background: var(--bg-card);
  color: var(--text-primary);
  transition: border-color 200ms ease, box-shadow 200ms ease;
  width: 100%;
}

.field-input::placeholder {
  color: var(--text-tertiary);
}

.field-input:focus {
  outline: none;
  border-color: var(--text-secondary);
  box-shadow: 0 0 0 2px var(--ring-color);
}

/* Error state */
.field.error .field-input {
  border-color: var(--state-error-border);
  background: var(--state-error-bg);
}
.field.error .field-input:focus {
  box-shadow: 0 0 0 2px rgba(220,38,38,0.12);
}

/* Success state */
.field.success .field-input {
  border-color: var(--state-success-border);
}

/* Disabled state */
.field-input:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  background: var(--bg-muted);
}
```

### Inline Error / Helper Text

```css
.field-message {
  font-family: var(--font-sans);
  font-size: 13px;
  line-height: 1.4;
  display: flex;
  align-items: flex-start;
  gap: 5px;
}

.field-message.error {
  color: var(--state-error);
}
.field-message.helper {
  color: var(--text-secondary);
}
.field-message.success {
  color: var(--state-success);
}

.field-message .icon {
  width: 14px;
  height: 14px;
  flex-shrink: 0;
  margin-top: 1px;
}
```

### Full Field Example (React + Tailwind)

```tsx
function FormField({
  label, error, hint, required, children
}: {
  label: string;
  error?: string;
  hint?: string;
  required?: boolean;
  children: React.ReactNode;
}) {
  return (
    <div className="flex flex-col gap-1.5 mb-5">
      <label className="text-sm font-medium text-[--text-primary]">
        {label}
        {required && <span className="text-red-600 ml-0.5">*</span>}
      </label>
      {children}
      {error && (
        <p className="text-[13px] text-red-600 flex items-center gap-1">
          <AlertCircle size={13} />
          {error}
        </p>
      )}
      {hint && !error && (
        <p className="text-[13px] text-[--text-secondary]">{hint}</p>
      )}
    </div>
  );
}
```

---

## Field Groups

### Two-Column Layout

```css
.field-group {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

@media (max-width: 640px) {
  .field-group { grid-template-columns: 1fr; }
}
```

### Section Divider in Form

```css
.form-section {
  margin-top: 32px;
  padding-top: 32px;
  border-top: 1px solid var(--border-section);
}

.form-section-title {
  font-family: var(--font-sans);
  font-size: 16px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 20px;
}
```

### Form Actions (Submit Row)

```css
.form-actions {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 10px;
  margin-top: 32px;
  padding-top: 24px;
  border-top: 1px solid var(--border-section);
}
```

---

## Select / Dropdown Input

```css
.field-select {
  border: 1px solid var(--border-default);
  border-radius: 7.5px;
  padding: 9px 36px 9px 14px;
  font-size: 15px;
  font-family: var(--font-sans);
  background: var(--bg-card);
  color: var(--text-primary);
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg width='12' height='8' viewBox='0 0 12 8' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1L6 7L11 1' stroke='%235e5d59' stroke-width='1.5' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 12px center;
  cursor: pointer;
  transition: border-color 200ms ease;
}
.field-select:focus {
  outline: none;
  border-color: var(--text-secondary);
  box-shadow: 0 0 0 2px var(--ring-color);
}
```

---

## Checkbox & Radio

```css
/* Custom checkbox */
.checkbox-wrap {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  cursor: pointer;
}

.checkbox-input {
  width: 16px;
  height: 16px;
  border: 1.5px solid var(--border-default);
  border-radius: 4px;
  background: var(--bg-card);
  flex-shrink: 0;
  margin-top: 2px;
  appearance: none;
  transition: all 150ms ease;
  cursor: pointer;
}

.checkbox-input:checked {
  background: var(--bg-button);
  border-color: var(--bg-button);
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 12 10' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 5L4.5 8.5L11 1.5' stroke='%23faf9f5' stroke-width='1.8' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: center;
}

.checkbox-input:focus-visible {
  outline: none;
  box-shadow: 0 0 0 2px var(--ring-color);
}

.checkbox-label {
  font-size: 14px;
  color: var(--text-primary);
  line-height: 1.5;
}

/* Radio — same as checkbox, border-radius: 50% */
.radio-input {
  border-radius: 50%;
}
.radio-input:checked {
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 8 8' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='4' cy='4' r='2.5' fill='%23faf9f5'/%3E%3C/svg%3E");
}
```

---

## Toggle / Switch

```css
.toggle-wrap {
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
}

.toggle {
  position: relative;
  width: 36px;
  height: 20px;
  background: var(--border-default);
  border-radius: 10px;
  transition: background 200ms ease;
  flex-shrink: 0;
}

.toggle.on {
  background: var(--bg-button);
}

.toggle::after {
  content: '';
  position: absolute;
  top: 2px;
  left: 2px;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #fff;
  box-shadow: var(--shadow-sm);
  transition: transform 200ms ease;
}

.toggle.on::after {
  transform: translateX(16px);
}

.toggle-label {
  font-size: 14px;
  color: var(--text-primary);
}
```

---

## Tag Input (Chip Input)

```css
.tag-input-wrap {
  min-height: 42px;
  border: 1px solid var(--border-default);
  border-radius: 7.5px;
  padding: 6px 10px;
  background: var(--bg-card);
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  align-items: center;
  transition: border-color 200ms ease;
}
.tag-input-wrap:focus-within {
  border-color: var(--text-secondary);
  box-shadow: 0 0 0 2px var(--ring-color);
}

.tag {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  padding: 2px 8px;
  background: var(--bg-muted);
  border-radius: 4px;
  font-size: 13px;
  color: var(--text-secondary);
}

.tag-remove {
  width: 14px;
  height: 14px;
  color: var(--text-tertiary);
  cursor: pointer;
  transition: color 150ms ease;
}
.tag-remove:hover { color: var(--text-primary); }
```

---

## Multi-Step Form Indicator

```css
.steps {
  display: flex;
  align-items: center;
  gap: 0;
  margin-bottom: 40px;
}

.step {
  display: flex;
  align-items: center;
  gap: 8px;
  flex: 1;
}

.step-circle {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  border: 1.5px solid var(--border-default);
  background: var(--bg-card);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 500;
  color: var(--text-secondary);
  flex-shrink: 0;
  transition: all 200ms ease;
}

.step.active .step-circle {
  border-color: var(--text-primary);
  background: var(--bg-button);
  color: var(--text-on-button);
}

.step.done .step-circle {
  border-color: var(--text-secondary);
  background: var(--bg-muted);
  color: var(--text-secondary);
}

.step-label {
  font-size: 13px;
  color: var(--text-secondary);
}
.step.active .step-label {
  color: var(--text-primary);
  font-weight: 500;
}

/* Connector line */
.step-connector {
  flex: 1;
  height: 1px;
  background: var(--border-default);
  margin: 0 8px;
}
.step-connector.done {
  background: var(--text-secondary);
}
```

---

## Form Error Banner (Top of Form)

```css
.form-error-banner {
  padding: 12px 16px;
  border-radius: 7.5px;
  background: var(--state-error-bg);
  border: 1px solid var(--state-error-border);
  color: var(--state-error);
  font-size: 14px;
  display: flex;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 24px;
}

.form-error-banner .icon {
  flex-shrink: 0;
  margin-top: 1px;
}
```
