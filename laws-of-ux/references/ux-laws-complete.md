# All 30 Laws of UX — Complete Reference

Source: lawsofux.com. Each law includes definition, when to apply, violation signals, and code fix.

---

## Visual Hierarchy & Perception

### 1. Aesthetic-Usability Effect
**Definition:** Users perceive aesthetically pleasing design as design that's more usable.
**When:** Every component. Polish is not optional.
**Violation:** Unstyled defaults, no hover states, inconsistent border-radius, no transitions.
**Fix:** Add `transition: all 200ms`, consistent radius system (card 12px, badge 6px, pill 9999px), subtle shadows, hover transforms.

### 2. Law of Prägnanz (Simplicity)
**Definition:** People perceive and interpret ambiguous or complex images as the simplest form possible.
**When:** Icons, layouts, data visualization, any complex display.
**Violation:** Overly detailed icons, cluttered layouts, too many visual treatments competing.
**Fix:** Remove decorative elements that don't serve function. Use whitespace generously. Simplify icon strokes.

### 3. Von Restorff Effect (Isolation)
**Definition:** When multiple similar objects are present, the one that differs from the rest is most likely to be remembered.
**When:** CTAs, alerts, new features, badges, important data points.
**Violation:** All elements same weight/color, primary CTA doesn't stand out, no visual emphasis on key data.
**Fix:** Accent color on primary CTA, `font-weight: 600`, `box-shadow`, or `ring` on the element that matters most.

### 4. Law of Similarity
**Definition:** The human eye tends to perceive similar elements in a design as a complete picture, shape, or group.
**When:** Cards, badges, nav items, status indicators, button groups.
**Violation:** Same-type elements styled inconsistently (different card heights, mixed badge shapes).
**Fix:** Consistent styling per element type. All cards same structure, all badges same shape, all status indicators same size.

### 5. Law of Proximity
**Definition:** Objects that are near, or proximate to each other, tend to be grouped together.
**When:** Form fields, action buttons, metadata, any grouped content.
**Violation:** Equal spacing everywhere, related items far apart, unrelated items too close.
**Fix:** `gap: 0.5rem` within groups, `gap: 2rem` between groups. Tailwind: `gap-2` within, `gap-8` between.

### 6. Law of Common Region
**Definition:** Elements tend to be perceived into groups if they are sharing an area with a clearly defined boundary.
**When:** Cards, sections, toolbars, grouped settings.
**Violation:** Flat layout with no visual containers, heavy black borders, missing section backgrounds.
**Fix:** Subtle background (`bg-muted/50`), `border border-border/50`, `rounded-xl`, or `shadow-sm` to define regions.

### 7. Law of Uniform Connectedness
**Definition:** Elements that are visually connected are perceived as more related than elements with no connection.
**When:** Timelines, step indicators, flowcharts, category-coded items.
**Violation:** Steps without connecting lines, color codes that don't flow through related elements.
**Fix:** Connecting lines between steps (`border-l-2`), consistent color families across related items.

---

## Cognitive Load & Decision Making

### 8. Cognitive Load
**Definition:** The amount of mental resources needed to understand and interact with an interface.
**When:** Every component — always minimize mental effort.
**Violation:** Too much info at once, no hierarchy, requiring users to remember previous context.
**Fix:** Progressive disclosure (`<details>`), clear visual hierarchy, smart defaults, contextual help.

### 9. Hick's Law
**Definition:** The time it takes to make a decision increases with the number and complexity of choices.
**When:** Menus, dropdowns, action lists, settings, filter panels.
**Violation:** More than 7 options visible, no grouping, no default selected.
**Fix:** Max 5-7 visible options. Group into categories. Provide defaults. Use "More" overflow for extras.

