# JS30 - Class #4 (Array Cardio Day 1)
### 1.초기 코드
![](https://i.imgur.com/MEgfvhZ.jpg)
위와 같은 배열이 주어져있고, Array.prototype의 filter, map, sort, reduce를 적용시켜본다. 이때 Prototype이란, JS에서 Function() 인스턴스에 자동으로 만들어지는 속성이다. 인스턴스들은 생성자 함수의 prototype 속성을 통해 공통의 메소드와 속성을 공유하고 상속한다.
### 2.코드 수정 및 결과
1. Array.prototype.filter
> const fifteen = inventors.filter((inventor) => (inventor.year >= 1500 && inventor.year < 1600));
> 
Arrow Function을 이용하여 inventor의 year가 1500 이상, 1600 미만이면 Filter하여 fifteen 배열로 저장해줬다. console.table을 이용하여 출력한 결과는 다음과 같다. console.table은 table 형태로 출력한다.
![](https://i.imgur.com/MzqjVLi.jpg)

2. Array.prototype.map
> const fullNames = inventors.map(
        (inventor) => `${inventor.first} ${inventor.last}`
      );
>
Array.prototype.map을 이용하여 모든 요소에 대하여 해당 Arrow Function을 통해 새로운 배열을 재구성한다. inventors의 각 배열의 first와 last를 공백을 두고 배열을 구성한다.
![](https://i.imgur.com/G5N5Hql.jpg)

3. Array.prototype.sort
> const ordered = inventors.sort((a,b) => a.year > b.year ? 1:-1);
> 
특정 조건에 따라 정렬해주는 함수이다. a, b가 주어지고 a의 year가 크면 1, 아니면 -1이므로 year 기준 오름차순으로 정렬된다.
![](https://i.imgur.com/aulamf5.jpg)

4. Array.prototype.reduce
> const totalYears = inventors.reduce((total, inventor) => {
        return total + (inventor.passed - inventor.year);
      }, 0);
>
reduce는 누적 계산을 나타낸다. inventors의 모든 수명의 합을 구하기 위해 inventor.passed - inventor.year으로 수명을 계산하고 total에 더해서 return한다. 초기 값은 0이 된다.
![](https://i.imgur.com/HOg47di.jpg)
