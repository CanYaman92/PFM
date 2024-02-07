using System;
using System.Collections.Generic;
 
class Program
{
    static List<double> expenses = new List<double>();
    static List<double> income = new List<double>();
 
    static void Main()
    {
        Console.WriteLine("Welcome to the Personal Finance Manager!");
 
        while (true)
        {
            DisplayMenu();
 
            string choice = Console.ReadLine()?.ToLower(); // Check for null input
 
            if (choice != null)
            {
                switch (choice)
                {
                    case "1":
                        AddExpense();
                        break;
                    case "2":
                        AddIncome();
                        break;
                    case "3":
                        ViewExpenses();
                        break;
                    case "4":
                        ViewIncome();
                        break;
                    case "5":
                        ViewFinancialSummary();
                        break;
                    case "6":
                        CalculateTotalExpenses();
                        break;
                    case "7":
                        CalculateTotalIncome();
                        break;
                    case "8":
                        CalculateNetIncome();
                        break;
                    case "9":
                        CalculateExpensePercentage();
                        break;
                    case "10":
                        CalculateSavings();
                        break;
                    case "11":
                        ClearData();
                        break;
                    case "12":
                        Exit();
                        break;
                    default:
                        Console.WriteLine("Invalid choice. Please try again.");
                        break;
                }
            }
            else
            {
                Console.WriteLine("Error: Console input is null.");
            }
        }
    }
 
    static void DisplayMenu()
    {
        Console.WriteLine("\n1. Add Expense");
        Console.WriteLine("2. Add Income");
        Console.WriteLine("3. View Expenses");
        Console.WriteLine("4. View Income");
        Console.WriteLine("5. View Financial Summary");
        Console.WriteLine("6. Calculate Total Expenses");
        Console.WriteLine("7. Calculate Total Income");
        Console.WriteLine("8. Calculate Net Income");
        Console.WriteLine("9. Calculate Expense Percentage");
        Console.WriteLine("10. Calculate Savings");
        Console.WriteLine("11. Clear Data");
        Console.WriteLine("12. Exit");
        Console.Write("Enter your choice (1-12): ");
    }
 
    static void AddExpense()
    {
        Console.Write("Enter expense amount: $");
        if (double.TryParse(Console.ReadLine(), out double amount))
        {
            expenses.Add(amount);
            Console.WriteLine("Expense added successfully!");
        }
        else
        {
            Console.WriteLine("Invalid amount. Please try again.");
        }
    }
 
    static void AddIncome()
    {
        Console.Write("Enter income amount: $");
        if (double.TryParse(Console.ReadLine(), out double amount))
        {
            income.Add(amount);
            Console.WriteLine("Income added successfully!");
        }
        else
        {
            Console.WriteLine("Invalid amount. Please try again.");
        }
    }
 
    static void ViewExpenses()
    {
        if (expenses.Count == 0)
        {
            Console.WriteLine("No expenses recorded.");
        }
        else
        {
            Console.WriteLine("\nExpenses:");
            foreach (var expense in expenses)
            {
                Console.WriteLine($"- ${expense}");
            }
        }
    }
 
    static void ViewIncome()
    {
        if (income.Count == 0)
        {
            Console.WriteLine("No income recorded.");
        }
        else
        {
            Console.WriteLine("\nIncome:");
            foreach (var i in income)
            {
                Console.WriteLine($"- ${i}");
            }
        }
    }
 
    static void ViewFinancialSummary()
    {
        CalculateTotalExpenses();
        CalculateTotalIncome();
        CalculateNetIncome();
        CalculateExpensePercentage();
        CalculateSavings();
    }
 
    static void CalculateTotalExpenses()
    {
        double totalExpenses = 0;
        foreach (var expense in expenses)
        {
            totalExpenses += expense;
        }
        Console.WriteLine($"Total Expenses: ${totalExpenses}");
    }
 
    static void CalculateTotalIncome()
    {
        double totalIncome = 0;
        foreach (var i in income)
        {
            totalIncome += i;
        }
        Console.WriteLine($"Total Income: ${totalIncome}");
    }
 
    static void CalculateNetIncome()
    {
        double totalExpenses = 0;
        foreach (var expense in expenses)
        {
            totalExpenses += expense;
        }
 
        double totalIncome = 0;
        foreach (var i in income)
        {
            totalIncome += i;
        }
 
        double netIncome = totalIncome - totalExpenses;
        Console.WriteLine($"Net Income: ${netIncome}");
    }
 
    static void CalculateExpensePercentage()
    {
        double totalExpenses = 0;
        foreach (var expense in expenses)
        {
            totalExpenses += expense;
        }
 
        double totalIncome = 0;
        foreach (var i in income)
        {
            totalIncome += i;
        }
 
        double expensePercentage = (totalExpenses / totalIncome) * 100;
        Console.WriteLine($"Expense Percentage: {expensePercentage:F2}%");
    }
 
    static void CalculateSavings()
    {
        double totalExpenses = 0;
        foreach (var expense in expenses)
        {
            totalExpenses += expense;
        }
 
        double totalIncome = 0;
        foreach (var i in income)
        {
            totalIncome += i;
        }
 
        double savings = totalIncome - totalExpenses;
        Console.WriteLine($"Savings: ${savings}");
    }
 
    static void ClearData()
    {
        expenses.Clear();
        income.Clear();
        Console.WriteLine("Data cleared successfully!");
    }
 
    static void Exit()
    {
        Console.WriteLine("Exiting the Personal Finance Manager. Goodbye!");
        Environment.Exit(0);
    }
}
