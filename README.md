# Tack  [![](https://jitpack.io/v/kayoSun/Tack.svg)](https://jitpack.io/#kayoSun/Tack) [![](https://github.com/kayoSun/resource/blob/master/svgs/apachelicense.svg)](LICENSE.txt)


Tack是一款简单、快捷、轻量级的Bundle数据注入和存储的扩展框架

使用Tack，你可以实现：

1. 从Bundle\Intent读取常用数据类型数据
2. 向Bundle\Intent存入常用数据类型数据
3. 从Bundle\Intent读取数据并注入到Activity中的变量
4. 从Bundle\Intent读取数据并注入到Fragment中的变量
5. 通过工厂更方便的创建Bundle，避免硬编码

## 依赖

> 添加JitPack仓库

```Groovy
maven { url 'https://jitpack.io' }
```

> 添加依赖

```Groovy
dependencies {
	annotationProcessor 'com.github.kayoSun.Tack:tackprocessor:${lastversion}'
	implementation 'com.github.kayoSun.Tack:tackapi:${lastversion}'
}
```
## 混淆配置
```Proguard
-keep class com.kayo.lib.tack.annos.**
-keep class * extends com.kayo.lib.tack.api.ITackImpl
-keepclasseswithmembernames class * {
    @com.kayo.lib.tack.annos.* <fields>;
}
```

## 使用

### 1.为Activity变量注入数据，可以设置key,如果不设置key，则取变量名
```java
public class MainActivity extends AppCompatActivity {

    //注入数据，key为agr1
    @Paste
    String agr1;

    //注入数据，key为您指定的name
    @Paste("name")
    String agr2;

    @Inject//注入数据
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```
### 2.Fragment同Acticity
```java
public class MainFragment extends Fragment {

    //注入数据，key为agr1
    @Paste
    String agr1;

    //注入数据，key为您指定的name
    @Paste("name")
    String agr2;

    @Inject//注入数据
    @Override
    public void onViewCreated(@NonNull View view, @Nullable Bundle savedInstanceState) {
       super.onViewCreated(view, savedInstanceState);
    }
}

```
### 3.您可以用指定数据类型注解，可以设置默认值
支持的注解

| Annotation   |   Data Type |
|--------------|-------------|
| PasteB       |   byte      |
| PasteD       |   double    |
| PasteF       |   float     |
| PasteI       |   int       |
| PasteL       |   long      |
| PasteS       |   String    |
| Paste        |   any       |

```java
public class MainActivity extends AppCompatActivity {

    //指定String类型注解，默认值为abc
    @PasteS(defaultVar = "abc")
    String agr1;

    ... ...
}
```





##  Gradle版本注意事项

| Tack version | Android Projects |
|--------------|------------------|
| 0.0.2        | Gradle 4.6       |
| 0.0.3        | Gradle 4.6       |
| 1.0.0        | Gradle 6.+       |


## 联系作者

欢迎提issue<br>


## License
```
Copyright 2018 Kayo

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
