# Assignment1
// Problem A
abstract class Role {
  void displayRole();
}

// Problem B 
class Person implements Role {
  String name;
  int age;
  String address;
  Role role;

  Person(this.name, this.age, this.address, this.role);

  String getName() {
  return name;
}

int getAge() {
  return age;
}

String getAddress() {
  return address;
}

  @override
  void displayRole() {
    role.displayRole();
  }
}

class _StudentRole implements Role {
  @override
  void displayRole() {
    print("Role: Student");
  }
}

// Problem C
class Student extends Person implements Role {
  String studentID;
  String grade;
  List<double> courseScores;

  Student(
    String name,
    int age,
    String address,
    this.studentID,
    this.grade,
    this.courseScores,
  ) : super(name, age, address, _StudentRole());

  double calculateAverageScore() {
  double total = 0;
  for (int i = 0; i < courseScores.length; i++) {
    total += courseScores[i];
  }
  double average = total / courseScores.length;
  return average;
}


  @override
  void displayRole() {
    print("Role: Student");
  }

  void displayStudentInfo() {
    print("Student Information:\n");
    displayRole();
    print("Name: $name");
    print("Age: $age");
    print("Address: $address");
    print("Average Score: ${calculateAverageScore().toStringAsFixed(1)}");
  }
}

class _TeacherRole implements Role {
  @override
  void displayRole() {
    print("Role: Teacher");
  }
}

// Problem D
class Teacher extends Person implements Role {
  String teacherID;
  List<String> coursesTaught;

  Teacher(String name,int age,String address,this.teacherID,this.coursesTaught,): 
  super(name, age, address, _TeacherRole());

  @override
  void displayRole() {
    print("Role: Teacher");
  }

  void displayTeacherInfo() {
    print("Teacher Information:\n");
    displayRole();
    print("Name: $name");
    print("Age: $age");
    print("Address: $address");
    print("Courses Taught:");
    for (var course in coursesTaught) {
      print("- $course");
    }
  }
}

// Problem E
void main() {
  Student student = Student("John Doe",20,"123 Main St","S123","A",[90, 85, 92]);
  student.displayStudentInfo();

  print("\n");

  Teacher teacher = Teacher(
    "Mrs. Smith",
    35,
    "456 Oak St",
    "T456",
    ["Math", "English", "Bangli"],
  );
  teacher.displayTeacherInfo();
}
