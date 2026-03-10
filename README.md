# Merge Two Sorted Arrays

## 📌 Problem
Given two sorted arrays `a[]` and `b[]`, merge them into sorted order such that:
- The first `a.length` smallest elements remain in array `a`
- The remaining elements are stored in array `b`

The final arrays should remain **sorted**.

---

## 🧠 Approach

1. Create a temporary array `c` of size `a.length + b.length`.
2. Use three pointers:
   - `i` → traverse array `a`
   - `j` → traverse array `b`
   - `k` → insert elements into array `c`
3. Compare elements of `a` and `b` and store the smaller one in `c`.
4. Copy remaining elements if one array finishes.
5. Copy the first `a.length` elements back into `a`.
6. Copy the remaining elements into `b`.

---

## 💻 Java Implementation

```java
class Solution {
    public void mergeArrays(int a[], int b[]) {

        int[] c = new int[a.length + b.length];
        int i = 0, j = 0, k = 0;

        while(i < a.length && j < b.length){
            if(a[i] < b[j]){
                c[k++] = a[i++];
            }
            else{
                c[k++] = b[j++];
            }
        }

        while(i < a.length){
            c[k++] = a[i++];
        }

        while(j < b.length){
            c[k++] = b[j++];
        }

        // Copy first part to array a
        for(i = 0; i < a.length; i++){
            a[i] = c[i];
        }

        // Copy remaining part to array b
        for(j = 0; j < b.length; j++){
            b[j] = c[a.length + j];
        }
    }
}
📊 Example
Input
a = [1,5,9]
b = [2,3,8]
Merged Array
[1,2,3,5,8,9]
Output
a = [1,2,3]
b = [5,8,9]
⏱ Time Complexity
O(n + m)
💾 Space Complexity
O(n + m)
 
✍️ Author
Sanjeev Sharma
