# FelobaterWael
package com.mycompany.student_grade_tracker;


public class Student {
    private String name;
    private double grade;

    public Student(String name, double grade) {
        this.name = name;
        this.grade = grade;
    }

    public String getName() {
        return name;
    }

    public double getGrade() {
        return grade;
    }
    
    public String getStatus(){
        if(grade>=85)
            return "Excellent";
        else if(grade>=70)
            return "Good";
        else if(grade>=50)
            return "Pass";
        else
            return "Fail";
    }

    
package com.mycompany.student_grade_tracker;
import java.util.ArrayList;

import java.util.Scanner;
//import java.io.Serializable;

public class Student_Grade_Tracker {


    public static void main(String[] args) {
       
        Scanner sc=new Scanner(System.in);
        
         while (true) {

            System.out.println("========== STUDENT GRADE TRACKER ==========");
            System.out.println("1. Add Student");
            System.out.println("2. Display Students");
            System.out.println("3. Show Statistics");
            System.out.println("4. Search Student");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            int choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {

                case 1:
                    addStudent(sc);
                    break;

                case 2:
                    displayStudents();
                    break;

                case 3:
                    calculateStatistics();
                    break;

                case 4:
                    searchStudent(sc);
                    break;

                case 5:
                    System.out.println("Exiting program...");
                    sc.close();
                    return;

                default:
                    System.out.println("Invalid choice. Try again.");
            }
    }
 }

      
         
static ArrayList<Student> students = new ArrayList<>();

    public static void addStudent(Scanner sc) {
        System.out.print("Enter student name: ");
        String name = sc.nextLine();

        System.out.print("Enter student grade: ");
        double grade = sc.nextDouble();
        sc.nextLine();

        students.add(new Student(name, grade));

        System.out.println("Student added successfully.");
    }
    
    public static void displayStudents() {

        if (students.isEmpty()) {
            System.out.println("No student data available.");
            return;
        }

        System.out.println("========== STUDENT REPORT ==========");

        for (Student s : students) {
            System.out.println(
                    "Name: " + s.getName() +
                    " | Grade: " + s.getGrade() +
                    " | Status: " + s.getStatus());
        }

        System.out.println("====================================");
    }
    
    public static void calculateStatistics() {

        if (students.isEmpty()) {
            System.out.println("No student data available.");
            return;
        }

        double total = 0;
        double highest = students.get(0).getGrade();
        double lowest = students.get(0).getGrade();

        String highestStudent = students.get(0).getName();
        String lowestStudent = students.get(0).getName();

        for (Student s : students) {

            total += s.getGrade();

            if (s.getGrade() > highest) {
                highest = s.getGrade();
                highestStudent = s.getName();
            }

            if (s.getGrade() < lowest) {
                lowest = s.getGrade();
                lowestStudent = s.getName();
            }
        }

        double average = total / students.size();

        System.out.println("========== STATISTICS ==========");
        System.out.println("Average Grade : " + average);
        System.out.println("Highest Grade : " + highest + " (" + highestStudent + ")");
        System.out.println("Lowest Grade  : " + lowest + " (" + lowestStudent + ")");
        System.out.println("================================");
    }

    public static void searchStudent(Scanner sc) {

        if (students.isEmpty()) {
            System.out.println("No student data available.");
            return;
        }

        System.out.print("Enter student name to search: ");
        String searchName = sc.nextLine();

        boolean found = false;

        for (Student s : students) {
            if (s.getName().equalsIgnoreCase(searchName)) {

                System.out.println("Student Found:");
                System.out.println("Name   : " + s.getName());
                System.out.println("Grade  : " + s.getGrade());
                System.out.println("Status : " + s.getStatus() + "");

                found = true;
                break;
            }
        }
        
        if (!found) {
            System.out.println("Student not found.");
        }
    }
}

    
}
