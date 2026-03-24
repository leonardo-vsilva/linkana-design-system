# Linkana Design System

> Machine-readable design system specification for AI-assisted UI generation.
> Human-readable documentation: https://linkana.mintlify.app
> Technical rules for code review: `.claude/commands/design-check.md`

---

## 1. Visual Theme & Atmosphere

Clean, achromatic B2B SaaS product for procurement and supplier management.
Monochromatic and professional — color is used exclusively for semantic meaning
(status, feedback, data visualization), never for decoration. High information
density with structured whitespace. Every visual decision is functional.
Dark mode supported via `.dark` CSS class.

---

## 2. Color Palette & Roles

**Pure Black (#171717)** — Primary CTA buttons, filled actions, strong headings
**Off-White (#FAFAFA)** — Page backgrounds, canvas surfaces
**Neutral-100 (#F5F5F5)** — Secondary backgrounds, table header rows, hover states
**Neutral-200 (#E5E5E5)** — Card borders, input borders, dividers, separators
**Neutral-500 (#737373)** — Muted text, secondary labels, placeholders, helper text
**Neutral-800 (#262626)** — Body text, default foreground, table cells
**Pure White (#FFFFFF)** — Card surfaces, modal and popover backgrounds, input fills
**Destructive Red (#DC2626)** — Error messages, destructive action buttons, error borders
**Warning Amber (#D97706)** — Warning banners, caution status indicators
**Success Green (#16A34A)** — Approved status, success confirmations, correct answers
**Chart Orange (#F97316)** — Data visualization only
**Chart Teal (#0D9488)** — Data visualization only
**Chart Dark Blue (#1E3A5F)** — Data visualization only
**Chart Yellow (#EAB308)** — Data visualization only

---

## 3. Typography Rules

Font family: Inter, -apple-system, BlinkMacSystemFont, sans-serif.
Inter is declared explicitly — system fonts vary across OS (Segoe UI on Windows),
Inter ensures visual consistency. No other custom or decorative typefaces.

Size scale (use only these four values):
- 12px — Metadata, timestamps, counters, badge text, keyboard shortcuts
- 14px — Universal default: body, labels, descriptions, table cells, button text
- 20px — Section headings, card titles, panel headings
- 24px — Page title only — one per screen

Removed from scale: 16px, 18px, 30px. Hierarchy within body text is achieved
through weight and color, not size variation.

Weight hierarchy:
- 400 Regular — Default for all non-actionable content: body, descriptions,
  display values, helper text, table data
- 500 Medium — Interactive and navigational elements: form labels, buttons,
  nav items, column headers, active states
- 600 Semibold — All headings: card titles, section titles, page titles

700 Bold is not part of the system.

Letter spacing:
- Body (≤ 14px): default (0)
- Headings (20px, 24px): -0.01em (tracking-tight)

Line height:
- Body and labels (≤ 14px): 1.5
- Single-line headings (20px+): 1.25

Text color hierarchy — muted-foreground is the DEFAULT, foreground is the exception:
- text-foreground — Active / primary: titles, key values, selected items, inline CTAs
- text-muted-foreground — Support: body text, secondary labels, descriptions,
  helper text, display values
- text-muted-foreground/60 — Tertiary: timestamps, counters, metadata,
  keyboard shortcuts

No italic for UI elements. Maximum 2 font sizes simultaneously in utility screens
(sidebar, table, form): text-xs and text-sm. text-xl and text-2xl are exclusive
to headings.

---

## 4. Component Stylings

**Buttons:**
- Primary (Default): Filled Pure Black (#171717), white text, gently rounded edges
  (8px), 36px height, medium weight. Maximum ONE primary button per page.
- Secondary: White fill with subtle border (Neutral-200), black text, same shape.
- Ghost: No background, no border, black text — for inline actions in tables and cards.
- Destructive filled: Filled Destructive Red (#DC2626), white text — only when it is
  the sole high-emphasis action on screen.
- Destructive outline: Red border with red text, transparent fill — used when a
  destructive action must sit alongside a primary button on the same row.
- Icon button: Compact square (32px), ghost style, for edit/delete/overflow actions.
- Overflow rule: Maximum 2 buttons visible per action row. A third action and beyond
  collapse into a ••• dropdown trigger with tooltip "Mais ações".

**Cards / Containers:**
- White fill, whisper-thin border (Neutral-200), softly rounded corners (10px).
- Inner padding: 24px on all sides. Completely flat — no shadow, no elevation.
- Separation achieved through border contrast, not depth.

**Inputs / Form Fields:**
- White fill, thin border (Neutral-200), gently rounded (8px), 36px height.
- Focus: subtle 2px ring in primary color offset from the border.
- Error: red border (Destructive Red) with inline error message directly below.
- Field anatomy top-to-bottom: Label → Input → Helper text (muted) → Error text (red).
- Gap between fields: tight (16px). Gap between form sections: open (32px).
- Required fields marked with * appended to the label.

**Select / Combobox:**
- Select (dropdown chevron): for short fixed lists under ~10 options.
- Combobox (searchable dropdown): for long lists — countries, currencies, users.
- Both share the same visual treatment as inputs (same height, radius, border).

**Modals / Dialogs:**
- White surface, pronounced rounded corners (14px), dark translucent backdrop.
- Maximum 6 fields per modal. Maximum 2 columns per modal form.
- Footer: right-aligned actions with a subtle top border separator.

**Badges / Status Tags:**
- Status badge (Aprovado, Pendente, Reprovado): slightly rounded (6px), 12px text,
  20px height. Color signals semantic meaning.
- Category / label tag: fully pill-shaped (rounded-full), same height.
- Optional indicator: muted gray background with "Opcional" in small muted text.

**Tables / Lists:**
- Full content-area width. No rounded corners on cells.
- Header row: medium-weight text on a faint gray background with a bottom border.
- Data rows: 44px minimum height with a whisper-soft hover state.
- Row actions: right-aligned ghost icon buttons revealed on row hover.
- Empty state: centered layout with icon, title, description, and optional CTA.

**Navigation Sidebar:**
- 256px wide, fixed to the left edge. White with a single right border.
- Group labels: small uppercase muted text.
- Nav items: 36px height, medium weight, softly rounded on hover/active.
- Active item: faint gray background, full black text.

**Alerts / Banners:**
- Full-width within the content area, softly rounded (8px).
- Info: neutral gray background. Warning: warm amber tint. Error: light red tint.
  Success: light green tint. Each with a matching icon on the left.

---

## 5. Layout Principles

8-point spacing grid — all spacing values are multiples of 8px.
Primary scale: 8, 16, 24, 32, 40, 48, 64px.
4px used only for tight inline spacing (icon gaps, badge padding).

Page shell:
- Left sidebar: 256px fixed.
- Top app header: 64px (logo + global nav + user menu).
- Content area: starts at 256px from left, 64px from top.
- Content padding: 24px horizontal, 24px top, 40px bottom.

Container widths by context:
- Form pages (create, edit, CRUD): max 768px, horizontally centered.
- Preview and documentation pages: max 1152px, horizontally centered.
- Tables, dashboards, lists: full width — no max-width constraint.

Section rhythm:
- Section header: title (20px semibold) + optional description (14px muted) + optional action.
- Sections separated by 32px vertical gap or a 1px horizontal rule.
- Form field groups: 16px between fields, 32px between sections.

Viewport target: 1366×900px (standard laptop). Tables support horizontal scroll
on smaller viewports.
