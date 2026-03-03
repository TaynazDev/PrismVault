# Changelog

All notable changes to Prism Vault will be documented in this file.

## [2.0.5] - 2026-03-03

### 💱 Currency Selector — Rebuilt from Scratch

#### Fixed
- Removed the entire broken currency implementation and rebuilt it from the ground up
- Currency selector now works reliably with searchable dropdown, live exchange rates, and correct symbol display everywhere

#### Changed
- Exchange rates fetched on page load from `https://api.exchangerate-api.com/v4/latest/USD` and cached in localStorage (`pv_exchange_rates` / `pv_rates_timestamp`)
- Settings panel now shows "Rates live" (green dot) or "Using cached rates" (amber dot) instead of a vague timestamp
- localStorage keys changed to `pv_currency_code` and `pv_currency_symbol` (old scoped keys removed)
- Conversion modal reworded: "You have existing transactions in [OLD CODE]. What would you like to do?" with two clear buttons — "Convert figures" and "Keep figures" (removed Cancel button)
- Auto-detects user's local currency on first load via `Intl.NumberFormat().resolvedOptions().locale`
- Expanded region-to-currency detection map (80+ regions)
- `getCurrencySymbol()` API preserved — all 41+ call sites across the app continue to display the correct symbol (balance, transactions, budget, progress bars, goals, group pots, charts, coulda-bought, PDF export, etc.)
- Modal uses enhanced glassmorphism styling (`backdrop-filter: blur(32px)`)
- ILS (Israeli Shekel) excluded from the currency list
- Full world currency list retained: 150+ fiat currencies, XAU/XAG/XPT/XPD (precious metals), BTC/ETH (crypto)

---

## [2.0.0] - 2026-03-03

### 📐 Layout Structure Overhaul

#### Fixed
- Removed two stray `</div>` closing tags after the Treat Yourself section that prematurely closed the `.container` and `.dashboard` wrappers
- All sections from "You Could Have Bought" through Currency selector were previously **outside** the centred `.container` — they now sit correctly inside it
- Every page section (stat cards, streak, budget, treat, coulda-bought, heatmap, charts, savings goals, group pots, transactions, leaderboard, widget settings, categories, theme picker, currency) shares the same `max-width: 900px` centred column layout
- Verified all 18 sections fall within the single `.container` div (lines 4465–4953)
- Dashboard and container `<div>` nesting is now fully balanced (depth 0 at both closing tags)
- No conflicting `width: 100vw`, `max-width: 100%`, or `position: fixed/absolute` on section containers — no additional CSS removal needed
- No changes to colours, glassmorphism styling, fonts, or functionality

---

## [1.20.0] - 2026-03-03

### 💱 Currency Selector & Multi-Currency Support

#### Added
- Full currency selector in Settings with 140+ world currencies, precious metals (XAU, XAG, XPT, XPD), and crypto (BTC, ETH)
- Searchable dropdown with flag emoji, currency name, and code for every entry
- Live exchange rates fetched from ExchangeRate-API (free tier, USD-based)
- Cached rates with timestamp display ("Rates updated X mins/hours ago")
- Conversion modal when switching currencies on existing data — choose "Convert my figures" (applies exchange rate to all amounts) or "Keep my figures" (symbol-only swap)
- Converts transactions, budget, treat pot, savings goals, and recurring rules when converting
- Browser locale auto-detection via `Intl.NumberFormat` to set sensible default currency
- `getCurrencySymbol()` used across the entire app — all hardcoded `$` signs replaced
- Currency preference persisted in localStorage (`prismPayCurrency`)
- Dark glassmorphism styling matching the app aesthetic for selector, dropdown, and modal

### 🎨 Logo Update

#### Changed
- Navbar logo updated from prism triangle to gradient circle with bold `$` dollar sign
- Logo gradient adapts to active theme via `logoGradStop1` / `logoGradStop2` IDs

---

## [1.19.0] - 2026-03-03

### 📐 Layout Consistency & Content Container

