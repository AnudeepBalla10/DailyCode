# Lunchtime

This question is asked by Apple. 

>You are serving people in a lunch line and need to ensure each person gets a “balanced” meal. A balanced meal is a meal where there exists the same number of food items as drink items. Someone is helping you prepare the meals and hands you food items (i.e. F) or a drink items (D) in the order specified by the items string. Return the maximum number of balanced meals you are able to create without being able to modify items.
Note: items will only contain F and D characters

Ex: Given the following items…
```
items = "FDFDFD", return 3
the first "FD" creates the first balanced meal.
the second "FD" creates the second balanced meal.
the third "FD" creates the third balanced meal.
```
Ex: Given the following items…
```
items = "FDFFDFDD", return 2
"FD" creates the first balanced meal.
"FFDFDD" creates the second balanced meal.
```

## Simple Solution: 

```java
public class BalancedMeals {
    public static int maxBalancedMeals(String items) {
        int foodCount = 0;
        int drinkCount = 0;
        int balancedMeals = 0;

        for (int i = 0; i < items.length(); i++) {
            if (items.charAt(i) == 'F') {
                foodCount++;
            } else {
                drinkCount++;
            }

            if (foodCount == drinkCount) {
                balancedMeals++;
                foodCount = 0;
                drinkCount = 0;
            }
        }

        return balancedMeals;
    }

    public static void main(String[] args) {
        System.out.println(maxBalancedMeals("FDFDFD")); // Output: 3
        System.out.println(maxBalancedMeals("FDFFDFDD")); // Output: 2
    }
}
```
