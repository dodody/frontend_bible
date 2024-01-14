
# Reconciliation

###### 👉 관련 페이지
###### [리액트 공식페이지](https://react.dev/learn/preserving-and-resetting-state)

###### [구 리액트 공식페이지](https://react.dev/learn/preserving-and-resetting-state)


---


상황 react native에서 코딩을 하다가, ReactNavigation 라이브러리에서 

```
components ={() => <Components />}
```
로 하니까 오류가 뜨더라고, 린트 에러 같은데

> React reconciliation performs element type comparison with reference equality. The reference to the same element changes on each re-render when defining components inside the render block. This leads to complete recreation of the current node and all its children. As a result the virtual DOM has to do extra unnecessary work and possible bugs are introduced.


그래서 chatGPT에 검색해보니


> 리액트(React)에서 재조정(Reconciliation)은 엘리먼트 유형 비교를 참조 동등성(reference equality)을 사용하여 수행합니다. 이 말은 컴포넌트가 렌더 블록 내에서 정의될 때마다 동일한 엘리먼트에 대한 참조가 변경된다는 것을 의미합니다. 이것은 현재 노드와 그 모든 하위 자식을 완전히 다시 생성하도록 이끕니다. 이 결과로 가상 DOM이 불필요한 추가 작업을 수행해야 하며 가능한 버그가 발생할 수 있습니다.

이것을 이해하기 위해서는 몇 가지 개념을 살펴보아야 합니다.

참조 동등성(Reference Equality): JavaScript에서 객체와 배열은 참조 타입입니다. 이것은 객체나 배열이 다른 변수에 할당될 때 변수는 해당 객체나 배열을 참조하는 것을 의미합니다. 따라서 두 변수가 동일한 객체를 참조하면 그것들은 참조적으로 동등합니다.

렌더링(rendering): 리액트 컴포넌트는 데이터의 변경 또는 상태(State)의 변경으로 인해 다시 렌더링됩니다. 렌더링은 가상 DOM에 변화를 반영하고 화면에 업데이트를 수행합니다.

가상 DOM(Virtual DOM): 가상 DOM은 리액트가 화면 업데이트를 최적화하기 위해 사용하는 가상의 화면 표현입니다. 리액트는 가상 DOM을 이용하여 실제 DOM과 비교하고 변경 사항을 효율적으로 적용합니다.

문제는 다음과 같습니다. 리액트 컴포넌트 내부에서 렌더링 메서드 내에서 컴포넌트를 정의하는 경우(예: 함수 컴포넌트 내에서 다른 함수 컴포넌트를 정의), 매 렌더링마다 해당 컴포넌트가 다시 생성됩니다. 이것은 참조 동등성에 의해 인식됩니다. 따라서 리액트는 해당 엘리먼트가 변경되었다고 판단하고, 해당 엘리먼트의 모든 자식과 하위 엘리먼트를 다시 렌더링하게 됩니다.

이것은 문제를 일으킬 수 있습니다. 불필요한 재조정은 성능 문제를 초래할 수 있으며 예상치 못한 버그를 발생시킬 수 있습니다. 특히 컴포넌트가 많은 계층 구조에 있을 때 이러한 문제가 더 심각해질 수 있습니다.

해결 방법으로는 다음과 같은 것들이 있습니다:

컴포넌트를 렌더 메서드 내에서 정의하지 말고, 외부로 분리하여 정의하십시오.
클래스 컴포넌트 대신 함수 컴포넌트를 사용하면 일부 재조정 문제를 완화할 수 있습니다.
React.memo나 useMemo 등을 사용하여 불필요한 재조정을 방지하십시오.
컴포넌트의 키(key) 속성을 사용하여 재조정 동작을 제어하십시오.
이렇게 하면 리액트가 더 효율적으로 엘리먼트 재조정을 처리하고 성능을 향상시킬 수 있습니다.





라고 하더라고. 그래서 reconciliation 등에 대해 알아봐야할 이유가 생겼다.


---
<h6>
* 나만의 언어로 정리하는 것에 의의가 있는 프로젝트 입니다.
</h6>