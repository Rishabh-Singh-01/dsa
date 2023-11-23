## String Compression

Leetcode: [String Compression](https://leetcode.com/problems/string-compression/)

### Details

Language: **C++** \
Leetcode Level: Medium

#### Solution 1:

Description - Optimized Solution (also had to change chars array to reflect the compressed string)\
Time Complexity: O(n) \
Space Complexity: O(1)

```
class Solution {
public:
    // helper method
    void mutateArr(vector<char>& chars,int &changeInd, char &curEl, int &curElCount, int &totalSize){
        // change the index and their value
        chars[changeInd] = curEl;
        changeInd++;
        totalSize += 1;

        // change the values to the len fo curElCount
        if(curElCount > 1){
            string numStr = to_string(curElCount);
            int numStrLen = numStr.size();
            for(int i = 0; i < numStrLen; i++){
                chars[changeInd] = numStr[i];
                changeInd++;
            }

            totalSize += numStrLen;
        }
    }

    // main method
    int compress(vector<char>& chars) {
        int changeInd = 0;
        int curInd = 1;

        char curEl = chars[0];
        int curElCount = 1;
        int totalSize = 0;
        while(curInd < chars.size()){
            if(curEl == chars[curInd]) curElCount++;
            else{
                mutateArr(chars,changeInd, curEl, curElCount, totalSize);

                // resetting the value due to new element
                curEl = chars[curInd];
                curElCount = 1;
            }
            curInd++;
        }
        mutateArr(chars,changeInd, curEl, curElCount, totalSize);

        return totalSize;
    }
};
```
