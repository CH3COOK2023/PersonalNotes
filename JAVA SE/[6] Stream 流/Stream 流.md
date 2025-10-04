# Stream 流

## [1] Stream的创建

![image-20250328143040990](./imageResource/image-20250328143040990.png)

### 创建示例

![image-20250328143150930](./imageResource/image-20250328143150930.png)

### 小细节

<img src="./imageResource/image-20250328142936086.png" alt="image-20250328142936086" style="zoom:50%;" />

## [2] Stream 流的中间方法

### 方法汇总

![image-20250328143320835](./imageResource/image-20250328143320835.png)

![image-20250328143406382](./imageResource/image-20250328143406382.png)

### 过滤方法

![image-20250328143723757](./imageResource/image-20250328143723757.png)

### 注意事项

用过的流不能被再次使用，因为被用过了

![image-20250328143934719](./imageResource/image-20250328143934719.png)

### 获取与跳过

![image-20250328144146328](./imageResource/image-20250328144146328.png)

**小练习**

![image-20250328144303713](./imageResource/image-20250328144303713.png)

### 数据去重

![image-20250328144403587](./imageResource/image-20250328144403587.png)

**Ctrl + B** 跟进源码，会到达 Stream接口

**Ctrl + Alt + B** 是跟进到实现类，因此，我们可以看到其底层实际上是使用了HashSet进行去重的！



### 数据合并

如果类型不同，合并后的类型就是父类类型

![image-20250328145054981](./imageResource/image-20250328145054981.png)

### 类型转换

![image-20250328145436644](./imageResource/image-20250328145436644.png)

当然也可以是转化为自定义类

## [3] Stream 流的终结方法

![image-20250401101643073](./imageResource/image-20250401101643073.png)

### toArray方法

<img src="./imageResource/image-20250401102210645.png" alt="image-20250401102210645" style="zoom:33%;" />

### collect 方法

<img src="./imageResource/image-20250401104032709.png" alt="image-20250401104032709" style="zoom:50%;" />

<img src="./imageResource/image-20250401104135291.png" alt="image-20250401104135291" style="zoom: 50%;" />



收集到`List`中是会保留重复的元素，反之，`toSet`存到`HashSet`中是不会重复的！

储存为Map...

<img src="./imageResource/image-20250401110929562.png" alt="image-20250401110929562" style="zoom:50%;" />

键不允许重复！

当然可以写成lambda表达式

<img src="./imageResource/image-20250401111456080.png" alt="image-20250401111456080" style="zoom: 67%;" />

## [4] 总结

<img src="./imageResource/image-20250401111656194.png" alt="image-20250401111656194" style="zoom: 50%;" />
