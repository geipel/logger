# logger
C++ log abstraction

## Inspiration

The _Dr.Dobb's Journal_ (no longer in print) had published some articles that used the C++
left-shift operator (**`operator()<<`**) to define a logger based on **`std::ostream<>`**.
- DDJ October 2007 article by Petru Marginean, September 05, 2007: [_"Logging in C++"_](https://www.drdobbs.com/cpp/logging-in-c/201804215)
- DDJ ???? article by Filip Janiszewski, January 31, 2013: [_"A Lightweight Logger for C++"_](https://www.drdobbs.com/cpp/a-lightweight-logger-for-c/240147505)

Unfortunately, I cannot seem to retrieve either article or code from the website, anymore.
But as I recall, the basic premise was to take advantage of a destructer called when the
temporary instance representing a logger "line" instance goes out-of-scope.

These articles had been written without **`C++11`**, and I've used this theme multiple
times since, to use more recent language features.
However, one of the more obnoxious issues was the need for **`C`** macros, to report the
line number and file name from the source code (via `__LINE__` and `__FILE__`).

## Goals

- Re-implement from scratch in **`C++20`** using new features to remove the need for macros. :smiley:
- Thread safety
- Portable
- Efficient (limited overhead when optimized)
- Fully unit-tested
- Characterize use of heap
