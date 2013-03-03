var Main = (function(){

  function Main(){
		var $slider = $('#slider');
		var $container = $('#container');
		var $items = $('.items');
		var width = 570;
		var length = 7;
		var current = 0;
		var next = current+1;
		var timer;
		var duration = 750;
		var slide = function(next){
			window.clearInterval(timer);
			$container.animate({left: -(width*(next))},function(){
				if(current == length-1){
					current = 0;
					next = 1;
					$container.css({left: 0});
				}else{
					current++;
					next++;
				}
				window.setTimeout(function(){
					slide(next);
				},duration)
			});
		}
		this.init = function(){
			$items.clone().appendTo($container);
			$container.css({'width': width*length*2});
			timer = window.setTimeout(function(){
				slide(next);
			},duration);
		}
	}
	return Main;
})();

$(function(){
	var main = new Main();
	main.init();
})

