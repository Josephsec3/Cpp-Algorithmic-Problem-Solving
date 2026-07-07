# C++ Algorithmic Problem Solving: Minimum Distance Tracker

## 📌 Project Overview
This repository contains efficient C++ solutions for algorithmic problems focusing on array manipulation, optimization, and time-complexity management. 

This specific program identifies the minimum element in an array and calculates the shortest distance between any two occurrences of that minimum value.

## 🛠️ Code Logic & Optimization
* **Fast I/O:** Utilizes `ios_base::sync_with_stdio(false); cin.tie(nullptr);` to optimize standard input/output streams for competitive programming speeds.
* **Time Complexity:** $\mathcal{O}(N)$ — The array is processed in linear time, making it highly efficient for large datasets.
* **Space Complexity:** $\mathcal{O}(N)$ — Uses a dynamic `std::vector` to store the elements.

## 🚀 Corrected Source Code
```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    // Optimize input/output operations
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    int n; 
    if (!(cin >> n)) return 0;

    int min_val = INT_MAX;
    vector<int> a(n);
    
    // First pass: Read array and find the global minimum
    for (int i = 0; i < n; i++){
        cin >> a[i];
        min_val = min(min_val, a[i]);
    }

    int last_index = -1;
    int min_distance = INT_MAX;

    // Second pass: Find the minimum distance between duplicate minimum values
    for (int i = 0; i < n; i++){
        if (a[i] == min_val){
            if (last_index != -1) {
                min_distance = min(min_distance, i - last_index);
            }
            last_index = i;
        }
    }

    // Output the result (If no duplicate minimums found, outputs INT_MAX)
    cout << min_distance << "\n";
    return 0;
}
