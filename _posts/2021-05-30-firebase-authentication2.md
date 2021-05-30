---
layout: single
title: Firebase Authentication - (2)
categories: Firebase
tags: Firebase Authentication
toc: true  
toc_sticky: true
---
	

**Authentication/Login Activity - FirebaseUI( Google ) Example**

Firebase로 Google SignIn기능을 사용하기 위해서는 먼저 다음 과정이 필요하다.
1. [Firebase에 App project 등록](https://firebase.google.com/docs/android/setup?hl=ko)
2. Firebase Authentication 설정
  - Firebase의 console에서 project를 선택한 후 왼쪽 navigation에서 Authentication을 선택한다.
  - 만약 Google login을 사용하려면 "Sign-in method" tab에서 Google을 사용상태로 설정한다.
  - [SHA-1 설정](https://nacallmania.github.io/firebase/gradle-sha1/)
3. Project 수준 build.gradle 설정
  - dependency에 classpath 'com.google.gms:google-services:4.3.8' 추가
  - repositories에 google() 추가
4. [모듈 수준 build.gradle 설정](https://firebase.google.com/docs/auth/android/google-signin?hl=ko)

**Google Login을 위한 Activity의 간단 예제**
```java
// Firebase authentication기능을 사용하기 위해
private FirebaseAuth firebaseAuth = null;
// Google Sign In API를 call하기 위한 client
private GoogleSignInClient googleSignClient;
private static final int RC_SIGN_IN = 9001;
// Google Sign In Button
private SignInButton signInButton;

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_login);

    signInButton = findViewById(R.id.signInButton);

    GoogleSignInOptions signOpt = new GoogleSignInOptions.Builder(GoogleSignInOptions.DEFAULT_SIGN_IN)
            .requestIdToken(getString(R.string.default_web_client_id))
            .requestEmail()
            .build();

    googleSignClient = GoogleSignIn.getClient(this, signOpt);
    firebaseAuth = FirebaseAuth.getInstance();

    signInButton.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            SignIn();
        }
    });
}

private void SignIn() {
    Intent signInIntent = googleSignClient.getSignInIntent();
    startActivityForResult(signInIntent, RC_SIGN_IN);
}

// 로그 아웃을 위해 사용
private void SignOut() {
    FirebaseAuth.getInstance().signOut();
}

// 회원 탈퇴를 위해 사용
private void DeleteAccount() {
    firebaseAuth.getCurrentUser().delete();
}

// SignIn()의 startActivityForResult 의 결과
@Override
public void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);

    if (requestCode == RC_SIGN_IN) {
        Task<GoogleSignInAccount> task = GoogleSignIn.getSignedInAccountFromIntent(data);
        try {
            GoogleSignInAccount account = task.getResult(ApiException.class);
            AuthWithGoogleAccount(account);
        } catch (ApiException e) {
        }
    }
}

private void AuthWithGoogleAccount(GoogleSignInAccount acct) {

    AuthCredential credential = GoogleAuthProvider.getCredential(acct.getIdToken(), null);
    firebaseAuth.signInWithCredential(credential)
            .addOnCompleteListener(this, new OnCompleteListener<AuthResult>() {
                @Override
                public void onComplete(@NonNull Task<AuthResult> task) {
                    FirebaseUser usr = firebaseAuth.getCurrentUser();
                    if (task.isSuccessful() && usr != null) {
                        String name = usr.getDisplayName();
                        String email = usr.getEmail();
                        Uri photoUrl = usr.getPhotoUrl();
                        Toast.makeText(getBaseContext(), "로그인 성공", Toast.LENGTH_SHORT).show();
                    } else {
                        Toast.makeText(getBaseContext(), "로그인 실패", Toast.LENGTH_SHORT).show();
                    }

                }
            });
}
```

