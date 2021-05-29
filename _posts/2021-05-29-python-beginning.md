---
layout: single
title: Python을 배워 볼까?
categories: Python
tags: PyCharm VSCode Colab Jupyterlab
# 목차
toc: true  
toc_sticky: true 
---

#### **무엇을 설치할까?**

당연히 Python 공식 홈페이지에서 Python 최신 버전을 받아서 설치해야지.

IDE는 뭘 사용하지?

- **PyCharm** : JetBrains에서 만들었고 많은 기능이 있으며 다 좋은데...
- **Jupyter Notebook, JupyterLab** : Open Source 이며 계속 진화중
- **Colab** : Google에서 만든 Jupyter Notebook의 Cloud 버전쯤 되겠다
- **Visual Studio Code** : MS에서 제공하는 tool중에는 이게 제일 가볍고 쓰기 쉽지 않을까... 



**PyCharm**(https://www.jetbrains.com/ko-kr/pycharm/features/editions_comparison_matrix.html)

PyCharm은 Professional 과 Community 버전으로 나뉜다.

Cummunity버전만 사용해도 당연히 배우는 입장에서는 무리가 없지만 프로젝트를 진행하다보면 실제로 Test를 위한 Code Coverage 나 Profiler등이 필요하니 돈 들여서 제품을 만들때에는 Professional을 사용하자.



**JupyterLab**(https://jupyter.org/try)

Jupyter는 open source라서 계속 진화 중이고 인기 급상승 중인 JupytertLab.

특히 internet browser를 통해서 coding이 가능한 점을 높이 사고 싶다.

Colab(https://colab.research.google.com/notebooks/intro.ipynb)

Colab은 역시나 google 스럽다. Python설치 없이도 어디서든 작업이 가능하다. 나는 이미 Google Drive를 사용하고 있기에 연결해서 쓸수도 있고...



**Visual Studio Code**(https://code.visualstudio.com/)

Visual Studio Code는 Python만을 위한 전용 Tool은 아니지만 강력한 개발 Tool이라고 생각한다.

내가 Microsoft 제품에 매우 익숙해져 있어서 그럴지도 모른다...아니 그럴 가능성이 크지만...



Tool의 선택은 개취이니 나의 선택은 일단 Visual Studio Code와 Colab이다.

Visual Studio Code는 손에 익숙하고 MS의 powerful한 지원과 수많은 extension의 유혹을 뿌리칠 수 없으니 기본이고 Tensorflow를 해보고 싶으니 가장 쉽게 사용이 가능한 Colab을 선택할 것이다.

Colab이나 Jupyter Notebook가 사용이 편리한 장점이 있으나 Github와 연동해서 version control을 하는 것은 여간 번거롭지 않다.

실제 Project를 진행 한다면 나는 아마 주로 VSCODE/extension 과 Git/Github를 쓰지 않을까 싶다.

Project의 규모가 커지면 아마도 PyCharm을 고려해 보겠지...