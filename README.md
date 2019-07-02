# d3-progressbar
# 组件使用方式
# 第一步：使用vue-cli 构建项目
安装vue脚手架：npm install -g @vue/cli
#  
d3 插件：npm install -g -d3
# 第二步：创建项目
vue create test
# 第三步：全局注册组件
在main.js里面导入组件
<br/>
import d3progressbar from "d3-progressbar";
<br/>
Vue.use(d3progressbar);
# 第四步：组件使用
<br/><template>
<br/>  <div class="about">
<br/>    <d3-progressbar :bardata=bardata></d3-progressbar>
<br/>  </div>
<br/></template>
<br/><script>
<br/>	var barjson = {
<br/>			max:898, //进度条的最大值 ，同时也是进度条的值域 domain 
<br/>     space:40,//上下进度条的间距大小
<br/>			size:16,//文字的大小
<br/>			width:400,//svg的总宽度，即显示区域的总宽度
<br/>			rangelength:300,//比例尺映射的宽度，即映射域 range
<br/>			height:120,//svg的高度，即显示区域的总高度
<br/>			barheight:10,//进度条的高度
<br/>			pleft:80,//进度条距离左侧的宽度
<br/>			unit:"%",//单位 可选值为任意值
<br/>			r:1,//进度条的圆角值
<br/>			fontColor:"#000",
<br/>			barColor:["#ffff00","#ff6e02"],//进度条的渐变色 接收数组和字符串 ["red","#fff"] 或者 "#abbbdd"
<br/>			maxnumber:700, //显示数字的百分比总值，如果unit为%的时候可起作用
<br/>			// 主体样式
<br/>			// radius 圆角 如果参数没有r值的话，起作用 ，进度条圆角 可选
<br/>			// nameleft 左侧文字居左对齐,可选值有nameright 可选
<br/>			// after 右侧数字是紧跟在进度条的后面 可选值有 right ,数字在总进度条长度的右侧 可选
<br/>			// sortdown 数组排序 降序排列 可选值有sortup 升序排列 可选
<br/>			theme:"radius-nameright-after-sortdown", 
<br/>			data:[//进度条数据展示
<br/>				{"name":"学生证","number":700},
<br/>				{"name":"驾驶证吗","number":308},
<br/>				{"name":"身份证","number":208}
<br/>			]
<br/>		};
<br/>    export default{
<br/>		    data(){
<br/>		    	return{
<br/>		    		bardata:barjson
<br/>		    	}
<br/>		    },
<br/>    	mounted(){
<br/>		    	var data = this.bardata.data;
<br/>		    	setInterval(function(){
<br/>		    		for(var i = 0; i < data.length; i++){
<br/>		    			var dataitem = parseInt(Math.random()*200+400);
<br/>		       			data[i].number = dataitem;
<br/>			    	}
<br/>	    		},2000);
<br/>	    	}
<br/>    	}
<br/></script>
