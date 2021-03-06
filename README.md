# Android Architecture Components

Android 官方 MVVM

https://developer.android.google.cn/topic/libraries/architecture/index.html

## 注意事项

1. androidx 和 android.support 库无法兼容，[android.support 过渡到 androidx 的方法](https://blog.csdn.net/u014644594/article/details/85095831)
2. minSdkVersion >= 24, compileSdkVersion >= 28

## 依赖原文

Futures (found in androidx.concurrent)

``` gradle
dependencies {
    def futures_version = "1.0.0-alpha02"

    implementation "androidx.concurrent:concurrent-futures:$futures_version"
}
```

Lifecycle components (including ViewModel)

``` gradle
dependencies {
    def lifecycle_version = "2.0.0"

    // ViewModel and LiveData
    implementation "androidx.lifecycle:lifecycle-extensions:$lifecycle_version"
    // alternatively - just ViewModel
    implementation "androidx.lifecycle:lifecycle-viewmodel:$lifecycle_version" // For Kotlin use lifecycle-viewmodel-ktx
    // alternatively - just LiveData
    implementation "androidx.lifecycle:lifecycle-livedata:$lifecycle_version"
    // alternatively - Lifecycles only (no ViewModel or LiveData). Some UI
    //     AndroidX libraries use this lightweight import for Lifecycle
    implementation "androidx.lifecycle:lifecycle-runtime:$lifecycle_version"

    annotationProcessor "androidx.lifecycle:lifecycle-compiler:$lifecycle_version" // For Kotlin use kapt instead of annotationProcessor
    // alternately - if using Java8, use the following instead of lifecycle-compiler
    implementation "androidx.lifecycle:lifecycle-common-java8:$lifecycle_version"

    // optional - ReactiveStreams support for LiveData
    implementation "androidx.lifecycle:lifecycle-reactivestreams:$lifecycle_version" // For Kotlin use lifecycle-reactivestreams-ktx

    // optional - Test helpers for LiveData
    testImplementation "androidx.arch.core:core-testing:$lifecycle_version"
}
```

Navigation (including SafeArgs)

``` gradle

buildscript {
    repositories {
        google()
    }
    dependencies {
        classpath "androidx.navigation:navigation-safe-args-gradle-plugin:2.1.0-alpha01"
    }
}

apply plugin: "androidx.navigation.safeargs"

dependencies {
    def nav_version = "2.1.0-alpha01"

    implementation "androidx.navigation:navigation-fragment:$nav_version" // For Kotlin use navigation-fragment-ktx
    implementation "androidx.navigation:navigation-ui:$nav_version" // For Kotlin use navigation-ui-ktx
}
```

Paging

``` gradle
dependencies {
    def paging_version = "2.1.0"

    implementation "androidx.paging:paging-runtime:$paging_version" // For Kotlin use paging-runtime-ktx

    // alternatively - without Android dependencies for testing
    testImplementation "androidx.paging:paging-common:$paging_version" // For Kotlin use paging-common-ktx

    // optional - RxJava support
    implementation "androidx.paging:paging-rxjava2:$paging_version" // For Kotlin use paging-rxjava2-ktx
}
```

Room

``` gradle
dependencies {
    def room_version = "2.1.0-alpha06"

    implementation "androidx.room:room-runtime:$room_version"
    annotationProcessor "androidx.room:room-compiler:$room_version" // For Kotlin use kapt instead of annotationProcessor

    // optional - Kotlin Extensions and Coroutines support for Room
    implementation "androidx.room:room-ktx:$room_version"

    // optional - RxJava support for Room
    implementation "androidx.room:room-rxjava2:$room_version"

    // optional - Guava support for Room, including Optional and ListenableFuture
    implementation "androidx.room:room-guava:$room_version"

    // Test helpers
    testImplementation "androidx.room:room-testing:$room_version"
}
```

WorkManager

> Note: WorkManager requires compileSdk version 28 or higher.

``` gradle
 dependencies {
    def work_version = 2.0.0

    // (Java only)
    implementation "androidx.work:work-runtime:$work_version"

    // Kotlin + coroutines
    implementation "androidx.work:work-runtime-ktx:$work_version"

    // optional - RxJava2 support
    implementation "androidx.work:work-rxjava2:$work_version"
    // optional - Test helpers
    androidTestImplementation "androidx.work:work-testing:$work_version"
  }
```