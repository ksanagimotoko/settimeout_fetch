## 다른서버의 데이터 요청하기 

```javascript
// about:blank 를 실행하고 아래코드를 복사 붙여넣기 합니다.
fetch('https://jsonplaceholder.typicode.com/todos/1');

```
<br>
<br>
<br>
<br>
<br>







```javascript

fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => {
    console.log('C: 응답 도착'); // 네트워크 응답이 오면 실행됨
    console.log(response);
      //return response.json();
  });


```
<br>
<br>
<br>
<br>
<br>

### 응답처리하기 (처리하는것도 역시 시간걸림) 
```javascript
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => {
    console.log('C: 응답 도착'); // 네트워크 응답이 오면 실행됨
    return response.json();
  })
  .then(json => {
    console.log('D: JSON 처리 완료');
    console.log(json); // 실제 데이터 출력
  });



```
<br>
<br>
<br>
<br>
<br>


### 리스트안의 json
https://jsonplaceholder.typicode.com/todos

<br>
<br>
<br>
<br>
<br>


### 버튼으로 데이터 요청하기 
```html
<!DOCTYPE html>
<html lang="ko">
<head>
</head>
<body>
    <button id="fetchBtn">데이터 가져오기</button>
    <div id="result">
        <p class="loading">버튼을 클릭하여 데이터를 가져오세요.</p>
    </div>

    <script>
        const fetchBtn = document.getElementById('fetchBtn');
        const resultDiv = document.getElementById('result');

        fetchBtn.addEventListener('click', () => {
            // 버튼 비활성화 및 로딩 표시
            fetchBtn.disabled = true;
            resultDiv.innerHTML = '<p class="loading">데이터를 가져오는 중...</p>';

            fetch('https://jsonplaceholder.typicode.com/todos/1')
                .then(response => {
                    console.log('C: 응답 도착'); // 네트워크 응답이 오면 실행됨
                    return response.json();
                })
                .then(json => {
                    console.log('D: JSON 처리 완료');
                    console.log(json); // 실제 데이터 출력
                    
                    // 결과를 div로 나누어서 화면에 표시
                    let my_html = '<h3>결과:</h3>';
                    for (let key in json) {
                        my_html += `
                            <div class="data-item">
                                <div class="data-label">${key}:</div>
                                <div class="data-value">${json[key]}</div>
                            </div>
                        `;
                    }
                    resultDiv.innerHTML = my_html;
                    
                    // 버튼 다시 활성화
                    fetchBtn.disabled = false;
                })
                .catch(error => {
                    console.error('에러 발생:', error);
                    resultDiv.innerHTML = `
                        <div class="error">
                            <strong>에러 발생:</strong><br>
                            ${error.message}
                        </div>
                    `;
                    fetchBtn.disabled = false;
                });
        });
    </script>
</body>
</html>



```
