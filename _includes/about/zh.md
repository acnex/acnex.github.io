Hi，你好，欢迎访问我的博客。

## 足迹：


<div id="containerMap" style="height:400px;margin:3px auto; margin-bottom:40px;" tabindex="0"></div>

 <style>
#containerMap img {
    display: block; 
    max-width: 100%; 
    height: auto; 
    margin: auto auto auto auto !important; 
}
  </style>
<script type="text/javascript">
        //地图点开始
        var provinces = [{
          "name": "北京",
          "center": "116.405285,39.904989",
          "type": 1,
          "url":"#",
          "subDistricts": []
        }, {
          "name": "平泉",
          "center": "118.702322,41.017348",
          "type": 1,
          "url": "https://baike.baidu.com/item/%E5%B9%B3%E6%B3%89/2095343",
          "subDistricts": []
        }, {
          "name": "张家口",
          "center": "114.891135,40.772742",
          "type": 1,
          "url": "https://blog.cseve.com/archives/1615910459M35HZ7.html",
          "subDistricts": []
        }, {
          "name": "衡水",
          "center": "115.888286,37.800551",
          "type": 1,
          "subDistricts": []
        }, {
          "name": "唐山",
          "center": "118.447552,39.731565",
          "type": 1,
          "subDistricts": []
        }, {
          "name": "石家庄",
          "center": "114.462764,38.001667",
          "type": 1,
          "subDistricts": []
        }, {
          "name": "大同",
          "center": "113.283928,40.087981",
          "type": 1,
          "subDistricts": []
        }, {
          "name": "云冈石窟",
          "center": "113.137389,40.112397",
          "type": 1,
          "subDistricts": []
        }, {
          "name": "秦皇岛",
          "center": "119.251592,39.585187",
          "type": 1,
          "subDistricts": []
        }, {
          "name": "承德",
          "center": "117.943481,40.970627",
          "type": 1,
          "url": "https://baike.baidu.com/item/%E6%89%BF%E5%BE%B7", 
          "subDistricts": []
        }


        ];


        /**
        https://www.opengps.cn/Map/Tools/PickUpGPS_AMap.aspx
        **/

        //地图点结束


</script>

<script src="https://webapi.amap.com/maps?v=1.4.2&key=84ab23d4c9937d16d9e5cb127d9f123c"></script>
<script type="text/javascript">


        var map = new AMap.Map('containerMap',{resizeEnable: true,zoom:4});
        var markers = []; //province见Demo引用的JS文件
        for (var i = 0; i < provinces.length; i += 1) {
          var marker;

          if (provinces[i].type === 0) {
            var icon = new AMap.Icon({
              image: 'https://vdata.amap.com/icons/b18/1/2.png',
              size: new AMap.Size(24, 24)
            });
            marker = new AMap.Marker({
              icon: icon,
              position: provinces[i].center.split(','),
              offset: new AMap.Pixel(-12,-12),
              zIndex: 101,
              title: provinces[i].name,
              map: map
            });


          } else {
            marker = new AMap.Marker({
              position: provinces[i].center.split(','),
              title: provinces[i].name,
              url:provinces[i].url,
              map: map
            });



            if (provinces[i].type === 2) {
              var content= "<div class = 'taiwan'>宝岛台湾</div>";
              baodao = new AMap.Marker({
                content: content,
                position: provinces[i].center.split(','),
                title: provinces[i].name,
                offset: new AMap.Pixel(0,0),
                map: map
              });
            }

          }

          //s
          //点击合法marker重定向到parkInfo页面
          var _onClick = function(e) {
                  
             window.open(this.w.url,"_blank");        
          }
          //e
          markers.push(marker);
          //给所有的点标注添加点击事件
          AMap.event.addListener(marker, 'click', _onClick);
        }
        map.setMapStyle("amap://styles/normal");
        map.setFitView();
      </script>
<script type="text/javascript" src="https://webapi.amap.com/demos/js/liteToolbar.js"></script>
