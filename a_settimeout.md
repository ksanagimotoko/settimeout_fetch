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

### 2초간격으로 div만들며 텍스트 추가하기 
```html

<!DOCTYPE html>
<html lang="ko">
<body>
    <div class="container" id="container"></div>

    <script>
        const texts = ['hello', 'my name is', 'young-su'];
        const container = document.getElementById('container');

        texts.forEach((text, index) => {
            setTimeout(() => {
                const div = document.createElement('div');
                div.className = 'text-item';
                div.textContent = text;
                container.appendChild(div);
            }, index * 2000); // 2초 간격 (2000ms)
        });
    </script>
</body>
</html>




```
