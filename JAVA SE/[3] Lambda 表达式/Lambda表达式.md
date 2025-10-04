# Lambda表达式

函数式编程

函数式编程（Functional programming）是一种思想特点。 函数式编程思想，忽略面向对象的复杂语法，强调做什么，而不是谁去做。 而我们要学习的Lambda表达式就是函数式思想的体现。

```java
public static void main(String[] args) {
    int[] arr1 = {2, 1, 4, 3, 5};
    // 升序排列（默认）
    Arrays.sort(arr1);
    System.out.println(Arrays.toString(arr1));
    // 降序排列
    Integer[] arr2 = {2, 1, 4, 3, 5};
    Arrays.sort(arr2, new Comparator<Integer>() {
        @Override
        public int compare(Integer o1, Integer o2) {
            return o2 - o1;
        }
    });
    System.out.println(Arrays.toString(arr2));
    // 降序排列（用Lambda表达式简化）
    arr2 = new Integer[]{2, 1, 4, 3, 5};
    Arrays.sort(arr2, (Integer o1, Integer o2) -> {
        return o2-o1;
    });
    System.out.println(Arrays.toString(arr2));
}
```

`()`对应着方法的形参

`->`固定格式

`{}`对应着方法的方法体

___

Arrays.sort(arr2, ~~new Comparator<Integer>() {~~
        ~~@Override~~
        ~~public int compare~~(Integer o1, Integer o2) {
            return o2 - o1;
        }
    ~~}~~  );

___

Lambda表达式只能简化**函数式接口**的匿名内部类的写法。

> 函数式接口：有且仅有一个抽象方法的接口，接口上方加上`@Functional Interface`注解。如果不满足要求就会报错，满足就不包报错。

```java
public class lbd{
    public static void main(String[] args) {
        // 一般匿名内部类
        method(new Swim() {
            @Override
            public void swim() {
                System.out.println("正在游泳~");
            }
        });

        method(() ->{
            System.out.println("lambda 在游泳");
            }
        );
    }

    public static void method(Swim s)
    {
        s.swim();
    }
}

@FunctionalInterface
interface Swim{
    public abstract void swim();
}

```

Lambda 表达式还支持更省略的写法，例如只有有`1`个参数的时候甚至不需要括号；此外，数据类型也可以省略。类似`if`语句的省略，但是可读性不好。



例如用`Arrays.sort()`方法来按照长度排序升序。

```java
public static void main(String[] args) {

    String[] fruits = {"apple", "banana", "pineapple", " orange", " pear", " grape", " kiwi", " mango"};

    Arrays.sort(fruits, new Comparator<String>() {
        @Override
        public int compare(String o1, String o2) {
            return o1.length() - o2.length();
        }
    });
    System.out.println(Arrays.toString(fruits));

    Arrays.sort(fruits,( o1,  o2) ->{
            return o1.length() - o2.length();
        }
    );
}
```



再比如，我们列出学生成绩单，然后要求：

```java
public static void main(String[] args) {
    String[] name = {
            "Alice", "Bob", "Charlie", "David", "Eve", "Frank", "Grace", "Heidi", "Ivan", "J
            "Kevin", "Luna", "Mason", "Nora", "Oliver", "Penny", "Quinn", "Ryan", "Sophia", 
            "Uma", "Victor", "Wendy", "Xavier", "Yvonne", "Zachary", "Aiden", "Bella", "Cale
            "Ethan", "Faith", "Gabriel", "Hannah", "Isaac", "Julia", "Kai", "Lily", "Max", "
            "Oscar", "Piper", "Quinn", "Roman", "Sara", "Tyler", "Violet", "Wyatt", "Ximena"
            "Zoe", "Adam", "Brianna", "Cameron", "Danielle", "Elijah", "Fiona", "Gavin", "Ha
            "Jasmine", "Kyle", "Leah", "Mia", "Noah", "Olivia", "Parker", "Quentin", "Riley"
            "Thomas", "Ulysses", "Valentina", "William", "Xander", "Yasmin", "Zane", "Alex",
            "Connor", "Destiny", "Evan", "Finn", "Genevieve", "Henry", "Isabella", "Jack", "
            "Logan", "Madison", "Nathan", "Ophelia", "Phoenix", "Quinn", "Raphael", "Samanth
            "Vivian", "Wyatt", "Xochitl", "Yara", "Zoe"
    };
    int[] score = new int[100];
    Random randomScore = new Random();
    for (int i = 0; i < 100; i++) {
        score[i] = randomScore.nextInt(30)+40; // 生成 0 - 100 的随机数
    }
    int[] age = new int[100];
    Random randomAge = new Random();
    for (int i = 0; i < 100; i++) {
        age[i] = randomAge.nextInt(3) + 18; // 生成 18 - 20 的随机数
    }
    Student[] students = new Student[100];
    for (int i = 0; i < 100; i++) {
        students[i] = new Student(name[i], age[i], score[i]);
    }
    // 排序规则：首先成绩从低到高，其次年龄从低到高，最后名字从短到长
    Arrays.sort(students, new Comparator<Student>() {
        @Override
        public int compare(Student o1, Student o2) {
            int temp = o1.getScore() - o2.getScore();
            if (temp == 0) {
                temp = o1.getAge() - o2.getAge();
                if (temp == 0) {
                    temp = o1.getName().length() - o2.getName().length();
                }
            }
            return temp;
        }
    });
    for (Student student : students)
        System.out.println(student);
}
```

```out
Output:
Score:40	Age:20	Name:Ryan
Score:40	Age:20	Name:Riley
Score:41	Age:20	Name:Oscar
Score:42	Age:18	Name:Henry
Score:42	Age:19	Name:Lily
Score:42	Age:19	Name:Victor
Score:42	Age:20	Name:Diana
Score:42	Age:20	Name:Hannah
Score:44	Age:20	Name:Julia
Score:45	Age:19	Name:Madison
Score:45	Age:20	Name:Wyatt
Score:46	Age:18	Name:Judy
Score:46	Age:18	Name:Wyatt
Score:46	Age:18	Name:Xander
Score:46	Age:18	Name:Natalie
...
```





