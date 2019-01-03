```
svg.selectAll("aaa")
    .data(data)
    .enter()
```
- "aaa"를 찾고, data를 aaa와 bind
- enter()는 data중 aaa에 있지 않은 아이들만 return 
[D3.js: How to handle dynamic JSON Data](http://pothibo.com/2013/09/d3-js-how-to-handle-dynamic-json-data/)