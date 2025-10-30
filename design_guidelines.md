# AI Rounds Assistant - Design Guidelines

## Design Approach

**Selected Approach:** Medical Minimalism inspired by professional healthcare systems (Epic, athenahealth) with clean dashboard aesthetics

**Core Principles:**
- Clinical efficiency: Information-dense layouts optimized for rapid scanning
- Professional restraint: Medical-grade UI with soft, calming aesthetic (light gray + soft blue direction)
- Data clarity: Clear visual hierarchy for patient information and AI outputs
- Offline-ready: Visual feedback for sync states and cached data

---

## Typography System

**Font Families:**
- Primary: Inter (UI elements, body text) - via Google Fonts
- Monospace: JetBrains Mono (patient IDs, timestamps, data values)

**Hierarchy:**
- Page Titles: text-3xl font-semibold tracking-tight
- Section Headers: text-xl font-semibold
- Subsection Headers: text-lg font-medium
- Body Text: text-base font-normal leading-relaxed
- Labels: text-sm font-medium uppercase tracking-wide
- Data Values: text-lg font-mono
- Helper Text: text-sm text-muted-foreground

---

## Layout System

**Spacing Primitives:**
Use Tailwind units: 2, 4, 6, 8, 12, 16 for consistent rhythm
- Component padding: p-4 to p-6
- Section spacing: space-y-6 to space-y-8
- Card gaps: gap-4
- Dashboard grid gaps: gap-6

**Grid Structure:**
- Main dashboard: Two-column layout (sidebar + content area)
- Sidebar: Fixed width w-64, full height
- Content area: flex-1 with max-w-7xl container
- Cards: 2-3 column grids on desktop (grid-cols-1 md:grid-cols-2 lg:grid-cols-3)

---

## Component Library

### Navigation & Layout

**Sidebar Navigation:**
- Full-height fixed sidebar with subtle shadow
- Logo/branding at top (h-16)
- Main navigation items with icons (Heroicons)
- Active state: distinct background treatment
- Sync status indicator at bottom
- Compact, icon-only collapsed state option

**Top Bar:**
- Breadcrumb navigation on left
- Search/quick actions center
- User profile + settings on right
- Height: h-16
- Sticky positioning

### Dashboard Components

**Summary Cards (Key Metrics):**
- Grid of 4 cards showing: Total Summaries, Patients Today, AI Insights Generated, Offline Cache Status
- Each card: p-6 with icon, large number (text-3xl font-bold), label, and mini trend indicator
- Hover: subtle elevation change

**Patient List Table:**
- Compact table with alternating row treatment
- Columns: Patient ID (monospace), Name, Last Updated, Status Badge, Quick Actions
- Row height: h-12 for scanning efficiency
- Sortable headers with arrow indicators
- Row hover: highlight state
- Empty state: centered illustration + helper text

**AI Insights Comparison Panel:**
- Side-by-side comparison layout for 5 AI models
- Each model: dedicated column with header (model name + icon)
- Content: scrollable text area with identical height
- Visual confidence indicators (small badges)
- Expandable sections for full output
- Sticky headers during scroll

### Forms & Input

**Note Input Area:**
- Large textarea: min-h-64 with border treatment
- Character count indicator (bottom right)
- Dictation button (floating, bottom right with microphone icon from Heroicons)
- Auto-save indicator with timestamp
- Format selector buttons (SOAP/Freeform) as tabs above textarea

**Voice Transcription Interface:**
- Prominent microphone button with pulsing animation during recording
- Waveform visualization (simple bars) during dictation
- Real-time transcription text appearing below
- Stop/Cancel controls clearly visible
- Status text: "Listening...", "Processing...", "Transcription complete"

### Data Visualization

**Progress Charts (Recharts):**
- Line chart: Summaries over time (7-day, 30-day toggles)
- Bar chart: AI model usage distribution
- Donut chart: Note type breakdown (SOAP vs Freeform)
- Container: p-6 with header (text-lg font-semibold)
- Responsive: aspect-video on mobile, fixed height on desktop
- Tooltips on hover with data values

**Status Indicators:**
- Online/Offline badge: small pill shape with icon
- Sync status: animated icon when syncing
- Cache status: storage usage progress bar
- Model availability: colored dot indicators (available/unavailable)

### Content Display

**Summary Display Cards:**
- White card background with border
- Header: Patient name + ID, timestamp (text-sm text-muted)
- Summary content: prose formatting (max-w-prose)
- Tags for categories/specialties
- Action footer: Edit, Export, Share buttons (ghost variants)
- Expandable for full note view

**AI Model Output Cards:**
- Stacked or grid layout per model
- Model badge with logo/icon
- Confidence score visualization (small progress bar or star rating)
- Output text in comfortable line-height (leading-relaxed)
- Copy to clipboard button
- Collapse/expand controls

### Settings Panel

**Settings Layout:**
- Tabbed interface: General, AI Models, Offline, Account
- Two-column form layout on desktop (label left, control right)
- Clear section dividers with headings
- Google Translate toggle with description text
- API key inputs (obscured) with visibility toggle
- Save changes button (sticky at bottom on mobile)

---

## Specific Feature Implementations

### Dashboard Landing View
- Hero section: Statistics summary (4-card grid) at top
- Recent activity: Patient list table (10 most recent)
- Quick actions: Large CTA buttons (+ New Summary, Start Dictation, View Insights)
- Right sidebar: Today's stats widget + offline cache status

### Multi-AI Comparison View
- Fixed header with patient context
- 5-column grid for model outputs (equal width)
- Model headers: sticky during scroll
- Side-by-side comparison with vertical dividers
- Summary consensus section at bottom (aggregated insights)
- Export all button (top right)

### Progress Tracking Dashboard
- 3 primary charts in 2-column grid
- Time range selector (7d, 30d, 90d, All) at top right
- Summary statistics above charts (Total, Average, Peak)
- Filter controls: by date range, by AI model, by note type
- Export data button

### Offline Mode Indicators
- Persistent status bar when offline (subtle banner at top)
- Queue indicator showing pending syncs (badge count)
- Visual treatment for cached vs. live data (subtle icon)
- Sync now manual trigger button in status bar

---

## Accessibility & Interactions

- Focus states: clear outline treatment for keyboard navigation
- Skip links for main navigation
- ARIA labels for all interactive elements
- Loading states: skeleton screens for data-heavy components
- Error states: inline validation with helpful messages
- Success feedback: toast notifications (top-right, auto-dismiss)
- Confirmation dialogs for destructive actions

---

## Responsive Behavior

**Desktop (1024px+):** Full sidebar + multi-column layouts
**Tablet (768px-1023px):** Collapsible sidebar + 2-column grids
**Mobile (<768px):** Hidden sidebar (hamburger menu) + single column stacks

---

## Performance Considerations

- Lazy load AI comparison outputs
- Virtualized scrolling for long patient lists
- Debounced search/filter inputs
- Optimistic UI updates for better perceived performance
- Progressive loading for charts (show skeleton, then data)

---

This design creates a professional, efficient medical interface optimized for clinical workflows while maintaining the clean, calming aesthetic appropriate for healthcare environments.