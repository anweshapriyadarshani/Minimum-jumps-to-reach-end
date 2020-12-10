# Minimum-jumps-to-reach-end
You are given an array of nonnegative integers. Let's say you start at the beginning of the array and are trying to advance to the end. You can advance at most, the number of steps that you're currently on. Determine whether you can get to the end of the array.  For example, given the array [1, 3, 1, 2, 0, 1], we can go from indices 0 -> 1 -> 3 -> 5, so return true.  Given the array [1, 2, 1, 0, 0], we can't reach the end, so return false.

#include <bits/stdc++.h>
using namespace std;
 
// Function to return the minimum number
// of jumps to reach arr[h] from arr[l]
int minJumps(int arr[], int n)
{
 
    // Base case: when source and
    // destination are same
    if (n == 1)
        return 0;
 
    // Traverse through all the points
    // reachable from arr[l]
    // Recursively, get the minimum number
    // of jumps needed to reach arr[h] from
    // these reachable points
    int res = INT_MAX;
    for (int i = n - 2; i >= 0; i--) {
        if (i + arr[i] >= n - 1) {
            int sub_res = minJumps(arr, i + 1);
            if (sub_res != INT_MAX)
                res = min(res, sub_res + 1);
        }
    }
 
    return res;
}
 
// Driver Code
int main()
{
    int arr[] = { 1, 3, 6, 3, 2,
                  3, 6, 8, 9, 5 };
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Minimum number of jumps to";
    cout << " reach the end is " << minJumps(arr, n);
    return 0;
}
