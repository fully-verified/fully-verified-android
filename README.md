# Fully Verified library documentation - Android

## 1. Project configuration

The first step is to set the value at least to `minSdkVersion=21` in file `build.gradle`

### Adding dependencies

Create `libs` folder in project root directory.

Unzip fullyverifiedsdk-1.48.4.zip in the already created `libs` folder.

Next in project `build.gradle` file in section allprojects -> repositories add local maven repository.
```gradle
maven { url file("${rootProject.projectDir}/libs") }
```

Whole section should be similar to this:
```
allprojects {
    repositories {
        google()
        jcenter()
        maven { url file("${rootProject.projectDir}/libs") }
    }
}
```

The next step is adding a dependency to application module:

```gradle
    implementation "com.fully_verified:fullyverifiedsdk:1.48.4"
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
