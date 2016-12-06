> Canvas中文文档 [https://developer.mozilla.org/zhCN/docs/Web/API/Canvas_API](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API)

* 目标效果

![目标效果](http://upload-images.jianshu.io/upload_images/3922003-e49e238659b1bd00.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 代码

  1. HTML
  
			<!--圆环html--> 
			<canvas id="circle" height="132px" width="132px">        
			</canvas>  

  2. JS

		    circle();
		    function circle() {
		        var canvas = document.getElementById('circle');
		        var ctx = canvas.getContext("2d");
		    
		        /*填充文字*/
		    
		        ctx.font = "18px Microsoft YaHei";
		        /*文字颜色*/
		        ctx.fillStyle = '#4b4d4e';
		        /*文字内容*/
		        var insertContent = '语言';
		        var text = ctx.measureText(insertContent);
		        /*插入文字，后面两个参数为文字的位置*/
		        /*此处注意：text.width获得文字的宽度，然后就能计算出文字居中需要的x值*/
		        ctx.fillText(insertContent, (132 - text.width) / 2, 58);
		    
		        /*填充百分比*/
		        ctx.fillStyle = '#e24464';
		        var ratioStr = '25%';
		        var text = ctx.measureText(ratioStr);
		        ctx.fillText(ratioStr, (132 - text.width) / 2, 85);
		    
		        /*开始圆环*/
		        var circleObj = {
		            ctx: ctx,
		            /*圆心*/
		            x: 66,
		            y: 66,
		            /*半径*/
		            radius: 55,
		            /*环的宽度*/
		            lineWidth: 22
		        }
		    
		        /*有色的圆环*/
		        /*从-90度的地方开始画*/
		        circleObj.startAngle = 0;
		        /*从当前度数减去-90度*/
		        circleObj.endAngle = Math.PI * 2 * 0.25;
		        circleObj.color = '#e24464';
		        drawCircle(circleObj);
		    
		        /*灰色的圆环*/
		        /*开始的度数-从上一个结束的位置开始*/
		        circleObj.startAngle = circleObj.endAngle;
		        /*结束的度数*/
		        circleObj.endAngle = Math.PI * 2;
		        circleObj.color = '#e9e9e9';
		        drawCircle(circleObj);
		    
		    }
		    /*画曲线*/
		    function drawCircle(circleObj) {
		        var ctx = circleObj.ctx;
		        ctx.beginPath();
		        ctx.arc(circleObj.x, circleObj.y, circleObj.radius, circleObj.startAngle, circleObj.endAngle, false);
		        //设定曲线粗细度
		        ctx.lineWidth = circleObj.lineWidth;
		        //给曲线着色
		        ctx.strokeStyle = circleObj.color;
		        //连接处样式
		        ctx.lineCap = 'round';
		        //给环着色
		        ctx.stroke();
		        ctx.closePath();
		    }
    


* 其他

   如果要实现这样的效果
   ![目标效果](http://upload-images.jianshu.io/upload_images/3922003-4b1b98133f399520.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
    
    1. 先画灰色的圆环，再画有色的圆环；
    2. 从-90度开始开始画。
    3. 祝你好运。