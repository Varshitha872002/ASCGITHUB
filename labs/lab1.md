:keyboard: **LAB 1**  

1) Implement the following methods in a class. 
```
public void add (int a, int b)      	
  ``` 
  <br> Invoke these methods by passing appropriate parameters and display the output in the main method.
  <br> Hint: To call `add(short a, short b)` method, you may need to use `add((short)5,(short)6)`
  <br>Implement appropriate versions of the `add()` method in a class so that 
  - `add(10,20)` returns 30
  - `add(10,20,30)` returns 60
  - `add(10.5, 20.1)` returns 30.6
  - `add(“Hello”,20)` returns “Hello 20”

CODE:

  public class MethAdd {
    int add(int a, int b) {
        return a+b;
    }
    int add(int a, int b, int c) {
        return a+b+c;
    }
    double add(double a, double b) {
        return a+b;
    }
    String add(String str, int n) {
        return str + " " + n;
    }

    public static void main(String[] args) {
        MethAdd sum = new MethAdd();
        System.out.println(sum.add(10,20));
        System.out.println(sum.add(10,20, 30));
        System.out.println(sum.add(10.5,20.1));
        System.out.println(sum.add("Hello" ,20));
    }
}

2) Define a class Student with the following attributes
  - studentId of type integer
  - studentName of type String
  - city of type String
  - marks1 of type integer
  - marks2 of type integer
  - marks3 of type integer
  - feePerMonth of type float
  - isEligibleForScholarship of type boolean
  Implement the following methods in addition to the setter and getter methods for the various attributes
  - getAnualFee() which returns the product of feePerMonth and 12
  - getTotalmarks() which returns the sum of marks1, marks2 and marks3
  - getAverage() which returns the average of marks1, marks2 and marks3
  - getResult() which returns “pass” if the person has scored more than 60 in each subject, or returns “fail” otherwise
  Create another class TestMain with the main() method which performs the following actions
  - Creates three Student objects
  - Populates the objects using the setter methods
  - Displays the name of the Student who has the highest total marks
  - Prints the name and fee of the Student who pays the least monthly fee
  - Prints the name, total marks , average marks , result, and “Scholarship available” or “Scholarship not available” based on the student’s eligibility for every student.

For the following assignments create an exclusive class called Tester which contains the main method. Create objects of other classes, make calls to the methods, and test your code using this Class’s main method.

CODE - 
Student.java

public class Student {
    public int S_Id;
    public String S_Name;
    public String city;
    public int marks1;
    public int marks2;
    public int marks3;
    public float feePerMonth;
    public boolean isEligibleForScholarship;

    public Student(int S_Id, String S_Name, String city, int marks1, int marks2, int marks3, float feePerMonth, boolean isEligibleForScholarship) {
        this.S_Id = S_Id;
        this.S_Name = S_Name;
        this.city = city;
        this.marks1 = marks1;
        this.marks2 = marks2;
        this.marks3 = marks3;
        this.feePerMonth = feePerMonth;
        this.isEligibleForScholarship = isEligibleForScholarship;
    }

    public int getAnnualFee() {
        return (int) (feePerMonth * 12);
    }
    public int getTotalmarks() {
        return marks1 + marks2 + marks3;
    }
    public double getAverage() {
        return getTotalmarks() / 3.0;
    }
    public String getResult() {
        return (marks1 > 60 && marks2 > 60 && marks3 > 60) ? "pass" : "fail";
    }
    public String getScholarshipStatus() {
        return isEligibleForScholarship ? "Scholarship available" : "Scholarship not available";
    }
}

Testmain.java 

public class TestMain {
    public static void main(String[] args) {
        Student s1 = new Student(1, "Varshi", "Vijayawada", 90,95,98, 9000.0f, true);
        Student s2 = new Student(2, "Vani", "Jaggaiahpet", 80,88,88, 10000.0f, true);
        Student s3 = new Student(3, "Likki", "Mangollu", 87,58,78, 8000.0f, false);
        Student[] std = {s1, s2, s3};
        Student highestTotalMarks = getHigest(std);
        System.out.println(highestTotalMarks.S_Name);
        Student LeastMonthlyFee = getLeastMonthly(std);
        System.out.println(LeastMonthlyFee.S_Name + LeastMonthlyFee.feePerMonth);
        for (Student student : std) {
            System.out.println("\nName: " + student.S_Name);
            System.out.println("Total Marks: " + student.getTotalmarks());
            System.out.println("Average Marks: " + student.getAverage());
            System.out.println("Result: " + student.getResult());
            System.out.println("Scholarship Status: " + student.getScholarshipStatus());
        }
    }
    public static Student getHigest(Student[] std) {
        Student highestTotalMarks = std[0];
        for (int i = 1; i < std.length; i++) {
            if (std[i].getTotalmarks() > highestTotalMarks.getTotalmarks()) {
                highestTotalMarks = std[i];
            }
        }
        return highestTotalMarks;
    }

