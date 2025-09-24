MyFiance v2 — Project Specification
1. Project Overview

Purpose: Expense tracking app with AI-assisted enhancements.

Core functionality: Add, edit, delete, and view expenses.

Future goals: AI suggestions, auto-categorization, reports.

2. Models

Expense

id: UUID

name: String

amount: Double

date: Date

category: String

notes: Optional<String>

ExpenseFilter (optional for future filtering)

startDate: Date?

endDate: Date?

categoryId: UUID?

Services

ExpenseService

add(expense: Expense)

update(expense: Expense)

delete(expenseId: UUID)

listExpenses(filter: ExpenseFilter?) → [Expense]

3. User Stories

View a list of expenses

Add a new expense

Edit an existing expense

Delete an expense

(Future) View reports, filter expenses, AI suggestions

4. Constraints / Validation Rules

Amount must be a positive number

Date defaults to today if not provided

All fields required except Notes

5. UI Flows & Layout
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

6. Code Generation Sequence

Generate Models & ExpenseService (CRUD)

Generate Expenses List screen with navigation & interactions

Generate Add/Edit Expense screen

Test each chunk before moving to the next

(Future) Add reports, filters, AI enhancements

7. Notes for AI & Developers

Keep layouts conceptual (top, bottom, floating buttons)

Follow validation rules from constraints section

Use this README as the single source of truth for all features
