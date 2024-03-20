#include <iostream>
#include <fstream>
using namespace std;
void displayMatrix(int **matrix, int rows, int cols) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << matrix[i][j] << "\t";
        }
        cout << endl;
    }
}

int** createMatrix(int rows, int cols) {
    int** matrix = new int*[rows];
    for (int i = 0; i < rows; i++) {
        matrix[i] = new int[cols];
    }
    return matrix;
}

void deleteMatrix(int** matrix, int rows) {
    for (int i = 0; i < rows; i++) {
        delete[] matrix[i];
    }
    delete[] matrix;
}
int** readMatrixFromFile(string filename, int& rows, int& cols) {
    ifstream file(filename);
    if (!file) {
        cerr << "Error opening file: " << filename << endl;
        exit(1);
    }

    file >> rows >> cols;

    int** matrix = createMatrix(rows, cols);

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            file >> matrix[i][j];
        }
    }

    file.close();
    return matrix;
}

// Function to perform matrix sum
int matrixSum(int** matrix, int rows, int cols) {
    int sum = 0;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            sum += matrix[i][j];
        }
    }
    return sum;
}

// Add other matrix operations functions similarly

// Function to display menu and handle user input
int menu() {
    int choice;
    cout << "\nMatrix Operations Menu:" << endl;
    cout << "1. Sum of Matrix\n2. Product of Matrix\n3. Row-wise Average\n"
         << "4. Column-wise Average\n5. Average of whole Matrix\n"
         << "6. Row-wise Sorting of Matrix\n7. Column-wise Sorting of Matrix\n"
         << "8. Scalar Matrix Addition\n9. Addition of two Matrices\n"
         << "10. Scalar Matrix Subtraction\n11. Subtraction of two Matrices\n"
         << "12. Scalar Matrix Multiplication\n13. Multiplication of two Matrices\n"
         << "14. Scalar Matrix Division\n15. Matrix Transpose\n16. Matrix Determinant\n"
         << "17. Matrix Inverse\n0. Exit\n";
    cout << "Enter your choice: ";
    cin >> choice;
    return choice;
}

int main() {
    int choice;
    int rows, cols;

    do {
        choice = menu();

        switch (choice) {
            case 1: {
                // Sum of Matrix
                // Get matrix from user or file
                // Call matrixSum function
                // Display result
                break;
            }
            // Add cases for other matrix operations

            case 0:
                cout << "Exiting program. Goodbye!" << endl;
                break;

            default:
                cout << "Invalid choice. Please try again." << endl;
        }

    } while (choice != 0);

    return 0;
}
