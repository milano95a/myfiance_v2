Models:
- Expense
  - id: UUID
  - name: String
  - amount: Decimal
  - date: Date
  - category: Category
  - notes: String (optional)

- Category
  - id: UUID
  - name: String
  - color: String
