# Dart: Silent Failure Due to Missing `rethrow` in Exception Handling

This repository demonstrates a common error in Dart exception handling where a missing `rethrow` statement can lead to unexpected silent failures. The `bug.dart` file showcases the problem, while `bugSolution.dart` provides the corrected version.

## Problem

In the initial code (`bug.dart`), the `catch` block within the `fetchData` function handles exceptions but doesn't rethrow them.  This means that errors during the API call or JSON decoding are caught, but the `main` function's `try-catch` block never sees the error.  The program continues execution without indicating the problem. 

## Solution

The `bugSolution.dart` file addresses the issue by adding `rethrow` at the end of the `catch` block in `fetchData`.  This ensures that the exception is propagated back up the call stack, allowing the outer `try-catch` block in `main` to handle the error appropriately. 

## How to reproduce

1. Clone this repository.
2. Run `bug.dart`. Note that even if the API call fails, it will only print a local error and not rethrow the error.
3. Run `bugSolution.dart`. Now, if the API call fails, it propagates the error properly, showing the true error in the console.