#### Changed
- All page sections now sit inside a shared `max-width: 900px` centred container
- Container uses flexbox column layout with a consistent `22px` gap between every section
- Removed per-section `margin-bottom` in favour of the unified container gap
- Header, stat cards, budget, treat yourself, heatmap, chart, savings goals, group pots, transactions, widget settings, categories, and theme picker all share the same constrained width
- Nothing stretches edge-to-edge on desktop — only the background is full-width
- Mobile (≤ 640px): container is 100% width with `16px` side padding and `18px` gap
- Small screens (≤ 390px): container tightens to `12px` side padding and `16px` gap
- No changes to colours, fonts, glassmorphism, or component-level styling

---

## [1.18.0] - 2026-03-03

### 🔍 Transaction Search & Filter Bar

#### Added
- Real-time text search input that filters by transaction description, note, or category
- Category dropdown filter populated dynamically from all used categories (default + custom)
- Date range dropdown: This Week, This Month, Last Month, All Time
- Type toggle buttons (All / Income / Expenses) replacing old filter-btn pills
- All filters work simultaneously — text + category + date + type combine for precise results
- Smooth fade-out / fade-in animation when the transaction list updates
- Empty state message adapts: different text when no transactions exist vs. no matches
- Search bar styled with glassmorphism aesthetic matching the app design

---

## [1.17.0] - 2026-03-03

### 🧾 Attach Receipt to Transactions

#### Added
- "Attach Receipt" button (📎) on each transaction in the history list
- Opens native file picker accepting JPEG and PNG images (max 2 MB)
- Converts uploaded image to base64 and stores it alongside the transaction in localStorage
- Small thumbnail preview replaces the attach button once a receipt is saved
- Clicking the thumbnail opens a fullscreen glassmorphism lightbox with the receipt image
- Lightbox closes on click-outside, close button, or pressing the × button
- Smooth zoom and hover effects on thumbnails for polished UX

---

## [1.16.0] - 2026-03-03

### 🎨 App Logo & Favicon

#### Added
- `PrismVaultAppIcon.jpeg` set as browser tab favicon and Apple touch icon
- Navbar SVG logo replaced with the actual app icon image (36×36px rounded square)
- "Prism" text retains its gradient styling, "Vault" stays white
- Responsive sizing: logo scales down gracefully across all breakpoints (32px → 26px)
- Image rendered with `border-radius` and subtle box-shadow for polished look

---

## [1.15.0] - 2026-03-03

### 📤 Export to CSV & Download PDF Report

#### Added
- "Export CSV" button in the Transactions section header with a download icon
- Generates a CSV file containing Date, Amount, Type, Category, and Note for every transaction
- Automatic browser download named `prism-vault-export-[month]-[year].csv`
- Pure JavaScript implementation using Blob and URL.createObjectURL — no external libraries
- Notes are properly escaped with double-quote wrapping for CSV compatibility
- "PDF Report" button alongside the CSV button with a document icon
- Generates a styled A4 PDF of the current month’s transactions via jsPDF (CDN)
- PDF features a branded PrismVault header with gradient-colored title
- Summary section shows total income, total expenses, net balance, and top spending category
- Full transaction table with alternating row shading and color-coded amounts (green/red)
- Pagination with footer on every page showing report month and page numbers
- Automatic download as `prism-vault-[month]-[year].pdf`
- Both buttons styled with glassmorphism hover glow and responsive layout

---

## [1.14.1] - 2026-03-03

### 💤 Inactivity Nudge

#### Added
- Friendly dismissable card appears when no transactions have been logged for 3+ days
- Dynamic message adapts: "don't fall behind" at 3 days, "don't lose track" at 7+ days with exact day count
- Glassmorphism card with amber accent border and smooth slide-in animation
- Dismiss on click hides the nudge and sets a 3-day cooldown before it can reappear
- Cooldown stored in localStorage so the nudge doesn't nag after dismissal
- Calculates inactivity gap from the most recent transaction date in localStorage
- Brand-new users (no transactions yet) get a grace period — nudge won't appear until 3 days after first visit

