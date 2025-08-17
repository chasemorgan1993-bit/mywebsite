# Green Color Migration Strategy

## Phase 1: Setup CSS Variables (✅ Complete)
- [x] Create comprehensive CSS variable system
- [x] Define semantic color names
- [x] Include opacity variants and gradients

## Phase 2: Include Variables in Base Template
1. Add CSS variables import to base layout
2. Test variable availability across all pages
3. Verify no conflicts with existing styles

## Phase 3: Systematic Color Replacement

### Step 1: Find All Green Color Instances
Use these search patterns to locate colors:

**Hex Colors:**
```bash
# Find all green hex colors
grep -r "#7ED957\|#ACE1AF\|#6BC242" layouts/ content/ static/
```

**RGB/RGBA Colors:**
```bash
# Find RGB green values
grep -r "rgb.*126.*217.*87\|rgb.*172.*225.*175" layouts/ content/ static/
```

**Gradient Patterns:**
```bash
# Find green gradients
grep -r "linear-gradient.*#7ED957\|linear-gradient.*#ACE1AF" layouts/ content/ static/
```

### Step 2: Replace by Component Priority
1. **Buttons and CTAs** (highest priority)
2. **Navigation elements**
3. **Card borders and backgrounds**
4. **Text links and accents**
5. **Hover states and transitions**

### Step 3: Update Files in Order
1. `layouts/_default/baseof.html` (main CSS)
2. `layouts/shortcodes/fee-calculator.html`
3. `content/blog/choosing-payment-processor.md` (inline styles)
4. Any other components with green colors

## Phase 4: Testing and Validation
1. Visual regression testing
2. Cross-browser compatibility
3. Mobile responsiveness check
4. Accessibility contrast validation

## Phase 5: Documentation and Guidelines
1. Create component usage guide
2. Document color hierarchy rules
3. Establish brand consistency guidelines

---

## Find and Replace Patterns

### Regex Patterns for Color Replacement

**Find bright green hex:**
```regex
#7ED957
```
**Replace with:**
```
var(--color-primary)
```

**Find light green hex:**
```regex
#ACE1AF
```
**Replace with:**
```
var(--color-primary-light)
```

**Find green gradients:**
```regex
linear-gradient\(135deg,\s*#ACE1AF,\s*#7ED957\)
```
**Replace with:**
```
var(--gradient-primary)
```

**Find green with opacity:**
```regex
rgba\(172,\s*225,\s*175,\s*0\.[0-9]+\)
```
**Replace with:**
```
var(--green-[opacity-level])
```

### VS Code Find/Replace Commands

1. Open VS Code
2. Use Ctrl/Cmd + Shift + F for global search
3. Enable regex mode (.*) 
4. Search for patterns above
5. Replace systematically

---

## Color Usage Guidelines

### Component-Specific Applications

#### Buttons
```css
/* Primary Button */
.button-primary {
  background: var(--btn-primary-bg);
  color: var(--btn-primary-text);
  border: 2px solid var(--btn-primary-border);
}

.button-primary:hover {
  background: var(--color-primary-dark);
  transform: translateY(-2px);
  box-shadow: 0 15px 35px var(--shadow-green-hover);
}
```

#### Links
```css
a {
  color: var(--text-link);
  text-decoration: none;
}

a:hover {
  color: var(--text-link-hover);
  text-decoration: underline;
}
```

#### Cards
```css
.card {
  background: var(--card-bg);
  border: 2px solid var(--card-border);
  box-shadow: 0 4px 12px var(--card-shadow);
}

.card:hover {
  border-color: var(--card-hover-border);
  box-shadow: 0 15px 30px var(--card-hover-shadow);
}
```

#### Form Elements
```css
input, select, textarea {
  border: 2px solid var(--form-border);
  background: var(--form-bg);
}

input:focus, select:focus, textarea:focus {
  border-color: var(--form-focus-border);
  box-shadow: 0 0 0 3px var(--form-focus-shadow);
}
```

---

## Brand Consistency Rules

### Color Hierarchy
1. **Primary Green** (`--color-primary`): Main CTAs, important buttons
2. **Light Green** (`--color-primary-light`): Borders, subtle accents
3. **Dark Green** (`--color-primary-dark`): Hover states, active elements

### Usage Guidelines
- **Headlines**: Use primary text color, accent with primary green
- **Body Text**: Always use `--text-primary` for readability
- **Links**: Use `--text-link` with `--text-link-hover` for interactions
- **Buttons**: Primary actions use `--btn-primary-*`, secondary use outlines
- **Borders**: Use `--border-primary` for main elements, `--border-secondary` for subtle divisions
- **Backgrounds**: Maintain contrast ratios above 4.5:1 for accessibility

### Never Use Bright Greens For:
- Large background areas (overwhelming)
- Body text (poor readability)
- Multiple elements at once (reduces hierarchy)

---

## Cross-Browser Testing Checklist

### Desktop Browsers
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)

### Mobile Browsers
- [ ] Chrome Mobile
- [ ] Safari iOS
- [ ] Samsung Internet
- [ ] Firefox Mobile

### Test Points
- [ ] Color accuracy across browsers
- [ ] CSS variable support
- [ ] Gradient rendering
- [ ] Hover states functionality
- [ ] Focus states visibility
- [ ] High contrast mode compatibility

### Accessibility Testing
- [ ] WCAG AA contrast ratios (4.5:1 minimum)
- [ ] Color blindness simulation
- [ ] Screen reader compatibility
- [ ] Keyboard navigation visibility

---

## Implementation Order

1. **Import CSS variables** into base template
2. **Replace button colors** (highest visual impact)
3. **Update navigation** elements
4. **Migrate card components**
5. **Convert text links**
6. **Update form elements**
7. **Test all hover states**
8. **Validate accessibility**
9. **Document final color system**