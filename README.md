# L_02_Z3
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Введіть розмірність матриці n: ");
        int n = scanner.nextInt();
        int[][] matrix = new int[n][n];
        Random random = new Random();
        // Заповнюю матрицю випадковими значеннями в інтервалі [-n, n]
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                matrix[i][j] = random.nextInt(2 * n + 1) - n;
            }
        }

        // Виводжу матрицю на екран
        System.out.println("Матриця:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print(matrix[i][j] + "\t");
            }
            System.out.println();
        }

        int saddlePointCount = 0;

        // Знаходження сідлових точок
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int currentValue = matrix[i][j];
                boolean isSaddlePoint = true;

                // Перевірка, чи елемент є мінімальним в своєму рядку
                for (int k = 0; k < n; k++) {
                    if (matrix[i][k] < currentValue) {
                        isSaddlePoint = false;
                        break;
                    }
                }

                // Перевірка, чи елемент є максимальним в своєму стовпці
                for (int k = 0; k < n; k++) {
                    if (matrix[k][j] > currentValue) {
                        isSaddlePoint = false;
                        break;
                    }
                }

                if (isSaddlePoint) {
                    saddlePointCount++;
                    System.out.println("Сідлова точка знайдена: A[" + i + "][" + j + "] = " + currentValue);
                }
            }
        }

        System.out.println("Загальна кількість сідлових точок: " + saddlePointCount);
    }
}
