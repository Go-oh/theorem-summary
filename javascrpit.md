
### 기초 명령어

command | meaning
--------|------------
alert();    | 브라우저에 경고창 출력(팝업창). int, double, string 출력가능
console.log(); | console 창에 출력
document.write(); | 브라우저 자체에 출력
typeof() | 타입확인. *number(int, double)* or *string* 오로 출력

```javascript
alert(10);          //chrome에 10출력
alert(10*10)        //chrome에 100출력
console.log(20);    //console에 20출력
document.write("hello world!"); //chrome에 hello world! 출력
typeof 10           //number
typeof 10.1         //number
typeof "hi"         //string
```

### Math class

command | meaning
--------|------------
Math.pow() | power, 제곱
Math.round() | 반올림
Math.ceil() | 올림
Math.floor() | 내림

```javascript
Math.pow(3, 2);         //3^2 = 9
Math.round(2.3);        //2
Math.round(2.7);        //3
Math.ceil(2.1);         //3
Math.floor(2.9);        //2
```

### String class

command | meaning
--------|------------
.length | 문자열 길이
.indexOf() | 문자열 위치 


### 변수

command | meaning
--------|------------
var     | 변수 선언

```javascript
var a = 1;
alert(a);       //1
var b = 2, c = 3;
alert(b+c)      //5
```

### 비교

- `==` : 단순 비교
- `===` : 엄격히 비교(strict equal). 동등 연산자라고도 하며 `data type`이 일치하면 true
    - <a href="http://bitly.kr/DyPQrT6441f"> javascript equality table </a>

```javascript
alert(1 == '1');            //true
alert(1 === '1');           //false
//undefined와 null은 '아무값도 없는 것'이나 프로그래머가 의도했는지, 그렇지 않은지가 다름
alert(undefined == null)    //true
alert(undefined === null)   //false

// 참고
typeof null         //"object"
typeof undefined    //"undefined"
typeof 1            //"number"
typeof "1"          //"string"
typeof '1'          //"string"
typeof NaN          //"number", NaN = Not a Number ex)0/0 = NaN
var a = 1;          //"number". if(a), true
var a;              //"undefined". if(a), false
```

### 비교와 prompt

- `prompt()` : 프롬프트창을 띄움. 사용자로부터 입력받을때 사용

```javascript
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8"/>
    </head>
    <body>
        <script type="text/javascript">
            var id = prompt("아이디를 입력하세요");
            if(id == 'Go-oh'){
                var passwd = prompt("비밀번호를 입력하세요");
                if(passwd == 1111)
                    alert(id + "님 반갑습니다.");
                else 
                    alert("다시 로그인 해주세요");
            }
            else
                alert("아이디를 다시 입력해주세요")
        </script>
    </body>
</html>
```