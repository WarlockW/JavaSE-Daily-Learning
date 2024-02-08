<h1>抽象类的实际意义</h1>


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
