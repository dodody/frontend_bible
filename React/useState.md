
# useState

###### 👉 관련 페이지
###### [리액트 공식페이지](https://react.dev/learn/preserving-and-resetting-state)

---

```
const [state, setState] = useState(initailState);
```

우리 리액트 이렇게 똑똑해요
- Adding State to a componentns
- Updating state based on the previous state
- Updateing object and array in state
- Avoing recreating the initial state
- Storing information from previous renders

훅이기 때문에, 컴포넌트 최 상위 수준에서만 쓸 수 있고, 자체 훅에서만 호출 가능.

루프나 조건 내에서는 호출할 수 없기 때문에, -> 이걸 원할 경우에는 새components를 빼서 작업해라

strict 모드에는 초기화 함수를 두번 호출한다. >> 개발 환경에서만 작동하는 액션.

일단 React에서 하는 행동이고, 실수로 발생하는 불순물을 찾기 위해서 개발 환경에서 두번 발생시킨다고 한다


> 도당췌 초기화 함수라는게 무슨 액션이람말이가. 
> 이걸 모르겠으니, 작동원리에 대해 queue에 대해 공부가 필요하다. 
>


```
setSomething
```

다른 값이 들어가게 되면, 다시 렌더링을 촉발시킨다. 

```
setAge(prev => prev + 1)
```

이렇게 하면 보류상태를 참조해서 값을 더해줄 수 있는데


```
const [age, setAge] = useState(30); 
setAge(prev => prev + 1) // 31
setAge(prev => prev + 1) // 32
setAge(prev => prev + 1) // 33
```

이런식으로 동기적으로 작동하게 된다.



렌더링은, 컴포넌트가 화면에서 보이지 않게 되면, state값은 모두 사라지게 된다.
>
> 렌더링에 대해서 공부를 해야한다. 
> 





---
<h6>
* 나만의 언어로 정리하는 것에 의의가 있는 프로젝트 입니다.
</h6>