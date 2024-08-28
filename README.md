# 🤗이스트소프트 백엔드 개발자 부트캠프[6기]
## 🌐프로젝트01 - 프론트엔드 프로젝트

### ✏목표
#### 보편적 측면에서의 목표
##### 현대의 개발 환경에서는 프론트엔드와 백엔드 간의 경계가 더욱 흐려지고 있다. 이러한 맥락에서 팀 협업과 개발 역량을 향상시키기 위해 백엔드 개발자가 프론트엔드에 대한 이해를 갖추는 것이 중요하다.

#### 개인적 측면에서의 목표
##### 이번 부트 캠프 기간동안 배운 프론트엔드 관련 기술들을 최대한 연습하고 익히도록 한다.

-------------------------------------------
### ✏개발 환경 및 베포URL
#### - 개발환경 : Visual Studio Code
#### - 배포URL
##### pc-version : <https://sodami-hub.github.io/pc_hodu/>
##### movile-version : <https://sodami-hub.github.io/mobile_hodu/>
-------------------------------------------
### ✏요구사항 명세
1. 피그마를 참고하여 페이지 구현을 한다.
2. 모바일 화면도 고려하여 페이지 구현을 한다.
3. 스크롤시 헤더가 고정되게 한다.(단, 처음에는 고정된 상태가 아니다.)
4. 스크롤 탑 버튼을 구현한다.<br>
  a. 스크롤 탑 버튼은 스크롤시 나타난다.<br>
  b. 스크롤 탑 버튼은 푸터 아래로 내려가지 않는다.<br>
  c. 스크롤 탑 버튼을 누르면 스크롤이 최상단으로 올라갑니다.(단, 부드럽게 올라가야 된다.)<br>
5. 구독하기 모달창<br>
  a. 이메일을 입력하고 ```Subscribe``` 버튼을 클릭하면 모달창이 나타난다.<br>
  b. 이메일 유효성 검사를 진행해야 한다.(값이 들어가지 않거나 이메일 형식이 유효하지 않으면 alert 창으로 경고 문구가 떠야 된다.)<br>
  c. 이메일이 잘 입력되었다면 모달창이 뜬다. 이때 모달창의 ```OK! I love HODU``` 버튼을 클릭하면 form이 제출되고 모달창이 닫힌다.

-------------------------------------------
### ✏프로젝트 구조와 개발 일정
##### 프로젝트 구조
📦FRONTEND_FINAL_PROJECT  
 ┣ 📂images  
 ┣ 📂mobile_version<br> 
 ┣ 📂pc_version
 
 ##### 개발 일정
 2024.08.19(월) ~ 2024.08.28(수)

-------------------------------------------
### ✏화면 구성

| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

| Command | Description |
| --- | --- |
| `git status` | List all *new or modified* files |
| `git diff` | Show file differences that **haven't been** staged |


### ✏에러와 에러 해결
#### 😢개인프로젝트 기간동안 해결하지 못한 문제들에 대해서 정리해보았습니다.
##### 1. figma 화면과 html로 작성한 화면의 폰트 차이 : figma의 font-weight 속성을 그대로 가져왔을 때 차이가 발생하는 것으로 보인다.
##### 2. 모달 창에서의 form 제출
- 모달창이 열리자마자 바로 닫히는 현상이 발생.
- 동일한 주소를 두번 입력(Subscribe) 하면 정상 작동함.
- 개발자 도구의 디버그를 통해서 현상을 파악하게 됨.
    - 어떤 상황에서 모달 창의 확인 버튼을 누르지 않았음에도 바로 다음 단계로 넘어감.
    - 이벤트 기본 동작과 이벤트 버블링을 막는 함수를 추가했지만 변화가 없음.
    - 다음 이벤트가 발생할 때까지 대기하는 함수를 통해서 모달창이 자동으로 닫히는 현상을 막음
    - 그러나 이벤트를 막았기 때문에 input에 입력한 email 값을 전달할 수 없는 문제가 발생.
    - email 값을 javascript의 전역변수에 넣어서 전달하는 것처럼 구현.
``` 
// 이메일 유효성 검사 및 모달 열기
function check(e) {
    e.preventDefault(); // 이벤트 기본 동작 방지
    e.stopPropagation(); // 이벤트 버블링 방지

    let emailInput = document.getElementById('email');
    let email = emailInput.value;

    if (emailChk(email)) {  
        emailvalue= email;  
        toggleModal('block');
        waitForEvent(document.getElementById('modal-btn'), 'click').then(() => {
            toggleModal('none');
        });
    } else {
        alert("이메일을 정확히 입력하세요.");
    }
}
```

-------------------------------------------
### 😊개발하며 느낀 점
- 화면을 완성해 나가는 즐거움
- 좀 더 공부하고 연습을 해야겠다... 특히 javascript...
