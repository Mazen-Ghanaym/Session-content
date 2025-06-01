# General II Session

## [Session Recording](https://cisuezedu-my.sharepoint.com/:v:/g/personal/ugs_55542_ci_suez_edu_eg/EbgAj_fg6W9PpHjRR2iyYjYBWLdg-1TpozHinVebJNf4IQ?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=pGdk6c)

## Table of Contents

- [Functions](#functions)
- [Lambda Functions](#lambda-functions)
- [Prefix Sum & Suffix Sum](#prefix-sum)
- [Difference Array](#difference-array)
- [Binary Search Built In](#binary-search)

### Functions

- [C++ Function Declaration](https://www.programiz.com/cpp-programming/function)
- [C++ Function Definition](https://www.programiz.com/cpp-programming/function)
- [C++ Function Call](https://www.programiz.com/cpp-programming/function)
- [C++ Function Parameters](https://www.programiz.com/cpp-programming/function)
- [C++ Function Return Value](https://www.programiz.com/cpp-programming/function)
- [C++ Function Overloading](https://www.programiz.com/cpp-programming/function)
- [pass by value, pass by reference](https://www.programiz.com/cpp-programming/function)

#### Function Declaration

  ```cpp
  return_type function_name(parameters) {
      // code
  }
  ```

#### Function Call

  ```cpp
  function_name(parameters);
  ```

  Example:

  ```cpp
  int add(int a, int b) {
      return a + b;
  }

  int main() {
      int a = 5, b = 10;
      cout << add(a, b) << endl;
      return 0;
  }
  ```

#### Function Overloading

  Example:

  ```cpp
  int add(int a, int b) {
      return a + b;
  }

  double add(double a, double b) {
      return a + b;
  }

  int main() {
      int a = 5, b = 10;
      double c = 5.5, d = 10.5;
      cout << add(a, b) << endl;
      cout << add(c, d) << endl;
      return 0;
  }
  ```

#### Pass by Value

  Example:

  ```cpp
  void swap(int a, int b) {
      int temp = a;
      a = b;
      b = temp;
  }

  int main() {
      int a = 5, b = 10;
      swap(a, b);
      cout << a << " " << b << endl;
      return 0;
  }
  ```

#### Pass by Reference

  Example:

  ```cpp
  void swap(int &a, int &b) {
      int temp = a;
      a = b;
      b = temp;
  }

  int main() {
      int a = 5, b = 10;
      swap(a, b);
      cout << a << " " << b << endl;
      return 0;
  }
  ```

## Lambda Functions

  Syntax:

  ```cpp
  [capture clause] (parameters) -> return_type {
      // code
  }
  ```

  Example:

  ```cpp
  auto add = [](int a, int b) -> int {
      return a + b;
  };

  int main() {
      cout << add(5, 10) << endl;
      return 0;
  }
  ```

## Prefix Sum

  Example:

  ```cpp
  int n = 5;
  int a[] = {1, 2, 3, 4, 5};
  int prefix_sum[n];

  prefix_sum[0] = a[0];
  for (int i = 1; i < n; i++) {
      prefix_sum[i] = prefix_sum[i - 1] + a[i];
  }
  ```

## Difference Array

  Example:

  ```cpp
  int n = 5;
  int diff[n + 1];

  int q;
  cin >> q;
  while(q--){
      int l, r, x;
      cin >> l >> r >> x;
      diff[l] += x;
      diff[r + 1] -= x;
  }

  for (int i = 1; i <= n; i++) {
      diff[i] += diff[i - 1];
  }

  for (int i = 1; i <= n; i++){
      cout << diff[i] << " ";
  }
  cout << endl;
  ```

## Binary Search

  Example:

  ```cpp
  #include <iostream>
  #include <algorithm>

  using namespace std;

  int main() {
      int a[] = {1, 2, 3, 4, 5};
      int n = sizeof(a) / sizeof(a[0]);
      int key = 3;

      if (binary_search(a, a + n, key)) {
          cout << "Element found" << endl;
      } else {
          cout << "Element not found" << endl;
      }

      return 0;
  }
  ```

## References

- [C++ Functions](https://www.programiz.com/cpp-programming/function)
- [C++ Lambda Functions](https://www.programiz.com/cpp-programming/lambda-function)
- [C++ Prefix Sum](https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/)
- [C++ Difference Array](https://www.geeksforgeeks.org/difference-array-range-update-query-o1/)
- [C++ Binary Search](https://www.geeksforgeeks.org/binary-search/)

## Problems

- [Prime Function](https://codeforces.com/group/n3sTiYtHxI/contest/348734/problem/D)
  - [Solution](https://www.ideone.com/ABUNkN)
- [N Times](https://codeforces.com/group/n3sTiYtHxI/contest/348734/problem/H)
  - [Solution](https://www.ideone.com/nJQCJd)
- [Swapping With Matrix](https://codeforces.com/group/n3sTiYtHxI/contest/348734/problem/I)
  - [Solution](https://www.ideone.com/OiEREs)
- [Frequency Array](https://codeforces.com/group/h8UCFDEN7d/contest/558462/problem/Q)
  - [Solution](https://www.ideone.com/OW0s4I)
- [Static Range Sum Queries](https://cses.fi/problemset/task/1646)
  - [Solution](https://www.ideone.com/jICvwE)
- [Odd Queries](https://codeforces.com/contest/1807/problem/D)
  - [Solution](https://www.ideone.com/Q2MXAU)
- [Difference Array](https://www.hackerrank.com/challenges/crush/problem)
  - [Solution](https://www.ideone.com/tvpQGY)
- [Binary Search](https://codeforces.com/group/h8UCFDEN7d/contest/558417/problem/V)
  - [Solution](https://www.ideone.com/LcKfVV)
