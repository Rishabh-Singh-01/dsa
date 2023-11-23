## Maximum Number of Vowels in a Substring of Given Length

Leetcode: [Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)

### Details

Language: **C** \
Leetcode Level: Medium

#### Solution 1:

My Solution: Brute Force\
Time Complexity: O(n\*k) \
Space Complexity: O()

```
int maxVowels(char* s, int k) {
    char* cur = s;
    char* temp;
    int localCount = 0;
    int totalCount = 0;
    while(*cur != '\0'){
        temp = cur;
        localCount = 0;
        for(int i = 0; i < k; i++){
            char tempChar = *temp;
            if(tempChar == '\0') break;
            if( tempChar == 'a' ||
                tempChar == 'e' ||
                tempChar == 'i' ||
                tempChar == 'o' ||
                tempChar == 'u'
            ) localCount++;
            temp++;
        }
        if(localCount > totalCount) totalCount = localCount;
        cur++;
    }
    return totalCount;
}
```

#### Solution 2:

My/Community Solution: Best Solution\
Time Complexity: O(n) \
Space Complexity: O(1)

```
bool isVowel(char tempChar){
    if( tempChar == 'a' ||
        tempChar == 'e' ||
        tempChar == 'i' ||
        tempChar == 'o' ||
        tempChar == 'u'
    ) return true;
    return false;
}

int maxVowels(char* s, int k) {
    char* first = s;
    char* second = s;
    int helper = k;
    int count = 0;
    int totalCount = 0;
    while(helper > 0){
        if(isVowel(*second)) count++;
        helper--;
        second++;
    }
    if(count > totalCount) totalCount = count;
    second--;
    while(*second != '\0'){
        second++;
        if(*second == '\0') continue;
        if(isVowel(*second)) count++;
        if(isVowel(*first)) count--;
        first++;

        if(count > totalCount) totalCount = count;
    }

    return totalCount;
}
```
