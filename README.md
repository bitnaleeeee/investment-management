# B2C 투자 관리 서비스의 관리자 기능 구현

## 실행결과

![ezgif com-gif-maker](https://user-images.githubusercontent.com/99943583/202637983-13ef1bcf-9464-439f-aa4c-04dcecc3a78d.gif)


#### STACK
<img src="https://img.shields.io/badge/JavaScript-FFCA28?style=flat-square&logo=javascript&logoColor=white"/> <img src="https://img.shields.io/badge/React.js-58c3cc?style=flat-square&logo=React&logoColor=white"/> <img alt="SASS" src ="https://img.shields.io/badge/SASS-CC6699.svg?&style=flat-square&logo=Sass&logoColor=white"/> <img src="https://img.shields.io/badge/aws(EC2)-F6BB43?style=flat-square&logo=amazonaws&logoColor=white"/>
<img src="https://img.shields.io/badge/git-F05032?style=flat-square&logo=git&logoColor=white"> <img src="https://img.shields.io/badge/github-181717?style=flat-square&logo=github&logoColor=white"> <img src="https://img.shields.io/badge/fontawesome-339AF0?style=for-flat-square&logo=fontawesome&logoColor=white">


## 팀 소개

- [이빛나 (팀장)](https://github.com/bitnaleeeee)
- [모상빈](https://github.com/Topbin2)
- [김진석](https://github.com/genuine-seok)
- [박우빈](https://github.com/Debonchocola)
- [이의연](https://github.com/strongpond)
- [조성호](https://github.com/CSH111)
- [전대원](https://github.com/eodnjs467)

<br />

## 프로젝트 소개 

- 목표 : 투자 관리 서비스의 관리자 기능 구현
- 기간 : 2022.11.12 ~ 2022.11.18
- 주관 : 원티드 


## 폴더 구조 

```
📦 src
├── 📂 pages
│   ├──📜 Login
│   │  ├── Login.js
│   │  ├── Login.scss
│   │  └── Logout.js
│   │
│   └──📜 Main
│      ├── Main.js
│      ├── Main.scss
│      ├── User.js
│      ├── User.scss
│      └── UserList.js
│
├── 📂 views
│   ├──📜 data
│   │  ├── brokers.json
│   │  └── numberStatus.json
│   │
│   ├── DataTable.js
│   ├── DataTable.scss
│   ├── DenseTable.js
│   ├── Slider.js
│   ├── Slider.scss
│   └── UserDataTable.jss
│
├── common.scss
├── index.js
└── Router.js
```
## 구현 사항

- [x] 계좌목록 데이터 조회 기능 구현
- [x] 페이지네이션 기능 구현
- [x] 계좌 목록 사용자 이름 클릭시 사용자 정보 조회
- [x] 사용자상세 데이터 조회
- [x] 사용자상세 페이지네이션
- [x] 로그인, 로그아웃

<br />

## 주요 기능

### json-server 을 활용 전체 데이터 조회 기능 구현

```js
useEffect(() => {
  fetch('http://localhost:4000/accounts?_expand=user', {
    method: 'GET',
    headers: {
      Authorization: 'Bearer ' + token,
    },
  })
    .then(response => response.json())
    .then(result => {
      setData(result);
    });
  console.log(token);
}, []);
```

### 사용자 이름 클릭시 해당 사용자 상세 정보 조회 기능 구현

```js
const pageDetail = e => {
  if (e.field === 'userName') {
    let val = data[e.row.id];
    navigate(`user/${val.id}`);
  }
};
```

```js
useEffect(() => {
  fetch(`http://localhost:4000/users/${userid}`, {
    method: 'GET',
    headers: {
      Authorization: 'Bearer ' + token,
    },
  })
    .then(response => response.json())
    .then(result => {
      setUsers(result);
    });
}, []);
```

<br>


## 프로젝트 설치 및 실행

<br/>

1. Git Clone
```plaintext
$ git clone https://github.com/pre-onboading-2team/Week1_2_Issue_List.git
```

2. 프로젝트 패키지 설치
```plaintext
$ npm install
```
3. 프로젝트 실행

```plaintext
$ npm start
```

<br/>

### Server 실행 방법

/src/server 에 서버 폴더가 존재합니다
* 디셈버앤컴퍼니 백엔드 데이터에 cors이슈가 있어, 해결방안으로 서버코드를 수정하였습니다.

1. 관련 패키지 설치

```
$ npm install
```

2. 로컬 서버 실행

```
$ npm start
```
