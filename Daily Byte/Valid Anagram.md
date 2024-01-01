import java.util.Arrays;

class HelloWorld {
    public static void main(String[] args) {
        System.out.println(validAnagram("cat", "tac"));
        System.out.println(validAnagram("listen", "silent"));
        System.out.println(validAnagram("program", "function"));
    }
    
    public static boolean validAnagram(String s, String t){
        if (s.length() != t.length()) {
            return false;
        }
        char[] x = s.toCharArray();
        char[] y = t.toCharArray();
        Arrays.sort(x);
        Arrays.sort(y);
        
        return Arrays.equals(x,y);
    }
}
