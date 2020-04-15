# TypeScript 基础类型

## 1. 基本形式

TypeScript相比于js的区别是:在定义变量时添加了数据类型,基本形式为 

**let 变量名:数据类型 = 值;**

此外还提供了**枚举类型**

## 2. 数据类型的举例
### 		2.1  js中的数据类型

- 布尔值
- 字符串
- 数字
- Null
- undefined
- Object
- Symbol(ES6)

以上是js中的七种数据类型,点击这里复习数据类型

### 		2.2 基本数据类型

1. 布尔值

   ```ts
   var isDone: boolean = true;//在变量后新加: 变量数据类型
   console.log(isDone);
   ```

   

2. 数字类型

   ```ts
   let b: number = 0o12;//ECMA5以后不识别0123的八进制,需要0o开头
   var c: number = 0b10011010;//支持二进制数字输入
   console.log(b);// 10
   console.log(c);// 154
   ```

   

3. 字符串

   双引号单引号都会识别

   ```ts
   var nae: string = 'giao';
   console.log(nae);// name好像作为保留字了,根据官网的name打代码,就出现编译不成功
   ```

   支持模板字符串

   ```ts
   var snn:string = '用大铁锅';
   var sn:string = `我想要熬翔在天上${snn}`;//模板字符串用反向引号,且其中变量用$钱钱包围, 还可以换行之类,js钻钱眼儿了吗$$
   console.log(sn);
   ```

   

4. 数组

   ts有两种方式可以定义数组

   ```ts
   var a: number[]=[1,2,3,4];//number是数组内值的数据类型
   console.log(a);
   var b: Array<number> = [1,1,1,1,1];
   //文档上说这是使用数组范型 Array<number></挠头>
   console.log(b);
   ```

   

5. 元组Tuple

   元组类型允许表示一个已知元素数量和类型的数组，各元素的类型不必相同。

   ```ts
   var c: [number, string];
   c = [1, 'aaaa'];
   console.log(c);//成功赋值
   var c = ['a', 'a'];//会报错
   //报错语句:后续变量声明必须属于同一类型。变量“c”必须属于类型“[number, string]”，但此处却为类型“string[]”。ts(2403)
   ```

   当访问一个越界的元素时,官方文档上的这些都报错了(是不是完善后不允许随便越界了?)

   ```ts
   x[3] = 'world'; // OK, 字符串可以赋值给(string | number)类型
   
   console.log(x[5].toString()); // OK, 'string' 和 'number' 都有 toString
   
   x[6] = true; // Error, 布尔不是(string | number)类
   ```

   

6. 枚举

   enum类型是对JavaScript标准数据类型的一个补充。像C#等其它语言一样，使用枚举类型可以为一组数值赋予友好的名字。(感觉就是一队编号的士兵中间使用等号隔开)

   注意: 中间不要加等号, 要不然搞成对象了

   ```ts
   enum Pig {Xiang = 1, Di}//当只给第一个士兵编号时, 后面的士兵自动依次报数
   let a: number = Pig.Di;
   console.log(a);//用名字找编号
   
   enum Pig {Xiang = 1, Di}
   let a: number = Pig.Di;
   console.log(a);
   let b: string = Pig[1];
   console.log(b);//用编号找名字
   
   enum Ka {S = 1, T = 4, O = 6, P = 8}//自己给士兵编号
   console.log(Ka[8]);
   console.log(Ka.O);
   
   ```

   

7. Any

   anytype来了,就是随便什么类型都可以,让编译器跳过类型检查

   ```ts
   let notSure: any = '我是变态';//我们成功回到了js
   console.log(notSure);
   notSure = '我要变数字';
   console.log(typeof notSure);
   notSure = 112;
   console.log(typeof notSure);
   notSure = false;
   console.log(typeof notSure);
   ```

   当数组中存储的数据类型不确定时也可以用any

   ```ts
   let arr: any[] = [1, 'abc',false];
   console.log(arr);
   ```

   

8. viod

   某种程度上来说,void类型像是与any类型完全相反,它表示没有类型. 当函数没有返回值时,我们会拿到其返回值类型是void.

   ```ts
   function a(): void{//函数在没有返回值时可以在声明后加viod
       console.log('你追我');
       
   }
   let b:void = null;//变量如果声明为void就只能赋予null和undefined
   
   ```

   

9. Null 和 undefined

   类型就是 null 或 undefined

   用处不大,就是为了所有东西都type一下?

   默认情况下`null`和`undefined`是所有类型的子类型。 就是说你可以把 `null`和`undefined`赋值给`number`类型的变量.其他类型都包括这两个类型

10. Never类型

    ```ts
    // 返回never的函数必须存在无法达到的终点
    function infiniteLoop(): never {
        while (true) {
        }//没太看懂
    }
    ```

    

11. Object类型

    Object是一个复杂数据类型,有别于另六个基本数据类型

12. 类型断言

    类型断言就是对 any 声明的变量下断言, 告诉编译器我知道它的类型,你得听我的

    

    类型断言有两种方式

    其一是尖括号语法

    ```ts
    let notSure: any = '我就和你嘿嘿嘿';
    console.log(typeof notSure);
    (<string>notSure);
    notSure = false;
    console.log(notSure);//再次赋值还是可以赋值啊,并没有改变确切的类型啊
    
    ```

    另一个是as

    ```ts
    let notSure: any = '我就和你嘿嘿嘿';
    console.log(typeof notSure);
    (notSure as string);//在这里,效果同上
    notSure = false;
    console.log(notSure);
    ```

    

## 3. 结语

typeof 为各种数据进行了类型确认. 当然还保留了var, 只不过用的是 any ,换了个马甲

新增了enum(枚举)类型, 可以通过值和序号分别得到对应的序号和值

总而言之,就是语言更加严谨, 且保留了一定程度的不严谨.































