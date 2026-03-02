# Changelog

All notable changes to Prism Vault will be documented in this file.

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

- [ ] Export data as CSV
- [ ] Monthly spending trends chart
- [ ] Recurring transaction templates
- [ ] Dark/Light theme toggle
- [ ] Multi-currency support
- [ ] Expense tags and notes
- [ ] Savings goals tracking
- [ ] Sync transactions to Firestore
- [ ] Mobile app (React Native)
