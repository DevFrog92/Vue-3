 # Vue 3

Vue는 Options API를 기반으로 하나의 객체를 하나의 모듈로 만들어 컴포넌트라 칭하는 라이브러이다. Options API는 하나의 객체를 변수와 메서드 등관 같은 특정한 옵션 기능으로 나눈다.

## Vue의 특징

### 가상 DOM
Vue는 모든 선언적 변수의 값을 DOM에 즉시 반영하지 않고 가상 노드에 먼저 반영한 후 최종적으로 완성된 DOM을 브라우저가 랜더링하게 된다.

### 선언적 랜더링(Declarative Rendering)
DOM 엘리먼트에게 다시 렌더링할 것을 명령하지 않고 DOM과 연결된 상태와 속성이 변경될 떄 자동으로 DOM 엘리먼트가 업데이트 되는 것을 의미한다.

## Vue 2와 다른 Vue 3의 특징

### Composition API
Composition API는 컴포넌트를 작성할 때 함수 기반의 방법을 제시한다. 또한 은닉화된 코드는 컨포넌트들이 재활용할 수 있다.

### Suspense
Suspense는 컴포넌트가 데이터를 받아오기 전까지 기본 contents를 표시할 수 있는 기능이다.

### Teleport

### 여러 개의 v-model directive

### 프록시로 진화된 반응성
Vue는 내부적으로 객체릐 속성을 setter와 getter로 변환하여 반응성을 가지도록 했지만, 미리 정의되지 않은 속성의 추가는 getter와 setter의 호출을 할 수 없다. 그렇기 때문에 watch 옵션은 객체의 속성 추가나 배열의 아이템이 추가되는 것과 같은 변화에 대해서는 반응하지 못했다. Vue 3는 composition API를 통해 데이터를 프록시로 변환하여 사용할 수 있는 방법을 제시한다. 프록시는 ES6에서 소개된 객체로, 데이터와 프레임워크 사이에서 데이터의 전달 및 변환, 관리를 담당한다.

### Fragments
하나의 컴포넌트가 여러 개의 루트 노드를 가지는 것을 의미한다. Vue 2에서도 여러 개의 루트 노드를 컴포넌트에 할당할 수 있었으나 non-props 속성을 컴포넌트에 정의된 루트 노드에 전달하도록 설계가 되어 있었기 때문에, 여러 개의 루트 노드를 가지면 어느 노드에 속성을 전달해야 할지 애매해서 버그가 나타날 수 있는 문제점이 있다. 이를 피하기 위해서 기존에는 하나의 `<div>` 생성하고 그 안에 HTML을 작성하는 것을 암묵적으로 받아들였다. 하지만 Vue 3의 경우 해당 사항에 대한 걱정을 할 필요 없이 여러 개의 루트 노드를 작성해도 된다. 하지만 non-props 속성을 적용할 때는 반드시 어떠한 노드가 전달 받을 것인지 명싱해 주어야 한다.

### Emit option

### CreateRender

<br>

## Vue 3 basic

### setup
Vue 3는 composition API를 이용해 컴포넌트를 만들 수 있다. 그리고 이 composition API는 setup 함수 내에서 사용이 가능하다. setup 함수는 객체를 반환하느데 이객체 내에는 화면을 담당하는 HTML에서 사용할 변수들이 들어있어야 한다.

``` javascript
setup() {
  const data = 100
  return { data }
}
```

기존에 Vue 2에서 사용하던 `watch`나 `computed` 옵션은 모두 setup 함수에서도 구현이 가능하다. 기존 `methods` 옵션으로 제공하던 함수의 경우는 변수로 할당하여 setup로 반환한다.

``` javascript
setup() {
  const sum = (a, b) => a + b
  return { sum }
}
```