---

## [1.14.0] - 2026-03-03

### ⚠️ Budget Warning System

#### Added
- Dismissable warning banner at the top of the dashboard when spending reaches 80% of the set budget
- Orange glassmorphism banner with warning icon at the 80% threshold, showing remaining budget
- Red glassmorphism banner with stronger alert at 100%+ threshold, showing overspend amount
- Banner automatically re-appears with upgraded severity if spending crosses from warning to danger
- Dismiss state persisted per-session (sessionStorage) — resets each visit so users stay informed
- Browser Notification API integration: push notifications sent for each threshold level (once per session)
- Polite notification permission prompt on first load with "Enable" / "Not now" buttons
- Permission prompt only shown when browser supports Notification API and permission is still `default`
- Smooth slide-in animation for both the banner and the notification prompt

---
## [1.13.0] - 2026-03-03

### 🎛️ Dashboard Widget Settings

#### Added
- New "Dashboard Widgets" settings section for toggling individual dashboard cards on/off
- Toggleable widgets: Balance, Budget Progress, Spending Chart, Streak, Biggest Splurge, Treat Yourself Fund, and Weekly Report
- Toggle states saved to localStorage and persist across sessions
- Smooth fade-in animation when widgets are re-enabled
- Reuses existing glassmorphism toggle switch design for consistency
- Hidden widgets are fully removed from layout (no empty gaps)

---
## [1.13.1] - 2026-03-03

### 🤝 Settle Up for Group Pots

#### Added
- "Settle Up" button on each Group Pot card — marks the pot as settled across all members
- Green checkmark badge replaces the button once settled, visible to all pot members in real time
- Settlement date logged and displayed below the badge ("Settled on Mar 3, 2026")
- "Who paid last" label shows the name of the member who most recently settled the pot
- Settle status synced to Firebase Firestore via batch write to all member sub-collections
- Settled pots get a subtle green border highlight
- Optimistic local update if Firestore write fails (graceful offline support)

---

## [1.12.0] - 2026-03-03

### 👤 User Profile Page

#### Added
- Profile setup modal prompts after first sign-in for display name and avatar
- 8 illustrated emoji avatar options: 👾 🔥 🚀 💎 🌈 🐱 🧊 ✨
- Avatar and display name shown in the top nav bar next to Sign Out
- Clicking the nav avatar re-opens the profile editor to update name/avatar anytime
- Profile data (name, avatar) saved to Firebase Firestore under the user's UID
- Skip option for users who want to set up later (defaults to 👾)
- Glassmorphism profile card with gradient heading, avatar selection grid, and animated transitions
- Profile loads from Firestore on sign-in for cross-device persistence
- Firebase Auth displayName kept in sync with profile changes

---

## [1.11.0] - 2026-03-03

### ⚙️ Manage Categories

#### Added
- New "Manage Categories" settings section on the dashboard
- Users can add custom categories with a name and emoji icon
- Custom categories appear alongside defaults in the quick-add modal dropdown
- Deletion of custom categories via × button on each chip (defaults are protected)
- Visual chip display of all categories: defaults shown dimmed, custom shown with delete button
- "Defaults" and "Custom" labelled sections for clear separation
- Category name input with Enter key support for quick adding
- Emoji input field with placeholder fallback (🏷️) when left empty
- Duplicate category names prevented (case-insensitive check across defaults + custom)
- Custom categories saved to localStorage (`prismPayCustomCategories`)
- Dropdown auto-rebuilds on add/delete to keep quick-add modal in sync
- Glassmorphism card with consistent app styling

---

## [1.10.0] - 2026-03-03

### 😂 Emoji Reactions on Transactions

#### Added
- Reaction button on every transaction in the history list
- Tap the 😀 button to open a floating picker with 5 emojis: 💀😭👀🤑😂
- Selected emoji displays inline next to the transaction amount
- Tap the same emoji again to remove it (toggle behavior)
- Clicking outside the picker automatically closes it
- Glassmorphism-styled picker with blur backdrop and pop-in animation
- Firebase integration: when logged in, reactions sync to Firestore per user (`users/{uid}/transactionReactions/{txId}`) for future shared-pot visibility
- Falls back to localStorage for offline / anonymous users

