$(function() {

/*---- Navigation ----*/

	var $page = $('html,body'),
        $body = $('body'),
        $window = $(window),
        windowHeight;

	function scrollToElement(target) {
        var y = 0;

        if (target && $(target).length) {
            y = $(target).offset().top;
        }

        $page.stop().animate({scrollTop: y}, 'slow', 'swing');
    }

    $body.on('click', '#top-menu a , #bottom-menu a , .to-doctors-btn', function(e){
        e.preventDefault();
        scrollToElement($(this).attr('href'));
    });



/*---- Top Slider ----*/

	var dSlideSpeed = 50;
	var dTimeOut = 8000;
	var dNeedLinks = false;
	var slideNum = 0;
	var slideTime;
	slideCount = $('#slider .slide').size();
	var animSlide = function(arrow){
	    clearTimeout(slideTime);
	    $('.slide').eq(slideNum).fadeOut(dSlideSpeed);
	        if(arrow == 'next'){
	            if(slideNum == (slideCount-1)){slideNum=0;}
	            else{slideNum++}
	        }
	        else if(arrow == 'prew')
	        {
	            if(slideNum == 0){slideNum=slideCount-1;}
	            else{slideNum-=1}
	        }
	        else{
	            slideNum = arrow;
	        }
	    $('.slide').eq(slideNum).addClass('flip').siblings().removeClass('flip');
	    $('.slide').eq(slideNum).fadeIn(dSlideSpeed, rotator);
	    $('.control-slide.active').removeClass('active');
	    $('.control-slide').eq(slideNum).addClass('active');

        /*---- Top Slider Interconnection with services ----*/
        $('.services-provide-block ul li:eq(' + slideNum + ')').addClass('active').siblings().removeClass('active');
	}

	function sliderResize(){
		var slider = $('#slider');
		var imgH = $('#slider .slide img').height();
		var imgH2 = $('#slider .slide.flip img').height();
		if($window.width() <= 568){
			if(imgH<=0){
				slider.css('height', imgH2 + 'px');
			} else{
				slider.css('height', imgH + 'px');
			}
		}
	}

	var $adderSpan = '';
	$('.slide').each(function(index) {$adderSpan += '<span class = "control-slide">' + index + '</span>';});
	$('<div class ="sli-links">' + $adderSpan +'</div>').appendTo('#slider-wrap');
	$('.control-slide:first').addClass('active');
	$('.control-slide').click(function(){
	    var goToNum = parseFloat($(this).text());
	    animSlide(goToNum);
	});

	var pause = false;

	var rotator = function(){
	  	if(!pause){slideTime = setTimeout(function(){animSlide('next')}, dTimeOut);}
	}

	$('#slider-wrap').hover(
	    function(){clearTimeout(slideTime); pause = true;},
	    function(){pause = false; rotator();
	});

	rotator();

/*---- Awards slider ----*/

	var awardSlideSpeed = 600;
	var awardTimeOut = 4000;
	var awardNeedLinks = true;
	var awardSlideNum = 0;
	var awardSlideTime;
	awardSlideCount = $('.our-awards-slider .award-img').size();
	var awardSlide = function(arrow){
	    clearTimeout(awardSlideTime);
	    $('.award-img').eq(awardSlideNum).fadeOut(awardSlideSpeed);
	        if(arrow == 'next'){
	            if(awardSlideNum == (awardSlideCount-1)){awardSlideNum=0;}
	            else{awardSlideNum++}
	        }
	        else if(arrow == 'prew')
	        {
	            if(awardSlideNum == 0){awardSlideNum=awardSlideCount-1;}
	            else{awardSlideNum-=1}
	        }
	        else{
	            awardSlideNum = arrow;
	        }
	    $('.award-img').eq(awardSlideNum).fadeIn(awardSlideSpeed, rotatorAward);
	}

	if(awardNeedLinks){
		var $linkArrow = $('<span id="prewbutton">&nbsp;</span><span id="nextbutton">&nbsp;</span>')
	    .appendTo('.our-awards-slider');
	    $('#nextbutton').click(function(){
	        awardSlide('next');
	    })
	    $('#prewbutton').click(function(){
	        awardSlide('prew');
	    })
	}

	var pause = false;
	var rotatorAward = function(){
	  	if(!pause){awardSlideTime = setTimeout(function(){awardSlide('next')}, awardTimeOut);}
	}

	$('.our-awards-slider').hover(
	    function(){clearTimeout(awardSlideTime); pause = true;},
	    function(){pause = false; rotatorAward();
	});

	rotatorAward();

/*---- Google Map ----*/

	function initialize() {

		var secheltLoc = new google.maps.LatLng(49.47216, -123.76307);

		var myMapOptions = {
			scrollwheel: false
			,draggable: false
			,zoom: 15
			,center: secheltLoc
			,mapTypeId: google.maps.MapTypeId.ROADMAP
		};

		var theMap = new google.maps.Map(document.getElementById('map_canvas'), myMapOptions);

		var image = 'img/point.png';

		var marker = new google.maps.Marker({
			map: theMap,
			draggable: false,
			position: new google.maps.LatLng(49.47216, -123.76307),
			icon: image,
			visible: true
		});

		var boxText = document.createElement('div');

		var contentString = '<div id="content-boolean">'+
	      '<h1>We Care GmbH</h1>'+
	      '<p>20603 Arch Street Little Rock, AR 72206</p>'+
	      '</div>';

		var myOptions = {
			 content: contentString
			,disableAutoPan: false
			,maxWidth: 200
			,pixelOffset: new google.maps.Size(35, -70)
			,zIndex: null
			,boxStyle: {
			  width: "200px"
			 }
			,infoBoxClearance: new google.maps.Size(1, 1)
			,closeBoxURL: ""
			,isHidden: false
			,pane: "floatPane"
			,enableEventPropagation: false
		};

		google.maps.event.addListener(marker, 'click', function (e) {
			ib.open(theMap, this);
		});

		var ib = new InfoBox(myOptions);

		ib.open(theMap, marker);
	}

	google.maps.event.addDomListener(window, 'load', initialize);

/*---- Animation Effects ----*/

	$('.section').on('scrollSpy:enter', function(){

		$(this).addClass('current');

		$.fn.fade = function (ops) {
		  	var $elem = this;
		  	var res = $.extend({ delay: 400, speed: 800 }, ops);
		  	for (var i=0, pause=0, l=$elem.length; i<l; i++, pause+=res.delay) {
		   		$elem.eq(i).delay(pause).animate({'opacity' : '1'} , res.speed);
		  	}
		  	return $elem;
		};

		$('#about-us.current ul.list-of-our-pacients li').fade();

		$('#our-doctors.current ul.list-of-doctors li:first-child').addClass('flip');

		var el =  $('#our-doctors.current ul.list-of-doctors li'),

		i = 0;

		function autoChange(){
			i++;
			el.filter(':eq('+i+')').addClass('flip');
		}
		setInterval(autoChange, 600);

		$('#sb.current .f-left').animate({'left' : '0'} , 1000 , 'linear' , function(){
			$('#sb.current .f-right').animate({'right' : '0'} , 1000 , 'linear');
		});

	});

	$('.section').on('scrollSpy:exit', function(){});

	$('.section').scrollSpy();

	$('.services-provide-block h3:first-child').animate({'opacity' : '1'} , 1000 , 'linear' , function(){
		$('.services-provide-block ul li.item-1').animate({'left' : '0'} , 1000 , 'linear' , function(){
			$('.services-provide-block ul li.item-2').animate({'left' : '0'} , 1000 , 'linear' , function(){
				$('.services-provide-block ul li.item-3').animate({'left' : '0'} , 1000 , 'linear' , function(){
					$('a.to-doctors-btn').animate({'opacity' : '1'} , 1000 , 'linear');
					$('.services-main-title').animate({'top' : '0', 'opacity' : '1'} , 700 , 'linear');
				});
			});
		});
	});


	$('.pseudo-menu').click(function(e){
		e.preventDefault();
		$('#top-menu').slideToggle();
	});

	var $sections = $('section.section[id]');
	var $buttonTop = $('.button-top');
	var $buttonBottom = $('.button-bottom');
	var currentButtonTopState = null;

	function getNextSection() {
		var topFoldOffset = $window.scrollTop();
      	var bottomFoldOffset = (topFoldOffset + (windowHeight / 2));

      	var $current = $sections.filter(function() {
			var top = $(this).offset().top;
			var bottom = top + $(this).height();
			return (
	        	(top <= bottomFoldOffset && top >= topFoldOffset)
		        || (bottom <= bottomFoldOffset && bottom >= topFoldOffset)
		        || (top <= topFoldOffset && bottom >= bottomFoldOffset)
	      	);
    	});

    	return $sections.eq($sections.index($current.last()) + 1);
	}

	$window
		.on('scroll', function () {
			var topState = $(this).scrollTop() > 1 ? 'block' : 'none';
			var $next = getNextSection();

			if (currentButtonTopState !== topState) {
				$buttonTop.parent().css('display', topState);
				currentButtonTopState = topState;
			}

			$buttonBottom.css('display', $next.length ? 'block' : 'none');
	    })
	    .on('resize.height', function() {
	    	var height = $(this).height();
	    	if (windowHeight !== height) {
	    		windowHeight = height;
	    	}
	    	sliderResize();
	    })
	    .trigger('resize.height');

    $body
    	.on('click', '.button-top' , function (e) {
    		e.preventDefault();
    		scrollToElement();
    	})
		.on('click', '.button-bottom' , function (e) {
	    	e.preventDefault();
    		var $next = getNextSection();

	    	if ($next.length) {
	    		scrollToElement($next);
	    	}
	    });

    /*---- Contact form ----*/
    $('.contact-form').submit(function(e) {
        e.preventDefault();
        var $this = $(this);
        $this.find('div.error').remove();
        $this.find('.error').removeClass('error');
        var button = $this.find('button');
        $('<div class="loading">Loading...</div>').insertAfter(button);
        $.post($this.attr('action'), $this.serialize(), function(response) {
            if (response.error) {
                $('<div class="error" />').text(response.error).insertAfter(button);
            } else if (response.errors) {
                $.each(response.errors, function(name, error) {
                    $this.find('#' + name).addClass('error');
                    $('<div class="error" />').text(error).insertAfter(button);
                });
            } else if (response.success) {
                $('<div class="success" />').text(response.success).insertAfter(button);
            }
            $this.find('.loading').remove();
        }, 'json');
    });
});




