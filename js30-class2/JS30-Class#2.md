# JS30 - Class #2 (JS + CSS Clock)
### 1.초기 코드
![](https://i.imgur.com/PX6GgKe.jpg)

CSS로 정적인 시계가 구현되어 있다. 이것을 실제 시계로 나타내기 위해서 해야 할 일은 다음과 같다.
* 현재 시각 받아오기
* JS을 이용하여 받아온 현재 시각 Update & CSS 처리
* 실제 시계와 비슷한 효과 주기 

### 2.코드 수정
> .hand {
 transform-origin: 100%;
        transform: rotate(90deg);
        transition: all 0.05s;
        transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
}
>
시계와 같은 회전을 보이기 위해서 3개의 침의 회전 기준이 오른쪽 끝 점이 되어야 한다. transform-origin의 100%는 상하:중간, 좌우:오른쪽을 나타낸다. transition은 화면 전환 시 점진적인 효과를 나타낸다. 이때 transition-timing-function의 값을 cubic-bezier로 설정하여 마치 실제 시계와 같은 움직임을 나타내도록 해줬다.
>  const secondHand = document.querySelector(".second-hand");
      const minsHand = document.querySelector(".min-hand");
      const hourHand = document.querySelector(".hour-hand");
>
3개의 침을 현재 시각에 맞게 각각 처리해줘야 하므로 JS의 변수로 가져온다.
>  function setDate() {
        const now = new Date();
         const seconds = now.getSeconds();
        const secondsDegrees = (seconds / 60) * 360 + 90;
        secondHand.style.transform = `rotate(${secondsDegrees}deg)`;
        const mins = now.getMinutes();
        const minsDegrees = (mins / 60) * 360 + (seconds / 60) * 6 + 90;
        minsHand.style.transform = `rotate(${minsDegrees}deg)`;
        const hour = now.getHours();
        const hourDegrees = (hour / 12) * 360 + (mins / 60) * 30 + 90;
        hourHand.style.transform = `rotate(${hourDegrees}deg)`;
      }
>
Date의 get ~ 함수를 이용하여 현재 시각의 시, 분, 초를 얻을 수 있다. 현재 시각을 이용하여 수학적 계산을 통해 침의 각도를 구한다. 그리고 각 침의 각도를 이용하여 style의 transform 속성의 Rotate 해주면 현재 시각을 나타내는 시계를 구현할 수 있다.
> setInterval(setDate, 1000);
>
setInterval 함수를 통해 1초마다 setDate 함수를 실행시켜 매 초마다 현재 시각을 받아와서 시계에 적용시켜준다.

### 3.결과
![](https://i.imgur.com/IN5UzD0.jpg)
