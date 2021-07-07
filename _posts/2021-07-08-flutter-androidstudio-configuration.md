---
layout: single
title: Flutter Setting for Android Studio
categories: Flutter
tags: Flutter, AndroidStudio
toc: true  
toc_sticky: true
---



Android Studio에서 Flutter를 Setting하기 위해서는...

1. Flutter 를 download 하고 원하는 설치 folder에 압축을 푼다.
2. 압축이 풀린 Flutter folder에서 flutter _console.bat 파일을 찾아서 실행한다.
3. Flutter의 설치 상태를 확인하기 위하여 Commnad prompt에서 아래와 같이 flutter doctor 를 입력한다.

![flutterdoctor](https://github.com/nacallmania/nacallmania.github.io/blob/master/images/flutterdoctor.png)



4. 위 그림과 같이 Unable to locate Android SDK가 나타나는 경우는 flutter가 Android SDK 가 설치된 folder 위치를 알 수 있도록 설정해 주면 된다.   

   flutter config --android-studio-dir=폴더 위치 

![flutterdoctor2](https://github.com/nacallmania/nacallmania.github.io/blob/master/images/flutterdoctor2.png)

5. Android SDK위치를 설정한 후에도 Android license 오류가 발생할 수 있다. 이 경우는 flutter doctor --android-licenses를 실행하면 된다. 

   ![flutterdoctor3](https://github.com/nacallmania/nacallmania.github.io/blob/master/images/flutterdoctor3.png)

   그런데 이렇게 해도 여전히 license 오류가 발생하는 경우도 있다.  

   이 것은 Android SDK의 Tool 중에 Android SDK Command-line Tools가 설치되지 않은 경우일 수 있다. 따라서 

   Android Studio의 Setting의 Android SDK -> SDK Tools에서 Android SDK Command-line Tools 를  check해 주면 된다.

   이제 flutter doctor --android-licenses를 다시 실행해 보자.

   
