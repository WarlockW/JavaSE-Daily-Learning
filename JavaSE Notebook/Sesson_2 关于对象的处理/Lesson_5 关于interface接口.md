<h1>关于inteface的初步理解</h1>
情景：实现司机开车。</br>
</br>
有2个对象，司机和车辆。可是车辆有很多种：桑塔纳、飞度、宝来......</br>
</br>
如果没有接口：司机的drive方法就要有：</br>

```
public class Driver {
    public void drive(Santana san){
        // 驾驶桑塔纳
    } 
    public void drive(Fit fit){
        // 驾驶飞度
    } 
    public void drive(Bora bora){
        // 驾驶宝来
    } 
}

class Santana {
    // 方法略
}

class Fit {
    // 方法略
}

class Bora {
    // 方法略
}
```

如果以后有新的车，需要继续加，每增加一种车，你就要去改写 Driver 类。</br>
</br>
如果用了接口，简单了：</br>

```
public class Driver {
    public void drive(Car car){
        // 驾驶汽车
    } 
}

interface Car{
    // 方法略
}
```

如果以后增加车的种类，上面的代码不用改，每增加一种车，只要：</br>

```
class Santana implements Car {
    // 方法略
}

class Fit implements Car {
    // 方法略
}

class Bora implements Car {
    // 方法略
}
```
