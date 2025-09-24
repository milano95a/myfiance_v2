# MyFiance v2 — Updated Project Specification

## 1. Project Overview
**Purpose:** Expense tracking app 
**Core functionality:** Add, edit, delete, and view expenses.  

---

## 2. Models

### Expense
```swift
@Model
class Expense {
    @Attribute(.unique) var id: UUID
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
    func listExpenses() -> [Expense]
}
```

---

## 4. User Stories

- **View Expenses List:** Users can see all expenses in a scrollable list.  
- **Add Expense:** Users can create a new expense entry.  
- **Edit Expense:** Users can update an existing expense.  
- **Delete Expense:** Users can remove an expense from the list.  

---

## 5. Constraints / Validation Rules

- Amount must be a positive number.  
- Date defaults to today if not provided.  
- All fields are required except Notes.  

---

## 6. UI Flows & Layout

### Expenses List Screen
- Navigation Bar: Title "Expenses"  
- Scrollable list of expenses  
- Floating Add button → Add Expense screen  
- Tap expense → Edit Expense screen  
- Swipe/delete gesture → Delete expense  

### Add/Edit Expense Screen
- Form fields: Name, Amount, Date, Category, Notes  
- Save → calls ExpenseService.add() or .update()  
- Cancel → back to Expenses List  

---

## 7. Database / Persistence Layer

**Purpose:** Provide persistent storage for expenses using SwiftData.  

### SwiftData Model

**Expense**

| Field    | Type   | Optional | Notes                      |
|----------|--------|----------|----------------------------|
| id       | UUID   | ❌       | Primary key, unique        |
| name     | String | ❌       | Expense name              |
| amount   | Double | ❌       | Must be positive          |
| date     | Date   | ❌       | Defaults to today if missing |
| category | String | ❌       | Expense category          |
| notes    | String | ✅       | Optional notes            |

### SwiftData Implementation Notes
- CRUD operations implemented via `ModelContext`.  
- Use `FetchDescriptor` and `#Predicate` for listing and filtering.  
- SwiftData automatically handles persistence and change tracking.  
- Save context after every add/delete (updates are automatic).  

---

## 8. Code Generation Sequence

1. Implement Models & ExpenseService (with SwiftData)  
2. Implement ViewModels (ExpenseListViewModel, AddEditExpenseViewModel)  
3. Implement Expenses List screen & navigation  
4. Implement Add/Edit Expense screen
5. Set up SwiftData container and dependency injection
6. Test all features  

---

## 9. Notes for AI & Developers

- Keep layouts conceptual (top, bottom, floating buttons).  
- Follow validation rules from constraints section.  
- Use this README as the single source of truth for all features.  
- SwiftData requires iOS 17+ minimum deployment target.

---

## 10. ViewModels

### ExpenseListViewModel
- Purpose: Connect Expenses List UI with ExpenseService.  
- Responsibilities: Load expenses, handle deletion.  
- State: `expenses: [Expense]`, `isLoading: Bool`, `errorMessage: String?`  
- Methods: `loadExpenses()`, `deleteExpense(id: UUID)`

### AddEditExpenseViewModel
- Purpose: Connect Add/Edit Expense UI with ExpenseService.  
- State: `expense fields`, `isSaving: Bool`, `errorMessage: String?`  
- Methods: `saveExpense()`

---

## 11. App Setup

### SwiftData Configuration
- Create `ModelContainer` for `Expense` model
- Pass `ModelContext` to services
- Configure in main App file

### Dependency Injection
- Pass `ExpenseService` instance to ViewModels
- Use environment or manual injection

---
