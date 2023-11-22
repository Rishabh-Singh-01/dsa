## Increasing Triplet Subsequence

Leetcode: [Increasing Triplet Subsequence](https://leetcode.com/problems/increasing-triplet-subsequence/)

### Code

Language: **C**

#### Solution 1:

My solution - Brute Force \
Time Complexity: O(n^3) \
Space Complexity: O(1)

```
bool increasingTriplet(int* nums, int numsSize) {
    int i = 0;
    int j = i + 1;
    int k = j + 1;

    while( i < numsSize - 2){
        j = i + 1;
        while( j < numsSize - 1){
            k = j + 1;
            while( k < numsSize){
                if(nums[k] > nums[j] && nums[j] > nums[i]) return true;
                k++;
            }
            j++;
        }
        i++;
    }

    return false;
}
```

#### Solution 2:

Better Solution: More optimized version \
Time Complexity: O(n) \
Space Complexity: O(1) \
Description: Would be more helpful when triplets are needed to print

```
bool increasingTriplet(int* nums, int numsSize) {
    int i = 0;

    int globalFirstVal = INT_MAX;
    int globalSecondVal = INT_MAX;

    int firstVal = INT_MAX;
    int secondVal = INT_MAX;

    while(i < numsSize){
        if(nums[i] > globalSecondVal && nums[i] > globalFirstVal) return true;

        if(nums[i] < firstVal){
            firstVal = nums[i];
            secondVal = INT_MAX;
        }

        if(nums[i] > firstVal && nums[i] < secondVal) secondVal = nums[i];

        // assigning globalVariable
        if(secondVal < globalSecondVal){
            globalSecondVal = secondVal;
            globalFirstVal = firstVal;
        }

        i++;
    }

    return false;
}
```

-- OR --

Same Solution: Same as above solution 2 but using structs (more fancy) \
Time Complexity: O(n) \
Space Complexity: O(1)

```
struct twoValPairs{
    int firstValue;
    int secondValue;
};

bool increasingTriplet(int* nums, int numsSize) {
    int i = 0;

    struct twoValPairs globalPair;
    globalPair.firstValue = INT_MAX;
    globalPair.secondValue = INT_MAX;

    struct twoValPairs localPair;
    localPair.firstValue = INT_MAX;
    localPair.secondValue = INT_MAX;

    while(i < numsSize){
        if(nums[i] > globalPair.secondValue && nums[i] > globalPair.firstValue)
            return true;

        if(nums[i] < localPair.firstValue){
            localPair.firstValue = nums[i];
            localPair.secondValue = INT_MAX;
        }

        if(nums[i] > localPair.firstValue && nums[i] < localPair.secondValue)
            localPair.secondValue = nums[i];

        // assigning globalVariable
        if(localPair.secondValue < globalPair.secondValue){
            globalPair.secondValue = localPair.secondValue;
            globalPair.firstValue = localPair.firstValue;
        }

        i++;
    }

    return false;
}
```

#### Solution 3:

Better Solution: Most optimized version \
Time Complexity: O(n) \
Space Complexity: O(1) \
Description: Even removes the extra variables

```
struct twoValPairs{
    int firstValue;
    int secondValue;
};

bool increasingTriplet(int* nums, int numsSize) {
    int i = 0;

    struct twoValPairs localPair;
    localPair.firstValue = INT_MAX;
    localPair.secondValue = INT_MAX;

    while(i < numsSize){
        if(nums[i] > localPair.secondValue && nums[i] > localPair.firstValue)
            return true;

        if(nums[i] < localPair.firstValue)
            localPair.firstValue = nums[i];

        if(nums[i] > localPair.firstValue && nums[i] < localPair.secondValue)
            localPair.secondValue = nums[i];

        i++;
    }

    return false;
}
```
