# 06장: 리액트 개발 도구로 디버깅하기

## 6.1 리액트 개발 도구란?

react-dev-tool
리액트로 만들어진 다양한 애플리케이션을 디버깅하기 위해 만들어짐
리액트 웹, 리액트 네이티브 등 다양한 플랫폼에서 사용 가능
브라우저 확장 프로그램으로 사용할 수 있다

## 6.2 리액트 개발 도구 설치

리액트 개발 도구를 브라우저 확장 도구로 설치
성공적으로 설치되었다면 우측 상단에 있는 확장 도구 모음에 리액트 로고가 표시되는 것을 확인할 수 있다

리액트 로고 색상 의미
회색: 리액트 개발 도구가 정상적으로 접근할 수 없는 페이지, 리액트로 개발되지 않은 페이지
빨간색: 개발 모드인 리액트 웹 애플리케이션에 정상적으로 리액트 개발 도구가 접근할 수 있음
파란색: 실제 프로덕션에 배포되어 있는 웹 애플리케이션에 방문한 경우

## 6.3 리액트 개발 도구 활용하기

Components, Profiler이라는 디버그 도구를 사용하여 리액트 애플리케이션에서 일어나는 대부분의 작동을 확인해 볼 수 있다

Components

현재 리액트 애플리케이션의 컴포넌트 트리를 확인할 수 있다
컴포넌트 구조 뿐만 아니라 props와 내부 hooks 등 다양한 정보를 확인할 수 있다
컴포넌트 트리에서 기명 함수로 선언되어 컴포넌트명을 알 수 있다면 해당 컴포넌트명을 보여주고, 만약 익명 함수로 선언돼 있다면 Anonymous라는 이름으로 컴포넌트를 보여준다
함수 선언식과 함수 표현식으로 생성한 컴포넌트는 모두 정상적으로 함수명을 표시한다
컴포넌트를 기명 함수로 선언해야 개발 도구에서 확인하기 쉬워진다
함수를 기명 함수로 바꾸기 어렵다면 함수에 `displayName` 속성을 추가하는 방법도 있다
익명 함수로 선언하기 곤란한 경우, 혹은 함수명과는 별도로 특별한 명칭을 부여해 명시적으로 확인이 필요한 경우에 `displayName`을 사용하면 좋다

컴포넌트 트리에서 컴포넌트를 선택했을 때 해당 컴포넌트에 대한 자세한 정보를 볼 수 있다
눈 아이콘: 해당 컴포넌트가 어디에서 렌더링되었는지 확인할 수 있다
벌레 아이콘: 콘솔 탭에 해당 컴포넌트의 정보가 `console.log`를 실행해 기록할 수 있다
개발 도구 화면에서 보기에는 복잡한 정보를 확인하거나 또는 해당 정보를 복사하는 등의 용도로 사용 가능하다
소스코드 아이콘: 해당 컴포넌트의 소스코드를 확인할 수 있다
`{}` 버튼으로 작독화된 코드를 읽고 디버깅 할 때 유용하게 사용할 수 있다

해당 컴포넌트가 받은 props를 확인할 수 있다
단순한 원시값뿐만 아니라 함수도 포함되어 있다
Copy value to clipboard: props 정보가 클립보드로 복사된다
Store as global variable: props 정보가 `window.$r`에 저장된다
Go to definition: 해당 변수가 정의된 곳으로 이동한다

컴포넌트에서 사용중인 훅 정보를 확인할 수 있다
`use`가 생략된 이름으로 나타난다
훅에 넘겨주는 함수를 익명 함수 대신 기명 함수로 넘겨주면 해당 훅을 실행할 때 실행되는 함수의 이름을 확인할 수 있다

`rendered by`로 해당 컴포넌트를 렌더링한 주체가 누구인지 확인할 수 있다
개발 모드에서 해당 컴포넌트를 렌더링한 부모 컴포넌트까지 확인할 수 있다

컴포넌트 메뉴를 활용하면 컴포넌트 트리에 대한 정보 뿐만 아니라 해당 컴포넌트에 대한 자세한 정보를 확인할 수 있다

Profiler

프로파일러는 리액트가 렌더링하는 과정에서 발생하는 상황을 확인하기 위한 도구이다
컴포넌트 렌더링 과정에서 발생하는 일을 확인할 수 있다
렌더링 과정에 개입해 디버깅에 필요한 내용을 기록해야 하기 때문에 프로덕션 빌드로 실행되는 리액트 애플리케이션에서는 사용할 수 없다

프로파일링 메뉴는 리액트가 렌더링할 때 어떠한 일이 벌어지는지 확인할 수 있는 도구이다
Start Profiling: 프로파일링이 시작된다
Reload and start profiling: 웹페이지가 새로고침되면서 이와 동시에 프로파일링이 시작된다
Stop Profiling: 프로파일링된 현재 내용을 모두 지운다
Load Profile / Save Profile: 프로파일링 결과를 저장하고 불러온다

Flamegraph
렌더 커밋별로 어떠한 작업이 일어났는지 나타낸다
너비가 넓을수록 해당 컴포넌트를 렌더링하는 데 오래 걸렸다는 것을 의미한다
각 컴포넌트에서 마우스 커서를 가져다 대면 해당 컴포넌트의 렌더링과 관련된 정보를 확인할 수 있다
렌더링되지 않은 컴포넌트는 회색으로 표시되며 Did not render라는 메시지가 표시된다
각 렌더 커밋별로 리액트 트리에서 발생한 렌더링 정보를 확인할 수 있다

Ranked
해당 커밋에서 렌더링하는 데 오랜 시간이 걸린 컴포넌트를 순서대로 나열한 그래프이다
렌더링이 발생한 컴포넌트에 대한 정보만 빠르게 파악할 수 있다

Timeline
시간이 지남에 따라 컴포넌트에서 어떤 일이 일어났는지를 확인할 수 있다
시간의 흐름에 따라 리액트가 작동하는 내용을 추적하는 데 유용하다

리액트 개발 도구를 활용하면 정적으로 생성된 컴포넌트 트리를 보는 것에서부터 프로파일링을 통해 리액트 애플리케이션이 시간이 지남에 따라 어떤 식으로 작동하는지, 불필요한 리렌더링이 일어나고 있는지 등을 확인할 수 있다

