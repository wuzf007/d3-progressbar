# d3-progressbar
## 组件使用方式
### 第一步：使用vue-cli 构建项目

安装vue脚手架;

```
//代码块
npm install -g @vue/cli;
```

d3 插件：;
```
//代码块
npm install -g -d3;
```

### 第二步：创建项目
<br/>

```
vue create test
```

### 第三步：全局注册组件

在main.js里面导入组件;

```
//代码块
import d3progressbar from "d3-progressbar";
Vue.use(d3progressbar);
```

### 第四步：组件使用

```
//代码块
<template>
  <div class="about">
    <d3progressbar :bardata=bardata></d3progressbar>
  </div>
</template>
<script>
	var barjson = {
			max:898, //进度条的最大值 ，同时也是进度条的值域 domain 
			space:40,//上下进度条的间距大小
			size:16,//文字的大小
			width:400,//svg的总宽度，即显示区域的总宽度
			rangelength:300,//比例尺映射的宽度，即映射域 range
			height:120,//svg的高度，即显示区域的总高度
			barheight:10,//进度条的高度
			pleft:80,//进度条距离左侧的宽度
			unit:"%",//单位 可选值为任意值
			r:1,//进度条的圆角值
			fontColor:"#000",
			barColor:["#ffff00","#ff6e02"],//进度条的渐变色 接收数组和字符串 ["red","#fff"] 或者 "#abbbdd"
			maxnumber:700, //显示数字的百分比总值，如果unit为%的时候可起作用
			// 主体样式
			// radius 圆角 如果参数没有r值的话，起作用 ，进度条圆角 可选
			// nameleft 左侧文字居左对齐,可选值有nameright 可选
			// after 右侧数字是紧跟在进度条的后面 可选值有 right ,数字在总进度条长度的右侧 可选
			// sortdown 数组排序 降序排列 可选值有sortup 升序排列 可选
			theme:"radius-nameright-after-sortdown", 
			data:[//进度条数据展示
				{"name":"学生证","number":700},
				{"name":"驾驶证吗","number":308},
				{"name":"身份证","number":208}
			]
		};
	export default{
		data(){
			return{
				bardata:barjson
			}
		},
		mounted(){
			var data = this.bardata.data;
			setInterval(function(){
				for(var i = 0; i < data.length; i++){
					var dataitem = parseInt(Math.random()*200+400);
					data[i].number = dataitem;
				}
			},2000);
		}
	}
</script>

```
