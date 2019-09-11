howto에 이미 존재하는 users테이블과 더불어 원래 계획했던 trainees 테이블을 추가하여 중개플랫폼으로 나아가려고 한다.<br>
그러기 위해서 users테이블과 추가할 trainees 테이블을 비교하여<br>
1. users 테이블에 trainee들도 같이 저장하고 구분할 수 있는 행을 추가한다.<br>
EX) Condition 행을 추가하여 trainer -> 트레이너, trainee-> 수강생으로 구분<br>
2. users 테이블과 별개로 trainee테이블을 추가하고 각각 1:1 관계를 가지는 하나의 loginInfo 테이블을 생성한다.<br>
EX) users --(1:1) -->> loginInfo <<--(1:1--trainees<br>
등 DB테이블을 확정해야한다.<br>
```
원래 계획부터 Trainer, Trainee가 존재하는 계획이었으므로 개발하면서 그렇게 적용했어야하지만,
DB개발이 서툴어서 우선 users(trainers)만 만들어서 사이트가 실행되게 만들었고 뒤늦게 추가한다.
(미리 계획하고 생각해본 후에 코딩해야한다는 것을 또 한번 느낀다.)
```

users|trainee|비고
----------|----------|----------
loginID|loginID|
loginPW|loginPW|
name|name|
gym|P/G|V
*email*|*email*|추가
*local*|*local*|추가
gender|gender|
career|*age*|V
bodypart|*bodypart*|V
playerSource|*goal*|V
count|주|V
Num|횟수|V

### trainee에 추가되는 부분<br>
P/G - 개인/그룹운동 희망<br>
local - 지역<br>
age - 나이대<br>
bodypart - 고민부위<br>
goal - 운동목표 (다이어트, 체력, 체형교정 등)<br>
주/횟수 - 희망하는 기간(주, 횟수)<br>
<br>
howto README에 미리 적어놓은 개발계획서의 이미지(아래)를 참고해서 적어보면<br>
users와 trainee의 항목이 객체형태나, 갯수가 비슷하다.<br><br>


![HowToImg](https://github.com/WonjeongPark/howto/blob/8e11d129095cfcc51f9e22b2f84a3546439e4b0e/HowToImg.png?raw=true)


`결론`

### users

loginID|loginPW|name|email|local|gender
----------|----------|----------|----------|----------|----------
로그인ID|비밀번호|이름|이메일|지역|성별

### Trainer

gym|career|bodypart|playerSource|count|Num
----------|----------|----------|----------|----------|----------
헬스장|경력|목표부위|동영상소스|횟수|성별

### Trainee

P/G|age|bodypart|goal|week|times
----------|----------|----------|----------|----------|----------
개인/그룹|나이대|고민부위|목적(다이어트, 체형교정 등)|목표기간|가능횟수

> 초반에 생각했던 1, 2가 아니라 이렇게 정한 이유는
1) 관리자계정(admin) 이나 임시계정 등을 추가할 때 쉽고
2) Trainer와 Trainee의 관리가 쉽다.

`계획의 중요성`<br>
개발계획서 작성당시 trainer와 trainee의 분리된 db 생성을 계획했었음에도<br>
1) 구체화된 계획을 세우지 않고<br>
2) server구축하고 db연결하면서 엄청난 오류를 겪었고 그 당시에는 문제해결이 우선이었기에<br>
<br>
이렇게 다시 db부터 수정해야하는 일이 생겼다.<br>
두 번일을 하지 않고 오류를 줄이기 위해 개발 전에 계획을 세우고 구체화시켜서 이런 실수를 하지말자!
