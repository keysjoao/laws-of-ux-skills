# Component-Type → UX Laws Mapping

Quick lookup: detect what's being built, surface only the relevant laws.

## Mapping Table

| Component Type | Primary Laws (always apply) | Secondary Laws (check if relevant) |
|---|---|---|
| **Form** | Proximity, Hick's, Postel's, Chunking, Cognitive Load | Fitts's, Doherty, Miller's, Tesler's, Paradox of Active User |
| **Dashboard** | Miller's, Pareto, Serial Position, Von Restorff, Selective Attention | Chunking, Cognitive Load, Prägnanz, Aesthetic-Usability |
| **Navigation** | Jakob's, Serial Position, Hick's, Fitts's | Proximity, Similarity, Miller's, Mental Model |
| **Wizard/Stepper** | Goal-Gradient, Zeigarnik, Peak-End, Chunking, Cognitive Load | Doherty, Flow, Tesler's, Paradox of Active User |
| **List/Table** | Miller's, Chunking, Serial Position, Selective Attention | Proximity, Similarity, Hick's, Working Memory |
| **Modal/Dialog** | Cognitive Load, Fitts's, Doherty, Tesler's | Hick's, Von Restorff, Flow, Prägnanz |
| **Card Layout** | Common Region, Proximity, Similarity, Uniform Connectedness | Aesthetic-Usability, Miller's, Prägnanz, Pareto |
| **Landing/Hero** | Von Restorff, Fitts's, Aesthetic-Usability, Peak-End | Hick's, Serial Position, Cognitive Bias, Choice Overload |
| **Empty/Error State** | Peak-End, Aesthetic-Usability, Jakob's | Paradox of Active User, Mental Model, Zeigarnik |
| **Settings/Config** | Tesler's, Hick's, Choice Overload, Chunking | Jakob's, Postel's, Cognitive Load, Pareto |
| **Search** | Postel's, Doherty, Hick's, Jakob's | Miller's, Selective Attention, Working Memory |
| **Notification/Toast** | Doherty, Von Restorff, Selective Attention | Peak-End, Flow, Serial Position |
| **Sidebar** | Jakob's, Serial Position, Fitts's, Proximity | Miller's, Hick's, Similarity, Common Region |
| **Tabs** | Hick's, Miller's, Serial Position, Jakob's | Proximity, Similarity, Mental Model |
| **Pagination** | Goal-Gradient, Miller's, Fitts's | Doherty, Jakob's, Working Memory |

## Code Patterns Per Law

### Fitts's Law
```css
/* Primary CTA — large and prominent */
.primary-cta {
  min-height: 44px;
  min-width: 120px;
  padding: 12px 24px;
  font-size: 1rem;
  font-weight: 600;
}
/* Destructive action — small and distant from primary */
.destructive { font-size: 0.875rem; opacity: 0.7; }
```

### Proximity
```css
/* Tight within groups, generous between */
.field-group { gap: 0.5rem; }
.section-gap { gap: 2rem; }
/* Or in Tailwind: gap-2 within, gap-8 between */
```

### Doherty Threshold
```css
/* All interactive transitions under 400ms */
.interactive { transition: all 200ms ease; }
/* Skeleton loader shape matches content */
.skeleton { animation: pulse 1.5s ease-in-out infinite; }
```

### Hick's Law
```jsx
{/* Max 5-7 visible options. Overflow into "More" */}
{items.slice(0, 5).map(item => <NavItem key={item.id} {...item} />)}
{items.length > 5 && <MoreMenu items={items.slice(5)} />}
```

### Von Restorff Effect
```css
/* Make the key element visually distinct */
.highlight {
  background: var(--accent);
  color: var(--accent-foreground);
  font-weight: 600;
  box-shadow: 0 0 0 2px var(--accent-ring);
}
```

### Jakob's Law
```
Nav: left sidebar or top bar (never bottom for desktop)
Search: top-right area
Profile/Settings: top-right corner
Tables: sortable headers, pagination at bottom
Forms: labels above inputs, submit button bottom-right
```

### Goal-Gradient
```jsx
{/* Show progress toward completion */}
<div className="flex items-center gap-2">
  <span>Step {current} of {total}</span>
  <div className="h-2 w-full rounded bg-muted">
    <div className="h-full rounded bg-primary" 
         style={{ width: `${(current/total)*100}%` }} />
  </div>
</div>
```

### Miller's Law
```
Dashboard metrics: 4-6 key numbers, not 15
Nav items: max 5-7 per level
Table columns: 5-7 visible, rest in expandable detail
Dropdown options: group into categories if >7
```

### Peak-End Rule
```jsx
{/* Celebrate completion */}
<div className="flex flex-col items-center gap-4 py-12">
  <CheckCircle className="h-16 w-16 text-green-500" />
  <h2 className="text-2xl font-bold">All done!</h2>
  <p className="text-muted-foreground">Your changes are live.</p>
</div>

{/* Inviting empty state, not a dead end */}
<div className="flex flex-col items-center gap-4 py-12">
  <Illustration />
  <p>No items yet</p>
  <Button>Create your first item</Button>
</div>
```

### Cognitive Load
```jsx
{/* Progressive disclosure — show essentials, hide details */}
<details>
  <summary>Advanced options</summary>
  <div className="space-y-4 pt-4">
    {/* Advanced fields here */}
  </div>
</details>
```

### Chunking
```jsx
{/* Break long forms into sections */}
<fieldset className="space-y-4">
  <legend className="text-lg font-semibold">Personal Info</legend>
  {/* 3-4 fields */}
</fieldset>
<fieldset className="space-y-4">
  <legend className="text-lg font-semibold">Address</legend>
  {/* 3-4 fields */}
</fieldset>
```

### Aesthetic-Usability
```css
/* Polish every interactive element */
button { border-radius: 8px; transition: all 200ms; }
button:hover { transform: translateY(-1px); box-shadow: 0 4px 12px rgba(0,0,0,0.1); }
/* Consistent border-radius system */
.card { border-radius: 12px; }
.badge { border-radius: 6px; }
.pill { border-radius: 9999px; }
```

### Tesler's Law
```jsx
{/* Hide complexity with smart defaults */}
<Select defaultValue="recommended">
  <SelectItem value="recommended">Recommended settings</SelectItem>
  <SelectItem value="custom">Custom configuration</SelectItem>
</Select>
```

### Serial Position
```
Put most important items FIRST and LAST in any list:
- Nav: Home first, Profile/Settings last
- Table: Key column leftmost, action column rightmost
- Dashboard: Primary metric top-left, summary bottom
```
