# `float` 를 clear하는 방법

float는 **블록상태의 객체를 정렬할때 사용하는 css속성**이다. 블록상태의 객체는 한자리를 혼자 다 차지 하기 때문에 다른 객체와 나란히 놓을 수 없다. 그럴때 사용하는 속성 중 하나가 float이다. 그러면 div의 가로값은 최소 크기로 변경된다. float상태가 된 div의 크기가 줄면서 빈 공간이 생기고 그 빈 공간에 뒤에 있던 div가 올라오게 된다.

하지만 div에 float속성을 주면 문제가 발생한다. float 상태는 말 그대로 요소가 둥둥 떠있는 상태이다. 앞에 요소가 떠있기 때문에 그 다음에 있는 요소가 그 자리가 비었다고 생각하고 그 자리로 올라오게 된다. 또한 부모의 자식들이 모두 float 상태일 때 부모는 자식을 인식하지 못하고 height값을 찾지 못한다.
이처럼 float를 적용한 요소는 일반적인 흐름에서 벗어나는 특징이 있어 다음의 요소에게 영향을 미치기 때문에 clear와 반드시 함께 사용해야한다.

## float를 clear하는 방법:

#### 1. `float`으로 대응하기

앞에 요소가 float인 상태에서 뒤에 요소가 float이 아닐 경우 이런 문제가 발생하기 때문에 그 다음 요소 역시 float 상태로 바꿔주면 해결된다.하지만 그 뒤에 요소들에게도 동일한 문제가 발생하기 때문에 완전한 해결책이라고 볼 수 없다.

#### 2. 부모에게 `overflow:hidden` 사용하기

자식요소가 float인 부모에게 overflow:hidden을 주면 부모가 자식을 담아낸다. 다만, 이 방법은 내용이 넘치면 안보이기 때문에 한계가 있다.

#### 3. 빈요소에 `clear:both` 넣기

float된 요소 밑에 빈 임의의 요소를 만들어 clear:both를 준다. clear는 취소하다는 뜻으로 float를 취소시킨다. 마크업의 흐름을 깨기 때문에 권장하는 방법이 아니다.

#### 4. 가상요소 `::after` 사용하기 (👍 권장)

부모요소에게 ::after를 사용하며 가상요소를 만들어 준다. 그리고 가상요소에게 display:block 요소를 적용해 한 줄 가득차게 한다. 빈 콘텐츠를 넣어주고, clear를 적용시킨다. 부모 뒤에 보이지 않는 가상요소를 만들어 뒤에 요소가 위로 따라 올라가지 않게 해준다. 가장 많이 사용하는 방법이다.

```css
float된 요소의 부모태그::after {
  content: "";
  display: block;
  clear: both;
}
```

> #### 가상요소(Pseudo-elements) 란?
>
> 가상요소는 가상의 요소를 만들고 내용을 넣어 출력하겠다는 것이다.  
> e.g. `::after`, `::before`

#### Reference

- [https://developer.mozilla.org/ko/docs/Web/CSS/float](https://developer.mozilla.org/ko/docs/Web/CSS/float)

---

[Back](../README.md)
