## Linear search & Binary search



## # Linear search

- Unordered data 
- Check all data from the beginning

```Java
int a[] ={3,4,6,8,5,3,2};
int data = 3;

psvm
for(int i =0; i<a.length; i++){
    if(data == a[i]){
        return "index : " + i
    }
}
```



## # Binary search

- Ordered data 
- Check from the middle and the middle of the data

```Java
int main(void) {
    int arr[20] = { 1,2,4,6,7,8,9,13,14,16,19,21,23,26,31,41,45,49,51,52 };
    int searchNum = 23;

    printf("arr배열에서 23's index is %d이다.\n", binarySearch(arr, searchNum, 0, 19));
    return 0;
}

int compare(int x, int y) {
    if (x > y) {
        return -1;
    }
    else if (x == y) {
        return 0;
    }
    else if (x < y) {
        return 1;
    }
}
 
int binarySearch(int arr[], int searchNum, int left, int right) {
    int middle;
    while (left <= right) {
        middle = (left + right) / 2;
        switch (compare(arr[middle], searchNum)) {
        case 1: //right
            left = middle + 1;
            break;
        case 0:
            return middle;
        case -1: // left
            right = middle-1;
            break;
        }
    }
    return -1;
 

}

```

