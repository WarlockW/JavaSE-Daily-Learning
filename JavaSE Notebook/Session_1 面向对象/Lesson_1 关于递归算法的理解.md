递归实际上就是自己调用自己，有几点注意事项： <br/>
要往已知道的方向递归---- <br/>
    比如f(n+2) = 2*f(n+1) + f(n) ,f(1) = 4,f(0) = 1。在写的时候要忘改为f(n) = 2*f(n-1) + f(n-2)，向已知方向靠近。 <br/>
    比如f(n+2) = 2*f(n+1) + f(n) ,f(20) = 1,f(21) = 4。在写的时候要忘改为f(n) = f(n+2) - 2*f(n+1)，向已知方向靠近。 <br/>


```
public class Recursive {
    static int fn(int n){
        if(n == 0){
            return 1;
        }

        if(n == 1){
            return 4;
        }

        return 2*fn(n-1) + fn(n-2);
    }

    public static void main(String[] args){
        System.out.println(fn(10));
    }
}
```
