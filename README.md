/*code-block-header*/
.code-block-header{
    position: relative;
}
.code-block-header:before {
    content: attr(pre_title);
    font-weight: bold;
    color: yellow;
    background-color: gray;
  font-size: 16px;
  padding: 2px 5px 0px 5px;
  position: absolute;
  top: 0;
  left: 0;
}
<pre class="code-block-header" pre_title="setup.py"><code class="language-python">
from setuptools import setup
setup()
</code></pre>

# test
``` javascript:hoge.txt
console.log("aaa")
```
``` javascript:aaa.js
var dc = document.getElementById('canvas').getContext('2d');
```

