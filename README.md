# android_studio
Android Studio w/ Java

### 1.설치 과정

    JDK 17 선택
 
<img width="914" alt="스크린샷 2022-04-26 오전 10 05 09" src="https://user-images.githubusercontent.com/49167217/165226753-69a5a302-51b3-4146-b169-3de03c6866f6.png">
    
    Dependencies 1. BootstrpFX 2. ControlsFX 선택
<img width="914" alt="스크린샷 2022-04-26 오전 10 05 17" src="https://user-images.githubusercontent.com/49167217/165226770-b6a5de4a-25d1-4457-a839-9223b27b05f8.png">
    
    SDK Platform 다운로드 (Android Tiramisu / API 32 / 12)
<img width="1094" alt="스크린샷 2022-04-26 오후 2 22 34" src="https://user-images.githubusercontent.com/49167217/165227624-a007b423-3f92-40c5-a3e1-274ed5b3965a.png">
    
    SDK Tools 다운로드 (Android Emulator / Android SDK Platform-Tools/ Google Play services)
<img width="1094" alt="스크린샷 2022-04-26 오후 2 22 41" src="https://user-images.githubusercontent.com/49167217/165227637-401bd510-257b-4133-8b3c-702298e0785a.png">

    Emulator API 32 / R 다운로드
<img width="1440" alt="스크린샷 2022-04-26 오전 11 42 25" src="https://user-images.githubusercontent.com/49167217/165226779-f7274461-f9c0-490f-9d41-aa01f0d52a1b.png">

### 2.webView 연결

#### 1) activity_main.xml 파일에 webView 컴포넌트 추가

#### 2) MainActivity.java 에 컴포넌트 연결
```java
package com.kbstar.helloandroid;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.webkit.WebSettings;
import android.webkit.WebView;

public class MainActivity extends AppCompatActivity {

    WebView webView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        webView = findViewById(R.id.webView);

        WebSettings webSettings = webView.getSettings();
        webSettings.setJavaScriptEnabled(true);

        webView.loadUrl("http://www.kbstar.com");
    }
}
```

<img width="1440" alt="스크린샷 2022-04-26 오후 1 46 43" src="https://user-images.githubusercontent.com/49167217/165226785-b586377e-cabd-4540-90c3-7d86478920fa.png">

#### 3. AndroidManifest.xml 설정 변경
    AndroidManifest.xml은 모든 안드로이드 프로그램을 관장하는 파일이다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.kbstar.helloandroid">
    <!--인터넷 접속 허용 설정-->
    <uses-permission android:name="android.permission.INTERNET"/>

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"

        android:usesCleartextTraffic="true"

        android:theme="@style/Theme.HelloAndroid">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
