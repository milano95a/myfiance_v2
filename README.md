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

