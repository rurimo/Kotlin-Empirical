# Why-Kotlin
Why should we migrate codes from Java to Kotlin? <br>
Helping research related to An Empirical Study on Quality of Android Applications written in Kotlin language.

![screenshot339785535](https://user-images.githubusercontent.com/27774870/75983478-f95bd900-5f2b-11ea-92b8-a04c358101b9.png) <br>
You can check more details [here](https://arxiv.org/abs/1808.00025) by Bruno Gois Mateus, Matias Martinez professor in France.


## 1. Functional programming

Functions in Kotlin are first-class values. It means they can be assigned to variables and passed around as parameters. <br>
This is one of the most powerful benefits of Kotlin and It took FP paradigms like modern languages: __Immutability__ 
<br>We can predict unpredictable conditions and data flow via immutability and pure functions. 
check [here](https://sidburn.github.io/blog/2016/03/14/immutability-and-pure-functions) <br>

This brings amazing stability and scalability for maintaining the application. <br>
And the other case, It provides beautiful flexibility from SDK and the Library developer's point.<br>
For example, a functionality "A" executes something blabla in the library scope.<br>
And an application has a dependency on the library, we want to do something "B" method after executes functionality "A".<br><br>

Then we can express it like this: A(B) <br>
It can't happen in OOP paradigms, the function "B" will be executed in functionality "A".<br>
So the function can pre/post-processing another function.<br>
This example validates it.
https://github.com/skydoves/Balloon/blob/master/balloon/src/main/java/com/skydoves/balloon/Balloon.kt#L500 <br>

The `setOnBalloonClickListener` doesn't need to get an interface (listener) as a parameter.<br>
It only takes a function and it will be executed when the listener is invoked.

## 2. Null Safety
Here is another of the powerful benefit of Kotlin: __Null Safety__ <br> 
Kotlin provides null safety, so as you know it prevents NullPointerException.<br>
One of the most important things to client developers, the application should never die. (crash)<br>
When an app dies, many users will complain and the quality of the service will be poor.

Via null safety, If the application got some crash, we can give users another chance to refresh the app and re-fetching data from network or database instead of just killing the app.<br>
This is a much attractive thing for client developers and backend developers. 

## 3. Extensions
Kotlin provides the ability to extend a class with new functionality without having to inherit from the class or use design patterns such as Decorator. This is done via special declarations called extensions. Kotlin provides extensions. <br><br>

In Java, we always made like what xxxUtils classes.<br>
But in Kotlin, we can create a class-based scoped function (extension function).<br>
For example, we want to change an integer value to time formatted string value.<br>
In Java, we should create a class, and write some functions in the class like this: 

```java
class TimeUtils {

   public static String intToTimeFormatString(Int value) {} 

}

```

We will use them like this:
```java
TimeUtils.intToTimeFormatString(myIntVariable)
```

In Kotlin, we don't need to create a class, and just write an extended function of Int.
```kt
Int.intToTimeFormatString(): String { }
```
 
We will use them like this:
```kt
myIntVariable.intToTimeFormatString() 
```
We can reduce so many repetitive and boilerplate codes.


## 4. Operator overloading 

```
Kotlin allows us to provide implementations for a predefined set of operators on our types.
These operators have fixed symbolic representation (like + or *) and fixed precedence.
```

We can overload previous operators like + or * and fixed precedence. This allows us to deal with variables much more flexibly. More, Kotlin could save functions to variables, so it means we can deal with functions much more flexibly. And Koltin already provides many kinds of operator overloaded extensions like kotlin.math pacakge. (https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.math/index.html)
<br>
The coroutines that asynchronous or non-blocking programming provided by language level already use it. 

```kt
val job = launch(Dispatchers.Default + threadLocal.asContextElement(value = "launch")) {

    println("Launch start, current thread: ${Thread.currentThread()}, thread local value: '${threadLocal.get()}'")

    yield()

    println("After yield, current thread: ${Thread.currentThread()}, thread local value: '${threadLocal.get()}'")
}

job.join()
```


## 5. Supports in Language Level 

In Android Programming, asynchronous is one of the most important things between developers. Android application task basically draws UI related things on the main thread, so we must handle many tasks asynchronously that is not related to UI like fetching data from network and database. Kotlin supports Coroutines in language level and we can return multiple asynchronously computed values via Flow.<br>

Moreover, Kotlin provides Android Extensions.<br>
Every Android developer using Java knows well the `findViewById()`.<br>

The function creates real boilerplate codes and many kinds of bugs because of unsafe typecasting.The Kotlin Android Extensions plugin allows us to obtain the same experience we have with some of these libraries, without having to add any extra code.

```kt
// Using R.layout.activity_main from the 'main' source set

import kotlinx.android.synthetic.main.activity_main.*

class MyActivity : Activity() {

    override fun onCreate(savedInstanceState: Bundle?) {

        super.onCreate(savedInstanceState)

        setContentView(R.layout.activity_main)

        

        // Instead of findViewById<TextView>(R.id.textView)

        textView.setText("Hello, world!")

    }

}
```

textView is an extension property for Activity, and it has the same type as declared in activity_main.xml (so it is a TextView).

# License
```
Designed and developed by 2020 rurimo

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