### 10. Miller's Law
**Definition:** The average person can only keep 7 (plus or minus 2) items in their working memory.
**When:** Nav items, tabs, dashboard cards, table columns.
**Violation:** 12 nav items, 15 dashboard metrics, 10+ columns visible.
**Fix:** 5-7 items per group. Paginate or collapse extras. Group related items under categories.

### 11. Chunking
**Definition:** A process by which individual pieces of an information set are broken down and then grouped together in a meaningful whole.
**When:** Long forms, data tables, content feeds, settings pages.
**Violation:** 20-field form with no sections, wall of text, undivided lists.
**Fix:** `<fieldset>` with `<legend>` for form sections. Section headers. Visual separators between logical groups.

### 12. Choice Overload
**Definition:** The tendency for people to get overwhelmed when they are presented with a large number of options.
**When:** Filters, dropdowns, feature toggles, pricing tiers.
**Violation:** 15 filter options visible, 8 pricing tiers, every toggle exposed.
**Fix:** "Recommended" label, smart defaults, collapsible advanced sections, max 3-4 primary options.

### 13. Cognitive Bias
**Definition:** Systematic patterns of deviation from norm or rationality in judgment.
**When:** Social proof, pricing, urgency indicators, recommendations.
**Violation:** Missing social proof, no anchoring, no scarcity signals where appropriate.
**Fix:** Show counts ("1,234 users"), anchor high ("was $99, now $49"), activity indicators ("3 people viewing").

---

## Interaction & Behavior

### 14. Fitts's Law
**Definition:** The time to acquire a target is a function of the distance to and size of the target.
**When:** Buttons, links, toggles, checkboxes, any clickable element.
**Violation:** Tiny click targets, primary CTA same size as secondary, important actions far from cursor.
**Fix:** Primary CTA `min-h-11 min-w-[120px]`. Touch targets `min-44px`. Destructive actions smaller and distant from primary.

### 15. Doherty Threshold
**Definition:** Productivity soars when a computer and its users interact at a pace (<400ms) that ensures that neither has to wait on the other.
**When:** Button clicks, API calls, form submissions, page transitions.
**Violation:** No loading indicator, spinner instead of skeleton, laggy transitions, blocking UI during requests.
**Fix:** Optimistic updates, skeleton loaders matching content shape, `transition: all 200ms`, progress indicators.

### 16. Flow
**Definition:** The mental state in which a person performing an activity is fully immersed in a feeling of energized focus.
**When:** Task-focused views, editors, wizards, creative tools.
**Violation:** Unnecessary confirmations, pop-ups interrupting work, forced context switches.
**Fix:** Remove unnecessary dialogs, auto-save, smooth transitions, don't force users out of their current task.

### 17. Goal-Gradient Effect
**Definition:** The tendency to approach a goal increases with proximity to the goal.
**When:** Multi-step flows, wizards, onboarding, uploads, progress tracking.
**Violation:** No progress indicator, no "step X of Y", no visual completion percentage.
**Fix:** Progress bar with percentage, "Step 2 of 4" label, completion celebration at end.

---

## Memory & Recall

### 18. Serial Position Effect
**Definition:** Users have a propensity to best remember the first and last items in a series.
**When:** Navigation, lists, dashboard metrics, table columns.
**Violation:** Most important items buried in the middle, random ordering.
**Fix:** Most important nav items first and last. Key table column leftmost, action column rightmost. Primary metric top-left.

### 19. Peak-End Rule
**Definition:** People judge an experience largely based on how they felt at its peak and at its end, rather than the total experience.
**When:** Success states, error states, empty states, onboarding completion.
**Violation:** Plain "Success" text, blank empty states, error dead-ends, no completion celebration.
**Fix:** Celebratory success states (icon + message + next action), inviting empty states with CTA, helpful error recovery.

### 20. Zeigarnik Effect
**Definition:** People remember uncompleted or interrupted tasks better than completed tasks.
**When:** Progress trackers, draft indicators, incomplete profiles, streak counters.
**Violation:** No indication of incomplete items, no draft state, no "X items remaining".
**Fix:** "3 tasks remaining" badges, draft indicators, progress trackers that show what's left.

