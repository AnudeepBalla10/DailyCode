# Jewels and Stones

🌴This question is asked by Amazon.🌴

> Given a string representing your stones and another string representing a list of jewels,
return the number of stones that you have that are also jewels.

Ex: Given the following jewels and stones...

- jewels = "abc", stones = "ac", return 2
- jewels = "Af", stones = "AaaddfFf", return 3
- jewels = "AYOPD", stones = "ayopd", return 0

```java
class HelloWorld {
    public static int jewelsAndStones(String jewels, String stones) {
        int count =0;
        for(char stone: stones.toCharArray()){
            if(jewels.indexOf(stone) > -1){
                count++;
            }
        }
        return count;
        
    }
    
    
    public static void main(String[] args) {
        System.out.println(jewelsAndStones("abc", "ab"));
        System.out.println(jewelsAndStones("Af", "AaaddfFf"));
        System.out.println(jewelsAndStones("AYOPD", "ayopd"));
    }
}

```
