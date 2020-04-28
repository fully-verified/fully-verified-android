# Fully Verified library documentation - Android

## 1. Project configuration

The first step is to set the value at least to `minSdkVersion=21` in file `build.gradle`

### Adding dependencies

In the Android Studio environment, it is possible to add a library module by using the command: „File → New → New module...”. From the list „New module” select „Import .JAR or .AAR Package” and click „Next”. In the field „File name” provide access path to file `com.fully_verified-fullyverifiedsdk-1.36.2-release.aar`. As a „Subproject name”, provide „fullyverifiedsdk” and click „Finish”.

The next step is to add a dependency to the created library module by modifying the file `build.gradle` and placing the following entry in the section „dependencies”:

`compile project(':fullyverifiedsdk')`

Since the library uses the AndroidX library and other, the following dependency must be added:

```gradle

dependencies {
	//other dependencies
    implementation project(':fullyverifiedsdk')
    implementation "androidx.core:core:1.1.0"
    implementation "androidx.core:core-ktx:1.1.0"
    implementation "androidx.legacy:legacy-support-v4:1.0.0"
    implementation "androidx.appcompat:appcompat:1.1.0"
    implementation "androidx.preference:preference:1.1.0"
    implementation "androidx.recyclerview:recyclerview:1.1.0"
    implementation "androidx.vectordrawable:vectordrawable:1.0.0"
    implementation "androidx.annotation:annotation:1.0.0"
    implementation "androidx.constraintlayout:constraintlayout:1.1.3"
    implementation "androidx.cardview:cardview:1.0.0"
    implementation "androidx.viewpager:viewpager:1.0.0"
    implementation "com.firebase:firebase-jobdispatcher:0.8.5"
    implementation "com.google.android.material:material:1.0.0"
    implementation "com.google.code.gson:gson:2.8.5"
    implementation "com.romandanylyk:pageindicatorview:1.0.3"
    implementation "com.squareup.okhttp3:okhttp:3.14.0"
    implementation "com.squareup.okhttp3:logging-interceptor:3.14.0"
    implementation "com.squareup.retrofit2:retrofit:2.5.0"
    implementation "com.squareup.retrofit2:converter-gson:2.5.0"
    implementation "com.squareup.retrofit2:adapter-rxjava2:2.5.0"
    implementation "com.twilio:video-android:5.1.0"
    implementation "io.sentry:sentry-android:1.7.16"
    implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:1.3.61"
    implementation "org.koin:koin-android:2.0.0-beta-1"
    implementation "org.koin:koin-androidx-scope:2.0.0-beta-1"
    implementation "org.koin:koin-androidx-viewmodel:2.0.0-beta-1"
    implementation "org.koin:koin-java:2.0.0-beta-1"
    implementation "io.reactivex.rxjava2:rxjava:2.2.0"
    implementation "io.reactivex.rxjava2:rxkotlin:2.3.0"
    implementation "io.reactivex.rxjava2:rxandroid:2.1.0"
    implementation "com.tbruyelle.rxpermissions2:rxpermissions:0.9.4"
    implementation "com.github.bumptech.glide:glide:4.9.0"
}

```

### Proguard

The following entry should be added to the proguard file:

```proguard
# FullyVerifiedSDK rules
-keep class com.fully_verified.fullyverifiedsdk.model.** { *; }
-keepclassmembers class com.fully_verified.fullyverifiedsdk.model.** { *; }
-keep class tvi.webrtc.** { *; }
-keep class com.twilio.video.** { *; }
-keepattributes InnerClasses
```

### Definition of AndroidManifest file

Add the following to `AndroidManifest.xml` file:

```xml
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.FLASHLIGHT" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```

Next, in `application` section, add `TransferActivity`:

```xml
        <activity
            android:name="com.fully_verified.fullyverifiedsdk.activities.FullyVerified"
            android:configChanges="orientation"
            android:screenOrientation="sensorPortrait"/>

        <activity
            android:name="com.fully_verified.fullyverifiedsdk.opsless.view.FullyVerified"
            android:configChanges="orientation"
            android:screenOrientation="sensorPortrait"/>
```
