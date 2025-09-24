# UI Flows & Layout (Minimal Version)

This document describes the **core screens and flows** for MyFiance v2, focusing on basic expense management: list, add, edit, and delete.

---

## 1. Home / Dashboard (Expenses List Only)

**Screen Layout:**
- **Navigation Bar (top)**
  - Title: "Expenses"
- **Body**
  - Vertical list of expenses → tap item → **Edit Expense**
- **Floating Action Button** → tap → **Add Expense**

**Interactions / Navigation:**
- Tap expense item → **Edit Expense screen**
- Tap Add button → **Add Expense screen**
- Swipe / delete gesture on expense → **Delete Expense**

---

## 2. Add / Edit Expense Screen

**Screen Layout:**
- Form fields:
  - Expense Name (text input)
  - Amount (numeric input)
  - Date (date picker, defaults to today)
  - Category (dropdown / selector)
  - Notes (optional)
- Buttons:
  - Save → validates & saves → returns to **Expenses list**
  - Cancel → discard changes → returns to **Expenses list**

**Optional Notes for AI:**
- Validate that Amount is numeric
- Auto-select today’s date by default

---

## 3. Navigation Flow (ASCII Diagram)

Home / Dashboard (Expenses List)
├─ Tap expense → Edit Expense → Save / Cancel → return to Expenses List
├─ Tap Add button → Add Expense → Save / Cancel → return to Expenses List
└─ Swipe / delete → Delete Expense

yaml
Copy code

---

## 4. Notes for AI Code Generation

- Start with **Expense model and ExpenseService** (CRUD methods: add, update, delete, list).  
- Then implement **Expenses List screen** with interactions.  
- Next implement **Add/Edit Expense screen**.  
- Keep layout conceptual (list, top navigation bar, floating button).  
- Test each part before adding new features.  
