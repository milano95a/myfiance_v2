### ExpenseService

Provides operations for managing expenses.

**Methods:**

- `add(expense: Expense)`: Add a new expense. Throws on failure.
- `update(expense: Expense)`: Update an existing expense. Throws if expense does not exist.
- `delete(expenseId: UUID)`: Delete an expense by its ID.
- `listExpenses(filter: ExpenseFilter) -> [Expense]`: List expenses, optionally filtered by start/end date or category.

struct ExpenseFilter {
    var startDate: Date?
    var endDate: Date?
    var categoryId: UUID?
}
