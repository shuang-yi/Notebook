# OOP
基本构成：

* classdef...end — Definition of all class components
* properties...end — Declaration of property names, specification of property attributes, assignment of default values
* methods...end — Declaration of method signatures, method attributes, and function code
* events...end — Declaration of event name and attributes
* enumeration...end — Declaration of enumeration members and enumeration values for enumeration classes.

## class
基本

```
classdef ClassName
	...
end
```

继承（从Array和handle两个类中继承）

```
classdef LinkedList < Array & handle
	...
end
```

### 继承
#### 初始化方式

```
function obj = classB(x,y,z)
        obj@classA(x,y);
        obj.z = z;
end
```
#### method 
继承的method要有同样的名称

```
function val = sum(obj)
        val = sum@classB(obj) + obj.z;
end
```
## properties
不设定初值，默认为`[]`
```matlab
classdef ClassName
   properties
      Prop1
      Prop2 = 'some text'
      Prop3 = sin(pi/12)
   end
end
```

在method中设定`set`和`get`，每次设定或查询相应变量时会自动调用

```
methods

   function obj = set.PropertyName(obj,value)
      ...
   end

   function value = get.PropertyName(obj)
      ...
   end

end
```

## method
## 在单独的文件中定义method

方法1

1. 若类名为`myClass`
2. 文件件名称必须为`@myClass`，且其父路径必须位于系统路径，
3. 必须含有`myClass.m`文件，这个文件定义了类（classdef），含有所有method声明
4. 该路径下所有m文件都为默认为一个method函数或者常数property，如果在`myClass.m`中没有声明，会报错

方法2

文件夹名称不一定是`@`开头，位于系统路径下，可以包含多个类声明。

### myClass.m文件基本内容

```
classdef myClass
	properties
		x
	end
	
	methods
		function obj = myClass(x)
			obj.x = x;
		end
		
		y = fun1(obj, y)
	end
	
	methods (Static)
		z = fun2(y)
	end
end		
```

这里，`myClass`初始化函数必须定义，`fun1`是普通方法，`fun2`是静态方法（即不需要**类**变量），这两个方法单独位于同名的m文件下，定义和普通函数一样，注意变量要完全相同。


