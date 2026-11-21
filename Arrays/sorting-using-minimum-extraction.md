# Sorting an Array Using Repeated Minimum Extraction

- problem-link: https://takeuforward.org/practice/dsa/selection-sort
- original-editorial-link: https://takeuforward.org/practice/dsa/selection-sort?tab=peer-solutions&sort=latest&discussion_id=15004

## Intuition
The idea is to repeatedly find the smallest element from the original array and place it into a new vector. 

Since we want the elements in ascending order, extracting the minimum element in every iteration guarantees that the new vector will contain elements in sorted order.

We continue this process until the original array becomes empty.

## Approach
1. Create an empty vector ans to store the sorted elements.

2. Traverse the original vector to find the minimum element.

3. Insert the minimum element into ans.

4. Remove that minimum element from the original vector.

5. Repeat steps 2–4 until the original vector becomes empty.

6. Return the resulting vector.

## Solution
```cpp
class Solution {
public:
    vector<int> selectionSort(vector<int>& nums) {
        vector<int> ans;

        while(!nums.empty()) {
            int mini = min_element(nums.begin(), nums.end()) - nums.begin();

            ans.push_back(nums[mini]);
            nums.erase(nums.begin() + mini);
        }
        
        return ans;
    }
};
```

## Complexity
**Time Complexity:**
O(n^2): In every iteration, we search for minimum element in the remaining vector. 
- First iteration: O(n)
- Second iteration: O(n-1)
- Third iteration: O(n-2)
- . . . 
- Last iteration: O(1)

Therefore, the total time complexity is T(n) = n(n+1)/2 = O(n^2).

Additionally, erasing an element from a vector can require shifting subsequent elements, which also takes linear time in the worst case. This does not change the overall O(n^2) complexity. 


**Space Complexity:**
O(n) — We create additional vector `ans` to store all the sorted elements.
In the worst case, it contains all n elements of the original array. 
Therefore, the additional space complexity is O(n).

## Conclusion
This approach sorts the array by repeatedly extracting its minimum element. It is a straightforward implementation of the selection-based sorting idea, using an additional vector to maintain the sorted result.

## Note: 
This approach is logically correct, but it uses O(n) extra space. Traditional selection sort improves the space complexity to O(1) by swapping elements within the original array instead of creating another vector. Both have O(n^2) time complexity.
