# 2주차 : 맡은 레이아웃 구조 짜기(HTML, CSS)

## todayList - 할 일 목록

- 자주 쓰는 할 일 목록들에서 추출된(혹은 입력된) 목록들의 공간
- 체크박스로 할 지, 아니면 완료되면 밑으로 따로 공간 만들어서 뺄 지 => 체크박스가 더 직관적일 것 같다.

### TODO

- 순서가 필요없는 요소들이기 때문에, ul 태그 내 li 태그를 활용했다.
  - 이 때 li 각각의 요소들 옆에 점이 생겼는데, list-style: none 으로 해결했다.

```html
<ul>
  <li>
    <input type="checkbox" class="lists" id="cbcss" />
    <span>헬스장 가기</span>
  </li>
</ul>
```

```css
li {
  color: steelblue;
  border: 3px solid lightgray;
  border-radius: 7px;
  padding: 8px 5px;
  margin: 10px;
  list-style: none; /* 해당 스타일 추가로 li 옆의 점을 없앴다. */
}
```

- 체크박스 자체의 CSS도 설정할 수 없나 찾아봤는데 HTML의 `label 태그`를 활용하면 가능했다.
- 체크박스의 id와 label태그의 for을 이용해 기본 input type인 체크박스는 숨기고, label을 체크 박스 형태로 구현하는 방식

```css
/* 1. 원래 체크박스 안 보이게 */
input#cbcss {
  display: none;
}

/* 2. 체크 이전 실제 체크박스 스타일링 */
input#cbcss + label:before {
  content: ""; /* 빈 칸으로 해줘야 박스가 만들어진다 */
  display: inline-block;
  width: 17px;
  height: 17px;
  margin-left: 5px;
  border: 2px solid #d06262;
  border-radius: 4px;
  vertical-align: middle;
  cursor: pointer;
}

/* 3. 체크 이후 체크 표시 스타일링 */
input#cbcss:checked + label:before {
  content: " \2714 "; /* 체크표시 CSS 코드 */
  background-color: #d06262;
  border-color: #d06262;
  color: white;
}
```

### 결과

![체크박스 CSS](https://user-images.githubusercontent.com/71033487/227699559-3eb92df3-3a56-4258-8284-46f9b68cbac2.gif)

## 마무리 & 해야 할 일

- 조금 더 친근한 필기체 형식으로 폰트 변경
- 배경 색, 폰트 색, 박스 형태 등 조정
- 추후 카테고리별 체크 박스 & 배경 색상 변경?
