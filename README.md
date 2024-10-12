RM task 2 C++

Q1) 
// Write a C++ program to sort a character array alphabetically using bubble sort. (lower case only). Eg: input: “worksheet” Output:  “eehkorstw
#include <iostream>
#include <cstring>
using namespace std;

int main() {
    
    
    char str[100] ;
    cout << "Enter the string: " << endl;
    cin >> str;
    int n = strlen(str);
    int temp;
    
    for (int i = 0 ; i < n ; i++){
        for (int j = 0 ; j < n -1 -i ; j++){
            if (str[j] >str[j+1]){
                temp = str[j];
                str[j] = str[j+1];
                str[j+1] = temp;
                
            }
        }
    }
    
    cout << "Sorted string: " << str << endl;
    return 0;
}


Q2)
// Write a C++ program to multiply two matrices and print the  product. If the entered matrices are not compatible then print a 

#include <iostream>
using namespace std;

int main() {
    
    int r1 , c1 , r2 , c2;
    cout << "Enter the dimensions of 1st matrix: " << endl;
    cin >> r1 >> c1;
    int mat1[r1][c1];
    
    cout << "Enter the dimensions of 2nd matrix: " << endl;
    cin >> r2 >> c2;
    int mat2[r2][c2];
    
    int res[r1][c2];
    if ( r2 != c2){
        cout << "Matrices are not compatible" << endl;
        return 0;
    }
    
    cout << "Enter the elements of 1st matrix: " << endl;
    for (int i =0; i <r1 ; i++){
        for (int j = 0 ; j < c1 ; j++ ){
            cin >> mat1[i][j];
        }
    }
    
    cout << "Enter the elements of 2nd matrix: " << endl;
    for (int i =0; i <r2 ; i++){
        for (int j = 0 ; j < c2 ; j++ ){
            cin >> mat2[i][j];
        }
    }
    
    
    
    for (int i = 0 ; i <r1 ; i++){
        for (int j = 0 ; j < c2 ; j++){
            res[i][j] = 0;
            for(int k = 0 ; k < c1 ; k++){
                res[i][j] += mat1[i][k] * mat2[k][j];
            }
        }
    }
    
    cout << "Product of the matrices: " << endl;
    for (int i = 0; i < r1 ; i++){
        for(int j = 0 ; j <c2 ; j++){
            cout << res[i][j] << " ";
            
        }
        cout <<endl;
    }
    return 0;
}

Q3)
// In a given matrix for all zero elements the corresponding row and column must be replaced with zeroes. Write a C++ program to do that. Eg: Input: [ 1 2 0 Output: [ 0 0 0 2 3 4 2 3 0 3 3 3 ] 3 3 0 ]


#include <iostream>
using namespace std;

int main() {
    
     int rows , cols;
     cout << "Enter the number of rows: "; 
     cin >> rows; 
     cout <<  "Enter the number od coloumns: " ; 
     cin >> cols;
     
     int matrix[rows][cols];
     
     cout << "Enter the elements of the matrix: " << endl;
     for (int i = 0 ; i < rows ; i++){
         for(int j = 0 ; j < cols ; j++){
             cin >> matrix[i][j];
             
         }
     }
     
    bool rowFlag[rows] = {false};
    bool colFlag[cols] = {false};

    
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (matrix[i][j] == 0) {
                rowFlag[i] = true;
                colFlag[j] = true;
                
        }
    }
    }
    
    
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (rowFlag[i] || colFlag[j]) {
                matrix[i][j] = 0;
            }
        }
    }
    
    cout << "Modified matrix:" << endl;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}


Q4)
// Hill Number

#include <iostream>
using namespace std;

int main() {
    
    string num;
    cout << "Enter a number : " ;
    cin >> num;
    
    int n = num.length();
    if (n % 2 == 0){
        cout << "Not a hill number" <<endl;
        return 0;
    }
    
    int flag = 1;
    for(int i =0 ; i < n/2 ; i++){
        if(num[i] > num[i+1]){
            flag = 0;
        }
    }
    for(int i =n/2 ; i < n ; i++){
        if(num[i] < num[i+1]){
            flag = 0;
        }
    }
    
    if(flag){
        cout << "It is a hill number" << endl;
        
    }
    else{
        cout << " not a hill number" << endl;
    }
    

    return 0;
}

Q6)
#include <iostream>
using namespace std;

// Bubble Sort function
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
    }
}

// Selection Sort function
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        swap(arr[minIndex], arr[i]);
    }
}

// Binary Search function
int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) {
            return mid; // Found the target at index mid
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1; // Target not found
}

int main() {
    int n;
    cout << "Enter the number of elements in the array: ";
    cin >> n;
    int arr[n];
    
    cout << "Enter the elements of the array: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    // Ask user for sorting choice
    char choice;
    cout << "Choose sorting method: 'b' for Bubble Sort, 's' for Selection Sort: ";
    cin >> choice;

    // Sort the array based on user choice
    if (choice == 'b') {
        bubbleSort(arr, n);
        cout << "Array sorted using Bubble Sort." << endl;
    } else if (choice == 's') {
        selectionSort(arr, n);
        cout << "Array sorted using Selection Sort." << endl;
    } else {
        cout << "Invalid choice!" << endl;
        return 0;
    }
    
    // Output the sorted array
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    // Binary search
    int target;
    cout << "Enter the number to search for: ";
    cin >> target;

    int result = binarySearch(arr, n, target);
    if (result != -1) {
        cout << "Number found at index: " << result << endl;
    } else {
        cout << "Number not found in the array." << endl;
    }

    return 0;
}

Q7)
// string copy

#include <iostream>
using namespace std;

int main() {
    char og[100], cop[100];
    cout << "Enter the string: ";
    cin.getline(og, 100);

    char *pog = og;
    char *pcop = cop;

    while (*pog != '\0') {  
        *pcop = *pog    ;  
        pog ++;              
        pcop++;             
    }
    
    *pcop = '\0';

    cout << "The copied string is: " << cop << endl;
    return 0;
}

Q10)
// fibonacci

#include <iostream>
using namespace std;

int n = 40;

int fib(int n){
    if(n <=1){
        return n;
        }
    return fib(n-1) + (n-2);
}

int main(){
    
    cout << "The first 40 terms of fibinacci series are: " << endl;
    int res;
    for(int i = 1 ; i < 41 ; i++){
        res = fib(i);
        cout << res << "  " ;
        
    }
}

Q11)
#include <iostream>
using namespace std;

int binarySearch(int arr[], int left, int right, int target) {
    if (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target)
            return mid;

        if (arr[mid] > target)
            return binarySearch(arr, left, mid - 1, target);

        return binarySearch(arr, mid + 1, right, target);
    }
    // Target not found
    return -1;
}

Q12)
int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;  
    }
    return n * factorial(n - 1);  
}

Q13)
#include <iostream>
using namespace std;

int main(){
    
    cout << "Enter a number: ";
    int num ;
    cin >> num;
    
    int ld , sum=0;
    while(num != 0){
        ld = num%10;
        sum = sum +ld;
        num = num/10;
    }
    
    cout << "The sum of the digits are: " << sum <<endl;
    
}

Q14)
#include <iostream>
using namespace std;


int gcd(int a, int b) {
    if (b == 0) {
        return a;  
    }
    return gcd(b, a % b);  
}

int main() {
    int num1, num2;

    cout << "Enter two numbers: ";
    cin >> num1 >> num2;

    int result = gcd(num1, num2);
    cout << "The GCD of " << num1 << " and " << num2 << " is " << result << endl;

    return 0;
}





