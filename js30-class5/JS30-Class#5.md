# JS30 - Class #5 (Flex Panels Image Gallery)
### 1.초기 코드

![](https://i.imgur.com/2VdG15a.jpg)

우리가 만들어야 할 웹 페이지와 다르게 아이템들이 1열로 정렬되어 있다. 또한 애니메이션 효과도 존재하지 않는다. 이번 Class를 통해 CSS와 CSS Flex에 대해 배운다.

### 2.코드 수정
> .panels{
    display: flex;
}
>
아이템들을 Column으로 정렬하고 관리하기 위해 Flexible Box로 선언해준다.

> .panel{
        flex: 1;
        justify-content: center;
        display: flex;
        flex-direction: column;
}
>
모든 panel(item)의 증가 너비, 감소 너비를 1로 설정해주었다. flex-basis의 값이 default로 auto로 설정됐기 때문에 남은 공간이 없도록 동등하게 구역을 나눠 정렬된다. justify-content를 통해 아이템의 진행축 배치를 설정할 수 있다. center 값을 줌으로서 item의 문자가 가운데로 배치되었다. 이때 진행축의 방향은 세로이다. display: flex를 통해 문자들을 Flexible Box로 선언해주고 flex-direction을 통해 하나의 행으로 정렬 돼있던 문자들을 하나의 열로 정렬 해준다.

> .panel > *{
        flex: 1 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
}

flex: 1 0 auto;를 통해 문자들이 panel에서 빈 공간을 갖지 않도록 정렬된다. 그리고 각 문자들을 Flex Container로 설정한 뒤 justify-content와 align-items 값 설정을 통해 문자들을 가운데로 배치했다.

> .panel > *:first-child {
        transform: translateY(-100%);
      }
      .panel.open-active > *:first-child {
        transform: translateY(0);
      }
      .panel > *:last-child {
        transform: translateY(100%);
      }
      .panel.open-active > *:last-child {
        transform: translateY(0);
      }
>

아무것도 하지 않는 기본 상태에서는 2번째 child 문자만 나타나므로 first-child와 last-child의 y 값을 평행이동하여 나타나지 않도록 한다. 그리고 panel 위에 마우스를 올렸을 때 없었던 문자들이 나타나야 하므로 open-active 상태가 되면 다시 원래 위치로 이동한다.

> const panels = document.querySelectorAll(".panel");
    function toggleOpen() {
        console.log("Hello");
        this.classList.toggle("open");
      }
    function toggleActive(e) {
        console.log(e.propertyName);
        if (e.propertyName.includes("flex")) {
          this.classList.toggle("open-active");
        }
      }
    panels.forEach((panel) => panel.addEventListener("click", toggleOpen));
      panels.forEach((panel) =>
        panel.addEventListener("transitionend", toggleActive)
      );
>
다음은 Java Script 코드이다. CSS를 수정한 상태에서 원하는 웹 페이지를 만들기 위해 추가해야할 기능은 마우스 클릭했을 때 해당 panel의 크기가 커지는 기능과 숨겨진 문자들을 나타나게 하는 것이다. 먼저 panel들을 변수로 저장하고, 마우스 클릭 됐을 때 toggleOpen이라는 함수가 실행되도록 EventListener를 추가해준다. 이때 애니메이션의 순서는 panel의 크기가 먼저 커지고, 다음으로 숨겨진 문자가 나타난다. CSS의 코드 중에서 panel의 크기와 글자의 크기를 증가시키는 내용이 있다.
> .panel.open {
        flex: 5;
        font-size: 40px;
      }
>
panel, open 2개의 class를 가지면 크기가 바뀌게 된다. 초기 class에는 open class가 없기 때문에 EventListener를 통해 open class를 추가해줘야 한다. 순서를 지키기 위해 먼저 마우스 클릭 됐을 때 this.classList.toggle을 통해 open이라는 class를 추가시켜준다. 만약 open이 없으면 추가시켜주고 있다면 제거해준다. 이후 안보였던 문자들을 나타내야하므로 Transition이 끝났을 때 toggleActive 함수를 실행시켜준다. open-active class의 속성은 1번째 자식 문자와 3번째 자식 문자들의 y 좌표를 원래대로 이동하는 것이다. 이때 Transitionend Event는 다른 곳에서도 불러질 수 있기 때문에 Transition된 속성을 이용한다. flex-grow와 font-size 값이 바뀌었으므로 e.PropertyName은 2개의 속성을 포함한다. 조건문을 통해 "flex"를 포함한다면 open-active class를 추가한다.

### 3.실행 결과

![](https://i.imgur.com/TlNzxNn.jpg)

