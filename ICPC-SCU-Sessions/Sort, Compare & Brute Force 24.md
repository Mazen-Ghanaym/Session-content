# Sort, compare & brute force

## [Session Recording](https://cisuezedu-my.sharepoint.com/:v:/g/personal/ugs_55542_ci_suez_edu_eg/EYTCelGXZ6tKjUk_OCyjGokBpDoFuSdSSN8Q1S9hcVS9AA?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=dQxU2M)

## Sort vector

### We can sort vectors using sort( ) built-in function

```cpp
vector< int > v = { 1, 3, 4, 2, 7, 6, 5, 8, 10, 9};
sort(v.begin(), v.end()); // vector will be sorted in ascending order.
// vector after sort will be like:
// v = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}; 
```

but we can pass the third parameter to sort in ascending or descending order.

We can use less to greater like this

```cpp
sort(v.begin(), v.end(), less< int >); // it will sort in ascending order and it is a default operator
sort(v.begin(), v.end(), greater< int >); // it will sort in descending order.
```

## Sort vectors using the compare function

we can pass a boolean function to the built-in sort function.

First, we can make Compare function outside the main function as follows:

```cpp
    //Sort in ascending order
    bool comp(int &a, int &b){
            return a < b; 
    }
```

```cpp
    //Sort in descending order
    bool comp(int &a, int &b){
            return a > b; 
    }
```

Now we can use it in sort function as a third parameter:

```cpp
sort(v.begin(), v.end(), comp);
```

But how does passing a function to another function work? I will explain this later.

Now, let's talk about lambda functions.

### What are lambda functions?

A lambda function is a function that we write within the main function.

```cpp
    auto sum1_n = [](int n) -> long long {
            return n * (n + 1) / 2;
    };  

    // auto is a appreviation for  function< "return type"(parameters)>
    // like the above example auto = function< ll (int n) >
    // We use [] to pass & operator to notice the compiler that uses any variable in main [&]
    // -> return datatype of the function
```

We can use lambda to make comp function in the main or pass it to the sort function.

```cpp
    auto comp = [](int &a, int &b) -> bool {
            return a < b; // sort in ascending order.
    }

    sort(v.begin(), v.end(), comp);

    // or pass it to sort directly
    sort(v.begin(), v.end(), [](int &a, int &b){
            return a < b;
    });
```

Problem:

[Developing Skills](https://codeforces.com/contest/581/problem/C)

### Sort vector of pair

```cpp
    sort(v.begin(), v.end(), less<pair<int,int>>());
    sort(v.begin(), v.end(), greater<pair<int,int>>());

    bool comp(pair<int, int> &a, pair<int, int> &b){
        return a.second < b.second; // sort in ascending order by the second element
    }

    sort( v.begin(), v.end(), comp);

    // USING lambda 
    sort( v.begin(), v.end(), [](pair<int,int> &a, pair<int,int> &b){
            if(a.first==b.first)
                    return a.second > b.second;
            return a.first < b.first;
    });
```

### Sort vector of struct

```cpp
    struct key {
        int x;
        bool operator< (const int & a) const{
            return x < a;
        }
    };

    vector<key> v= {1, 2, 3};
    sort(v.begin() , v.end());

    bool comp(const key &a, const key &b){
            return a.x < b.x;
    }
    sort(v.begin(), v.end(), comp);

    // And with lambda.
```

[Camp Cup](https://codeforces.com/group/vHdLQHscPA/contest/363025/problem/D)

### Sort sets

```cpp
    set<int, less<int>> st;
    set<int, greater<int>> st;

    struct key{
            int val;
            bool operator <(const key &rhs)const{
                    return val < rhs.val;
            }
    }
    set<key> st;

    struct key{
            bool operator ()(const int &lhs, const int &rhs)const{
                    return lhs < rhs;
            }
    }
    set<int, key> st;

    // sort with class:
    class comp{
        public:
            bool operator()(const int &a, const int &b){
                return a < b;
            }
    };
    set<int, comp> st;

```

[F. New job](https://codeforces.com/group/nm0n1RosrQ/contest/434817/problem/F)

### Sort map by key

```cpp
    struct key{
            int val;
            bool operator <(const key &rhs)const{
                    return val < rhs.val;
            }
    }

    map<key, int> mp;

    struct key{
            bool operator ()(const int &lhs, const int &rhs)const{
                    return lhs < rhs;
            }
    }
    map<int, int, key> mp;
    // Or You can convert it to vector of pair and sort it as you want

```

### Sort priority_queue

```cpp
    priority_queue<int> pq;    // large value in top
    priority_queue<int, vector<int>, greater<int>> pq // small value in top

    struct key{
            int val;
            bool operator <(const key &rhs)const{
                    return val < rhs.val;
            }
    }
    priority_queue<key> pq;

    struct key{
            bool operator ()(const int &lhs, const int &rhs)const{
                    return lhs < rhs;
            }
    }
    priority_queue<int, vector<int>, key> pq;
```

[Potions (Hard Version)](https://codeforces.com/problemset/problem/1526/C2)

### Brute force

#### Next & Prev Permutation in C++

```cpp
    // generate all permutations of a string
    string s = "abc";
    sort(s.begin(), s.end());
    do {
        cout << s << endl;
    } while (next_permutation(s.begin(), s.end()));

    // generate all permutations of a vector
    vector<int> v = {1, 2, 3};
    sort(v.begin(), v.end());
    do {
        for (int i = 0; i < v.size(); i++) {
            cout << v[i] << " ";
        }
        cout << endl;
    } while (next_permutation(v.begin(), v.end()));

    // prev_permutation
    string s = "cba";
    sort(s.begin(), s.end());
    do {
        cout << s << endl;
    } while (prev_permutation(s.begin(), s.end()));

    // generate all permutations of a vector
    vector<int> v = {3, 2, 1};
    sort(v.begin(), v.end());
    do {
        for (int i = 0; i < v.size(); i++) {
            cout << v[i] << " ";
        }
        cout << endl;
    } while (prev_permutation(v.begin(), v.end()));
```

[V. Easy ya bro easy](https://codeforces.com/group/nm0n1RosrQ/contest/434817/problem/V)

[J. Kitchen Plates](https://codeforces.com/group/mtMLJOBlO4/contest/465589/problem/J)

#### Power Set

```cpp
    // generate all subsets of a set
    vector<int> v = {1, 2, 3};
    int n = v.size();
    for (int i = 0; i < (1 << n); i++) {
        for (int j = 0; j < n; j++) {
            if (i & (1 << j)) {
                cout << v[j] << " ";
            }
        }
        cout << endl;
    }
```

[491. Non-decreasing Subsequences](https://leetcode.com/problems/non-decreasing-subsequences/description/)
