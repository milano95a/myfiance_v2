# UI Flows

This document describes the main user interface flows for the **MyFiance v2** expense tracking app. It details screens, elements, and navigation paths.

---

## 1. Main Screens

### 1.1 Home / Dashboard (Tab Bar)
**Purpose:** Main entry point with two tabs for expenses and reports.

**Tabs:**
1. **Expenses** – List of all expenses (default tab)  
2. **More** – Various reports and analytics

---

#### 1.1.1 Expenses Tab
**Purpose:** Show a list of expenses, allow quick search, and provide navigation to add expense or settings.

**Layout:**
- **Navigation Bar (top):**
  - Left: title ("Expenses")
  - Right: **Settings button**
- **Body:**
  - Search field below navigation bar
  - Vertical list of expenses (`ExpenseItemView`)
- **Floating button (bottom-right):** **Add Expense**

**Flow:**
- Scroll through expenses
- Tap search → filter the list dynamically
- Tap **Add Expense** → **Add Expense screen**
- Tap an expense → **Edit Expense screen**
- Swipe / delete gesture → call `ExpenseService.delete`
- Tap **Settings** → **Settings / Categories screen**

---

#### 1.1.2 More Tab
**Purpose:** Show reports and analytics.

**Elements:**
- Monthly spending summary (graph or chart)
- Category breakdown
- Filter by time period (day / week / month)

**Flow:**
- Tap chart item → optionally filter **Expense List** in Expenses tab
- Tap back → return to **More** tab

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
- **Save:** validate inputs → call `ExpenseService.add` or `update` → return to **Expenses tab**
- **Cancel:** discard changes → return to previous screen

---

### 1.3 Settings / Categories
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

Home / Dashboard (Tab Bar)
├─ Expenses Tab
│ ├─ Navigation Bar: Title (left), Settings button (right)
│ ├─ Search field → filter expenses
│ ├─ Scroll expense list
│ ├─ Tap expense → Edit Expense → Save / Cancel → Expenses
│ ├─ Floating Add button (bottom-right) → Add Expense → Save / Cancel → Expenses
│ └─ Settings button → Settings / Categories
└─ More Tab
├─ View reports
├─ Tap chart item → filter Expenses list
└─ Tap back → More Tab
