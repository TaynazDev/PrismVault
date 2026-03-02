# Prism Vault

A beautiful, modern budget tracker with a dark glassmorphism aesthetic. Track transactions, set spending limits, analyze spending patterns, and split bills with friends—all in one sleek app.

🌐 **[Live Demo](https://taynazdev.github.io/PrismVault)**

## Features

✨ **Dashboard Overview**
- Real-time balance, income, and expense tracking with smooth count-up animations
- Four glassmorphic stat cards: Balance, Income, Expenses, and Biggest Splurge
- Spending breakdown donut chart with gradient color scheme
- Spending streak tracker — consecutive days under daily budget average
- Weekly spending report banner (shown on Mondays) with top category and biggest transaction

💰 **Transaction Management**
- Add income and expense transactions with categories
- Quick-add modal for rapid logging (bottom-right FAB)
- Recurring transaction toggle — auto-logs on the same day each month
- Purple "Recurring" badge on auto-logged transactions
- Filter transactions by type (All, Income, Expenses)
- Delete individual transactions
- Sorted by most recent first

📊 **Budget Tracking**
- Set weekly or monthly spending limits
- Progress bar that fills with gradient color (pink → blue)
- Automatic warnings at 80% capacity (orange) and when exceeded (red)
- Spending streak rewards consecutive days of staying under budget
- Real-time budget status updates

🔥 **Spending Streak**
- Tracks consecutive days you stay under your daily budget average
- Flame emoji with dynamic contextual messages
- Glassmorphism card with orange gradient accent
- Persists across sessions via localStorage

🎁 **Treat Yourself Pot**
- Guilt-free spending pot with separate mini progress bar
- "Treat Yourself" category in quick-add modal
- Treat transactions excluded from main budget and streak calculations
- Pink gradient accent glassmorphism card

👑 **Biggest Splurge**
- Stat card highlighting your most expensive transaction this month
- Shows amount, category, and date at a glance
- Amber/orange gradient accent with crown emoji
- Updates dynamically whenever transactions change

📅 **Weekly Spending Report**
- Dismissable banner shown every Monday
- Summarizes last week's total spend, top category, biggest transaction
- Budget comparison with over/under indicator
- Slide-in/out animations

🎯 **Group Pots / Bill Splitting**
- Create named shared pots for group expenses
- Add multiple people and automatically calculate equal shares
- Invite friends by email — shared pots appear on their dashboard
- Real-time sync via Firebase Firestore
- Owner and member roles with shared deletion
- View each person's share amount at a glance

🎨 **Design & UX**
- Dark glassmorphism aesthetic with frosted glass cards
- Gradient accent color scheme (#f43f6e → #3b82f6)
- Staggered entrance animations on page load
- Smooth modal transitions with spring easing
- Hover states with soft gradient glows
- Fully responsive mobile design
- Smooth count-up animations for balance numbers

🔐 **Authentication**
- Firebase Authentication (email & password)
- Sign up / sign in with user profile
- Optional — the app is fully usable without signing in
- Sign-in required only for shared Group Pots
- User name displayed in header with sign-out button

💾 **Data Persistence**
- Transactions saved to localStorage (`prismPayTransactions`)
- Budget settings saved to localStorage (`prismPayBudget`)
- Recurring rules saved to localStorage (`prismPayRecurring`)
- Spending streak saved to localStorage (`prismPayStreak`)
- Treat Yourself pot saved to localStorage (`prismPayTreat`)
- Weekly report dismiss state saved to localStorage (`prismPayWeeklyDismissed`)
- Group Pots stored in Firebase Firestore with real-time sync
- Data persists across sessions and devices (pots)

## Tech Stack

- **HTML5** — Semantic markup
- **CSS3** — Glassmorphism, animations, responsive grid
- **Vanilla JavaScript** — No frameworks
- **Firebase Auth** — Email/password authentication
- **Firebase Firestore** — Real-time shared Group Pots
- **Chart.js** — Interactive donut chart
- **Inter Font** — Clean sans-serif typography
- **localStorage API** — Client-side persistence

## Getting Started

1. Visit [taynazdev.github.io/PrismVault](https://taynazdev.github.io/PrismVault)
2. Start adding transactions right away — no sign-in required
3. Set a budget to track spending
4. Sign in to create group pots and invite friends by email
5. All data is automatically saved

Or run locally:
```bash
# Clone the repository
git clone https://github.com/taynazdev/PrismVault.git

# Open index.html in a browser
open index.html
```

## File Structure

```
PrismPay/
├── index.html          # Single-file app (HTML + CSS + JS)
├── README.md           # This file
└── CHANGELOG.md        # Version history
```

## Browser Compatibility

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers (iOS Safari, Chrome Mobile)

## License

MIT License — Feel free to use and modify!
