# Popsicle Stand

🌴This question is asked by Amazon.🌴

>You’re running a popsicle stand where each popsicle costs $5. Each customer you encountered pays with either a $5 bill, a $10 bill, or a $20 bill and only buys a single popsicle. the customers that come to your stand come in the ordered given by the customers array where customers[i] represents the bill the ith customer pays with. Starting with $0, return whether or not you can serve all the given customers while also giving the correct amount of change.

Ex: Given the following customers…
```
customers = [5, 10], return true
collect $5 from the first customer, pay no change.
collet $10 from the second customer and give back $5 change.
```

Ex: Given the following customers…
```
customers = [10], return false
collect $10 from the first customer and we cannot give back change.
```

Ex: Given the following customers…
```
customers = [5,5,5,10,20], return true
collect $5 from the first 3 customers.
collet $10 from the fourth customer and give back $5 change.
collect $20 from the fifth customer and give back $10 change ($10 bill and $5 bill).
```


## Simple Solution
```java
public class PopsicleStand {
    public static boolean canServeAllCustomers(int[] customers) {
        int fiveDollarBills = 0;
        int tenDollarBills = 0;

        for (int payment : customers) {
            if (payment == 5) {
                fiveDollarBills++;
            } else if (payment == 10) {
                if (fiveDollarBills == 0) {
                    return false;
                }
                fiveDollarBills--;
                tenDollarBills++;
            } else { // payment is $20
                if (fiveDollarBills > 0 && tenDollarBills > 0) {
                    fiveDollarBills--;
                    tenDollarBills--;
                } else if (fiveDollarBills >= 3) {
                    fiveDollarBills -= 3;
                } else {
                    return false;
                }
            }
        }

        return true;
    }

    public static void main(String[] args) {
        System.out.println(canServeAllCustomers(new int[]{5, 10})); // Output: true
        System.out.println(canServeAllCustomers(new int[]{10})); // Output: false
        System.out.println(canServeAllCustomers(new int[]{5, 5, 5, 10, 20})); // Output: true
    }
}