    public static Student getLeastMonthly(Student[] std) {
        Student LeastMonthlyFee = std[0];
        for (int i = 1; i < std.length; i++) {
            if (std[i].feePerMonth < LeastMonthlyFee.feePerMonth) {
                LeastMonthlyFee = std[i];
            }
        }
        return LeastMonthlyFee;
    }
}

Tester.java

public class Tester {
    public static void main(String[] args) {
        TestMain.main(args);
    }
}


3) Write a method that accepts an integer as parameter and displays its multiplication table using for loop, as shown below. Implement 2 other methods which perform the same action but using a while and do-while loop respectively. E.g. if the input parameter is 2, then these methods must output the multiplication table as follows:
<br> 2 x 1 = 2 
<br> 2 x 2 = 4 
<br> ...
<br> 2 x 10 = 20

CODE - 

public class MultiplicationTable {

    public static void multiplicationTableFor(int n) {
        System.out.println("Multiplication table for " + n + " using for loop:");
        for (int i = 1; i <= 10; i++) {
            System.out.println(n + " x " + i + " = " + (n * i));
        }
    }

    public static void multiplicationTableWhile(int n) {
        System.out.println("Multiplication table for " + n + " using while loop:");
        int i = 1;
        while (i <= 10) {
            System.out.println(n + " x " + i + " = " + (n * i));
            i++;
        }
    }

    public static void multiplicationTableDoWhile(int n) {
        System.out.println("Multiplication table for " + n + " using do-while loop:");
        int i = 1;
        do {
            System.out.println(n + " x " + i + " = " + (n * i));
            i++;
        } while (i <= 10);
    }

    public static void main(String[] args) {
        int n = 2;
        multiplicationTableFor(n);
        System.out.println();
        multiplicationTableWhile(n);
        System.out.println();
        multiplicationTableDoWhile(n);
    }
}

5) Write a method which accepts a string as parameter and returns the number of words in it. For example, if the string is "Sum of 12 and 20 is 32", the method should return 4.

  CODE - 

  public class StringCount {

    public static int countWords(String input) {
        input = input.trim();

        if (input.isEmpty()) {
            return 0;
        }
        String[] words = input.split("\\s+");

        int wordCount = 0;
        for (String word : words) {
            if (word.matches("[a-zA-Z]+")) {
                wordCount++;
            }
        }
        return wordCount;
    }

    public static void main(String[] args) {
        String input = "Sum of 12 and 20 is 32";
        int wordCount = countWords(input);
        System.out.println("Number of words: " + wordCount); 
    }
}

7) Create a program with methods to test the functionality of the various methods of the String class
  - charAt
  - contains
  - length
  - indexOf
  - equals
  - equalsIgnoreCase
  - join
  - lastIndexOf
  - substring
  - tolowercase
  - touppercase
  - trim

CODE - 

public class StringTest {

    public static void testCharAt(String str, int index) {
        if (index >= 0 && index < str.length()) {
            char ch = str.charAt(index);
            System.out.println("charAt(" + index + ") = " + ch);
        } else {
            System.out.println("Index " + index + " is out of bounds for string \"" + str + "\"");
        }
    }

    public static void testContains(String str, String substring) {
        boolean contains = str.contains(substring);
        System.out.println("\"" + str + "\" contains \"" + substring + "\": " + contains);
    }

    public static void testLength(String str) {
        int length = str.length();
        System.out.println("Length of \"" + str + "\": " + length);
    }

    public static void testIndexOf(String str, String substring) {
        int index = str.indexOf(substring);
        System.out.println("Index of \"" + substring + "\" in \"" + str + "\": " + index);
    }

    public static void testEquals(String str1, String str2) {
        boolean isEqual = str1.equals(str2);
        System.out.println("\"" + str1 + "\" equals \"" + str2 + "\": " + isEqual);
    }

    public static void testEqualsIgnoreCase(String str1, String str2) {
        boolean isEqual = str1.equalsIgnoreCase(str2);
        System.out.println("\"" + str1 + "\" equalsIgnoreCase \"" + str2 + "\": " + isEqual);
    }

    public static void testJoin(String delimiter, String... elements) {
        String joinedString = String.join(delimiter, elements);
        System.out.println("Joined string with \"" + delimiter + "\": " + joinedString);
    }

