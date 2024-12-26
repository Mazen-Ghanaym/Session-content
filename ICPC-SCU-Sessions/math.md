# Math

## [Session Record](https://cisuezedu-my.sharepoint.com/:v:/g/personal/ugs_55542_ci_suez_edu_eg/ETkNBvT0NrdLpS2NGMgDLEgBWsiXZvrDB1I5lHl3iFZDRg?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=SGiPg8)

## Table of Contents

1. [Session Content](#session-content)
2. [Problems](#problems)

## Session Content

- [Addition](https://en.wikipedia.org/wiki/Addition)

    ``` cpp
    int x = 5, y = 10;
    int sum = x + y;
    ```

- [Subtraction](https://en.wikipedia.org/wiki/Subtraction)

    ``` cpp
    int x = 10, y = 5;
    int difference = x - y;
    ```

- [Multiplication](https://en.wikipedia.org/wiki/Multiplication)

    ``` cpp
    int x = 5, y = 10;
    int product = x * y;
    ```

- [Division](https://en.wikipedia.org/wiki/Division)

    ``` cpp
    int x = 10, y = 5;
    int quotient = x / y;
    ```

- [Exponentiation](https://en.wikipedia.org/wiki/Exponentiation)

    ``` cpp
    int x = 2, y = 3;
    int power = pow(x, y);
    ```

- [Roots](https://en.wikipedia.org/wiki/Square_root)

    ``` cpp
    int x = 16;
    int squareRoot = sqrt(x);
    ```

- [Factorial](https://en.wikipedia.org/wiki/Factorial)

    ``` cpp
    int x = 5;
    int factorial = 1;
    for (int i = 1; i <= x; i++) {
        factorial *= i;
    }
    ```

- [Ceiling Function](https://en.wikipedia.org/wiki/Floor_and_ceiling_functions)

    ``` cpp
    double x = 5.5;
    int ceil = ceil(x);
    ```

- [Floor Function](https://en.wikipedia.org/wiki/Floor_and_ceiling_functions)

    ``` cpp
    double x = 5.5;
    int floor = floor(x);
    ```

- [Modulo](https://en.wikipedia.org/wiki/Modulo_operation)

    ``` cpp
    int x = 10, y = 3;
    int remainder = x % y;
    ```

- [Divisibility](https://en.wikipedia.org/wiki/Divisibility)

    ``` cpp
    int x = 10, y = 5;
    if (x % y == 0) {
        cout << "Divisible";
    } else {
        cout << "Not Divisible";
    }
    ```

- [Logarithm](https://en.wikipedia.org/wiki/Logarithm)

    ``` cpp
    double x = 100;
    double logBase10 = log10(x);
    double logBase2 = log2(x);
    ```

- [Fibonacci Sequence](https://en.wikipedia.org/wiki/Fibonacci_number)

    ``` cpp
    int n = 10;
    int a = 0, b = 1, c;
    for (int i = 0; i < n; i++) {
        c = a + b;
        a = b;
        b = c;
    }
    ```

- [Arithmetic Progression](https://en.wikipedia.org/wiki/Arithmetic_progression)

    ``` cpp
    int a = 1, d = 2, n = 5;
    int sum = n * (2 * a + (n - 1) * d) / 2;
    ```

- [Geometric Progression](https://en.wikipedia.org/wiki/Geometric_progression)

    ``` cpp
    int a = 1, r = 2, n = 5;
    int sum = a * (pow(r, n) - 1) / (r - 1);
    ```

- [Divisors](https://en.wikipedia.org/wiki/Divisor)

    ``` cpp
    // O(n)
    int x = 10;
    for (int i = 1; i <= x; i++) {
        if (x % i == 0) {
            cout << i << " ";
        }
    }

    // O(sqrt(n))
    int x = 10;
    for (int i = 1; i <= sqrt(x); i++) {
        if (x % i == 0) {
            cout << i << " ";
            if (i != x / i) {
                cout << x / i << " ";
            }
        }
    }
    ```

- [Prime Numbers](https://en.wikipedia.org/wiki/Prime_number)

    ``` cpp
    // O(n)
    int x = 10;
    bool isPrime = true;
    for (int i = 2; i < x; i++) {
        if (x % i == 0) {
            isPrime = false;
            break;
        }
    }

    // O(sqrt(n))
    int x = 10;
    bool isPrime = true;
    for (int i = 2; i <= sqrt(x); i++) {
        if (x % i == 0) {
            isPrime = false;
            break;
        }
    }
    ```

- [Factorization](https://en.wikipedia.org/wiki/Integer_factorization)

    ``` cpp
    // O(n)
    int x = 10;
    for (int i = 2; i <= x; i++) {
        while (x % i == 0) {
            cout << i << " ";
            x /= i;
        }
    }

    // O(sqrt(n))
    int x = 10;
    for (int i = 2; i <= sqrt(x); i++) {
        while (x % i == 0) {
            cout << i << " ";
            x /= i;
        }
    }
    if (x > 1) {
        cout << x << " ";
    }
    ```

- [Greatest Common Divisor](https://en.wikipedia.org/wiki/Greatest_common_divisor)

    ``` cpp
    // O(n)
    int x = 10, y = 15;
    int gcd = 1;
    for (int i = 1; i <= min(x, y); i++) {
        if (x % i == 0 && y % i == 0) {
            gcd = i;
        }
    }

    ```

- [Euclidean Algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm)

    ``` cpp
    // O(log(min(x, y))) Euclidean Recursive
    
    int gcd(int x, int y) {
        if (y == 0) {
            return x;
        }
        return gcd(y, x % y);
    }

    // O(log(min(x, y))) Euclidean Iterative
    
    int gcd(int x, int y) {
        while (y != 0) {
            int temp = y;
            y = x % y;
            x = temp;
        }
        return x;
    }

    // O(log(min(x, y))) Euclidean built-in

    int x = 10, y = 15;
    int gcd = __gcd(x, y);

    ```

- [Least Common Multiple](https://en.wikipedia.org/wiki/Least_common_multiple)

    ``` cpp
    // O(n)
    int x = 10, y = 15;
    int lcm = max(x, y);
    while (true) {
        if (lcm % x == 0 && lcm % y == 0) {
            break;
        }
        lcm++;
    }

    // O(log(min(x, y)))
    int x = 10, y = 15;
    int lcm = x * y / __gcd(x, y);
    ```

- [Quadratic Equation](https://en.wikipedia.org/wiki/Quadratic_equation)

    ``` cpp
    double a = 1, b = 5, c = 6;
    double d = b * b - 4 * a * c;
    if (d > 0) {
        double x1 = (-b + sqrt(d)) / (2 * a);
        double x2 = (-b - sqrt(d)) / (2 * a);
    } else if (d == 0) {
        double x = -b / (2 * a);
    } else {
        cout << "No Real Roots";
    }
    ```

- [Base Conversion](https://en.wikipedia.org/wiki/Numeral_system)

    ``` cpp
    string convert_from_decimal_to_base(int n, int base){
    string num = "";
    while(n){
        int rem = n % base;
        num += char((rem < 10 ? rem + '0' : (rem - 10 + 'A')));
        n /= base;
    }
    reverse(num.begin(), num.end());
    return num;
    }
    int from_any_base_to_decimal(string num, int base){
        int n = 0;
        for(int i = 0; i < num.size(); i++){
            n *= base;
            n += (isdigit(num[i]) ? num[i] - '0' : num[i] - 'A' + 10);
        }
        return n;
    }
    ```

- [Pythagorean Theorem](https://en.wikipedia.org/wiki/Pythagorean_theorem)

    ``` cpp
    double a = 3, b = 4;
    double c = sqrt(a * a + b * b);
    ```

- [Matrix](https://en.wikipedia.org/wiki/Matrix_(mathematics))

    ``` cpp
    int matrix1[2][2] = {{1, 2}, {3, 4}};
    int matrix2[2][2] = {{5, 6}, {7, 8}};
    int result[2][2];
    // add
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            result[i][j] = matrix1[i][j] + matrix2[i][j];
        }
    }

    // multiply
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            result[i][j] = 0;
            for (int k = 0; k < 2; k++) {
                result[i][j] += matrix1[i][k] * matrix2[k][j];
            }
        }
    }
    ```

- [Euclidean Geometry](https://en.wikipedia.org/wiki/Euclidean_geometry)

    ``` cpp
    // distance between two points
    double x1 = 1, y1 = 1, x2 = 4, y2 = 5;
    double distance = sqrt(pow(x2 - x1, 2) + pow(y2 - y1, 2));

    // slope of a line
    double x1 = 1, y1 = 1, x2 = 4, y2 = 5;
    double slope = (y2 - y1) / (x2 - x1);

    // area of a triangle
    double a = 3, b = 4, c = 5;
    double s = (a + b + c) / 2;
    double area = sqrt(s * (s - a) * (s - b) * (s - c));

    // area of a circle
    double r = 5;
    double area = M_PI * r * r;

    // circumference of a circle
    double r = 5;
    double circumference = 2 * M_PI * r;

    // area of a rectangle
    double width = 3, height = 4;
    double area = width * height;

    // perimeter of a rectangle
    double width = 3, height = 4;
    double perimeter = 2 * (width + height);

    // area of a square
    double side = 5;
    double area = side * side;

    // perimeter of a square
    double side = 5;
    double perimeter = 4 * side;
    ```

- [Permutations](https://en.wikipedia.org/wiki/Permutation)

    ``` cpp
    int n = 5, r = 3;
    int permutation = 1;
    for (int i = 0; i < r; i++) {
        permutation *= n - i;
    }

    // nPr = n! / (n - r)!
    int n = 5, r = 3;
    int permutation = factorial(n) / factorial(n - r);
    ```

- [Combinations](https://en.wikipedia.org/wiki/Combination)

    ``` cpp
    int n = 5, r = 3;
    int combination = 1;
    for (int i = 0; i < r; i++) {
        combination *= n - i;
        combination /= i + 1;
    }

    // nCr = n! / (r! * (n - r)!)
    int n = 5, r = 3;
    int combination = factorial(n) / (factorial(r) * factorial(n - r));
    ```

- [Pascal's Triangle](https://en.wikipedia.org/wiki/Pascal%27s_triangle)

    ``` cpp
    int n = 5;
    int pascal[n][n];
    for (int i = 0; i < n; i++) {
        for (int j = 0; j <= i; j++) {
            if (j == 0 || j == i) {
                pascal[i][j] = 1;
            } else {
                pascal[i][j] = pascal[i - 1][j - 1] + pascal[i - 1][j];
            }
        }
    }
    ```

## Problems

- [Problem 1](https://codeforces.com/problemset/problem/1325/A)
- [Problem 2](https://codeforces.com/problemset/problem/797/A)
- [Problem 3](https://codeforces.com/problemset/problem/822/A)
- [Problem 4](https://codeforces.com/problemset/problem/546/A)
- [Problem 5](https://codeforces.com/problemset/problem/742/A)
- [Problem 6](https://codeforces.com/problemset/problem/486/A)
