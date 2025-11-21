
# EX 2D Pattern Matching using Naive Approach.
## DATE: 15-10-2025
## AIM:
To write a Java program to for given constraints.
Given text string with length n and a pattern with length m, the task is to prints all occurrences of pattern in text.
Note: You may assume that n > m.

Examples: 

Input:  text = "THIS IS A TEST TEXT", pattern = "TEST"
Output: Pattern found at index 10

Input:  text =  "AABAACAADAABAABA", pattern = "AABA"
Output: Pattern found at index 0, Pattern found at index 9, Pattern found at index 12
## Algorithm
1. Read the text string and pattern string from the user.
2. Store the lengths of the text (n) and pattern (m).
3. Iterate through the text from index 0 to n - m.
4. For each index, compare the substring of text with the pattern character by character.
5. If all characters match, print the starting index as a valid pattern occurrence.

## Program:
```
Program to implement Reverse a String
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151
```
```java
import java.util.Scanner;

public class NaivePatternSearch {
    static void search(String text, String pattern) {
        int n = text.length();
        int m = pattern.length();
        for (int i = 0; i <= n - m; i++) {
            int j;
            for (j = 0; j < m; j++) {
                if (text.charAt(i + j) != pattern.charAt(j))
                    break;
            }
            if (j == m)
                System.out.println("Pattern found at index " + i);
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String text = scanner.nextLine();
        String pattern = scanner.nextLine();
        search(text, pattern);
        scanner.close();
    }
}

```
## Output:
<img width="642" height="195" alt="image" src="https://github.com/user-attachments/assets/4efc289f-dca6-4165-85dd-81f81750baa9" />

## Result:
The program successfully implemented and the expected output is verified.
