Reference: https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/
# Get Started with LINQ in C#
## LINQ and Generic Types (C#)
(https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/linq-and-generic-types)

LINQ query variables are typed as `IEnumerable<T>` or a derived type such as `IQueryable<T>`. When you see a query variable that is typed as IEnumerable<Customer>, it just means that the query, when it is executed, will produce a sequence of zero or more Customer objects.

If you prefer, you can avoid generic syntax by using the var keyword. The var keyword instructs the compiler to infer the type of a query variable by looking at the data source specified in the from clause. When you use IEnumerable<T> or var to declare LINQ query variables, compiled code are the same.
## Basic LINQ Query Operations (C#)
 
(https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/basic-linq-query-operations)
 
 The `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).
 
The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression. When the query is executed, the range variable will serve as a reference to each successive element in `customers`. 

The `group` clause enables you to group your results based on a key that you specify. 

custQuery is an IEnumerable<IGrouping<string, Customer>>. When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop. The outer loop iterates over each group, and the inner loop iterates over each group's members.
## Data Transformations with LINQ (C#)
(https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/data-transformations-with-linq)<br/>
code refer to ex2/DataTransSample/DataTransSample

To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.

LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents. 
## Type Relationships in LINQ Query Operations (C#)
(https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations)

Queries that do not Transform the Source Data
1. The type argument of the data source determines the type of the range variable.
2. The type of the object that is selected determines the type of the query variable. Here `name` is a string. Therefore, the query variable is an `IEnumerable<string>`.
 3. The query variable is iterated over in the `foreach` statement. Because the query variable is a sequence of strings, the iteration variable is also a string.
 
 Queries that Transform the Source Data
1. The type argument of the data source is always the type of the range variable in the query.
2. Because the `select` statement produces an anonymous type, the query variable **must** be implicitly typed by using `var`.
3. Because the type of the query variable is implicit, the iteration variable in the foreach loop **must** also be implicit.
## Query Syntax and Method Syntax in LINQ (C#)
(https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq)
 
**Query syntax** and **method syntax** are semantically identical, but many people find query syntax simpler and easier to read. Some querie must be expressed as method calls. For example, you must use a method call to express a query that retrieves the number of elements that match a specified condition. You also must use a method call for a query that retrieves the element that has the maximum value in a source sequence. 

`Where(num => num % 2 == 0)` This inline expression is called a *lambda expression*. It is a convenient way to write code that would otherwise have to be written in more cumbersome form as an anonymous method or a generic delegate or an expression tree. In C# `=>` is the lambda operator, which is read as "goes to". The num on the left of the operator is the input variable which corresponds to num in the query expression. The compiler can infer the type of num because it knows that numbers is a generic `IEnumerable<T>` type. The body of the lambda is just the same as the expression in query syntax or in any other C# expression or statement; it can include method calls and other complex logic. The "return value" is just the expression result.

In the previous code example, note that the `OrderBy` method is invoked by using the dot operator on the call to `Where`. `Where` produces a filtered sequence, and then `Orderby` operates on that sequence by sorting it. Because queries return an `IEnumerable`, you compose them in method syntax by chaining the method calls together. This is what the compiler does behind the scenes when you write queries by using query syntax. And because a query variable does not store(I think it should be store here?). the results of the query, you can modify it or use it as the basis for a new query at any time, even after it has been executed.

## C# Features That Support LINQ
(https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/features-that-support-linq)

Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly. The use of var makes it possible to create anonymous types, but it(indicate what?) can be used only for local variables. 

## Walkthrough: Writing Queries in C# (LINQ)
(https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq)

The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types. 






