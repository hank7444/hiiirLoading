HiiirLoading.js
==================

# Description

寫來自己方便做loading效果的plugin, 有全畫面loading跟針對特定區塊loading並遮蔽區塊的功能

This is a really simple jquery plugin for showing loading effect.

It has only two effect, full-loading & area-loading.


## How to use it ##

### step1: link the CSS file

```
<link href="hiiirLoading/hiiirLoading.css" rel="stylesheet">
```

### step2: link the js file & jquery

```
    <script src="jquery-1.9.1.min.js"></script>
    <script src="hiiirLoading/hiiirLoading.js"></script>
```

### step3: use & enjoy it!

```
	// full
	$.hiiirLoading('fadeIn', settings);
	$.hiiirLoading('fadeOut', settings);
	
	// area
	$(selector).hiiirLoading('fadeIn', settings);
	$(selector).hiiirLoading('fadeOut', settings);
	
```


## options


```
// fadeIn
$.hiiirLoading('fadeIn', {
	msg: '測試fadeIn', // loading面板上要顯示的訊息
	time: 1000, // fadeIn的時間, 單位:ms, 預設值: 1000
	isFade: true, // 是否要使用fade遮蔽全部畫面, 預設值: true
	startCallback: function() { // 當開始fadeIn時呼叫
		console.log('fadeIn Start');
	},
	endCallback: function() { // 當fadeIn結束時呼叫
		console.log('fadeIn End');
	}
});

// fadeOut
$.hiiirLoading('fadeOut', {
	time: fadeOut的時間, 單位:ms, 預設值: 1000
	startCallback: function() { // 當開始fadeOut時呼叫
		console.log('fadeOut Start');
	},
	endCallback: function() { // 當fadeOut結束時呼叫
		console.log('fadeOut End');
	}
});

指定區域loading:

// fadeIn
$('#testarea').hiiirLoading('fadeIn', {
	time: 1000, // fadeIn的時間, 單位:ms, 預設值: 1000
	isFade: true, // 是否要使用fade遮蔽全部畫面, 預設值: true
	startCallback: function() { // 當開始fadeIn時呼叫
		console.log('begin area fadein');
	},
	endCallback: function() { // 當fadeIn結束時呼叫
		console.log('finish area fadein');
	},
	loading: { // loading圖示設定
		//top: 20, // 同等margin-top, 預設值: 0
		//left: 40 // 同等margin-left, 預設值: 0
	},
	fade: { // fade參數設定
		width: '100%', // 寬度, 預設值: '100%'
		height: '100%', // 高度, 預設值: '100%'
		top: 0, // 同等margin-top, 預設值: 0
		left: 0, // 同等margin-left, 預設值: 0
		zindex: 5000, // 同等zindex, 預設值: 5000
		selectors: [ // 其他區塊要跟著用fade遮蔽時, 在此陣列中設定
			{
				selector: $('#sidearea'), // 區塊物件
				settings: {
					width: '100%', // 寬度, 預設值: '100%'
					height: '100%', // 高度, 預設值: '100%'
					top: 0, // 同等margin-top, 預設值: 0
					left: 0, // 同等margin-left, 預設值: 0
					zindex: 5000, // 同等zindex, 預設值: 5000
				}
			},
			{
				selector: $('#anotherarea'),
				settings: {}
			}
			...
		]
	},
});

// fadeOut
$('#testarea').hiiirLoading('fadeOut', {
	time: 1000, // fadeOut的時間, 單位:ms, 預設值: 1000
	startCallback: function() {	// 當開始fadeOut時呼叫
		console.log('begin area fadeout');
	},
	endCallback: function() {	// 當fadeOut結束時呼叫
		console.log('finish area fadeout');
	},
	fade: {
		selectors: [
			{
				selector: $('#sidearea'), // 區塊物件
			},
			{
				selector: $('#anotherarea'),
			}
			...
		]
	}
});

```
    


