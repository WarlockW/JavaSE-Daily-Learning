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