### 21. Working Memory
**Definition:** A cognitive system that temporarily holds and manipulates information needed to complete tasks.
**When:** Multi-screen flows, reference data, complex forms.
**Violation:** Requiring users to remember info from a previous screen, no persistent context.
**Fix:** Breadcrumbs, persistent summaries, inline reference, don't require memorization across pages.

---

## System Design Principles

### 22. Jakob's Law
**Definition:** Users spend most of their time on other sites. This means that users prefer your site to work the same way as all the other sites they already know.
**When:** Navigation, forms, tables, search, e-commerce flows.
**Violation:** Nav on the right side, search at bottom, unconventional form layouts, non-standard icons.
**Fix:** Left sidebar or top nav, search top-right, profile top-right, tables with sort headers + bottom pagination, labels above inputs.

### 23. Postel's Law (Robustness)
**Definition:** Be liberal in what you accept, and conservative in what you send.
**When:** Search inputs, form fields, filters, any user input.
**Violation:** Strict input validation that rejects valid entries, no fuzzy matching, format-sensitive fields.
**Fix:** Fuzzy search, flexible date formats, trim whitespace, case-insensitive matching, helpful error messages.

### 24. Tesler's Law (Conservation of Complexity)
**Definition:** For any system there is a certain amount of complexity which cannot be reduced.
**When:** Configuration, settings, advanced features.
**Violation:** All complexity exposed to user, no defaults, every option visible.
**Fix:** Smart defaults, "Recommended" presets, advanced options in collapsible sections, complexity handled by system.

### 25. Occam's Razor
**Definition:** Among competing hypotheses that predict equally well, the one with the fewest assumptions should be selected.
**When:** Feature design, UI flows, component architecture.
**Violation:** Extra buttons, redundant elements, features that serve no user need.
**Fix:** Remove elements that don't serve function. One clear CTA over multiple competing actions. Simplest solution wins.

### 26. Pareto Principle (80/20)
**Definition:** For many events, roughly 80% of the effects come from 20% of the causes.
**When:** Feature prioritization, dashboard design, layout hierarchy.
**Violation:** All features equal weight, dashboard shows everything, no hierarchy.
**Fix:** Identify 2-3 key user actions per page. Make primary flow frictionless. Dashboard shows only actionable metrics.

---

## Attention & Focus

### 27. Selective Attention
**Definition:** The process of directing our awareness to relevant stimuli while ignoring irrelevant stimuli.
**When:** Data display, dashboards, complex pages, search results.
**Violation:** Everything same visual weight, no emphasis on current task, competing visual elements.
**Fix:** Bold/accent only key data points. Mute secondary info (smaller, lighter, `text-muted-foreground`). Clear hierarchy.

### 28. Mental Model
**Definition:** What the user believes about the system at hand, based on their past experiences.
**When:** Any interface — users bring expectations from similar apps.
**Violation:** Unfamiliar terminology, icons that don't match meaning, unexpected workflow order.
**Fix:** Use standard terminology, conventional icons, expected workflow order. Kanban = Trello-like, tables = spreadsheet-like.

### 29. Paradox of the Active User
**Definition:** Users never read manuals but start using the software immediately.
**When:** Onboarding, first-time UX, tooltips, help systems.
**Violation:** Long instruction pages, required tutorials, non-obvious interfaces.
**Fix:** Self-explanatory UI, inline labels, contextual tooltips on hover, learn-by-doing onboarding.

### 30. Parkinson's Law
**Definition:** Any task will inflate until all of the available time is spent.
**When:** Form design, input constraints, task timing.
**Violation:** Unbounded text areas, no time expectations, infinite scrolling without purpose.
**Fix:** Constrained input areas (`maxLength`), clear time expectations ("takes 2 min"), auto-save, quick actions.
