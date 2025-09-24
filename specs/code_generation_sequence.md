## Code Generation Sequence

To generate the app with AI efficiently, follow this sequence of steps:

1. **Models & Services**  
   - `Expense`, `ExpenseFilter`, `ExpenseService`, `Category`  
   - Define data structures, methods, and validations  
2. **Expenses Tab**  
   - Expense list, search field, Add button, Settings button  
   - Implement interactions: tap expense, tap Add, tap Settings  
3. **Add / Edit Expense Screen**  
   - Form fields and Save/Cancel buttons  
   - Integrate with `ExpenseService`  
4. **Settings / Categories Screen**  
   - Category list and management (Add/Edit/Delete)  
   - Preferences (currency, date format, AI settings)  
5. **Tab Bar & Navigation**  
   - Link Expenses Tab, More Tab, and other screens  
6. **More Tab** *(future)*  
   - Reports, charts, filtering  
7. **AI-enhanced Features**  
   - Auto-categorization, expense suggestions, predictive insights  

**Best Practices:**
- Generate **small chunks** and run each independently  
- Test each screen/component as you go  
- Use specs as prompts for AI; keep them concise and relevant  
- Refactor and integrate incrementally  
