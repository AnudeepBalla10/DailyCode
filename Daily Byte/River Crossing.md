# River Crossing

🌴This question is asked by Amazon.🌴

> A frog is attempting to cross a river to reach the other side. Within the river, there are stones located at different positions given by a stones array (this array is in sorted order). Starting on the first stone (i.e. stones[0]), the frog makes a jump of size one potentially landing on the next stone. If the frog’s last jump was of size x, the frog’s next jump may be of size x - 1, x, or x + 1. Given these following conditions return whether or not the frog can reach the other side.
Note: The frog may only jump in the forward direction.

Ex: Given the following stones…
```
stones = [0, 1, 10], return false.
The frog can jump from stone 0 to stone 1, but then the gap is too far to jump to the last stone (i.e. the stone at position 10)
```
Ex: Given the following stones…
```
stones = [0, 1, 2, 4], return true.
The frog can jump from stone 0, to stone 1, to stone 2, to stone 4.
```

## Using HashSet
```java
import java.util.HashMap;
import java.util.HashSet;
import java.util.Map;
import java.util.Set;

public class FrogJump {

    public static boolean canCross(int[] stones) {
        // Map to store the stones and the possible jump sizes that can reach each stone
        Map<Integer, Set<Integer>> stoneMap = new HashMap<>();
        for (int stone : stones) {
            stoneMap.put(stone, new HashSet<>());
        }
        // The first stone can be reached with a jump size of 0
        stoneMap.get(stones[0]).add(0);

        for (int stone : stones) {
            for (int jumpSize : stoneMap.get(stone)) {
                // Try all possible jump sizes: x-1, x, x+1
                for (int nextJump = jumpSize - 1; nextJump <= jumpSize + 1; nextJump++) {
                    if (nextJump > 0 && stoneMap.containsKey(stone + nextJump)) {
                        stoneMap.get(stone + nextJump).add(nextJump);
                    }
                }
            }
        }

        // Check if the last stone has any possible jump sizes that can reach it
        return !stoneMap.get(stones[stones.length - 1]).isEmpty();
    }

    public static void main(String[] args) {
        int[] stones = {0, 1, 10};
        System.out.println(canCross(stones));  // Output: false
    }
}
