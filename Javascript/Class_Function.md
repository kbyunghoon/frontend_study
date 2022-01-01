<p align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/1200px-Unofficial_JavaScript_logo_2.svg.png" width="400px" />
</p>

리액트 처음 시작했을 때는 클래스형 컴포넌트를 배우고 웹을 만들었지만 그 이후부터 현재까지 계속 함수형 컴포넌트를 사용하고 있다. 그 당시에는 차이에 대해 자세히 몰랐지만 현재 정확히 집고 넘어가기 위해 글을 썼다.


# 클래스형과 함수형의 차이
일단 생김새부터 보자.
## 선언 방식
### 클래스형 컴포넌트
```javascript
import React, { Component } from 'react';

class app extends Component {
  render() {
    return (
      <div>
        
      </div>
    );
  }
}

export default app;
```

- 클래스형은 class 키워드가 필요하며 Component로 상속을 받아야 한다.
- 또한 render() 메소드가 꼭 있어야한다.

### 함수형 컴포넌트
```javascript
import React from 'react';

function app(props) {
  return (
    <div>
      
    </div>
  );
}

export default app;
```
또한 요즘에는 화살표 함수를 사용하여 자주 사용한다.
```javascript
import React from 'react';

const app = () => {
  return (
    <div>
      
    </div>
  );
};

export default app;
```

## 차이점
### 클래스형 특징
- state 기능과 라이프사이클(lifecycle) 기능을 사용할 수 있다.
- 임의 메서드를 정의할 수 있다.
- render() 함수가 있어야 하며, jsx를 return 해야 한다.
### 함수형 특징
- state 기능과 라이프사이클 기능 대신 **리액트 v16.8에 도입된 Hooks 기능을 사용**한다.
- 메모리 자원을 클래스형보다 덜 사용한다.
- 컴포넌트 선언이 편하다.
### 일반 함수와 화살표 함수 차이
#### this
- 일반 함수는 **함수가 어떻게 호출된 방법에 따라 this에 바인딩할 객체가 동적으로 결정**된다.
- 화살표 함수는 **상위 스코프의 this**를 가리킨다

### props
#### 클래스형
```javascript
import React, { Component } from 'react';

class app extends Component {
  render() {
    const { name } = this.props;
    return (
      <div>
        이름 : {name}
      </div>
    );
  }
}

export default app;
```
- 클래스형에서는 this.props로 값을 불러올 수 있따.

#### 함수형
```javascript
import React from 'react';

const app = ({name}) => {
  return (
    <div>
      이름 : {name}
    </div>
  );
};

export default app;
```
- 함수형에서는 props를 불러올 필요 없이 바로 불러올 수 있다.
