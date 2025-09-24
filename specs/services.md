## ExpenseService

Provides operations for managing expenses.

### Methods

- **add(expense: Expense)**  
  Add a new expense. Throws on failure.

- **update(expense: Expense)**  
  Update an existing expense. Throws if expense does not exist.

- **delete(expenseId: UUID)**  
  Delete an expense by its ID.

- **listExpenses(filter: ExpenseFilter) -> [Expense]**  
  List expenses, optionally filtered by start/end date or category.

---

### ExpenseFilter

Optional filters to limit the results of `listExpenses`:

- **startDate: Date?** — Only include expenses on or after this date.  
- **endDate: Date?** — Only include expenses on or before this date.  
- **categoryId: UUID?** — Only include expenses in this category.
