package sample;

import java.util.Scanner;

public class MatrixMultiplication {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter the number of rows and columns of 1st matrix: ");
        int rowsOfFirstMatrix = input.nextInt();
        int columnsOfFirstMatrix = input.nextInt();
        int[][] matrix1 = new int[rowsOfFirstMatrix][columnsOfFirstMatrix];

        System.out.println("Enter the elements of 1st matrix: ");
        for(int i = 0; i < rowsOfFirstMatrix; i++){
            for(int j = 0; j < columnsOfFirstMatrix; j++){
                matrix1[i][j] = input.nextInt();
            }
        }

        System.out.println("Enter the number of rows and columns of the 2nd matrix: ");
        int rowsOfSecondMatrix = input.nextInt();
        int columnsOfSecondMatrix = input.nextInt();

        while(columnsOfFirstMatrix != rowsOfSecondMatrix){
            System.out.println("Matrices cannot be multiplied! Dimension error!");
            System.out.println("Enter the number of rows and columns of 2nd matrix: ");
            rowsOfSecondMatrix = input.nextInt();
            columnsOfSecondMatrix = input.nextInt();
        }

        int[][] matrix2 = new int[rowsOfSecondMatrix][columnsOfSecondMatrix];

        System.out.println("Enter the elements of 2nd matrix: ");
        for(int i = 0; i < rowsOfSecondMatrix; i++){
            for(int j = 0; j < columnsOfSecondMatrix; j++){
                matrix2[i][j] = input.nextInt();
            }
        }

        int[][] product = product(matrix1, matrix2);
        System.out.println("Product of matrices: ");
        for(int i = 0; i < rowsOfFirstMatrix; i++){
            for(int j = 0; j < columnsOfSecondMatrix; j++){
                System.out.printf("%d ", product[i][j]);
            }
            System.out.printf("%n");
        }
        input.close();
    }

    public static int[][] product(int[][] matrix1, int[][] matrix2){
        int columnsOfFirstMatrix = matrix1[0].length;
        int rowsOfSecondMatrix = matrix2.length;

        int rowsOfFirstMatrix = matrix1.length;
        int columnsOfSecondMatrix = matrix2[0].length;
        int[][] product = new int[rowsOfFirstMatrix][columnsOfSecondMatrix];
        for(int i = 0; i < rowsOfFirstMatrix; i++){
            for (int j = 0; j < columnsOfSecondMatrix; j++){
                int sum = 0;
                for(int k = 0; k < rowsOfSecondMatrix; k++){
                    sum = sum + matrix1[i][k] * matrix2[k][j];
                }
                product[i][j] = sum;
            }
        }
        return product;
    }
}
