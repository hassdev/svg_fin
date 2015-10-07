<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<title>svg animation</title>
<style>
	html, body {
		width: 100%;
		height: 100%;
		padding: 0;
		margin: 0;
	}
	body {
		overflow: hidden;
	}

	#wrapper {
		width: 100%;
		min-height: 100%;
		margin: 0 auto;
		position: relative;
	}

	svg {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		margin: 0 auto;
		width: 100%;
		height: 100%;
		outline: 1px solid blue;
	}
</style>
</head>

<body>
	<div id="wrapper">
		<p id="status1"></p>
		<svg id="mysvg" width="300" height="300"></svg>
	</div>
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
	<script>
		$(document).ready(function(){
		    var d = document;
		    var mysvg = d.getElementById("mysvg");

		    var mx, my, random, xmid, ymid, input;

		    //add event to svg
	        mysvg.addEventListener("mousemove", function(e) {
	            //aqcuire mouse position relative to svg
	            mx = e.clientX;
	            my = e.clientY;
	        });

		    setInterval(function() {
		        //svg size
		        var svgw = $("svg").width();
		        var svgh = $("svg").height();

		        //center point of svg
		        xmid = svgw/2;
		        ymid = svgh/2;

		        //random numbers
		        random = {
		            a: Math.floor(Math.random()*25),
		            b: Math.floor(Math.random()*25),
		            c: Math.floor(Math.random()*25)
		        };

		        //display datas
		        $("#status1").html("X Position : " + mx + "<br>Y Position: " + my + "<br><br>Center Point X: " + xmid + "<br><br>Center Point Y: " + ymid + "<br><br>Width: " + svgw + "<br>Height: " + svgh + "<br><br>Random Value a: " + random.a + "<br>Random Value b: " + random.b + "<br>Random Value c: " + random.c);
		        
		        //add <path> to svg
	            input = '<path d="M ' + xmid + ',' + ymid + ' l ' + 0 + ',' + 0 + ' ' + ((mx-xmid)/2) + ',' + random.a + ' ' + ((mx-xmid)-((mx-xmid)/2)) + ',' + ((my-ymid)-random.a) + ' ' + '" stroke="orange" stroke-width="7" stroke-linejoin="round" fill="none" />';

		        $("#mysvg").html(input);
		    }, 10);
		});
	</script>
</body>
</html>
