# TIS: Markdown에서 Image 삽입 방식

## TIS: Image파일 삽입 시, 파일 깨짐현상 해결
### Issue
1. 각 카테고리에 관련 image를 함께 저장했고, 폴더 경로로 이미지를 업로드하려고 시도했다. 하지만, 이미지파일은 전혀 출력되지 않고 "파일이 깨졌음"을 알리는 아이콘과 이미지 주소 앞에 입력한 파일설명 문구만 렌더링되었다.[->go to Analysis.no1](#Analysis)
2. 폴더 주소를 변경했지만, md파일 내 image깨짐 현상은 해결되지 않았다.[->go to Analysis.no2](#Analysis)
3. 여전히 이미지가 깨진 파일로 렌더링되었다. [->go to Analysis.no3](#Analysis)


### Analysis
1. 업로드된 image 자체는 repository에서 확인해보아도 깨지지 않았다. 이를 통해, image의 오류가 아님을 알 수 있었다. 그래서 폴더 주소작성오류라고 판단했고, 주소작성 편의를 위해 image 파일들을 모두 img라는 폴더 내에 저장하는 방식으로 저장경로를 수정 및 폴더 주소를 변경해 해결을 시도했다. [->go to Issue.no2](#Issue)

2. [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)과 구글링을 통해 탐색한 결과, **폴더경로 주소**가 아닌, **웹 상의 링크 주소**로 이미지를 삽입하는 방식이 보다 안정적이라는 것을 알게 되었다. 그래서 repository에 업로드해둔 image파일들의 주소를 **commit 리스트 내에서 복사**해서 md파일에 삽입했다. [->go to Issue.no3](#Issue)
![commit 리스트에서 이미지 링크 추출](https://github.com/ShinAhYoung21/TIL/blob/main/img/commit%EC%97%90%EC%84%9C%20img%EB%A7%81%ED%81%AC%EB%B3%B5%EC%82%AC.PNG?raw=true)

3. **다른 방식으로 image파일의 링크를 얻을 수 있는 경우**를 고려해보기로 했다.[->go to Solved](#Solved)


### Solved
GitHub repository에서 image파일의 링크를 얻는 경우를 생각해봤다. commit 아니면 **repository 폴더 안에서 image파일을 열고, 웹 링크를 얻을 수 있다는 것**을 떠올렸다.
![repository에서 img폴더로 진입](https://github.com/ShinAhYoung21/TIL/blob/main/img/TIS_md_img1.PNG?raw=true)
![img폴더 내에서 링크 얻기 원하는 이미지 클릭](https://github.com/ShinAhYoung21/TIL/blob/main/img/TIS_md_img2.PNG?raw=true)
![image파일의 웹 주소(링크)복사하여 md파일에 입력](https://github.com/ShinAhYoung21/TIL/blob/main/img/TIS_md_img3.PNG?raw=true)
위 이미지와 같은 순서로 진행하여 해결했다.


### Learned
1. Markdown에서는 **이미지 업로드 시, 웹 주소를 쓰는 편이 안정적**이다.
2. md파일 내에 image를 삽입하려거든, **image파일을 먼저 GitHub repository에 업로드**시켜둬야 한다.
3. 업로드, 링크추출 등 image 다루는 작업의 편의를 위해 **image 업로드 전용 폴더를 활용**하는 것이 좋다.