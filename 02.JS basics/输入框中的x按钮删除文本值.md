# 实现输入框中的 x 按钮删除文本值

``` html
<div class="has-feedback">
    <label class="text-info">输入地址</label>
    <input class="form-control"></input>

    <!-- 删除按钮 -->
    <i>&time;</i>
</div>

```

```javascript
$(function(){
    $('i').click(function(){
        $('input')[0].value = '';
    })
})
```
