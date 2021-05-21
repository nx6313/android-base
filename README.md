# nxx-android-base

![](https://img.shields.io/badge/%E6%9C%80%E6%96%B0Tag%E5%80%BC-v3.2.0-orange)

## 如何使用

### Step 1. Add the JitPack repository to your build file
###### Add it in your root build.gradle at the end of repositories:
    allprojects {
        repositories {
            ...
            maven { url 'https://jitpack.io' }
        }
    }

### Step 2. Add the dependency
    dependencies {
        implementation 'com.github.nx6313:nxx-android-base:Tag'
    }
    
## 请开启 dataBinding 与 viewBinding
    android {
        ...
        buildFeatures {
            dataBinding = true
            viewBinding = true
        }
        ...
    }
    
## Activity 创建规则方式

##### 示例代码
    class MainActivity : BaseActivity<ActivityMainBinding>(ActivityMainBinding::inflate) {

        override fun createFinish() {
        }
    }
> 说明：正常创建好 Activity 文件后，将继承类改为 BaseActivity 即可。范型需指定当前 activity 页面的 ViewBinding 对象。父类 BaseActivity 接受两个参数，第一个参数为当前页面的 inflate、第二个参数为页面状态栏信息文字的颜色，Boolean 类型 [ true: 黑色文字、false: 白色文字 ]（可不传，默认值为：true）

## 配置沉浸式状态栏

> 默认已集成沉浸式状态栏，你只需要将 manifests 中的 application 主题配置为以下即可。
```java
android:theme="@style/Theme.AndroidBase"
```
> Activity 创建好并添加以上主题后，页面呈现将为全屏。即页面整体内容将延伸至状态栏。如果需要页面标题栏，请在页面根布局或适当位置使用 StatusBarHeightView 组件，其目的是显出状态栏的位置
> StatusBarHeightView 组件的属性有：use_type [enum 可选值：use_height、use_padding_top]、title_bar_color [color 标题栏颜色，默认白色]、main_bg_color [color 页面主体颜色，默认透明]、title_bar_show_shadow [boolean 是否显示标题栏底部阴影，默认 false]
```java
com.nx.androidbase.widget.StatusBarHeightView
```

## 分包 配置 MultiDex

##### 如果 minSdkVersion 为 21 或更高值，只需在 defaultConfig 中加入 multiDexEnabled true 即可
    defaultConfig {
        ...
        multiDexEnabled true
    }
##### 如果minSdkVersion 为 20 或更低值
1. 在 defaultConfig 中加入 multiDexEnabled true
```java
defaultConfig {
    ...
    multiDexEnabled true
}
```
2. 添加依赖
```java
implementation 'com.android.support:multidex:1.0.3'
```
3. Application 继承 MultiDexApplication 或者 在 Application 中添加 MultiDex.install(this)

## 请加入如下依赖项
    implementation 'com.qmuiteam:qmui:2.0.0-alpha10'
    implementation "org.jetbrains.anko:anko:0.10.8"
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.2.0")
    implementation("androidx.lifecycle:lifecycle-common-java8:2.2.0")
    implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:2.2.0")
    implementation("androidx.lifecycle:lifecycle-livedata-ktx:2.2.0")
    implementation 'com.facebook.rebound:rebound:0.3.8'
    implementation 'com.airbnb.android:lottie:3.4.2'
    implementation 'com.blankj:utilcode:1.10.0'
    implementation 'com.hjq:toast:8.8'
    implementation 'com.orhanobut:logger:2.2.0'
    implementation "com.squareup.retrofit2:retrofit:2.9.0"
    implementation "com.squareup.retrofit2:converter-gson:2.9.0"
    implementation "com.squareup.retrofit2:adapter-rxjava2:2.9.0"
    implementation('com.github.ihsanbal:LoggingInterceptor:3.0.0') {
        exclude group: 'org.json', module: 'json'
    }
    implementation 'com.squareup.okhttp3:okhttp:3.14.9'
    implementation 'io.reactivex.rxjava2:rxjava:2.2.5'
    implementation 'io.reactivex.rxjava2:rxandroid:2.1.0'
    implementation 'com.youth.banner:banner:2.1.0'
    implementation 'com.github.bumptech.glide:glide:4.10.0'
    implementation 'org.greenrobot:eventbus:3.1.1'
