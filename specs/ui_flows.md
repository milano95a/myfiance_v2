# UI Flows & Layout (AI-Friendly Spec)

This document describes the screens, UI elements, and navigation flows for **MyFiance v2**.  
It is structured to allow AI-assisted code generation while remaining human-readable.

---

## 1. Home / Dashboard (Tab Bar)

**Tabs:**
1. **Expenses** – Default tab
2. **More** – Reports & analytics

### 1.1 Expenses Tab

**Screen Layout:**
- **Navigation Bar (top)**
  - Left: Title ("Expenses")
  - Right: Settings button → navigates to **Settings / Categories**  
- **Body**
  - Search field (top of body) → filters expense list dynamically
  - Expense list (vertical scrolling list) → tap item → **Edit Expense**  
- **Floating Action Button** → tap → **Add Expense**  

**Interactions / Navigation:**
- Tap **Search field** → filter expense list
- Tap expense item → **Edit Expense screen**
- Tap Add button → **Add Expense screen**
- Tap Settings button → **Settings / Categories screen**

**Optional Notes for AI:**
- Search field optional input
- Expense list: show most recent first, scrollable
- Floating Add button always visible

---

### 1.2 More Tab

*(To be defined later)*

---

### 1.3 Add / Edit Expense Screen

**Screen Layout:**
- Form fields:
  - Expense Name (text input)
  - Amount (numeric input)
  - Date (date picker, defaults to today)
  - Category (dropdown / selector)
  - Notes (optional)
- Buttons:
  - Save → validates & saves → returns to **Expenses Tab**
  - Cancel → discard changes → returns to previous screen

**Optional Notes for AI:**
- Validate that Amount is numeric
- Auto-select today’s date by default
- Category dropdown can include AI-suggested categories

---

### 1.4 Settings / Categories Screen

**Screen Layout:**
- List of categories (name, color)
- Buttons:
  - Add → add new category
  - Edit / Delete → update or remove category
- Preferences (optional):
  - Currency
  - Date format
  - AI settings

**Interactions / Navigation:**
- Tap Add → open form → save → update list
- Tap category → edit/delete → save or delete → update list

---

## 2. Navigation Flow (ASCII Diagram)

Home / Dashboard (Tab Bar)
├─ Expenses Tab
│ ├─ Search field → filter expenses
│ ├─ Tap expense → Edit Expense → Save / Cancel → return to Expenses
│ ├─ Tap Add button → Add Expense → Save / Cancel → return to Expenses
│ └─ Tap Settings button → Settings / Categories → back
└─ More Tab
└─ (To be defined)

yaml
Copy code

---

## 3. Notes for AI Code Generation

- Use structured layout: navigation bar, body, floating buttons, lists, forms.  
- Use default values where indicated (e.g., today’s date).  
- All screens should be responsive and handle dynamic data.  
- AI-suggested enhancements can include auto-categorization and spending predictions.  
- Avoid pixel-perfect positions; conceptual layout (top, bottom, floating) is sufficient.
