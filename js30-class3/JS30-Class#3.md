# JS30 - Class #3 (Playing with CSS Variables and JS)
### 1.초기 코드
![](https://i.imgur.com/dqQvzZq.jpg)

맨 위에 'Update CSS Variables with JS'라는 문구가 나타나있다. 이때 'JS'는 hl이라는 Class로 지정되어 있다. 바로 밑에는 Range 설정이 가능한 Spacing, Blur와 색상 설정이 가능한 Base Color가 존재한다. 마지막으로 제일 아래에는 사진 한 장이 나타나있다. 초기 코드는 Range 혹은 Color Picker 기능이 작동하지 않는다. 이것을 기능에 맞게 작동하기 위해 코드를 수정해야 한다.
* 실시간으로 변하는 값들을 바로 적용 가능하도록 변수화
* addEventListener를 통해 실시간 적용

### 2.코드 수정
> :root {
    \-\-base: yellow;
}
>
root 아래에서 (전역) --base라는 변수 사용
> img {
    background: var(\-\-base)
}
>
var으로 변수 값을 불러와서 사용
> const inputs = document.querySelectorAll(".controls input")
>
controls 클래스의 하위 모든 input 태그를 변경
> function handleUpdate() {
    const suffix = this.dataset.sizing || "";
>
this.dataset을 통해 data-에 접근하고, sizing 속성 값이 있으면 값을 사용
(Color를 나타내는 \-\-base는 "px" 형태가 아니다.)
> document.documentElement.style.setProperty(
    `--${this.name}`, this.value + suffix);
    }
>
setProperty 함수를 이용하여 값 변경
> inputs.forEach((input) => input.addEventListener("change", handleUpdate))
> inputs.forEach((input) => input.addEventListener("mousemove", handleUpdate))
> 
Arror Function을 이용하여 값이 변경되거나 마우스가 움직였을 때 Event Listener 추가
### 3.결과
![](https://i.imgur.com/2IHr3WX.jpg)
