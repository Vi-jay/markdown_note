1. 定义函数

   ```typescript
   //1
   type func = (a: number) => void;
   let f: func = function (a) {
       console.log(a);
   } 
   //2
   interface func {
       (a:number):void
   }
   let f: func = function (a) {
       console.log(a);
   };
   //3
   function func(a:number):number;
   function func(a):number {
       return a;
   }
   
   ```

2. 泛型 `可以作用在类和函数上`

   ```typescript
   function testSay<T, Q>(n: { say(): T }, s: Q): T | Q {
       return s;
   }
   
   
   //此处泛型可以省略，会自动根据参数类型推导泛型T
   testSay({
       say() {
           return "asd"
       }
   }, 1);
   
   //testSay("asd");
   //testSay<String>("asd");
   
   ```

3. 重载

   ```typescript
   //类方法重载
   interface AS {
       hello(x: string): number;
       hello(x: number): string;
   }
   class AA implements AS{
       hello(x: string): number;
       hello(x: number): string;
       hello(x: string | number): number | string {
           return undefined;
       }
   }
   //函数重载
   function as(x: number): number;
   function as(x: string): number;
   function as(x: number | string): number {
       return 1;
   }
   ```

4. 引入声明文件(xx.d.ts文件)

   ```typescript
   ///<reference path="a.d.ts"/>
   const x = 12 === AEnum.age;
   console.log(x);
   ```

   > tsconfig中配置可以统一引入指定目录的声明文件
   >
   > 在.d声明文件中定义任何东西都需要使用`declare namescpe xxx{}`表示声明一个类型

   **声明文件常用于为一些非ts库提供api**

   ```typescript
   //some-lib.js
   exports.sayTest = function sayTest(n) {
       return +n;
   }
   //some-lib.d.ts
   export declare function sayTest(n: string): number;
   
   //test.ts
   ///<reference path="a.d.ts"/>
   import {sayTest} from "./some-lib";
   console.log(sayTest("22")); //22
   
   ```