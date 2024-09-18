# CODESOFT

import java.util.ArrayList;
import java.util.Scanner;

class Student {
    private String name;
    private int rollNo;
    private String roomNo;

    public Student(String name, int rollNo, String roomNo) {
        this.name = name;
        this.rollNo = rollNo;
        this.roomNo = roomNo;
    }

    public String getName() {
        return name;
    }

    public int getRollNo() {
        return rollNo;
    }

    public String getRoomNo() {
        return roomNo;
    }

    @Override
    public String toString() {
        return "Student [Name=" + name + ", Roll No=" + rollNo + ", Room No=" + roomNo + "]";
    }
}

class HostelManagement {
    private ArrayList<Student> students;

    public HostelManagement() {
        students = new ArrayList<>();
    }

    public void addStudent(Student student) {
        students.add(student);
        System.out.println("Student added successfully.");
    }

    public void removeStudent(int rollNo) {
        Student studentToRemove = null;
        for (Student student : students) {
            if (student.getRollNo() == rollNo) {
                studentToRemove = student;
                break;
            }
        }
        if (studentToRemove != null) {
            students.remove(studentToRemove);
            System.out.println("Student removed successfully.");
        } else {
            System.out.println("Student with Roll No " + rollNo + " not found.");
        }
    }

    public void displayStudents() {
        if (students.isEmpty()) {
            System.out.println("No students in the hostel.");
        } else {
            for (Student student : students) {
                System.out.println(student);
            }
        }
    }
}

public class HostelManagementApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        HostelManagement hostelManagement = new HostelManagement();
        
        while (true) {
            System.out.println("\nHostel Management System");
            System.out.println("1. Add Student");
            System.out.println("2. Remove Student");
            System.out.println("3. Display Students");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter student name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter roll number: ");
                    int rollNo = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter room number: ");
                    String roomNo = scanner.nextLine();
                    Student student = new Student(name, rollNo, roomNo);
                    hostelManagement.addStudent(student);
                    break;
                
                case 2:
                    System.out.print("Enter roll number of student to remove: ");
                    int rollNoToRemove = scanner.nextInt();
                    hostelManagement.removeStudent(rollNoToRemove);
                    break;
                
                case 3:
                    hostelManagement.displayStudents();
                    break;
                
                case 4:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
        }
    }
}







