# logger
C++ log abstraction

## Inspiration

The _Dr.Dobb's Journal_ (no longer in print) had published some articles that
used the C++ left-shift operator (**`operator()<<`**) to define a logger based
on **`std::ostream<>`**.
- DDJ October 2007 article by Petru Marginean, September 05, 2007: [_"Logging in C++"_](https://www.drdobbs.com/cpp/logging-in-c/201804215)
- DDJ ???? article by Filip Janiszewski, January 31, 2013: [_"A Lightweight Logger for C++"_](https://www.drdobbs.com/cpp/a-lightweight-logger-for-c/240147505)

Unfortunately, neither article or code is available from the website anymore.
But the basic premise was to take advantage of a destructer called when the
_temporary instance_ representing a logger "line" goes out-of-scope.

These articles had been written without **`C++11`**, and I've used this theme
multiple times since, to use more recent language features.
However, one of the more obnoxious issues was the persistent need for **`C`**
macros, to report the line number and file name from the source code (via
`__LINE__` and `__FILE__`).

Fortunately, **`C++20`** has the new
[`source_location`](https://en.cppreference.com/w/cpp/utility/source_location).
feature :smiley:

## Goals

- Implement logger from scratch in **`C++20`**, without macros, to support `std::ostream<>`.
- Thread safe
- Exception safe
- Portable
- Efficient (limited overhead when optimized)
- Const-correct semantics
- Fully unit-tested
- Use stack where possible.
- Characterize use of heap.
- Investigate limited support for **async-signal safe** usage.
