
### Java 泛型
泛型是一种 “代码模板”，可以用一套代码套用各种类型。  
泛型的好处是使用时不必对类型进行强制转换，它通过编译器对类型进行检查。  

虚拟机中没有泛型，只有普通类和普通方法，所有泛型类的类型参数在编译时都会被擦除，泛型类并没有自己独有的 Class 类对象。比如并不存在 List<String>.class 或是 List<Integer>.class，而只有 List.class。

`注意泛型的继承关系：可以把 ArrayList<Integer> 向上转型为 List<Integer>（T 不能变！），但不能把 ArrayList<Integer> 向上转型为 ArrayList<Number>（T 不能变成父类）`

```java
public class ArrayList<T> {
    private T[] array;
    private int size;
    public void add(T e) {...}
    public void remove(int index) {...}
    public T get(int index) {...}
}

// 不指定泛型参数类型时，编译器会给出警告，且只能将 <T> 视为 Object 类型；
// List list = new ArrayList();
// 
// 创建可以存储 String 的 ArrayList:
ArrayList<String> strList = new ArrayList<String>();
// 创建可以存储 Float 的 ArrayList:
ArrayList<Float> floatList = new ArrayList<Float>();
// 创建可以存储 Person 的 ArrayList:
ArrayList<Person> personList = new ArrayList<Person>();

// 创建可以存储 Number 的 ArrayList（可以省略后面的 Number，编译器可以自动推断泛型类型）:
List<Number> list = new ArrayList<>();

// 可以在接口中定义泛型类型
// 实现此接口的类必须实现正确的泛型类型
// 
// Person 排序的例子
import java.util.Arrays;

public class Main 
{
    public static void main(String[] args) 
    {
        Person[] ps = new Person[] {
            new Person("Bob", 61),
            new Person("Alice", 88),
            new Person("Lily", 75),
        };
        Arrays.sort(ps);
        System.out.println(Arrays.toString(ps));
    }
}

class Person implements Comparable<Person> 
{
    String name;
    int score;
    Person(String name, int score) 
    {
        this.name = name;
        this.score = score;
    }

    public int compareTo(Person other) 
    {
        return this.name.compareTo(other.name);
    }

    public String toString() 
    {
        return this.name + "," + this.score;
    }
}

public interface Comparable<T> 
{
    /**
     * 返回 -1: 当前实例比参数 o 小
     * 返回 0: 当前实例与参数 o 相等
     * 返回 1: 当前实例比参数 o 大
     */
    int compareTo(T o);
}
```