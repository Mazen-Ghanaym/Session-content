# General III Session

## [Session Recording](https://cisuezedu-my.sharepoint.com/:v:/g/personal/ugs_55542_ci_suez_edu_eg/Ebw0cdKACHVMry1DXxLO4VUBz_c-brOkHPhc7h4kgIU-kg?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=Xtacp6)

## Table of Contents

- [Frequency Array](#frequency-array)
- [Prefix Sum & Suffix Sum](#prefix-sum)
- [Prefix Sum 2D](#prefix-sum-2d)
- [Difference Array or Partial Sum](#difference-array)
- [Partial Sum 2D](#partial-sum-2d)

### Frequency Array

```cpp
int n = 10;
int a[n] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
int freq[n] = {0};

for (int i = 0; i < n; i++) {
    freq[a[i]]++;
}

for (int i = 0; i < n; i++) {
    cout << freq[i] << " ";
}
```

Problem: [Frequency Array](https://codeforces.com/group/n3sTiYtHxI/contest/348752/problem/Q)

### Prefix Sum

```cpp
int n = 10;
int a[n] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
int prefix[n] = {0};
int suffix[n] = {0};

prefix[0] = a[0];
for (int i = 1; i < n; i++) {
    prefix[i] = prefix[i - 1] + a[i];
}

suffix[n - 1] = a[n - 1];
for (int i = n - 2; i >= 0; i--) {
    suffix[i] = suffix[i + 1] + a[i];
}

for (int i = 0; i < n; i++) {
    cout << prefix[i] << " ";
}
cout << endl;
for (int i = 0; i < n; i++) {
    cout << suffix[i] << " ";
}
```

Problem: [Range sum query](https://codeforces.com/group/n3sTiYtHxI/contest/348752/problem/R)

### Prefix Sum 2D

```cpp
int n = 3, m = 3;
int a[n][m] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
int prefix[n][m] = {0};

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        prefix[i][j] = a[i][j];
        if (i > 0) {
            prefix[i][j] += prefix[i - 1][j];
        }
        if (j > 0) {
            prefix[i][j] += prefix[i][j - 1];
        }
        if (i > 0 && j > 0) {
            prefix[i][j] -= prefix[i - 1][j - 1];
        }
    }
}

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        cout << prefix[i][j] << " ";
    }
    cout << endl;
}
```

Problem: [Forest Queries](https://cses.fi/problemset/task/1652)

### Difference Array

```cpp
int n = 5;
int diff[n + 1] = {0};

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

Problem: [Difference Array](https://www.hackerrank.com/challenges/crush/problem)

### Partial Sum 2D

```cpp
int n = 3, m = 3;
int diff[n + 1][m + 1] = {0};

int q;
cin >> q;
while(q--){
    int x1, y1, x2, y2, x;
    cin >> x1 >> y1 >> x2 >> y2 >> x;
    diff[x1][y1] += x;
    diff[x2 + 1][y1] -= x;
    diff[x1][y2 + 1] -= x;
    diff[x2 + 1][y2 + 1] += x;
}

for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= m; j++) {
        diff[i][j] += diff[i - 1][j] + diff[i][j - 1] - diff[i - 1][j - 1];
    }
}

for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= m; j++) {
        cout << diff[i][j] << " ";
    }
    cout << endl;
}
```

Problem: [Cherry and Bits](https://www.codechef.com/problems/CENS20A)
