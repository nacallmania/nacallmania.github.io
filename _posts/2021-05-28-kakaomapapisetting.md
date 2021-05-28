---
layout: single
title: KAKAO MAP API 설정 -  Android Native App
---

KAKAO 지도 API를 사용하기 위한 설정은 다음 위치에서 설명하고 있다. https://apis.map.kakao.com/android/guide/ 

잊어 버릴 수 있으니 좀 더 간단히 요약해 둔다.



1. kakao Map SDK 를 download 한다. https://apis.map.kakao.com/download/android/sdk/Android_DaumMap_SDK_1.4.1.0.zip

2. SDK file의 압축을 풀면 

   - libDaumMapAndroid.jar 파일과 3개의 so 파일이 있을 것이다.
   - libDaumMapAndroid.jar 파일은 libs folder 아래에 복사한다.
   - 나머지 folder는 main folder 아래에 jniLibs folder 를 만들고 아레에 복사한다.

3. AndroidManifest.xml 에 Permission 과 APP KEY를 추가한다.

   ```xml
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
   ```

```xml
	Application Tag 안에는
    <meta-data android:name="com.kakao.sdk.AppKey" android:value="6d5e7f6d5dc5fb3cdbf0bd62540b4244"/>     
```

4. kakao 개발자 사이트(https://developers.kakao.com)에서 현재 작성하고 있는 APP을 등록한다.

   - 위의 App Key value는 App을 등록하고 얻은 **네이티브 키**이다.

   - 또한 플랫폼을 Android로 등록해야 하는데 **키 해시**를 입력하는 부분이 있다.

   - 키 해시를 얻는 부분이 번거로우므로 아래의 class를 만들고 Activity 의 생성부에서 호출하여 키 해시 값을 얻도록 하자.

     ```java
     import android.content.Context;
     import android.content.pm.PackageInfo;
     import android.content.pm.PackageManager;
     import android.content.pm.Signature;
     import android.util.Base64;
     import android.util.Log;
     
     import java.security.MessageDigest;
     import java.security.NoSuchAlgorithmException;
     
     public class HashKeyHelper {
         public String getHashKey(Context context) {
             PackageInfo packageInfo = null;
             try {
                 packageInfo =  context.getPackageManager().getPackageInfo(context.getPackageName(), PackageManager.GET_SIGNATURES);
             } catch (PackageManager.NameNotFoundException e) {
                 e.printStackTrace();
             }
             if (packageInfo == null)
                 Log.e("KeyHash", "KeyHash:null");
     
             for (Signature signature : packageInfo.signatures) {
                 try {
                     MessageDigest md = MessageDigest.getInstance("SHA");
                     md.update(signature.toByteArray());
                     String hashstr = Base64.encodeToString(md.digest(), Base64.DEFAULT);
                     Log.d("KeyHash", hashstr);
                     return hashstr;
                 } catch (NoSuchAlgorithmException e) {
                     Log.e("KeyHash", "Unable to get MessageDigest. signature=" + signature, e);
                 }
             }
             return "";
         }
     }
     ```

​			

```
```

