**jQuery** provides support for standard JS mouse events as well as some custom ones. In jQuery it’s easy to capture whether mouse point has entered in the boundary of an object or left from (mouseenter, mouseleave) or something else happened (like click, dblclick etc). But you are in trouble if you need to capture the direction of your mouse. And it would be fantastic if there was a plugin which can fire custom mouse-direction event on any elements which you can then listen to and bind a listener routine.

I wrote this small plugin (jQuery MouseDirection Plugin) this afternoon to trigger eight custom event for any visible element in the DOM structure. Here is the source code. This plugin registers eight custom directional event like up,down,left,right,top-left,top-right,bottom-left, bottom-right and one more generic event called “mousedirection” where you can capture the direction of the mouse using event object’s “direction” parameters (like event.direction)

And here is how you can use it

```html
<head>
<title>jQuery Mouse Direction Plugin Demo</title>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<style type="text/css">
.container {
height: 150px;
margin: 20px;
padding: 20px;
width: 300px;
border: 1px solid #888;
}
</style>
<body>
<div class="container">
Move your mouse over this box
</div>
<script type=’text/javascript’>
(function($){
	$.mousedirection();
	$(".container").bind("mousedirection", function (e) {
		$(this).html("Mouse Direction: <b>"+e.direction+"</b>");
	});
})(jQuery);
</script>
<script src="http://code.jquery.com/jquery-latest.js" type="text/javascript" charset="utf-8"></script>
<script src="jquery.mousedirection.js" type="text/javascript" charset="utf-8"></script>
</body>
```

To save from the overwork of running a check whether the mouse has entered on the supplied DOM elements (via selectors) I have located the active element under the mouse pointer and triggered the event only on that object – this was a huge performance boost 🙂

Download the complete plugin with the example.html from the link below