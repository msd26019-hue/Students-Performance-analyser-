# Students-Performance-analyser-
A Python-based student performance analysis system

students = []

n = int(input("Enter number of students: "))

# Taking student details
for i in range(n):
    name = input("Enter student name: ")

    marks = []

    for j in range(3):
        m = float(input("Enter marks: "))
        marks.append(m)

    average = sum(marks) / 3

    # Calculating grade
    if average >= 80:
        grade = "A"
    elif average >= 60:
        grade = "B"
    elif average >= 40:
        grade = "C"
    else:
        grade = "Fail"

    students.append([name, average, grade])


# Displaying student report
print("\n--- Student Performance Report ---")

for student in students:
    print("Name:", student[0])
    print("Average:", student[1])
    print("Grade:", student[2])
    print()


# Calculating class average
class_average = sum(s[1] for s in students) / n

print("Class Average:", class_average)


# Finding topper
topper = max(students, key=lambda s: s[1])
print("Topper:", topper[0])


# Finding lowest-performing student
lowest = min(students, key=lambda s: s[1])

print("Lowest Performing Student:", lowest[0])
print("Average Marks:", lowest[1])


# Counting pass and fail students
pass_count = 0
fail_count = 0

for student in students:
    if student[1] >= 40:
        pass_count += 1
    else:
        fail_count += 1

print("Pass:", pass_count)
print("Fail:", fail_count)


# Counting Grade A students
a_count = 0

for student in students:
    if student[2] == "A":
        a_count += 1

print("Students with Grade A:", a_count)


# Calculating pass percentage
pass_percentage = (pass_count / n) * 100

print("Pass Percentage:", pass_percentage, "%")

search_name = input("Enter student name to search: ")

found = False

for student in students:
    if student[0].lower() == search_name.lower():
        print("Student Found!")
        print("Name:", student[0])
        print("Average:", student[1])
        print("Grade:", student[2])
        found = True
        break

if not found:
    print("Student not found!")

students.sort(key=lambda s: s[1], reverse=True)

print("\n--- Students Ranked by Performance ---")

for student in students:
    print(student[0], "-", student[1], "-", student[2])

with open("student_report.txt", "w") as file:
    file.write("STUDENT PERFORMANCE REPORT\n\n")

    for student in students:
        file.write(
            f"Name: {student[0]}, "
            f"Average: {student[1]}, "
            f"Grade: {student[2]}\n"
        )

print("Report saved successfully!")


