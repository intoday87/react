# react

- class component를 사용시 메서드를 이벤트 함수에 넘길 때 closure 문제 해결
  ```diff
  import React from "react"

  type Props = {}

  export default class App extends React.Component<Props> {
    state = {
      a: 10
    }

  +    click = () => { // 익명함수로 click에 선언하게 되면 `const click = () => { ... }` 형태로 트랜스파일 되는것 같다. this도 `const context = this`로 해서 상수로 넘어가는 듯
  +      window.alert(this.state.a)
  +    }
  -    click { // 이렇게 한다면 현재 class의 this context에 바인딩된 상태라 함수 자체를 div onclick에 넘겼을때 this는 현재 class 인스턴스의 this가 아니다
  -      window.alert(this.state.a)
  -    }
  
    render() {
      return (
        <div onClick={this.click}>div click</div>
      )
    }
  }
  ```
  - typescript playground로 볼려고 했는데 장애나서 
