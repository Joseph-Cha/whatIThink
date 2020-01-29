## React Native
React Native(이하 RN)은 Facebook 오픈소스 프레임워크로, JS로 코딩하여 하이브리드앱을 빌드할 수 있다.<br>
1. JS로 코딩할 수 있다는 점
2. 코드를 작성하면서 실시간으로 그 결과를 확인 할 수 있다는 점
3. 컴파일 과정을 거치지 않는다는 점
4. IOS, Android 사이 코드를 공유할 수 있다는 점, 
5. 기존 하이브리드 앱이 WebView에 화면을 만들어 놓고 모바일 앱으로 접근하는 것에 비해<br>
실제 네이티브 UI를 사용하여 구현하기 때문에 퍼포먼스가 올라가 모바일 앱과의 괴리감도 줄어드는 점<br>
6. redux, MobX 아키텍쳐 지원한다는 점(React니까 당연한건가..?)

등 여러 장점이 있지만
1. 로직히 복잡해지거나 뷰 스택이 쌓일 수록 속도가 느려진다던지
1. 그래서 에러가 나면 원인을 찾기가 힘들고 유지보수가 어렵다는 의견도 있고
2. 아직 성장하는 오픈 소스 프레임워크이기 때문에 <br>
RN의 업데이트 상황에 따라 변경된 모듈로 인해 에러 상황이 발생되어 수정이 필요하다는 점
3. 비지니스 로직은 재사용가능하지만 IOS, Android 별 특징적인 부분은 각각의 API를 사용해야한다.<br>
4. 내부적인 제약이 존재한다는 점(JS 애니메이션보다 네이티브에서 제공하는 애니메이션 사용 권장 등)
5. 한국어 자료가 많이 없다는 점

등의 단점이 있다.

## 시작하기
[참고1](https://busy.org/@anpigon/react-native-1--1542639852750), [Expo](https://velog.io/@max9106/React-Native-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EB%84%A4%EC%9D%B4%ED%8B%B0%EB%B8%8Creact-native-%EB%91%90-%EA%B0%80%EC%A7%80-%EB%B0%A9%EB%B2%95-c4k0gxe0tc)
[React Native CLI](https://velog.io/@max9106/React-Native-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EB%84%A4%EC%9D%B4%ED%8B%B0%EB%B8%8Creact-native-%EB%91%90-%EA%B0%80%EC%A7%80-%EB%B0%A9%EB%B2%95-2-React-Native-CLI-bmk0gz4izg)<br>
RN을 시작하는 방법으로는 크게 Expo CLI와 React Native CLI를 꼽을 수 있다.<br>
### Expo
미리 정해진 API가 구성되어 세팅되어 있다.<br>
1. 미리 기본적인 것들이 세팅되어 있는 것은 설치해서 사용하기 때문에 개발 시작이 간편하다.
2. 또한 배포하기도 매우 쉽다. 첫 배포 후 업데이트의 경우에도 publish만 해주면 알아서 업데이트 되기 때문이다.<br><br>

하지만 <br>
1. 포함되어 있는 API만 사용 가능하고 필요 기능을 하는 모듈을 추가로 만들어 사용할 수 없다.(혹은 eject)
2. native 파일을 숨겨두고 알아서 관리해주는 툴이기 때문에 개발자가 완전히 제어할 수 없다.

```
RN Core나 Expo SDK에서 지원하지 않는 네이티브 모듈들을 사용해야 할 때 eject를 한다.
eject하면 순수 JavaScript로 이루어진 프로젝트를 Expo 모바일 클라이언트로부터 꺼내준다.
그리고 Xcode나 Android Studio 네이티브 프로젝트를 만든다.
eject 후에 여전히 Expo SDK에 dependency가 있긴 하지만, 프로젝트는 더이상 expo client에 속한다고 볼 수 없다.
```
[출처](https://floydkim.github.io/2019-05-04-React-Native-EXPO%EC%99%80-%EC%9D%B4%EB%B3%84%ED%95%98%EA%B8%B0/)
, [환경설정 참고](https://medium.com/@catherinPark/react-native-%ED%99%98%EA%B2%BD%EC%84%A4%EC%A0%95-87a3e768aa91)<br>

* eject이란 추출한다는 의미로 expo에서 지원하지 않는 기능들을 사용하기 위해 expo에서 native로 바꿔주는 것이다.<br>
expo는 JS파일을 RN으로 번들링하여 expo client에 내려주는 서버와 EXPO-CLI - expo 모바일 client와의 통신서버 2개가 동작하고<br>
expo로 작성한 JS코드들은 EXPO 모바일 client 에서만 동작하므로 native library를 사용할 수 없다.<br>
또한 expo에 들어가는 앱은 순수 JS로 작성되고 iOS나 Android 레이어가 필요없다.<br>
expo에서 native를 사용하기위해 eject한다는 것은 JS로 작성된 앱을 EXPO 모바일 client에서 꺼내주는 것이다.<br>
따라서 eject을 하면 iOS, Android 각 부분의 처리가 필요하다.<br><br>

아직 RN 부분은 익숙하지 않아서 100% 이해 되진 않지만 일단 대략적인 흐름이라도 잘 알아두자!<br>

### React Native CLI
직접 세팅부터 API 구성까지 개발 할 수 있으며 native 파일을 다룰 수 있다.<br>
1. 필요 기능이 있는 경우 모듈을 만들어 사용 할 수 있다.<br>

하지만<br>
1. 초기 구성이 오래걸린다.
2. 배포하기 불편하다.
3. IOS는 Mac에서만 개발 가능하다.


