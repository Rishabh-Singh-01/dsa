## Can Place Flowers

Leetcode: [Can Place Flowers](https://leetcode.com/problems/can-place-flowers/)

### Code

Language: **C**

#### Solution 1:

My solution - More length and non cleaner \
Time Complexity: O(n) \
Space Complexity: O(1)

```
bool canPlaceFlowers(int* flowerbed, int flowerbedSize, int n) {

    if(flowerbedSize == 1) return ((flowerbed[0] + n) <= 1) ? true: false;
    if(flowerbedSize == 2)
        return ((flowerbed[0] + flowerbed[1] + n) <= 1) ? true : false;

    // for flowerbedSize >= 3
    int prev = 0;
    int cur = 1;
    int next = 2;
    if(flowerbed[prev] == 0 && flowerbed[cur] == 0){
        flowerbed[prev] = 1;
        n--;
    }

    while(next < flowerbedSize && n > 0){
        if(flowerbed[prev] == 0 && flowerbed[cur] == 0 && flowerbed[next] == 0){
            flowerbed[cur] = 1;
            n--;
        }
        next++;
        cur++;
        prev++;
    }
    if(n <= 0) return true;

    next--;
    cur--;
    prev--;
    if(flowerbed[cur] == 0 && flowerbed[next] == 0){
        flowerbed[next] = 1;
        n--;
    }

    if(n <= 0) return true;
    return false;
}
```

#### Solution 2:

Better Solution: Much cleaner \
Time Complexity: O(n) \
Space Complexity: O(1)

```
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        if (n==0) return true;
        int nn = 0;
        int i=0;
        while (i<flowerbed.length) {
            if (flowerbed[i]==1) i+=2;
            else if ((i==0 || flowerbed[i-1] ==0) && ( i==flowerbed.length-1||flowerbed[i+1] ==0)) {
                if (++nn==n) return true;
                i+=2;
            }
            else
                i++;
        }
        return false;
    }
```
