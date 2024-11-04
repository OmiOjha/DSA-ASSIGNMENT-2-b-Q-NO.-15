To implement a book availability checker in a library, we can create a sorted list of book IDs and then use a search algorithm to check for the availability of a specific book ID. For efficient searching in an ordered list, a binary search is ideal since it has a time complexity of 
𝑂
(
log
⁡
𝑛
)
O(logn), which is faster than a linear search for large lists.

Steps
1.Define an Array for Book IDs: We'll use an array of integers to hold the ordered list of book IDs.
2.Binary Search Function: Implement a binary search function to check if a specific book ID is in the list.
3.Main Function: In the main function, the program will prompt the user to enter a book ID and search for it in the ordered list.

C Program Implementation:

#include <stdio.h>

#define MAX_BOOKS 100

// Binary Search Function to search for a book ID in a sorted list

int binarySearch(int arr[], int size, int target) {
    
    int left = 0;
    int right = size - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        // Check if target is at mid
        if (arr[mid] == target) {
            return 1;  // Book ID found
        }
        // If target is greater, ignore the left half
        else if (arr[mid] < target) {
            left = mid + 1;
        }
        // If target is smaller, ignore the right half
        else {
            right = mid - 1;
        }
    }
    return 0;  // Book ID not found
}

int main() {
    
    int books[MAX_BOOKS] = {1001, 1003, 1005, 1010, 1012, 1015, 1020, 1025, 1030};  // Sorted list of book IDs
    int size = 9;  // Number of books currently in the list
    int bookID;

    printf("Enter the Book ID to search for: ");
    scanf("%d", &bookID);

    // Search for the book ID using binary search
    if (binarySearch(books, size, bookID)) {
        printf("Book with ID %d is available in the library.\n", bookID);
    } else {
        printf("Book with ID %d is not available in the library.\n", bookID);
    }

    return 0;
}

Explanation:

1.Binary Search Function (binarySearch):

a.The function takes an ordered array arr, its size, and the target book ID to search for.
b.It uses a binary search approach by comparing the target to the middle element of the array. If the target matches, it returns 1 (indicating the book is found).
c.If the target is greater than the middle element, it searches the right half; if smaller, it searches the left half.
d.If the book ID is not found after all comparisons, it returns 0.

2.Main Function:

a.A sorted list of book IDs (books) is initialized.
b.The program prompts the user to input the book ID they want to search for.
c.It calls binarySearch with the books array, the number of books (size), and the book ID entered by the user.
d.Based on the result, it displays whether the book is available or not.
