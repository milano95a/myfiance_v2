protocol ExpenseService {
    func add(expense: Expense) throws
    func update(expense: Expense) throws
    func delete(expenseId: UUID) throws
    func listExpenses(filter: ExpenseFilter) -> [Expense]
}

struct ExpenseFilter {
    var startDate: Date?
    var endDate: Date?
    var categoryId: UUID?
}
