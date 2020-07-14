# hover시 밑줄이 생기는 menu

## 1. preview

### flex, before, after, transition, transform, overflow, fontawesome 사용
#### 요소의 앞뒤를 디자인하는 가상클래스 before, after

<img width="80%" src="https://j.gifs.com/vlB9N8.gif" />


## 2. 코드 분석

### 1) html

#### (1) a태그안에 icon 태그
- `icon` : `fontawesome`의 태그를 이용한다.

```html
<body>
    <div class="sns">
        <a href="#none"><i class="fa fa-facebook"></i></a>
        <a href="#none"><i class="fa fa-twitter"></i></a>
        <a href="#none"><i class="fa fa-google-plus"></i></a>
        <a href="#none"><i class="fa fa-linkedin"></i></a>
        <a href="#none"><i class="fa fa-instagram"></i></a>
    </div>
</body>

```

<br/><br/>

### 2) css

#### (1) 필요한 기능 import하기
- `Google Web Font`, `Fontawesome 4.7`을 import한다.
            
```css
/* Google Web Font */
@import url('https://fonts.googleapis.com/css?family=Raleway&display=swap');

/* Fontawesome 4.7 */
@import url('https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css');

```

<br/>

#### (2) 내부 요소를 중앙정렬시키기
- `body`내부 요소를 중앙정렬한다.


```css
body{
    margin: 0;
    display: flex;
    justify-content: center;  /*수평정렬*/
    align-items: center;      /*수직정렬*/
    height: 100vh;
}

a {
    text-decoration: none;
    color: #222;
  }
```


<br/>

#### (3) sns 태그의 a태그 구성하기

-`.sns a`에 크기 지정 및 가상클래스 생성하기

  : `a`태그는 `inline`구조로, 크기값을 줄 수 없지만, `display: inline-block`을 하면 크기값을 줄 수 있음  

  : `a`태그 안의 아이콘을 `text-align`, `line-height`로 수직, 수평중앙 설정하기
  
<br/>

-`.sns a`의 가상클래스 `before`를 위한 사전설정
  
  : `a`태그의 가상 자식요소인 `before`의 위치 고정을 위해 `a`태그의 속성을 `position:relative`를 함
  
  :  그러면 가상클래스를 부모 위에 겹칠 수 있게 됨.
  
  : `overflow: hidden`으로 설정하여, `a`의 자식인 `before`의 넘친 부분을 없앰
  
  <img  width="150%" src="https://postfiles.pstatic.net/MjAyMDA3MTRfMjU4/MDAxNTk0NzExNjE5MzE3.wnl2VJe1ng9WmMsnsXhRgGBh7b58EX18UEZMQxKtTXsg.LpNeZqoib8obm0bqRnORMzjvw8GehummTCiiMX61A_sg.PNG.rmawjdals/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-07-09_%EC%98%A4%ED%9B%84_8.53.13.png?type=w580"/>
  
  
  : 네모모양을 부모와 같은 둥글며 겉선이 흰색인 상태로 하기 위해) 
    자식의 넘치는 부분을 숨기게 함*/
  
```css
.sns{
    background-color: #f8f8f8;
    padding: 40px;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.13);
}

.sns a{
    border: 5px solid white;
    display: inline-block;      /*a태그 크기 조정 가능*/
    width: 80px;
    height: 80px;
    border-radius: 50%;
    font-size: 40px;
    background-color: #fff;
    margin : 10px;
    
    /* a태그안의 아이콘을 수직, 수평중앙시키기 */
    text-align: center;  /*수평중앙*/
    line-height: 1.2;    /*수직중앙, 이 속성을 자신의 높이값만큼 주면 수직중앙에 위치함*/

    position: relative;  /* 가상 자식요소인 before의 위치 고정*/
    overflow: hidden;    /* before의 부모인 a태그의 overflow : hidden 설정*/
}
    
```

