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

---

## 3. Services
```swift
protocol ExpenseService {
    func add(expense: Expense) throws
    func update(expense: Expense) throws
    func delete(expenseId: UUID) throws
    func listExpenses(filter: ExpenseFilter?) -> [Expense]
}