---

## [1.9.0] - 2026-03-03

### 🛒 "You Could Have Bought..." Card

#### Added
- Fun "You could have bought..." comparison card on the dashboard
- Takes total monthly spending and divides by fun preset prices
- 18 relatable presets: Spotify, Chipotle burritos, cinema tickets, Uber rides, lattes, pizzas, books, indie games, bubble teas, and more
- Picks a random comparison on each page load for variety
- Glassmorphism card with purple-to-pink gradient accent
- Shows count + item name with emoji, plus spending context line
- Graceful empty state when no expenses logged yet
- Updates dynamically on every transaction change

---

## [1.8.0] - 2026-03-02

### 🗓️ Spending Heatmap

#### Added
- Calendar-grid spending heatmap for the current month
- Each day rendered as a small square tile with intensity based on daily spending
- Pink-to-blue gradient scale — darker/more saturated = more spent
- Empty/no-spend days shown as dim glassmorphism tiles
- Hover tooltip showing exact amount and date for each day
- Today highlighted with a bright border ring
- Future days dimmed out
- "Less → More" legend bar with gradient swatches
- Fully responsive — shrinks gracefully on mobile
- Pure CSS + JavaScript, no extra libraries
- Updates dynamically on every transaction change

---

## [1.7.0] - 2026-03-02

### 👑 Biggest Splurge Stat Card

#### Added
- "Biggest Splurge" glassmorphism stat card on dashboard (4th card in grid)
- Automatically finds the most expensive transaction of the current month
- Shows amount, category, and date — updates in real-time on every transaction change
- Crown emoji icon with amber/orange gradient accent
- Stats grid expanded from 3 to 4 columns (2 columns on mobile)

---

## [1.6.0] - 2026-03-02

### 📊 Weekly Spending Report

#### Added
- Dismissable weekly report banner shown every Monday at the top of the dashboard
- Summarises last week: total spending, top category, biggest transaction, budget comparison
- Blue-to-purple-to-pink gradient accent bar
- Slide-in/slide-out animations
- Dismiss state saved to localStorage — won't reappear until next Monday
- Responsive 4-column → 2-column grid on mobile

---

## [1.5.0] - 2026-03-02

### 🎀 Treat Yourself Pot

#### Added
- "Treat Yourself" guilt-free spending pot card on the dashboard
- Set a monthly treat budget with its own pink gradient mini progress bar
- New "Treat Yourself" category in Quick Add — draws from treat pot, not main budget
- Treat transactions excluded from main budget and streak calculations
- Gentle over-budget message ("but you deserve it 💖")
- Save/reset treat pot to localStorage

---

## [1.4.0] - 2026-03-02

### 🔥 Spending Streak

#### Added
- Spending streak card on dashboard tracking consecutive days under daily budget average
- Flame emoji with orange gradient accent
- Dynamic messages based on streak length (0, 1-6, 7-29, 30+ days)
- Streak resets to 0 with gentle message when broken
- Trophy emoji at 30+ days
- Streak data (count, lastCheckedDate, broken) saved to localStorage
- Streak recalculates on add/delete transaction and budget changes

---

## [1.3.0] - 2026-03-02

### 🔁 Recurring Transactions

#### Added
- Recurring toggle in Quick Add modal with custom toggle switch
- Purple "Recurring" badge with repeat icon on recurring transactions in history
- Recurring rules saved to localStorage and auto-checked on page load
- If a recurring transaction is due today, it auto-logs itself
- Deleting a recurring transaction also removes the rule

---

## [1.2.0] - 2026-03-02

### 🎯 Firestore Group Pots & Invite Friends

**Live at:** https://taynazdev.github.io/PrismVault

