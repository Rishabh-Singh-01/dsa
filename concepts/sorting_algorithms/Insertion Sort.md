## Insertion sort

geeksforgeeks: [Insertion sort](https://www.geeksforgeeks.org/insertion-sort/)

### summary

Insertion sort is a simple sorting algorithm that works similar to the way you sort playing cards in your hands. The array is virtually split into a sorted and an unsorted part. Values from the unsorted part are picked and placed at the correct position in the sorted part.

##### selection sort algorithm follows like this:

To sort an array of size N in ascending order iterate over the array and compare the current element (key) to its predecessor, if the key element is smaller than its predecessor, compare it to the elements before. Move the greater elements one position up to make space for the swapped element.

- Basically, its like taking the first card/el in your right hand/sorted portion(half) of the array.
- Then take the next card/el, compare it from the whole hand meaning assuming cards/el are in ascending order compare the card/el from left hand side and travel through the element till it reached its right place
- Right place meaning basically if you see previous element as bigger than your current element then just swap if its smaller than current then just break the loop and pick the next card/el and repeat step 2.

##### complexity

The worst-case time complexity of the Insertion sort is O(N^2) \
The average case time complexity of the Insertion sort is O(N^2) \
The time complexity of the best case is O(N). \
The auxiliary space complexity of Insertion Sort is O(1)

### details

language: **c**

### code snippets

#### solution 1:

my/community solution\
time complexity: o(n^2) \
space complexity: o(1)

```
void swapAdjPlaces(int* arr, int i){
    int temp = arr[i];
    arr[i] = arr[i - 1];
    arr[i - 1] = temp;
}

void insert(int* arr, int i)
{
    while(i > 0){
        if(arr[i] > arr[i - 1]) break;
        swapAdjPlaces(arr, i);
        i--;
    }
}
//Function to sort the array using insertion sort algorithm.
void insertionSort(int arr[], int n)
{
    //code here
    int* arrPtr = &arr[0];
    for(int i = 1; i < n; i++){
        insert(arrPtr, i);
    }
}
```
