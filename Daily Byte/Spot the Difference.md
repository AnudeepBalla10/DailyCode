# Spot the Difference

👓This question is asked by Google.👓

> You are given two strings, s and t which only consist of lowercase letters. t is generated by shuffling the letters in s as well as potentially adding an additional random character. Return the letter that was randomly added to t if it exists, otherwise, return ’  ‘.

Note: You may assume that at most one additional character can be added to t.

Ex: Given the following strings...

- s = "foobar", t = "barfoot", return 't'
- s = "ide", t = "idea", return 'a'
- s = "coding", t "ingcod", return ''

  ```Java
  class TheDifference {
    public static void main(String[] args) {
        
        String s = "foobar", t = "barfoot";//return t
        System.out.println("The difference is "+ spotTheDifference(s,t));
        s = "ide"; t = "idea";//return a
        System.out.println("The difference is "+ spotTheDifference(s,t));
        s = "coding"; t= "ingcod";
        System.out.println("The difference is "+ spotTheDifference(s,t));
    }
    public static char spotTheDifference(String s, String t){
        for(char c: t.toCharArray()){
            int x = s.indexOf(c);
            if(x<0){
                return c;
            }
        }
        return ' ';
    }
}
  ```
