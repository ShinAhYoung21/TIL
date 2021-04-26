# MySQL 서버 연결 오류


## Issue

생활코딩 웹앱만들기 [DB이론2: MySQL](https://youtu.be/W7lmchYciMk)를 따라가고 있었다.
그런데, 패스워드를 입력하는 부분부터 막히기 시작했다.


## Analysis

다음 이미지와 같이, 로컬 서버에 입력할 수 없다는 에러 메시지가 출력되었다.

![로컬 서버에 입력 불가하다는 에러 메시지](https://github.com/ShinAhYoung21/TIL/blob/main/img/error_MySQLserverConnection.PNG?raw=true)

그래서 우선, 에러메시지를 그대로 구글링해봤다.

> 하지만, Stack 속 조언들은 여러 이론이 결합된 해결방법이 제시되어 현재로서는 전혀 이해할 수 없다.

> 한국어 블로그 속 정보들도 마찬가지였는데, 그 중 가장 간단해보이는 '서버가 제대로 켜져 있는지 확인하라'는 조언을 따라 해결을 시도했다.

> 아파치 매니저를 실행해보니, 실제로 MySQL서버가 stopped상태였고, start버튼을 눌렀지만, 제대로 실행되지 않았다. 버튼을 누른 후, 수 초 뒤 다시 stopped로 돌아갔다.
![stopped 상태로 머물러있는 MySQL서버](https://github.com/ShinAhYoung21/TIL/blob/main/img/error_MySQLserverStopped.PNG?raw=true)


## Solved

아직 해결하지 못했다.
걱정이된다. 이것 해결을 해야 다시 수업 진도를 따라갈 수 있을텐데....

> 내일 최대 3시간 투자를 해보고, 내가 실행 가능한 해결책을 찾지 못하면(해결하지 못하면), 서버를 다 지우고 다시 깔 방법 밖엔 없을 듯 하다.


## Learned

> **지식이 있어야 해결책도 알아들을 수 있다.** 내가 다룰 수 있는 것, 이해하는 부문이 적다보니 인터넷에 흩어져있는 여러 해결방안 중 대다수를 접목조차 시키지 못한다...
>공부하자!