    public static void testLastIndexOf(String str, String substring) {
        int lastIndex = str.lastIndexOf(substring);
        System.out.println("Last index of \"" + substring + "\" in \"" + str + "\": " + lastIndex);
    }

    public static void testSubstring(String str, int startIndex, int endIndex) {
        String substring = str.substring(startIndex, endIndex);
        System.out.println("Substring from index " + startIndex + " to " + endIndex + ": " + substring);
    }

    public static void testToLowerCase(String str) {
        String lowerCaseStr = str.toLowerCase();
        System.out.println("Lowercase of \"" + str + "\": " + lowerCaseStr);
    }

    public static void testToUpperCase(String str) {
        String upperCaseStr = str.toUpperCase();
        System.out.println("Uppercase of \"" + str + "\": " + upperCaseStr);
    }

    public static void testTrim(String str) {
        String trimmedStr = str.trim();
        System.out.println("Trimmed version of \"" + str + "\": \"" + trimmedStr + "\"");
    }

    public static void main(String[] args) {
        String str1 = "Hello World";
        String str2 = "hello world";
        String str3 = "Hello";

        testCharAt(str1, 6);
        testContains(str1, "World");
        testLength(str1);
        testIndexOf(str1, "o");
        testEquals(str1, str2);
        testEqualsIgnoreCase(str1, str2);
        testJoin("-", "Java", "is", "fun");
        testLastIndexOf(str1, "l");
        testSubstring(str1, 3, 8);
        testToLowerCase(str1);
        testToUpperCase(str1);
        testTrim("   Hello   "); 
    }
}
 
6) Define a class ArrayStore which contains an integer array as its instance variable. Create necessary methods for the following operations.
  - Accept 10 integers and store them into the array.
  - Display the elements of the array using while & for loops
  - Sort the array
  - Accept a number and return the number of times it occurs in the array
  - Insert a number into the array at a specified position
  - Return array that excludes duplicate elements in the original array. E.g. if the elements of the original array are [9,2,2,9,10,9] then return [9,2,10]

CODE - 

public class ArrayStore {
    private int[] array;

    public ArrayStore() {
        array = new int[10];
    }

    public void acceptIntegers(int[] numbers) {
        if (numbers.length != 10) {
            System.out.println("Please provide exactly 10 integers.");
            return;
        }
        array = Arrays.copyOf(numbers, numbers.length);
        System.out.println("Integers stored successfully.");
    }
    public void displayWithWhileLoop() {
        System.out.println("Displaying elements using while loop:");
        int i = 0;
        while (i < array.length) {
            System.out.print(array[i] + " ");
            i++;
        }
        System.out.println();
    }

     public void displayWithForLoop() {
        System.out.println("Displaying elements using for loop:");
        for (int i = 0; i < array.length; i++) {
            System.out.print(array[i] + " ");
        }
        System.out.println();
    }

   public void sortArray() {
        Arrays.sort(array);
        System.out.println("Array sorted successfully.");
    }

    public int countOccurrences(int number) {
        int count = 0;
        for (int i = 0; i < array.length; i++) {
            if (array[i] == number) {
                count++;
            }
        }
        return count;
    }

    public void insertNumber(int number, int position) {
        if (position < 0 || position >= array.length) {
            System.out.println("Invalid position. Please provide a position within the array range.");
            return;
        }
        array[position] = number;
        System.out.println("Number inserted successfully at position " + position + ".");
    }

    public int[] removeDuplicates() {
        int[] uniqueArray = new int[array.length];
        int index = 0;

        for (int i = 0; i < array.length; i++) {
            boolean isDuplicate = false;
            for (int j = 0; j < index; j++) {
                if (array[i] == uniqueArray[j]) {
                    isDuplicate = true;
                    break;
                }
            }
            if (!isDuplicate) {
                uniqueArray[index++] = array[i];
            }
        }

        return Arrays.copyOf(uniqueArray, index);
    }

    public static void main(String[] args) {
        ArrayStore store = new ArrayStore();

        int[] numbers = {9, 2, 2, 9, 10, 9, 5, 3, 7, 1};
        store.acceptIntegers(numbers);
        store.displayWithWhileLoop();
        store.displayWithForLoop();

        store.sortArray();
        store.displayWithForLoop();

        int numberToCount = 9;
        int count = store.countOccurrences(numberToCount);
        System.out.println("Number of occurrences of " + numberToCount + ": " + count);

        int numberToInsert = 15;
        int positionToInsert = 3;
        store.insertNumber(numberToInsert, positionToInsert);
        store.displayWithForLoop();
        int[] uniqueArray = store.removeDuplicates();
        System.out.println("Array with duplicates removed: " + Arrays.toString(uniqueArray));
    }
}







