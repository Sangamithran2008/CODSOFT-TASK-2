import java.util.Scanner;

public class StudentGradeCalculator {

    public static void main(String[] args) {
        // Create a Scanner object for user input
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("--- 🎓 Student Grade Calculator ---");

        // 1. Input: Get the number of subjects
        System.out.print("Enter the number of subjects: ");
        int numSubjects = 0;
        try {
            numSubjects = scanner.nextInt();
        } catch (java.util.InputMismatchException e) {
            System.err.println("Invalid input. Please enter a whole number.");
            scanner.close();
            return; // Exit the program on invalid input
        }

        if (numSubjects <= 0) {
            System.out.println("Number of subjects must be greater than zero.");
            scanner.close();
            return;
        }

        int totalMarks = 0;
        // Loop to get marks for each subject
        for (int i = 1; i <= numSubjects; i++) {
            System.out.printf("Enter marks obtained in Subject %d (out of 100): ", i);
            int marks = scanner.nextInt();

            // Input validation: Ensure marks are within the valid range (0-100)
            if (marks < 0 || marks > 100) {
                System.out.println("Invalid marks. Marks must be between 0 and 100. Please restart.");
                scanner.close();
                return; // Exit the program if marks are invalid
            }

            // 2. Calculate Total Marks
            totalMarks += marks;
        }

        // Close the scanner
        scanner.close();

        // 3. Calculate Average Percentage
        // We use casting to float to ensure floating-point division
        float averagePercentage = (float) totalMarks / numSubjects;

        // 4. Grade Calculation
        String grade;
        if (averagePercentage >= 90) {
            grade = "A+ (Outstanding)";
        } else if (averagePercentage >= 80) {
            grade = "A (Excellent)";
        } else if (averagePercentage >= 70) {
            grade = "B (Good)";
        } else if (averagePercentage >= 60) {
            grade = "C (Satisfactory)";
        } else if (averagePercentage >= 50) {
            grade = "D (Pass)";
        } else {
            grade = "F (Fail)";
        }

        // 5. Display Results
        System.out.println("\n--- Results Summary ---");
        System.out.println("Total Subjects: " + numSubjects);
        System.out.println("Total Marks: " + totalMarks);
        System.out.printf("Average Percentage: %.2f%%\n", averagePercentage);
        System.out.println("Grade Assigned: " + grade);
        System.out.println("-----------------------");
    }
}
