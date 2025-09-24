# myfiance_v2

# Expense Tracker

## Goal
Track daily expenses, categorize them, and view reports.

## Core Modules
- Expense Management
- Categories & Tags
- Reports & Analytics
- (Optional) User Accounts & Sync

## Domain Models
- Expense { id, name, amount, date, category, notes? }
- Category { id, name, color }

## Example UI
- ExpenseItemView → shows name & date (left), amount (right)
- ExpenseListView → vertical list of ExpenseItemViews
