## Max Number of K-Sum Pairs

Leetcode: [Max Number of K-Sum Pairs](https://leetcode.com/problems/max-number-of-k-sum-pairs/)

### Details

Language: **C/C++** \
Leetcode Level: Medium

#### Solution 1:

My Solution: Brute Force\
Time Complexity: O(n^2) \
Space Complexity: O(n)
Description: This solution uses an extra array for the elements that are flagged.

```
int maxOperations(int* nums, int numsSize, int k){
    int pairs = 0;
    int* arrPtr = (int*) calloc(numsSize, sizeof(int));
    for(int i = 0; i < numsSize; i++){
        for(int j = i + 1; j < numsSize; j++){
            if(arrPtr[i] != 0) break;
            if(arrPtr[j] != 0) continue;
            if(nums[i] + nums[j] == k){
                pairs++;
                arrPtr[i] = 1;
                arrPtr[j] = 1;
                break;
            }
        }
    }
    free(arrPtr);
    return pairs;
}
```

Community Solution: Brute Force\
Time Complexity: O(n^2) \
Space Complexity: O(1)
Description: This solution doesnot uses an extra array for the elements that are flagged but instead changes the element of the main array itself.

```
class Solution {
    public int maxOperations(int[] nums, int k) {
        int count = 0;
        for(int i = 0; i < nums.length; i++){
            if(nums[i] == -1) continue;
            for(int j = i + 1; j < nums.length; j++){
                if(nums[j] == -1) continue;
                if(nums[i] + nums[j] == k){
                    count++;
                    nums[i] = -1;
                    nums[j] = -1;
                    break;
                }
            }
        }
        return count;
    }
}
```

#### Solution 2:

My Solution: Better Solution\
Time Complexity: O(n) \
Space Complexity: O(n)
Description: This solution uses a hashMap and linked list to store elements and values but this is an overkill.

```
class Solution {
struct Node {
    int val;
    struct Node* next;
};
struct Node* createNode(int num){
    struct Node* newNode = new Node();
    newNode -> val = num;
    newNode -> next = NULL;
    return newNode;
}
struct Node* deleteNodeHead(struct Node* nodePtr){
    struct Node* nextNodePtr = nodePtr -> next;
    nodePtr -> next = NULL;
    return nextNodePtr;
}
struct Node* insertNodeAtHead(int num, struct Node* node){
    struct Node* newNode = createNode(num);
    newNode -> next = node;
    return newNode;
}
public:
    int maxOperations(vector<int>& nums, int k) {
        int count = 0;
        unordered_map<int,struct Node*> hashMap;
        for(int i = 0; i < nums.size(); i++){
            int counterPart = k - nums[i];
            if(hashMap[counterPart] == NULL){
                if(hashMap[nums[i]] == NULL) hashMap[nums[i]] = createNode(i);
                else hashMap[nums[i]] = insertNodeAtHead(i,hashMap[nums[i]]);
            }else{
                count++;
                hashMap[counterPart] = deleteNodeHead(hashMap[counterPart]);
            }
        }
        return count;
    }
};
```

Community Solution: Better Solution\
Time Complexity: O(nlogn) \
Space Complexity: O(1)
Description: This solution uses a sorting and 2 pointer approach. \
More Description: Now, Interviewer won't be happy with your brute solution, so just do some acting & behave like ya, I can improve it more. Tell him, why dont if we Sort the array & have 2 pointers one start from very begining & another from the end of the array.
Now we gonna get the sum,
if sum == k :- Increment our count & move our I & J pointer
if sum > k, Move our J pointer
if sum < k, Move our I pointer

```
class Solution {
    public int maxOperations(int[] nums, int k) {
        Arrays.sort(nums);
        int count = 0;
        int i = 0;
        int j = nums.length - 1;
        while(i < j){
            int sum = nums[i] + nums[j];
            if(sum == k) {
                count++;
                i++;
                j--;
            }
            else if(sum > k) j--;
            else i++;
        }
        return count;
    }
}
```

#### Solution 3:

My Solution: Best Solution\
Time Complexity: O(n) \
Space Complexity: O(n)
Description: This solution uses a hashMap to store a number of times value is shown (frequency map) and then computes on it.

```
class Solution {
public:
    int maxOperations(vector<int>& nums, int k) {
        int count = 0;
        unordered_map<int,int> hashMap;
        for(int i = 0; i < nums.size(); i++){
            int counterPart = k - nums[i];
            if(hashMap[counterPart] == 0){
                hashMap[nums[i]]++;
            }else{
                count++;
                hashMap[counterPart]--;
            }
        }
        return count;
    }
};
```
