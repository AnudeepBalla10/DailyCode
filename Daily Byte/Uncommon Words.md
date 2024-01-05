# Uncommon Words

🌴This question is asked by Amazon.🌴

> Given two strings representing sentences, return the words that are not common to both strings (i.e. the words that only appear in one of the sentences). You may assume that each sentence is a sequence of words (without punctuation) correctly separated using space characters.

Ex: given the following strings...

- sentence1 = "the quick", sentence2 = "brown fox", return ["the", "quick", "brown", "fox"]
- sentence1 = "the tortoise beat the haire", sentence2 = "the tortoise lost to the haire", return ["beat", "to", "lost"]
- sentence1 = "copper coffee pot", sentence2 = "hot coffee pot", return ["copper", "hot"]

```java
import java.util.HashMap;
import java.util.ArrayList;
import java.util.List;
import java.util.Map;

class HelloWorld {
    public static void main(String[] args) {
        String sentence1 = "the quick";
        String sentence2 = "brown fox";
        String[] array = uncommonWords(sentence1, sentence2);
        for (String element : array) {
            System.out.println(element);
        }
        sentence1 = "the tortoise beat the haire";
        sentence2 = "the tortoise lost to the haire";
        array = uncommonWords(sentence1, sentence2);
        for (String element : array) {
            System.out.println(element);
        }
        sentence1 = "copper coffee pot";
        sentence2 = "hot coffee pot";
        array = uncommonWords(sentence1, sentence2);
        for (String element : array) {
            System.out.println(element);
        }
        
        
        
    }

    public static String[] uncommonWords(String sentence1, String sentence2) {
        String[] s1 = sentence1.split("\\s+");
        String[] s2 = sentence2.split("\\s+");
        HashMap<String, Integer> wordFreq = new HashMap<>();

        for (String x : s1) 
            wordFreq.put(x, wordFreq.getOrDefault(x, 0) + 1);
        
        for (String y : s2) 
            wordFreq.put(y, wordFreq.getOrDefault(y, 0) + 1);

        List<String> singleFrequencyWords = new ArrayList<>();

        for (Map.Entry<String, Integer> entry : wordFreq.entrySet()) {
            if (entry.getValue() == 1) {
                singleFrequencyWords.add(entry.getKey());
            }
        }

        return singleFrequencyWords.toArray(new String[0]);
    }
}


```
