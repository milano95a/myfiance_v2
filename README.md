# MyFiance v2 — Full Project Specification

## 1. Project Overview
**Purpose:** Expense tracking app with AI-assisted enhancements.  
**Core functionality:** Add, edit, delete, and view expenses.  

---

## 2. Models

### Expense
struct Expense {
let id: UUID
var name: String
var amount: Double
var date: Date
var category: String
var notes: String?
}

shell
Copy code

### ExpenseFilter
struct ExpenseFilter {
var startDate: Date?
var endDate: Date?
var categories: [String]?
}

shell
Copy code

### MonthlySummary
struct MonthlySummary {
var month: Date
var totalAmount: Double
var categoryTotals: [String: Double]
}

yaml
Copy code

---

## 3. Services
protocol ExpenseService {
func add(expense: Expense) throws
func update(expense: Expense) throws
func delete(expenseId: UUID) throws
func listExpenses(filter: ExpenseFilter?) -> [Expense]
func monthlySummary(for month: Date) -> MonthlySummary
func suggestCategory(for name: String) -> String?
}

markdown
Copy code

- `monthlySummary(for:)` → returns total spending and category breakdown for a given month.  
- `suggestCategory(for:)` → AI-assisted category suggestion based on expense name.

---

## 4. User Stories

- **View Expenses List:** Users can see all expenses in a scrollable list.  
- **Add Expense:** Users can create a new expense entry.  
- **Edit Expense:** Users can update an existing expense.  
- **Delete Expense:** Users can remove an expense from the list.  
- **Filter Expenses:** Users can filter expenses by date range and category.  
- **Monthly Summary Report:** Users can view total spending and category breakdown for a selected month.  
- **AI Category Suggestion:** App suggests category while adding/editing expense based on name.

---

## 5. Constraints / Validation Rules

- Amount must be a positive number.  
- Date defaults to today if not provided.  
- All fields are required except Notes.  
- Filters can be empty (show all expenses).  

---

## 6. UI Flows & Layout

### Expenses List Screen
- Navigation Bar: Title “Expenses”  
- Scrollable list of expenses  
- Floating Add button → Add Expense screen  
- Tap expense → Edit Expense screen  
- Swipe/delete gesture → Delete expense  
- Filter button → opens Filter modal  

### Add/Edit Expense Screen
- Form fields: Name, Amount, Date, Category, Notes  
- Save → calls ExpenseService.add() or .update()  
- Cancel → back to Expenses List  
- Category field shows AI suggestions  

### Filter Modal
- Fields: Start Date, End Date, Category multi-select  
- Apply → updates expenses list  
- Cancel → dismiss modal  

### Monthly Summary Screen
- Month picker  
- Total spending displayed prominently  
- Bar/line chart for category-wise spending  
- Option to navigate back to expenses list  

---

## 7. Database / Persistence Layer

**Purpose:** Provide persistent storage for expenses using CoreData.  

### Entities

**CDExpense**

| Field    | Type  | Optional | Notes                      |
|----------|-------|---------|----------------------------|
| id       | UUID  | ❌      | Primary key               |
| name     | String| ❌      | Expense name              |
| amount   | Double| ❌      | Must be positive          |
| date     | Date  | ❌      | Defaults to today if missing |
| category | String| ❌      | Expense category          |
| notes    | String| ✅      | Optional notes            |

### CoreData Implementation Notes
- CRUD operations implemented via `NSManagedObjectContext`.  
- Use `NSFetchRequest` and `NSPredicate` for listing and filtering.  
- Map between `CDExpense` (CoreData) and `Expense` (app model).  
- Save context after every add/update/delete.  
- Optional enhancements: indices on `date` and `category`, batch deletes, cached monthly summaries.

---

## 8. Code Generation Sequence

1. Implement Models & ExpenseService (with CoreData)  
2. Implement ViewModels (ExpenseListViewModel, AddEditExpenseViewModel, FilterViewModel, SummaryViewModel)  
3. Implement Expenses List screen & navigation  
4. Implement Add/Edit Expense screen with AI suggestions  
5. Implement Filter modal  
6. Implement Monthly Summary screen  
7. Test all features  

---

## 9. Notes for AI & Developers

- Keep layouts conceptual (top, bottom, floating buttons).  
- Follow validation rules from constraints section.  
- Use this README as the single source of truth for all features.  
- Filters, reports, and AI category suggestions should not block basic CRUD functionality.  

---

## 10. ViewModels

### ExpenseListViewModel
- Purpose: Connect Expenses List UI with ExpenseService.  
- Responsibilities: Load expenses, handle deletion, apply filters.  
- State: `expenses: [Expense]`, `isLoading: Bool`, `errorMessage: String?`  
- Methods: `loadExpenses(filter: ExpenseFilter?)`, `deleteExpense(id: UUID)`, `applyFilter(filter: ExpenseFilter)`

### AddEditExpenseViewModel
- Purpose: Connect Add/Edit Expense UI with ExpenseService.  
- Responsibilities: Validate input, save expense, provide AI category suggestions.  
- State: `expense: Expense`, `isSaving: Bool`, `errorMessage: String?`, `categorySuggestion: String?`  
- Methods: `saveExpense()`, `fetchCategorySuggestion(for name: String)`

### FilterViewModel
- Purpose: Manage filters and pass them to ExpenseListViewModel.  
- State: `startDate: Date?`, `endDate: Date?`, `categories: [String]?`  
- Methods: `applyFilter()`, `clearFilter()`

### SummaryViewModel
- Purpose: Generate monthly spending summary.  
- State: `month: Date`, `summary: MonthlySummary?`, `isLoading: Bool`  
- Methods: `loadSummary(for month: Date)`
