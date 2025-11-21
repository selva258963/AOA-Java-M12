
# EX 2B Jump Game using Greedy Algorithm.
## DATE: 29-10-2025
## Aim:
To write a Java program to for given constraints.
You are given an array of integers. Each number represents the maximum number of steps you can jump forward from that position.

You start from the first element (index 0). 
Write a program to find the minimum number of jumps required to reach the last index of the array.

If it is not possible to reach the end, return -1.
## Algorithm
1. Read the size of the array and its elements from the user.
2. Initialize a variable reachable to store the farthest index that can be reached.
3. Traverse the array from index 0 to n-1.
4. If the current index is greater than reachable, return false.
5. Update reachable to the maximum of its current value and i + nums[i].
6. After completing the loop, return true.
7. Print whether the last index can be reached.

## Program:
```
Program to implement Jump Game
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151
```

```java
import java.util.Scanner;

public class JumpGame {

    public static boolean canReachLastIndex(int[] nums) {
        int reachable = 0;
        for (int i = 0; i < nums.length; i++) {
            if (i > reachable) {
                return false;
            }
            reachable = Math.max(reachable, i + nums[i]);
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Size of array
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt(); 
        }
        System.out.println("Can reach last index: " + canReachLastIndex(nums));
    }
}
```
## Output:
<img width="615" height="171" alt="image" src="https://github.com/user-attachments/assets/b27cbc51-ba72-43a5-9ca3-65e1dc636fa9" />

## Result:
The program successfully implemented and the expected output is verified.
