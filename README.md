# Quick-sort-with-Binary-Search
Creation of a filled int array. Quick sort the array. Given a random number. Find the random number through Binary Search.


import java.util.*;

public class AceTester {

	
	public static int[] numbers;
	public static int number;
	
	public static void main (String [] args){
		int[] array1 = new int[100];
		for(int i=0; i<99; i++){
			if((i%2)==1)
				array1[i] = i*i;
			else
				array1[i] = i;
		}
		
		//Printing Unsorted and Sorted Array
		System.out.println("The array Unsorted: ");
		for(int i = 0; i<array1.length-1; i++)
			System.out.print(array1[i]+ " ");
		System.out.println("\n\nThe array Sorted: ");
		sort(array1);
		for(int i = 0; i<array1.length-1; i++)
			System.out.print(array1[i]+ " ");
		
		// Printing Random number and Binary Search Random Number Position
		Random rand = new Random();
		int randPosition = rand.nextInt(array1.length-1);
		int randNum = array1[randPosition];
		System.out.println("\n\nThe random number position: " + randPosition);
		System.out.println("The random number: " + randNum);
		int bs= binarySearch(array1,randNum);
		System.out.println("\nBS Position: " + bs);
	}
	
    //-------------------------------------------------------------------------
	//Binary Search Method
	public static int binarySearch(int[] array, int seraching){
		int target = seraching;
		
		int low = 0;
		int high = (array.length-1);
		
		while(high > low){
			int middle = (low + (high-low)/2);
			int m = array[middle];
			
			if(m == target)
				return middle;
			else if(m > target)
				high = middle-1;
			else if(m < target)
				low = middle+1;	
		}
		return -1;
	}
	

    //-------------------------------------------------------------------------
	//QuickSort Method
     public static void sort(int[] values) {
             // check for empty or null array
             if (values ==null || values.length==0){
                     return;
             }
             numbers = values;
             number = values.length;
             quicksort(0, number - 1);
     }
     
     public static void quicksort(int low, int high) {
             int i = low, j = high;
             // Pivot = middle element
             int pivot = numbers[low + (high-low)/2];

             /* Divide and Conquer: Split into two lists
              * In each iteration, 
              * a number is identified from left side which is greater than the pivot value 
              * and a number from right side which is greater than the pivot value
              * When both are found, we swap the numbers
              */
             while (i <= j) {
                     /* If value from left list is smaller than pivot element
                      * move on to the next element in the left list
                     */ 
                     while (numbers[i] < pivot) 
                             i++;
                     
                     /* If value from right list is larger than pivot element
                      * move on to the next element in the right list
                     */ 
                     while (numbers[j] > pivot) 
                             j--;

                     /*  Values in left list larger than pivot element and values in
                      * right list larger than pivot element must be swapped.
                      * Then you increase i and j
                      */
                     if (i <= j) {
                             swap(i, j);
                             i++;
                             j--;
                     }
             }
             // Recursion
             if (low < j)
                     quicksort(low, j);
             if (i < high)
                     quicksort(i, high);
     }
     
     //Swapping Method
     public static void swap(int i, int j) {
             int temp = numbers[i];
             numbers[i] = numbers[j];
             numbers[j] = temp;
     }
     //-------------------------------------------------------------------------
     
     
}
