
# 地图 api


``` xml
<div id="map-container"></div>
```


``` xml
<script src="js/jquery.2.1.1.min.js"></script>
<script src="https://map.qq.com/api/gljs?v=1.exp&key=xxxxx"></script>
<script>
    //  code here
</script>
```

``` javascript

window.onload = function(){
    initMap();
}

function initMap() {
    //定义地图中心点坐标
    var center = new TMap.LatLng(10101010, 29229929)
    //定义map变量，调用 TMap.Map() 构造函数创建地图
    var map = new TMap.Map(document.getElementById('map-container'), {
        center: center,//设置地图中心点坐标
        zoom: 17.2, //设置地图缩放级别
    });

    //初始化marker
    var marker = new TMap.MultiMarker({
        id: "marker-layer", //图层id
        map: map,
        styles: { //点标注的相关样式
            "marker": new TMap.MarkerStyle({
                "width": 25,
                "height": 35,
                "anchor": { x: 16, y: 32 },
                "src": "img/contact_gps.png"
            })
        },
        geometries: [{ //点标注数据数组
            "id": "1",
            "styleId": "marker",
            "position": new TMap.LatLng(39.786817,116.563221),
            "properties": {
                "title": "marker"
            }
        }]
    });
}

````


## 参考

- https://lbs.qq.com/javascript_gl/index.html
