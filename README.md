# 1、leetcode717. 1比特与2比特字符
解法一：
--  
思路：
--
    判断是否是一字符：只有最后一个字符为1并且倒数第三个字符为1，或0，或00 时才返回true。  
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/22 12:12
 * @descriptor  717. 1比特与2比特字符
 */
public class IsOneBitCharacter_717 {
    public static boolean isOneBitCharacter(int[] bits) {
        int i = 0;
        for (i = 0; i < bits.length; i++) {
            if(i == bits.length-1 && bits[i] == 0)
                return true;
            if(bits[i] == 1)
                i++;
        }
        return false;
    }
    public static void main(String[] args) {
        int[] bits = {1, 1, 1, 0};
        boolean oneBitCharacter = isOneBitCharacter(bits);
        System.out.println(oneBitCharacter);
    }
}
</pre>
解法二：
--  
思路：
--
    贪心。三种字符分别为 0，10 和 11。因此最后一位是否为一比特字符，只和他左侧出现的连续的 1 的个数有关。如果 1 的个数为偶数个，那么最后一位是一比特字符，如果 1 的个数为奇数个，那么最后一位不是一比特字符，例如：010/0110/01110/011110。   
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/22 12:12
 * @descriptor  717. 1比特与2比特字符
 */
public class IsOneBitCharacter_717 {
    public static boolean isOneBitCharacter1(int[] bits) {
       int count = 0;
       int i = bits.length - 2;
       while(i >= 0 && bits[i] == 1){
           count ++;
           i --;
        }
       return count % 2 == 0;
    }
    public static void main(String[] args) {
        int[] bits = {1, 1, 1, 0};
        boolean oneBitCharacter = isOneBitCharacter(bits);
        System.out.println(oneBitCharacter);
    }
}
</pre>
