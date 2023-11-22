## Kids With the Greatest Number of Candies

Leetcode: [Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/description/)

### Code

Language: **C++**

#### Solution 1:

Time Complexity: O(n) \
Space Complexity: O(1)

```
class Solution {
    public:

    vector<bool> kidsWithCandies(vector<int>& candies, int extraCandies) {

        int maxCandies = -1;
        for(int i = 0; i < candies.size(); i++)
            maxCandies = max(candies[i], maxCandies);

        vector<bool> ans(candies.size());

        for(int i = 0; i < candies.size(); i++)
            ans[i] = candies[i] + extraCandies >= maxCandies ? true : false;

        return ans;
    }
};
```
