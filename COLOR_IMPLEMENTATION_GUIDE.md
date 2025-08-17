# Green Color Implementation Guide

## ✅ What's Already Done

1. **CSS Variable System Created** (`static/css/variables.css`)
   - Comprehensive color palette with semantic naming
   - Component-specific variables
   - Gradient definitions
   - Opacity variants

2. **Migration Strategy Document** (`MIGRATION_GUIDE.md`)
   - Step-by-step implementation plan
   - Brand consistency rules
   - Cross-browser testing checklist

3. **CSS Variables Imported** into base template

## 🔍 Current Color Analysis

Found **25+ instances** of bright green colors that need updating:
- `#7ED957` (primary green) - 8 instances
- `#ACE1AF` (light green) - 17+ instances
- Various gradients and combinations

## 📝 Exact Find/Replace Commands

### VS Code / Text Editor Method

**Step 1: Replace Primary Green**
```
Find: #7ED957
Replace: var(--color-primary)
```

**Step 2: Replace Light Green**
```
Find: #ACE1AF
Replace: var(--color-primary-light)
```

**Step 3: Replace Green Gradients**
```
Find: linear-gradient(135deg, #ACE1AF, #7ED957)
Replace: var(--gradient-primary)
```

**Step 4: Replace Reverse Gradients**
```
Find: linear-gradient(135deg, #7ED957, #ACE1AF)
Replace: var(--gradient-primary)
```

### Command Line Method (macOS/Linux)

```bash
# Navigate to your Hugo site directory
cd /Users/chasemorgan/themerchantguide

# Replace primary green
find layouts/ -name "*.html" -exec sed -i '' 's/#7ED957/var(--color-primary)/g' {} +

# Replace light green  
find layouts/ -name "*.html" -exec sed -i '' 's/#ACE1AF/var(--color-primary-light)/g' {} +

# Replace main gradient pattern
find layouts/ -name "*.html" -exec sed -i '' 's/linear-gradient(135deg, #ACE1AF, #7ED957)/var(--gradient-primary)/g' {} +

# Also check content files
find content/ -name "*.md" -exec sed -i '' 's/#7ED957/var(--color-primary)/g' {} +
find content/ -name "*.md" -exec sed -i '' 's/#ACE1AF/var(--color-primary-light)/g' {} +
```

## 🎨 Component-Specific Guidelines

### 1. Navigation Elements
```css
/* Current */
.nav-menu a:hover {
    background: linear-gradient(135deg, #ACE1AF, #7ED957);
}

/* Updated */
.nav-menu a:hover {
    background: var(--gradient-primary);
}
```

### 2. Buttons and CTAs
```css
/* Current */
.button {
    background: linear-gradient(135deg, #ACE1AF, #7ED957);
}

/* Updated */
.button {
    background: var(--btn-primary-bg);
    color: var(--btn-primary-text);
}
```

### 3. Form Elements
```css
/* Current */
input:focus {
    border-color: #7ED957;
    box-shadow: 0 0 0 3px rgba(172, 225, 175, 0.3);
}

/* Updated */
input:focus {
    border-color: var(--form-focus-border);
    box-shadow: 0 0 0 3px var(--form-focus-shadow);
}
```

### 4. Cards and Containers
```css
/* Current */
.post-card {
    border: 2px solid #ACE1AF;
}

/* Updated */
.post-card {
    border: 2px solid var(--card-border);
}
```

### 5. Text Links
```css
/* Current */
a {
    color: #7ED957;
}

/* Updated */
a {
    color: var(--text-link);
}
```

## 🧪 Testing Protocol

### Visual Testing Checklist
- [ ] Home page payment finder tool
- [ ] Navigation hover states
- [ ] Blog post cards and content
- [ ] Fee calculator interface
- [ ] Resource page elements
- [ ] Form focus states
- [ ] Button hover effects

### Browser Testing
```bash
# Test in these browsers:
- Chrome (latest)
- Firefox (latest) 
- Safari (latest)
- Edge (latest)
```

### Mobile Testing
- iPhone Safari
- Android Chrome
- Various screen sizes

## 🎯 Brand Hierarchy Rules

### Primary Green (`--color-primary` / #7ED957)
**Use for:**
- Main CTA buttons
- Primary links
- Active states
- Key highlights

**Don't use for:**
- Body text (poor contrast)
- Large backgrounds
- Multiple elements simultaneously

### Light Green (`--color-primary-light` / #ACE1AF)
**Use for:**
- Borders and outlines
- Subtle backgrounds
- Secondary accents
- Hover state backgrounds

**Don't use for:**
- Text (insufficient contrast)
- Primary CTAs (too light)

### Gradients (`--gradient-primary`)
**Use for:**
- Button backgrounds
- Card highlights
- Navigation active states
- Special emphasis areas

**Don't use for:**
- Text backgrounds
- Large content areas

## 🚀 Implementation Steps

### Phase 1: Core Template Updates
1. Update `layouts/_default/baseof.html`
2. Update `layouts/index.html`  
3. Update `layouts/_default/list.html`
4. Update `layouts/_default/single.html`

### Phase 2: Component Updates
1. Update `layouts/shortcodes/fee-calculator.html`
2. Check any other shortcodes
3. Update inline styles in content files

### Phase 3: Content File Updates
1. Update `content/blog/choosing-payment-processor.md`
2. Check other content files for inline styles

### Phase 4: Testing & Validation
1. Visual regression testing
2. Accessibility validation
3. Cross-browser testing
4. Mobile responsiveness

## 📋 Quick Command Reference

```bash
# Find all green colors
grep -rn "#7ED957\|#ACE1AF" layouts/ content/

# Count total instances
grep -r "#7ED957\|#ACE1AF" layouts/ content/ | wc -l

# Test CSS variables are working
curl -s http://localhost:1313/css/variables.css | head -10

# Validate CSS
# Use online CSS validator or browser dev tools
```

## ✅ Success Criteria

**Complete when:**
- [ ] Zero hardcoded green hex values in codebase
- [ ] All components use CSS variables
- [ ] Visual appearance unchanged
- [ ] Hover states work correctly
- [ ] Mobile display proper
- [ ] Accessibility maintained (4.5:1 contrast)
- [ ] Cross-browser compatibility confirmed

## 🔧 Quick Start Commands

```bash
# 1. Backup current files
cp -r layouts/ layouts_backup/

# 2. Run replacements
find layouts/ -name "*.html" -exec sed -i '' 's/#7ED957/var(--color-primary)/g' {} +
find layouts/ -name "*.html" -exec sed -i '' 's/#ACE1AF/var(--color-primary-light)/g' {} +

# 3. Test immediately
# Check http://localhost:1313/ in browser

# 4. If issues, restore backup
# rm -r layouts/ && mv layouts_backup/ layouts/
```

This systematic approach will give you a maintainable, consistent color system while preserving your brand's visual identity!