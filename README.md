# Offset介绍
```html 
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Offset介绍</title>
    <style>
        html,body{
            width: 100%;
            height:100%;
            margin:0  0;
            padding: 0 0;
        }
        .box{
            width: 80px;
            height:80px;
            position: absolute;
            background-color: saddlebrown;

        }
        .ras{
            width: 80px;
            height:80px;
            position: absolute;
            background-color: rebeccapurple;
            border-radius: 50%;
        }


    </style>
</head>
<body>
<div class="box" id="box"></div>
<div class="ras" id="ras"></div>



<script src="node_modules/jquery/dist/jquery.js"></script>
<script src="js/offset.js"></script>
</body>
</html>
```
```javascript



/////定义一个位置对象
var position = {};
position.top = 100;
position.left = 0;

/////步长 每一下移动的距离
var stepLength = 10;
$(function(){

    var maxHeight = $(window).height(); ////纵向移动的最大值
    var directionY = 1; ////移动的方向

    var maxWidth = $(window).width();
    var directionX = 1;

    /////分别设置x和y方向的速度
    var speedX = stepLength*Math.random();
    var speedY = stepLength*Math.random();

    /////设置offset的时候需要一个包含top和left的对象
    $("#box").offset(position);


    function move(){
        if(position.top>=(maxHeight-80)){
            directionY = -1;
        }
        if(position.top <= 0){
            directionY = 1;
        }

        if(position.left>=(maxWidth-80)){
            directionX = -1;
        }
        if(position.left<=0){
            directionX = 1;
        }
        position.top = position.top + directionY*speedY;
        position.left = position.left + directionX*speedX;


        $("#box").offset(position);
        requestAnimationFrame(move);
    }
    requestAnimationFrame(move);

    /////当窗体改变大小的时候重新设置移动的范围
    $(window).resize(function(){
        maxHeight = $(window).height();
        maxWidth = $(window).width();
    })
});
//$(".box").addClass('ras');//添加样式

var positions = {};
positions.top = 200;
positions.left = 10;
var  stepLengths = 2;
$(function(){

    var maxHeight = $(window).height(); ////纵向移动的最大值
    var directionY = 1; ////移动的方向

    var maxWidth = $(window).width();
    var directionX = 1;

    /////分别设置x和y方向的速度
    var speedX = stepLengths*Math.random();
    var speedY = stepLengths*Math.random();

    /////设置offset的时候需要一个包含top和left的对象
    $("#ras").offset(position);


    function move(){
        if(positions.top>=(maxHeight-80)){
            directionY = -2;
        }
        if(positions.top <= 0){
            directionY = 2;
        }

        if(positions.left>=(maxWidth-80)){
            directionX = -2;
        }
        if(positions.left<=0){
            directionX = 2;
        }
        positions.top = positions.top + directionY*speedY;
        positions.left = positions.left + directionX*speedX;


        $("#ras").offset(positions);
        requestAnimationFrame(move);
    }
    requestAnimationFrame(move);

    /////当窗体改变大小的时候重新设置移动的范围
    $(window).resize(function(){
        maxHeight = $(window).height();
        maxWidth = $(window).width();
    })
});




```
