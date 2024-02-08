<h1>抽象类的实际意义</h1>
Java中的抽象类本质上就是为后续继承该类的子类提供了一个类的模板。抽象类允许你定义一个包含抽象方法和非抽象方法（具体方法）的类，其中抽象方法是没有实现的方法，它们被声明为没有方法体的方法。这些抽象方法必须由继承抽象类的子类来提供具体的实现。</br>
</br>
通过定义抽象类，可以为子类提供一个通用的结构，包括一些共享的属性和行为。子类可以继承这个模板，并根据需要实现或覆盖父类中的方法。这种机制允许你在多个子类之间共享代码，并提供了一种方式来定义一组相关类的共同行为和属性。</br>

<h1>抽象类的使用方法</h1>

```
// 抽象类  
public abstract class Animal {  
      
    // 抽象方法  
    public abstract void makeSound();  
      
    // 具体方法  
    public void eat() {  
        System.out.println("Animal is eating.");  
    }  
}  
  
// 子类，继承抽象类并实现抽象方法  
public class Dog extends Animal {  
      
    @Override  
    public void makeSound() {  
        System.out.println("Woof!");  
    }  
}  
  
// 子类，继承抽象类并实现抽象方法  
public class Cat extends Animal {  
      
    @Override  
    public void makeSound() {  
        System.out.println("Meow!");  
    }  
}  
  
// 使用抽象类  
public class Main {  
    public static void main(String[] args) {  
        Animal dog = new Dog();  
        Animal cat = new Cat();  
          
        dog.makeSound();  // 输出: Woof!  
        dog.eat();        // 输出: Animal is eating.  
          
        cat.makeSound();  // 输出: Meow!  
        cat.eat();        // 输出: Animal is eating.  
    }  
}
```
在这个例子中，Animal 是一个抽象类，它定义了一个抽象方法 makeSound 和一个具体方法 eat。Dog 和 Cat 是 Animal 的子类，它们分别实现了 makeSound 方法，并继承了 eat 方法。Main 类演示了如何使用抽象类和它的子类 </br>
