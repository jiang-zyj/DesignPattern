案例：克隆羊

原型模式的注意事项和细节
1. 创建新的对象比较复杂时，可以利用原型模式简化对象的创建过程，同时也能够提高效率
2. 不用重新初始化对象，而是动态的获取对象运行时的状态
3. 如果原始对象发生变化（增加或减少属性），其他克隆对象也会发生相应的变化，
无需修改代码
4. 在实现深克隆的时候可能需要比较复杂的代码
5. 缺点：需要为每一个类配备一个克隆方法，这对全新的类来说不是很难，但是对
已有的类进行改造时，需要修改其源代码，违背了 ocp 原则。

深拷贝与浅拷贝
根据在复制原型对象的同时是否复制包含在原型对象中引用类型的成员变量，原型模式的克隆机制
分为两种：浅克隆和深克隆
1. 浅克隆
    在浅克隆中，如果原型对象的成员变量属性是值类型(如 int、double、byte、bool、char
    等基本数据类型【java中外加一个String】)，将值复制一份给克隆对象；如果原型对象的成员变量
    属性是引用类型(如类、接口、数组等)，则将引用对象的地址复制一份给克隆对象，也就是说，
    原型对象和克隆对象的成员变量指向相同的内存地址。如果一方改变引用数据类型，另一方也会改变
    简单来说，在浅克隆中，当原型对象被复制时，只复制它本身和其他包含的值类型的成员变量，而
    引用数据类型的成员变量并没有复制。

2. 深克隆
    在深克隆中，无论原型对象的成员变量是值类型还是引用类型，都将赋值一份给克隆对象
    深克隆有两种实现方式，一种是重写 clone 方法，并针对引用数据类型进行 clone
    第二种是通过对象序列化，将对象以流的方式写出，再将对象以流的方式写入。