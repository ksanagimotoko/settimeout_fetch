### n초뒤에 실행하기
```javascript
// 3초 뒤에 hello 출력하기
setTimeout(  function () {
      console.log('hello');
}, 3000);


```

<br>
<br>
<br>
<br>
<br>


### 실행순서 
```javascript
console.log('a');
setTimeout( function () {
    console.log( 'b' );
},3000);
console.log('c');
```






### 2초간격으로 div만들며 텍스트 추가하기 
```javascript

for(let i=0; i < texts.length; i++) {
     setTimeout(function()  {
           const d = document.createElement('div');
           d.innerText = texts[i];
           document.body.appendChild(d);
     }, i*2000);
}

```
