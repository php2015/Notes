

1.函数 和 变量的声明会被前置   函数表达式可以匿名 和 立即调用

2.命名函数表达式 用的少
3.function 构造器 用的少
var func = new function('a','b','console(a+b);')
func(1,2); // 3

                            !   !   !   !   !                < -- 全局的this -- >           !   !   !   !   !

            this === window     // true   this.document === document    // true 

                            !   !   !   !   !                < -- 一般函数的this -- >           !   !   !   !   !

                function f1(){
                    return this;       
                }
            //f1() === window // true , global object (node中的指向)
            //严格模式下 f1() === undefined // true

                            !   !   !   !   !                < -- 作为对象方法的函数的this -- >           !   !   !   !   !
            
                var o = {
                    prop: 37,
                    f: function() {
                        retuen this.prop;   (此处的this 指向o)
                    }
                }
                //console.log(o.f());     //logs 37   只要将函数作为对象的方法 像 o.f() 这样调用的话 this就会指向对象

                            !   !   !   !   !                < -- 对象原型链上的this -- >           !   !   !   !   !
            
                var o = {f: function(){ return this.a + this.b; } };
                var p = object.create(o);  //创建一个新对象，使用现有的对象来提供新创建的对象的__proto__。 p的原型指向o
                p.a = 1;
                p.b = 4;
                console.log(p.f()); //5
                //p的原型链上的o的this 仍然可以拿到p     

                            !   !   !   !   !                < -- 构造器中的this -- >           !   !   !   !   !

                function MyClass(){
                    this.a = 37;   //(此时此刻this指向window)
                }

                var o = new MyClass();  //(如果把他用作构造器 此时他的this指向空对象 空对象的原型是MyClass.prototype) 
                                        //此处this作为返回值 如果return了一个对象会将对象作为返回值
                console.log(o.a);       //37 (o上有一个属性a)


                函数属性 & arguments

                // foo.name - 函数名  !  foo.length - 形参个数   !    arguments.length - 实参个数
                function foo(x,y,z){

                }

                //arguments 是个类数组 
                arguments.callee 属性包含当前正在执行的函数 严格模式下禁止使用
                arguments[0] = 10; 会修改x为10 严格模式下无法修改  
                arguments[2] = 100; 如果z 没传参数的话 修改是失效的，是没有绑定关系的

                < -- bind 与 new -- >           !   !   !   !   !

            function foo() {
                this.b = 100;
                return this.a;
            }
            var func = foo.bind({a:1});

            func();     // 1
            new func(); // {b : 100}    用 new  如果 return不是对象的话 会返回this 一个空对象指针 空对象原型是foo.prototype

            1、谁最终调用函数，this最终指向谁(记住！)
                ①this指向谁，不应考虑函数在哪声明，而应该考虑函数在哪调用！！！
                ②this指向的永远只可能是对象，而不可能是函数。
                ③this指向的对象，叫做函数的上下文context，也叫函数的调用者。


                2、this指向的规律！！！(跟函数的调用方式息息相关，记住这点，相信你一定会分清this指向哒)
                ①通过函数名()调用的，this永远指向window
                ②通过对象.方法调用的，this指向这个对象。
                ③函数作为数组中的一个元素，用数组下标调用的，this指向这个数组
                ④函数作为window内置函数的回调函数使用，this指向window。
                setInterval setTimeout 等。
                ⑤函数作为构造函数，使用new关键字调用，this指向新new出的对象 对象的原型等于构造器的prototype属性

                < -- 模拟 bind 方法 -- >           !   !   !   !   !
            看bind方法模拟.html    
        