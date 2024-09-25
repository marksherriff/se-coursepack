---
title: Decomposition
---

# Design Decomposition

<iframe width="800" height="450" src="https://www.youtube.com/embed/cv-aOsqaTeA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="800" height="450" src="https://www.youtube.com/embed/CEJO1Ig8JaI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> __Slide Deck:__ [Design Decomposition](https://docs.google.com/presentation/d/1lctQhB-zKCbCSjNsSdN3aGvV2tsXfqJibiETjmuucXs/edit?usp=sharing)

In this lecture, we will focus on decomposing our system into individual classes and functions.

In structured programming, such as languages like C and Javascript, we use Functional Decomposition, where we decompose high-level general functions into lower and lower level functions, each of which performing a more and more specific task. Typically, we think of our functions being executed like a depth-first search in this way.

By contrast, Object-Oriented Decomposition is useful for modern software design. In Object-Oriented decomposition, we break our class down into classes, and describe the interactions of those classes.

## Single Responsibility Principle

__Each software module should have one, and only one, reason to change__

Consider the following partial class with some selected methods entered:

```java
public class Student {
    private String firstName, lastName, email;
    private List<Course> currentCourses;
    private List<CourseRecord> courseGrades;
    private boolean isTA;
    private Course courseTA;
    private double currentWeeklyHours;
    
    public double generateTranscriptDocument() {
        // does something with courseGrades;
    }
    
    public void semesterReset() {
        currentCourses.clear();
        isTA = false;
        courseTA = null;
        currentWeeklyHours = 0;
    }
    
    public void uploadFinalGrade(Grade grade, Course c) {
        CourseRecord courseRecord = new CourseRecord(c, grade);
        courseGrades.add(courseRecord);
    }
    
    public double calculateGPA() {
        // iterate through courseRecord
    }
    
    public double calculatePay(double hourlyRate) {
        return currentWeeklyHours * hourlyRate;
    }
}
```

This class feels awkward, like it is doing too much. That's because it is! Think of what *human-beings* using the software are *using this class for*:

- __Registrar__ - the registrar will want to `generateTranscriptDocument`
- __Professor__ - the professor will want to `uploadFinalGrade`
- __HR__ - HR will want to use `calculatePay`

Think of the reasons, however, that this class could change:

1) `__generateTranscriptDocument__` may need to change if the printed format changes.
2) `__uploadFinalGrade__` and `__calculateGPA__` may need to change if the available grades change (as they did during Covid with the addition of `CR`, `GC`, and `NC` grades)
3) `__calculatePay__` and fields about TAing may need to change if TAs are moved to a salaried position, or may need to work different if the student is a Graduate student.

In short, there's a lot of different reasons this class can change. This means that this class is violating the Single Responsibility Principle. As a hint, the *use-case* of each of the roles mentioned describes a *functional module*. Using that, we can break this class up:

```java
public class Student {
    ...
}

public class GPACalculator {
    public double calculateGPA(Student student);
}

public class Transcript {
    public void generateTranscript(Student student);
}

public class TAPayment {
    public double calculatePay(Student student);
}
```

Now, each of these classes has one responsibility. Yes, each of these classes is heavily dependent on Student, but that was still they case when they were all one-class. The key, however, is that if the software engineer receives a request to change a feature *related to GPA calculation*, they now know the primary class that they are working from. And because GPACalculation is *encapsulated* from Student, the developer for GPACalculator is significantly less likely to make changes that could break the other two *use-cases*.

Note that we probably *should* decompose this further. For instance, it probably would make sense to separate keeping track of the students current courses, from keeping track of their course history, from keeping track of their TA hours. But this is meant to just be a starting point.

## Class relationships:

![img.png](/img/uml_class_relationships.png)

There are 4 kinds of class relationships we will focus on.

### Inheritance/Realization

This relationship describes a inheritance relationship, where one class is implementing the interface of another. The arrow-head is on the side of the parent class or implemented interface. Generally, we use Realization for implementing interfaces and extending abstract classes, and we use inheritance for extending concrete classes. For example:

```java
public class ElectricCar extends Car {
    ...
}
```

Here, `EletricCar` **realizes** `Car`

### Aggregation/Composition

This is when one class has another instance(s) of another class as a field(s). For example:

```java
public class Car {
    Set<Tire> tires;
}
```

In the above case, Car **aggregates** tires.

The different between aggregation and composition is subtle. In **composition**, we are saying "one thing is composed of" another. For example, I am composed of a skeleton, muscles, etc. They are generally not separable entities (or at least, not meaningfully separable). By contrast, aggregation often implies an impermanent ownership where one class. For example, a Library Patron may check out a book, then adding the data of the book to a `List<Book>` called `checkedOut`. But the patron isn't **composed of** books, they simply *have* some books (aggregation).

When drawn in a diagram, the diamond is on the **owner's** side.

### Assocation

Association is when A is associated with B in some semantic way that implies a bidirectional relationship (That is, A is aware of B, and B is aware of A). For example, "Student enrolls in class". At a code level, this can take the form of something like a mutual aggregation (although that isn't explicitly required). For example, a `Student` enrolls in a `Course` - I would want to, from the `Student` access their set of `Course` objects, and from a `Course`, I would want to access a set of `Student` objects. This might look like:

```java
public class Student {
    private List<Course> courses;
    
    public void addCourse(Course c);
}

public class Course {
    List<Student> students;
    
    public void enrollStudents(Student s);
}
```

### Dependency

Dependency implies a one-directional association. For example, class A *uses* class B, however Class B is unaware of Class A. An example might be something like:

```java
public class Notification {
    public Email generateStudentNotificiationEmail(Student s, String message) {
        String emailAddress = s.getEmailAddress();
        Email notificationEmail = new Email(emailAddress, message);
        notificationEmail.send();
    }
}
```

Here, `Notification` is **dependent on** `Email` and `Student`. However, this **is not** an aggregation, because `Notification` doesn't have fields for `Email` or `Student`. However, it is still dependent on the interfaces of those two classes (i.e., if the Student interface for getting an email address changed, it might require a change in `Notification`).