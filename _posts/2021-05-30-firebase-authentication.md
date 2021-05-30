---
layout: single
title: Firebase Authentication - (1)
categories: Firebase
tags: Firebase Authentication
toc: true  
toc_sticky: true
---

앱에서 사용자의 신원 관리가 필요한 경우에 사용자 인증 기능이 필요하다.
이를 쉽게 구현하기 위해서 Firebase가 제공하는 인증 기능을 살펴본다.

Firebase 는 크게 2가지 인증 방법을 제공하는데...
FirebaseUI 인증을 사용하는 방법과 Firebase SDK를 사용하는 방법이 있다.

FirebaseUI 인증은 e-mail과 password, 전화번호 인증은 물론이고 Google, Facebook, Twitter을 비롯한 인기있는 ID 제공 업체를 이용한 사용자의 Login UI workflow를 제공한다.
FirebaseUI 인증은 ID 제공업체에서 정의한 UI/UX가 이미 정해져 있으므로 개발자의 요구에 맞지 않는 경우가 있을 수 있다.
이런 경우에는 Firebase SDK를 사용하여 Customize가 가능하다.
Firebase SDK를 이용하는 경우에 FirebaseUI가 제공하는 모든 기능과 더불어 익명 인증을 제공할 수 있지만 실제 구현 작업이 다소 번거롭다.

Firebase에 project로 등록한 앱은 사용자 등록을 통해 사용자 정보를 관리할 수가 있다.
신규 사용자를 생성하는 경우에는 createUserWithEmailAndPassword 메서드를 호출하여 생성하는 방법과 
ID 제공 업체를 통한 사용자 최초 Login 인증 처리시에 자동으로 사용자가 등록되는 방법이 있다.

인증이 정상적으로 이루어진 경우에는 사용자의 기본 profile 정보가 Firebase에 저장되고
Firebase Console -> Authentication -> Users tab에서 확인이 가능하다.
사용자의 인증 정보는  e-mail과 password 일 수도 있고 ID 제공 업체로부터 받은 OAuth 토큰 일 수도 있다.
Login이 전상적으로 이루어진 후에는 User profile 정보에 access 가능하고 Firebase 에 저장된 data에 대한 사용자 access 권한을 제어할 수 있다.

참고 : [Firebase에서 사용자 관리](https://firebase.google.com/docs/auth/android/manage-users?hl=ko)



