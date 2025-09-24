# MyFiance v2 — Full Project Specification

## 1. Project Overview
**Purpose:** Expense tracking app with AI-assisted enhancements.  
**Core functionality:** Add, edit, delete, and view expenses.  
**Future goals:** AI suggestions, auto-categorization, reports.

---

## 2. Models

### Expense
```swift
struct Expense {
    let id: UUID
    var name: String
    var amount: Double
    var date: Date
    var category: String
    var notes: String?
}
```

---

## 3. Services
```swift
protocol ExpenseService {
    func add(expense: Expense) throws
    func update(expense: Expense) throws
    func delete(expenseId: UUID) throws
    func listExpenses(filter: ExpenseFilter?) -> [Expense]
}
```

---

## 4. User Stories

View Expenses List: Users can see all expenses in a scrollable list.

Add Expense: Users can create a new expense entry.

Edit Expense: Users can update an existing expense.

Delete Expense: Users can remove an expense from the list.

---

## 4. Constraints / Validation Rules

Amount must be a positive number.

Date defaults to today if not provided.

All fields are required except Notes.

---

## 5. UI Flows & Layout
Expenses List Screen

Navigation Bar: Title “Expenses”

Vertical scrolling list of expenses

Floating Add button (bottom-right) → Add Expense screen

Tap expense → Edit Expense screen

Swipe/delete gesture → Delete expense

Add/Edit Expense Screen

Form fields: Name, Amount, Date, Category, Notes

Save → calls ExpenseService.add() or .update()

Cancel → return to Expenses List

Validation: Amount numeric, Date defaults to today

Navigation Flow (ASCII Diagram)
Expenses List
 ├─ Tap expense → Edit Expense → Save/Cancel → back to list
 ├─ Tap Add → Add Expense → Save/Cancel → back to list
 └─ Swipe/Delete → Delete expense

---

## 6. Code Generation Sequence

Generate Models & ExpenseService (CRUD)

Generate Expenses List screen with navigation & interactions

Generate Add/Edit Expense screen

Test each chunk before moving to the next

(Future) Add reports, filters, AI enhancements

---

## 7. Notes for AI & Developers

Keep layouts conceptual (top, bottom, floating buttons)

Follow validation rules from constraints section

Use this README as the single source of truth for all features
