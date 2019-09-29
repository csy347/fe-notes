# select 

``` css
select {
    border: solid 1px transparent; 
    /* Chrome和Firefox里面的边框是不一样的 */ 
    appearance:none; /*很关键：将默认的select选择框样式清除*/
    -moz-appearance:none;   
    -webkit-appearance:none; 
    
    /*在选择框的最右侧中间显示小箭头图片*/  
    background: url("../img/arrow-down.png") no-repeat scroll right center transparent;   
    /*为下拉小箭头留出一点位置，避免被文字覆盖*/  
    padding-right: 14px;
  
}

/*清除ie的默认选择框样式清除，隐藏下拉箭头*/  
select::-ms-expand { display: none; }

```

## 参考

http://www.imooc.com/wenda/detail/560853