<h1>定义及作用</h1>

在jdk1.5之前是需要我们自己创建枚举类的，在jdk1.5之后提供了enum帮我们创建枚举类，不过原理都是相同的。枚举类就是有固定对象的类，其中类的属性用private和final修饰，构造方法私有化。如果类中有属性肯定要有构造方法为其属性赋值，因为属性使用private和fainl修饰的不能通过set进行赋值，枚举类中的对象用public、static和final修饰。<br/>

<h2>传统方式实现枚举类</h2>

```
public class SeasonTest {
    public static void main(String[] args) {
        Season spring = Season.SPRING;
        System.out.println("spring = " + spring);
        String seasonName = spring.getSeasonName();
        System.out.println("seasonName = " + seasonName);
        String seasonDesc = spring.getSeasonDesc();
        System.out.println("seasonDesc = " + seasonDesc);
        Season summer = Season.SUMMER;
        System.out.println("summer = " + summer);
        String seasonName1 = summer.getSeasonName();
        System.out.println("seasonName1 = " + seasonName1);
        String seasonDesc1 = summer.getSeasonDesc();
        System.out.println("seasonDesc1 = " + seasonDesc1);
        Season autumn = Season.AUTUMN;
        System.out.println("autumn = " + autumn);
        String seasonName2 = autumn.getSeasonName();
        System.out.println("seasonName2 = " + seasonName2);
        String seasonDesc2 = autumn.getSeasonDesc();
        System.out.println("seasonDesc2 = " + seasonDesc2);
        Season winter = Season.WINTER;
        System.out.println("winter = " + winter);
        String seasonName3 = winter.getSeasonName();
        System.out.println("seasonName3 = " + seasonName3);
        String seasonDesc3 = winter.getSeasonDesc();
        System.out.println("seasonDesc3 = " + seasonDesc3);
    }
}

public class Season {
    /**
     * 类的属性使用private final修饰
     */
    private final String seasonName;
    private final String seasonDesc;

    /**
     * 如果类有属性肯定有构造方法为其赋值，因为属性是被private final修饰的
     * 不能通过Set方法为其赋值；
     */
    private Season(String seasonName, String seasonDesc){
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    /**
     * 提供方法获取属性值
     */
    public String getSeasonName(){
        return seasonName;
    }
    public String getSeasonDesc(){
        return seasonDesc;
    }

    /**
     * 创建枚举类的对象声明位（即创建固定对象）
     * 使用public static final修饰
     */
    public static final Season SPRING = new Season("spring","春暖花开");
    public static final Season SUMMER = new Season("summer","夏日炎炎");
    public static final Season AUTUMN = new Season("autumn","秋高气爽");
    public static final Season WINTER = new Season("winter","白雪皑皑");
}
```

<h2>使用enum实现枚举类</h2>

```
// 测试类
public class SeasonTest {
    public static void main(String[] args) {
        SeasonEnum spring = SeasonEnum.SPRING;
        System.out.println("spring = " + spring);
        String seasonName = spring.getSeasonName();
        System.out.println("seasonName = " + seasonName);
        String seasonDesc = spring.getSeasonDesc();
        System.out.println("seasonDesc = " + seasonDesc);
        SeasonEnum summer = SeasonEnum.SUMMER;
        System.out.println("summer = " + summer);
        String seasonName1 = summer.getSeasonName();
        System.out.println("seasonName1 = " + seasonName1);
        String seasonDesc1 = summer.getSeasonDesc();
        System.out.println("seasonDesc1 = " + seasonDesc1);
        SeasonEnum autumn = SeasonEnum.AUTUMN;
        System.out.println("autumn = " + autumn);
        String seasonName2 = autumn.getSeasonName();
        System.out.println("seasonName2 = " + seasonName2);
        String seasonDesc2 = autumn.getSeasonDesc();
        System.out.println("seasonDesc2 = " + seasonDesc2);
        SeasonEnum winter = SeasonEnum.WINTER;
        System.out.println("winter = " + winter);
        String seasonName3 = winter.getSeasonName();
        System.out.println("seasonName3 = " + seasonName3);
        String seasonDesc3 = winter.getSeasonDesc();
        System.out.println("seasonDesc3 = " + seasonDesc3);
    }
}

enum SeasonEnum {
    // [必须写在最前面！！！]
    // 先声明枚举类里面的所有成员类
    SPRING ("spring","春暖花开"),
    SUMMER("summer","夏日炎炎"),
    AUTUMN("autumn","秋高气爽"),
    WINTER("winter","白雪皑皑");

    /**
     * 提供的属性用private final修饰
     */
    private final String seasonName;
    private final String seasonDesc;

    /**
     * 如果类有属性肯定有构造方法为其赋值，因为属性是被private final修饰的
     * 不能通过Set方法为其赋值；
     */
    SeasonEnum(String seasonName, String seasonDesc) {
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    /**
     * 提供方法获取属性值
     */
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }
    
}
```
