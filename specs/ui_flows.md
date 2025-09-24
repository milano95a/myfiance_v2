# UI Flows

This document describes the main user interface flows for the **MyFiance v2** expense tracking app. It details screens, elements, and navigation paths.

---

## 1. Main Screens

### 1.1 Dashboard / Home
**Purpose:** Show an overview of recent expenses, totals, and categories.

**Elements:**
- Summary of total expenses (daily / weekly / monthly)
- Quick view of top categories
- Button to **Add Expense**
- Navigation menu (Categories, Reports, Settings)

**Flow:**
- Tap **Add Expense** → **Add Expense screen**
- Tap a category → **Category Detail screen** (filtered expense list)
- Tap **Reports** → **Reports screen**

---

### 1.2 Add / Edit Expense
**Purpose:** Add a new expense or update an existing one.

**Elements:**
- Expense Name (text input)
- Amount (numeric input)
- Date (date picker, defaults to today)
- Category (dropdown / selector)
- Notes (optional)
- Save / Cancel buttons

**Flow:**
- **Save:** validate inputs → call `ExpenseService.add` or `update` → return to **Home** or **Expense List**
- **Cancel:** discard changes → return to previous screen

---

### 1.3 Expense List / Category Detail
**Purpose:** Show a list of expenses, optionally filtered by category or date.

**Elements:**
- Vertical list of expenses (`ExpenseItemView`)
- Filter options (date range, category)
- Search bar (optional)
- Tap an item → **Edit Expense screen**

**Flow:**
- Scroll through expenses
- Tap an expense → **Edit Expense**
- Swipe / delete gesture → call `ExpenseService.delete`

---

### 1.4 Reports / Analytics
**Purpose:** Provide insights and summaries.

**Elements:**
- Monthly spending summary (graph or chart)
- Category breakdown
- Filter by time period (day / week / month)

**Flow:**
- Tap chart item → optionally filter **Expense List**
- Tap back → return to **Home**

---

### 1.5 Settings / Categories
**Purpose:** Manage categories and app settings.

**Elements:**
- List of categories (name, color)
- Add / edit / delete category
- Preferences (currency, date format, AI settings)

**Flow:**
- Tap **Add Category** → input name & color → save → update list
- Tap category → edit → save or delete

---

## 2. Navigation Flow (High-level)

Home/Dashboard

  ├─ Add Expense → Save / Cancel → Home
  
  ├─ Expense List → Tap item → Edit Expense → Save / Cancel → Expense List
  
  ├─ Category Detail → Filtered Expense List
  
  ├─ Reports → Filter / Tap chart → Expense List
  
  └─ Settings → Manage Categories / Preferences

