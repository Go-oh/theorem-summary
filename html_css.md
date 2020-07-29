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
- 추후 서술되지만, *position* 은 *margin* 에 적용된다. 즉, *content, padding, border, margin, position*
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
		- block 단위로 표시  
        ex)p(paragraph), h1(heading 1), div
    - inline element  
		- line(한 줄) 단위로 표시  
        ex)strong, span
		
- 위치  
	- 상대위치 : 기존 위치를 기준으로 위치 설정
	- 절대위치 : 문서 전체를 기준으로 위치 설정. 단, **부모 요소가 `position:relative;`면 부모 요소를 기준**으로 위치 설정
		- 박스가 겹치는 경우, `z-index` 를 이용해 앞으로 끌어오거나 맨 뒤로 보낼수 있다.
	- 고정위치 : 브라우저상에서 (*스크롤 무관하게*) 항상 보이게 할 때. 즉, 항상 같은 위치로 설정   
	
	참고 : <a href="https://jongpak.com/prob/post/52"> 절대위치와 상대위치 </a>  
	
위치 | 표기  
--------|--------  
상대위치 |position:relative;  
절대위치 |position:absolute;
고정위치 |position:fixed;


- floating
	- 박스를 좌 or 우로 배치
	- float 후에는 반드시 clear로 플로팅을 해제해야함
	
```html
<style>
	.mybox {    
	background:#999;
    width:300px;
    height:50px;
    float:both;
}
.mybox2 {    
	background:#999;
    width:300px;
    height:50px;
    float:left;
}
.mybox3 {    
	background:#aa0;
    width:300px;
    height:50px;
    float:right;
}

//별도의 class를 두어 clear 한다.
.clear {    
    /* 플로팅을 clear 해주지 않으면 레이아웃이 제대로 표시되지 않는다 */    
    clear:both;    
}
</style>

<div class="mybox">
    왼쪽 플로팅
</div>
<div class="mybox2">
    오른쪽 플로팅
</div>
<div class="mybox3">
    안녕하세요
</div>
<div class="clear"></div>
```
<a href="https://codepen.io/go-oh/pen/WNrWpNR"> 결과보기 </a>