#### Added
- Group Pots now stored in Firebase Firestore under each user's UID
- "Invite Friends" email input on pot creation form
- Email resolution against Firestore `users` collection — matched accounts get shared access
- Real-time pot sync via Firestore `onSnapshot` listener
- Owner / member badges on each pot card
- Owner can delete pot for all members; members can leave individually
- Status messages for unresolved invite emails
- Pots listener cleanup on sign-out
- Guard against duplicate event listener binding on re-init

#### Changed
- Pots no longer use localStorage — fully backed by Firestore
- `savePot()` wrapped in try/catch/finally for error resilience
- Auth toggle refactored to avoid recursive `arguments.callee` handler bugs

---

## [1.1.0] - 2026-03-02

### 🔐 Firebase Authentication

**Live at:** https://taynazdev.github.io/PrismVault

#### Added
- Firebase Authentication with email/password sign-in and sign-up
- Auth screen with glassmorphism card, mode toggle, and error handling
- User profile display in header with name and sign-out button
- All dashboard content gated behind authentication
- User UID written to Firestore `users` collection on sign-in/sign-up
- localStorage data scoped per user UID

---

## [1.0.0] - 2026-03-02

### 🎉 Initial Release

**Live at:** https://taynazdev.github.io/PrismVault

#### Added

**Dashboard & Analytics**
- Real-time financial summary with three stat cards (Balance, Income, Expenses)
- Smooth count-up animations on stat values on page load
- Donut chart component for spending breakdown by category using Chart.js
- Gradient color palette throughout (#f43f6e → #3b82f6)

**Transaction Management**
- Add transactions with description, amount, type (income/expense), and category
- Quick-add modal via floating action button (FAB) in bottom-right
- Transaction history list sorted by most recent
- Filter transactions by type (All, Income, Expenses)
- Delete individual transactions
- All transactions persisted to localStorage

**Budget Tracking**
- Set weekly or monthly spending limits
- Gradient progress bar showing spending percentage
- Color-coded warnings (normal → orange at 80% → red when exceeded)
- Real-time budget recalculation
- Change budget at any time

**Group Pots / Bill Splitting**
- Create named shared expense pots
- Add multiple people to each pot
- Automatic equal share calculation
- View each person's share breakdown
- Save multiple pots
- Delete pots when settled

**Design & UX**
- Dark glassmorphism aesthetic (#0a0a0f background)
- Frosted glass cards with `backdrop-filter: blur()`
- All interactive elements with hover states and gradient glows
- Staggered entrance animations for cards (fade in + slide up)
- Smooth modal open/close transitions with spring easing
- Fully responsive layout (desktop → mobile)
- Clean Inter sans-serif font from Google Fonts

**Data Persistence**
- localStorage for all user data (transactions, budget, pots)
- Automatic save on every action
- Data survives page refresh and browser restart

#### Categories Included
- Food
- Transportation
- Entertainment
- Shopping
- Bills
- Healthcare
- Salary
- Freelance
- Investment
- Other

(Quick-add modal uses simplified categories: Food, Transport, Subscriptions, Going Out, Clothes, Random, Other)

---

## Future Roadmap

- [x] Export data as CSV
- [x] Recurring transaction templates
- [x] Monthly spending trends chart
- [ ] Dark/Light theme toggle
- [ ] Multi-currency support
- [ ] Expense tags and notes
- [ ] Savings goals tracking
- [ ] Sync transactions to Firestore
- [ ] Mobile app (React Native)
- [ ] Browser notifications for budget alerts
- [ ] AI-powered spending insights and tips
- [x] User authentication and profiles
- [x] Group expense sharing and bill splitting
- [x] Receipt photo attachments to transactions
- [x] Inactivity nudges to encourage logging transactions
- [x] Weekly spending report banner
- [x] "You could have bought..." fun comparison card
- [x] Spending heatmap calendar view
- [x] Biggest splurge stat card
- [ ] Custom category management
- [ ] Dashboard widget settings for toggling cards on/off
- [x] Emoji reactions on transactions
- [x] User profile page with avatar selection
- [x] App logo and favicon
- [x] "Settle Up" button for Group Pots with real-time sync and "Who paid last" label
