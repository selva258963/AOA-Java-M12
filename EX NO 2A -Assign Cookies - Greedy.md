

# EX 2A Assign Cookies using Greedy Algorithm. 
## DATE: 15-10-2025

## AIM:
To Write a Java program for the following Constraints.
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximise the number of your content children and output the maximum number.

## Algorithm

1. Read the number of children and their greed factors.
2. Read the number of cookies and their sizes.
3. Sort both arrays (greed factors and cookie sizes) in ascending order.
4. Use two pointers to iterate through both arrays:
   - If the current cookie satisfies the current child’s greed, assign it and move to the next child.
   - Always move to the next cookie.
5. The number of assigned children is the final result.

## Program
```txt
Program to Assign Cookies using Greedy Algorithm
Developed by: Selvamuthukumaran V
Register Number: 212222040151
```

```java
import java.util.*;

public class AssignCookies {
    
    public static int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int i = 0, j = 0;
        while (i < g.length && j < s.length) {
            if (s[j] >= g[i]) i++;
            j++;
        }
        return i;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] g = new int[n];
        for (int i = 0; i < n; i++) g[i] = sc.nextInt();
        
        int m = sc.nextInt();
        int[] s = new int[m];
        for (int i = 0; i < m; i++) s[i] = sc.nextInt();
        
        System.out.println(findContentChildren(g, s));
    }
}
```

## Output:

<img width="209" height="271" alt="image" src="https://github.com/user-attachments/assets/b06626ae-826c-4038-a588-cd57e1c4a7f4" />


## Result:
The program successfully finds the maximum number of content children using the greedy cookie-assignment algorithm.
