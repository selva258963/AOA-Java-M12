
# EX 2E Pattern Matching using KMP Algorithm.
## DATE: 29-10-2025
## AIM:
To write a Java program for the following constraints.
Longest Palindromic Substring
Given a string s, return the longest palindromic substring in s.
using Manacher's Algorithm

## Algorithm
1. Start the program.
  - Read the input strings: the main text and the pattern to be searched.
2. Construct the LPS (Longest Prefix Suffix) array:
  - Initialize an array lps[] of size equal to the pattern.
  - Use two pointers to compute the length of the longest prefix which is also a suffix for each position.
3.Perform KMP Search:
  - Maintain two indices:
    i → index for text
    j → index for pattern
  - Compare text and pattern characters.
  - If characters match, move both forward.
  - If mismatch occurs:
    
     i. If j > 0, update j = lps[j – 1].
    
     ii. Else move i forward.
    
4. Record matches:
   - Whenever j == pattern.length, a full match is found.
   - Store the index (i − j) in the output list.
   - Reset j using the LPS array.
5. Display the result:
  - Print all starting indices where the pattern occurs.
  - If no match is found, print -1.
6. Stop the program.  

## Program:
```txt
Program to implement Pattern Matching using KMP Algorithm
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151
```
```java
import java.util.*;
public class KMP {

    public static int[] buildLPS(String pattern) {
        int m = pattern.length();
        int[] lps = new int[m];
        int len = 0;
        int i = 1;
        while (i < m) {
            if (pattern.charAt(i) == pattern.charAt(len)) {
                len++;
                lps[i] = len;
                i++;
            } else {
                if (len != 0) {
                    len = lps[len - 1];
                } else {
                    lps[i] = 0;
                    i++;
                }
            }
        }
        return lps;
    }

    public static List<Integer> KMPSearch(String text, String pattern) {
        List<Integer> result = new ArrayList<>();
        int n = text.length();
        int m = pattern.length();
        int[] lps = buildLPS(pattern);
        int i = 0; 
        int j = 0;
        while (i < n) {
            if (text.charAt(i) == pattern.charAt(j)) {
                i++;
                j++;
            }
            if (j == m) {
                result.add(i - j);  
                j = lps[j - 1];
            }
            else if (i < n && text.charAt(i) != pattern.charAt(j)) {
                if (j != 0)
                    j = lps[j - 1];
                else
                    i++;
            }
        }
        if (result.isEmpty()) result.add(-1);
        return result;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String text = sc.nextLine();
        String pattern = sc.nextLine();
        List<Integer> output = KMPSearch(text, pattern);
        for (int idx : output) {
            System.out.print(idx + " ");
        }
        sc.close();
    }
}
```

## Output:
<img width="545" height="197" alt="image" src="https://github.com/user-attachments/assets/f970222e-a73b-4f75-920d-60b1e3339a52" />

## Result:
The program successfully implemented and the expected output is verified.
