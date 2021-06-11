#include <stdio.h>
#include <stdlib.h>


int PARENT(int x){
    return x/2;
}
int LEFT(int x){
    return x*2;
}
int RIGHT(int x){
    return x*2+1;
}
/*
int lenght(int array[]){
    printf("size of array: %d, size of int: %d\n", sizeof(array), sizeof(int));
    return sizeof(array)/sizeof(int);
}
*/
void maxHeapify(int array[], int i, int heapSize){

    int l = LEFT(i+1)-1;
    int r = RIGHT(i+1)-1;
    int largest = 0;

    if (l <= heapSize-1 && array[l] > array[i]){
        largest = l;
    }else{
        largest = i;
    }

    if(r <= heapSize-1 && array[r] > array[largest]){
        largest = r;
    }

    if(largest != i){
        int temp = array[i];
        array[i] = array[largest];
        array[largest] = temp;
        maxHeapify(array, largest, heapSize);
    }
}

void buildMaxHeap(int array[],int length){

    int heapSize = length;// 0 <= heapSize <= length

    for(int i = (length/2)-1; i >= 0; i--){
        maxHeapify(array, i, heapSize);
    }
}

void heapSort(int array[], int length){
    //printf("length: %d\n", length);
    buildMaxHeap(array, length);
    int heapSize = length;
    int lll = length;

    for(int c = 0; c < lll; c++){
        printf("%d__", array[c]);
    }
    printf("\n");
    for(int i = length-1; i >= 1; i--){

        int temp = array[i];
        //printf("\n\narray[i]=%d\tarray[0]=%d\ttemp=%d\n", array[i], array[0], temp);
        //printf("  SWAP:\n");
        array[i] = array[0];
        array[0] = temp;

        heapSize--;
        //printf("  HEAPIFY: heap size is %d\n", heapSize);
        maxHeapify(array, 0, heapSize);
        /*
        printf("(array, 0, %d) :%d: ", heapSize, i);
        for(int c = 0; c < lll; c++){
            if(c == heapSize){
                printf(" | ");
            }
            printf("%d__", array[c]);

        }
        printf("\n\n");
        */
    }
}

int main()
{
    ///---------------GETTING INPUT AND PUTTING IT INTO ARRAY-----------------
    FILE *input;
    char fileName[50];
    int data = 0;
    int dataArrayLength = 0;

    printf("Enter the data file (abc.txt): ");
    scanf("%s", fileName);
    input = fopen(fileName,"r");
    int r = 0;

    for(fscanf(input,"%d", &data);!feof(input);fscanf(input,"%d", &data)){
        dataArrayLength++;
    }
    dataArrayLength++;

    fseek(input, 0, SEEK_SET);//Move the cursor (,,x) beginning of the file and move (,x,)0 byte from the file (x,,) input.
    int dataArray[dataArrayLength];
    int length = dataArrayLength;

    for(fscanf(input,"%d", &data);!feof(input);fscanf(input,"%d", &data)){
        dataArray[dataArrayLength-length] = data;
        length--;
    }
    fscanf(input,"%d", &data);
    dataArray[dataArrayLength-length] = data;

    //printf("sizeofArray is %d\n ", sizeof(dataArray));
    printf("\n_________________________________________________\n");
    printf("OLD\n");
    for(int i = 0; i< dataArrayLength; i++){
        printf("%d__", dataArray[i]);
    }
    printf("\nNEW\n");
    ///--------------------------------------------------------------------
    //buildMaxHeap(dataArray, dataArrayLength);
    heapSort(dataArray, dataArrayLength);
    for(int i = 0; i< dataArrayLength; i++){
        printf("%d__", dataArray[i]);
    }
    printf("\n_________________________________________________\n");

    return 0;
}
