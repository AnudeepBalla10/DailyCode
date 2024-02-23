# Moving Bricks

>You are transporting bricks on a construction site and want to work as efficiently as possible. The weight of each brick is given by bricks[i]. Given a wheelbarrow that can carry up to (not including) 5000 pounds, return then maximum number of bricks you can place in your wheelbarrow to transport.

Ex: Given the following bricks…

```
bricks = [1000, 1000, 1000, 2000], return 3.
```

Ex: Given the following bricks…
```
bricks = [1000, 200, 150, 200], return 4.
```

## Simple Implementation
```java
import java.util.Arrays;

public class Main {
    public static int maxBricks(int[] bricks) {
        Arrays.sort(bricks);
        int totalWeight = 0;
        int count = 0;
        for (int brick : bricks) {
            if (totalWeight + brick < 5000) {
                totalWeight += brick;
                count++;
            } else {
                break;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        int[] bricks = {1000, 2000, 1500, 3000, 100};
        System.out.println("Maximum number of bricks: " + maxBricks(bricks
