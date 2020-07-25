### Selector : 선택자
- 우선순위로 *inline > id > class* 이다.
    - inline
        - 말그대로 inline에 때려박음 
    - id : `#`으로 구분한다.     
    - class : `.`으로 구분한다.
        
```html
<style>
    #id {color:green;}
    .class {color:blue;}
</style>

//inline이 적용됨
<div id='id' class='class' style='color:magenta'>
  Go-oh
</div>

//id가 적용됨
<div id='id' class='class'>     
    Go-oh
</div>

//class가 적용됨
<div class='class'>     
    Go-oh
</div>
```
<a href="https://codepen.io/go-oh/pen/jOWRPzo"> 결과보기 </a>

- 선택자 활용의 좋은 예
    - id 선택자가 객체처럼 되어 class 선택자를 하나하나 다룬다.  
    -> 세부적인 수정 가능
    
```html
<style>
#memo.title {color:red; font-size: 20pt;}
#memo.content {color:blue; font-size: 11pt;}
</style>

<sector id="memo">
<p class="title">글 제목</p>
<p class="content">여기는 글 내용입니다.</p>
</sector>
```
<a href="https://codepen.io/sinbi/pen/ZBoLXo"> 결과보기 </a>
   
<br><br><br>

### Box model
- 안쪽부터 *content, padding, border, margin* 순이다.

![figure1](https://media.vlpt.us/images/yotae07/post/3fa079c7-5888-489b-8446-6e16ef392f03/margin,%20border,%20padding,%20and%20content.png)

- border: [굵기] [유형] [색상]
```html
border: 5px solid #000;    //실선
border: 5px dotted #0f0;   //점선(원형)
border: 5px dashed #00f;   //점선(사각형)
border: 5px double #ff0;   //이중선
```

- class 선택자를 활용
```html
.mybox{
            background:#999;
            width:300px;
            height:200px;
            margin:15px;
            border: 2px solid #000;    
            padding: 10px;
        }
```

<br><br><br>

### Position
- 화면표시모델
    - block element  
        ex)p, h1, div
    - inline element  
        ex)strong, span
