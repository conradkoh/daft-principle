<rules>
Follow these rules for code generations.

## Considerations

### Size of edits

When tackling complex changes prefer incremental changes, or creating completely new code and migrating over, to simplify the test.
For large complex migrations, make sure you use create a plan, and verify your changes against that plan as you proceed cautiously.

### Performance and Costs

When querying a database, always consider the performance of the query. Use an index when looking up on columns that have large volumes of data, or on well ordered columns.

If you are using a Convex backend, remember that the computations run in the database itself, making it feasible to do large numbers of DB calls and doing n+1 queries efficiently.

### Code Quality and Maintainability

Consider the SOLID principles and the DAFT coding principles, applying the right amount of abstraction when writing code.
</rules>

## <reference-material>

# DAFT Coding Principles

The DAFT coding principles are a set of principles that are used to guide the construction of effective abstractions in software development.

## D is for Dimensionality

When creating an abstraction in place of a third party library, it is important to determine the dimensionality of the problem we are abstracting over.
Examples:

- High dimensionality - the UI layer in HTML (e.g. div), due to the number of possible parameters used as an input
- Low dimensionality - a math utility function that computes the fibonacci sequence

## A is for Architecture

Consider the architecture of the programme. Depending on the size of the programme, the choices for abstractions would be vastly different.
There are also 2 different kids of projects

- Logically Specified: Clearly defined principles, apporach and outcomes. Logical reasoning is useful to tackle these problems.
- Contextually Specified: Defined more on preferences, conventions. Highly nuanced. More effective to tackle by doing research and following examples.

Do note that there is always a level of contextually specified code, especially when desiging the exposed API for users. After all, programming is a language. The idea is to focus highly in a given context, on logically specified code, and ensure that they are well documented, highly tested and performant. Then, for contextually specified functionality, we can defer tests to the external layers, to test things via the user interface for example.

Examples:

- Mixed architecture - a full stack app with mobile support, ETL, cron jobs
- Small logically specified architecture - a library that does sorting
- Large logically specified architecture - an ORM tool for a database

## F is for frequency of modification

The value of an abstraction is amplified by the frequency of modification of the code. The more the code needs to be iterated on, the more valuable ensuring that it is testable and well structured.

## T is for temporal binding of code to the project

Temporal binding is a measure of how relevant the piece of code will continue to be over the growth of the application in the overall architecture. If this piece of code is going to be more and more important, then it is strongly bound temporally to the project.
Examples:

- Highly bound: The entities of the domain in clean architecture
- Loosely bound: A migration script
  </reference-material>
