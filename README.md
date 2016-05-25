# UI
样式效果笔记

## 显示两行文字，第二行显示半行 ，第二行末尾加上浏览数
<pre>
<code>
//内容所占的大小，屏幕宽减去其他控件占的大小
int contentWidth = ToolsDevice.getWindowPx(mAct).widthPixels - Tools.getDimen(mAct, R.dimen.dp_120);//120=15*2+80+10
String content = map.get("content"); //获取内容
//屏幕第一行能放几个字，
int number = contentWidth / ToolsDevice.sp2px(act, Float.parseFloat(act.getResources().getString(R.dimen.dp_15).replace("dip", "")));
//第二行放一半
int number2 = number + (number / 2);
//如果一行显示不了
if (content.length() >= number) {
	tv_1.setText(content.substring(0, number));
	//如果两行能显示完就不显示后面的省略号
	if (content.length()<= number2 ) {
		tv_2.setText(content.substring(number, content.length()));
	} else {
		tv_2.setText(content.substring(number, number2) + "...");
	}
}else if (content.length() > 0 && content.length() < number) {
	tv_1.setText(content);
}
</code>
</pre>
### 这样再在第二个TextView后面加个浏览数就可以啦
