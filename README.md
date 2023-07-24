#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#pragma warning(disable:4996)

#define NUMSEMESTER 3 
#define MAX_STUDENTS 100 


void teacherMenu();
void studentMenu();
void addStudent();
void updateStudent();
void deleteStudent();
void displayStudent();
void calculateCGPA();
void saveToFile();
void loadFromFile();

typedef struct {
    int studentId;
    char studentName[50];
    float gpa[NUMSEMESTER];
    float cgpa;
    int numStudents;

} Student;
int numStudents = 0;

Student students[MAX_STUDENTS];

int main() {
    int choice;
    printf("\n===== Student Grade Management System =====\n");
    printf("1. Teacher's Entrance \n");
    printf("2. Student's Entrance \n");
    printf("3. Exit the program \n");
    printf("Please select option: ");
    scanf("%d", &choice);

    if (choice == 1) {
        teacherMenu();
    }
    else if (choice == 2) {
        printf("yes2");
    }
    else if (choice == 3) {
        printf("yes 3");
        return 0;
    }
    else {
        printf("no");
    }
    return 0;
}

void teacherMenu() {
    int choice = 0;
    while (1) {
        printf("\n===== Teacher's entrance =====\n");
        printf("1. Add New Student \n");
        printf("2. To update student grades \n");
        printf("3. Delete Student Record \n");
        printf("4. View student information \n");
        printf("5. Return to the previous menu \n");
        printf("Please select option: ");
        scanf("%d", &choice);
        if (choice == 1) {
            addStudent();
        }
        else if (choice == 2) {
            updateStudent();
        }
        else if (choice == 3) {
            deleteStudent();
        }
        else if (choice == 4) {
            displayStudent();
        }
        else if (choice == 5) {
            printf("no");
        }
        else printf("no");
    }
}

void addStudent() {
    int studentId;
    printf("please enter student ID: ");
    if (scanf("%d", &studentId) != 1) {
        while ((getchar()) != '\n');
        printf("Invalid student ID, please re-enter");
        return;
    }

    char studentName[50] ;
    studentName[49] = '\0';
    printf("Enter Student Name: ");
    scanf("%s", studentName);

    for (int semester = 0; semester < NUMSEMESTER; semester++) {
        int numberOfSubject;
        float totalGradePoints=0;
        int totalCredits=0;
       
       
        printf("please enter number of subject in %d semester: ", semester + 1);
        if (scanf("%d", &numberOfSubject) != 1) {
            printf("Invalid number of subject, please re-enter");
            while ((getchar()) != '\n');
            return;
        }

        for (int i = 0; i < numberOfSubject; i++) {
            char grade = 0;
            float score = 0;
            printf("please enter the grade of the %d subject in the %d semester: ", i + 1, semester + 1);
            (void) scanf(" %c", &grade);
            if (grade == 'A') {
                score = 4.0;
            }
            else if (grade == 'A-') {
                score = 3.75;
            }
            else if (grade == 'B+') {
                score = 3.5;
            }
            else if (grade == 'B') {
                score = 3.0;
            }
            else if (grade == 'B-') {
                score = 2.75;
            }
            else if (grade == 'C+') {
                score = 2.50;
            }
            else if (grade == 'C') {
                score = 2.0;
            }
            else if (grade == 'F') {
                score = 0;
            }
            else {
                printf("Invalid Grade: %c \n", grade);
                while (getchar() != '\n');
                return;
            }
            int credits = 0;
            printf("Please enter the credits hours for the %d subject in the %d semester: ", i + 1, semester + 1);

            if (scanf("%d", &credits) != 1) {
                printf("Invalid credit! \n");
                while (getchar() != '\n'); 
                return;
            }
           
            
            totalGradePoints += score * credits;
            totalCredits += credits;

            }
        
        students[numStudents].gpa[semester] = totalGradePoints / totalCredits;
        students[numStudents].studentId = studentId;
        strcpy(students[numStudents].studentName , studentName);
        float cgpa = (students[numStudents].gpa[0] + students[numStudents].gpa[1] + students[numStudents].gpa[2]) / 3;
        students[numStudents].cgpa = cgpa;
        cgpa = 0;
        
        
        
        
        }
    numStudents++;
    
    printf("Add Student Complete");
        
    }


void updateStudent() {
    printf("Enter the student ID :");
}

void deleteStudent() {
    printf("Enter the student ID :");
}

void calculateCGPA() {
    printf("Enter the student ID :");
};

void displayStudent() {
    for (int i = 0; numStudents > i; ) {
        printf("Student Name : %s\n", students[i].studentName);
       printf("Student Id : %d\n", students[i].studentId);
        printf("Student first semester gpa : %.2f\n", students[i].gpa[0]);
        printf("Student gpa : %.2f\n", students[i].gpa[1]);
        printf("Student gpa : %.2f\n", students[i].gpa[2]);
        printf("Student cgpa : %.2f\n", students[i].cgpa);

        i++;
        printf("\n\n");
    }
}

void studentMenu() {
    printf("Enter your student ID:");
}

void saveToFile() {
    printf("Enter your student ID:");
}

void loadFromFile() {
    printf("Enter your student ID:");
};
