## 1. Two Sum
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **exactly one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

#### Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```
#### Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```
#### Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
 ```

#### Constraints:

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

## Solution:
```cpp
#include <vector>
#include <unordered_map>

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        
        std::vector<int> result;               // store and return the two integers that sum to the target
        std::unordered_map< int, int > values; // store integers for faster lookup
        
        // iterate over all integers looking for sum to the target
        for ( int i = 0; i < nums.size(); ++i )
        {       
            // search for the value that sums to the target
            int difference = target - nums[i];
            auto found = values.find( difference );
            
            // stop once two values sum to the target
            if ( found != values.end() )
            {
                result.push_back( found->second );
                result.push_back( i );
                break;
            }
            // add the current value and continue
            values.insert( {nums[i], i} );
        }
        
        return result;
    }
};
```
