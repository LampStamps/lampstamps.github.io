[%SET [@page_type@]='home'/%]
[%site_value id:'footer_javascript'%]
	<script type="text/javascript">
		$('.row-slider').slick({
			dots: false,
			infinite: true,
			speed: 300,
			autoplay: true,
			slidesToShow: 4,
			slidesToScroll:1,
			responsive: [
				{
					breakpoint: 1199,
					settings: {
						slidesToShow: 3,
						slidesToScroll: 1,
					}
				},
				{
					breakpoint: 991,
					settings: {
						slidesToShow: 2,
						slidesToScroll: 1,
					}
				},
				{

					breakpoint: 767,
					settings: {
						slidesToShow: 2,
						slidesToScroll: 1,
					}
				},
				{

					breakpoint: 467, //xs view settings for main image
					settings: {
						slidesToShow: 1,
						slidesToScroll: 1,
					}
				}
			]
		});
</script>
[%/site_value%]
<div class="col-xs-12">
	[%if [@config:show_home_ads@]%]
		[%advert type:'text' template:'carousel' limit:'10' ad_group:''%]
			[%param *header%]
				<div id="homepageCarousel" class="carousel slide">
					[%if [@total_showing@] > 1%]
						<ol class="carousel-indicators">
							[%site_value id:'counter' type:'load'/%]
						</ol>
					[%/if%]
					<div class="carousel-inner">
			[%/param%]
			[%param *footer%]
					</div>
					[%if [@total_showing@] > 1%]
						<a class="left carousel-control" href="#homepageCarousel" data-slide="prev">
							<span class="fa fa-chevron-left"></span>
						</a>
						<a class="right carousel-control" href="#homepageCarousel" data-slide="next">
							<span class="fa fa-chevron-right"></span>
						</a>
					[%/if%]
				</div>
			[%/param%]
			[%param *ifempty%]
				<a class="neto-placeholder neto-placeholder-rotator btn-loads" data-loading-text="<i class='fa fa-spinner fa-spin' style='font-size: 14px'></i>" href="[@config:home_url@]/_cpanel?item=adw&page=view&id=New&plan_id=1">
					Click to add a banner<br/>
				</a>
			[%/param%]
		[%/advert%]
	[%/if%]
	<hr>
<aside class="col-xs-12 col-sm-3" id="left-sidebar">
	[%CACHE type:'cmenu' id:'sidebar'%]
	[%CATEGORYMENU sortby:'sortorder,selected,name' show_empty:'1'%]
		[%PARAM header%]
			<div class="panel panel-default hidden-xs">
				<div class="panel-heading"><h3 class="panel-title">Categories</h3></div>
				<ul class="list-group" role="navigation" aria-label="Category menu">
				[%/PARAM%]
				[%PARAM *level_1%]
					<li class="[%DATA id:'next_level' if:'ne' value:''%]dropdown dropdown-hover[%/DATA%]"><a href="[@url@]" class="list-group-item dropdown-toggle" >[@name@]</a>
						[%DATA id:'next_level' if:'ne' value:''%]
							<ul class="dropdown-menu dropdown-menu-horizontal">
								[@next_level@]
							</ul>
						[%/DATA%]
					</li>
				[%/PARAM%]
				[%PARAM *level_2%]
					<li class="[%DATA id:'next_level' if:'ne' value:''%]dropdown dropdown-hover[%/DATA%]">
						<a href="[@url@]" >[@name@]</a>
						[%DATA id:'next_level' if:'ne' value:''%]
							<ul class="dropdown-menu dropdown-menu-horizontal">
								[@next_level@]
							</ul>
						[%/DATA%]
					</li>
				[%/PARAM%]
				[%PARAM *level_3%]
					<li class="lv3-li">
						<a href="[@url@]" >[@name@]</a>
					</li>
				[%/PARAM%]
				[%PARAM footer%]
				</ul>
			</div>
		[%/PARAM%]
	[%/CATEGORYMENU%]
	[%/CACHE%]
</aside>
<div class="col-xs-12 col-sm-9">
	<section id="homepage-content" class="n-responsive-content" aria-label="Main Description">[@page_content@]</section>
	[%new_arrivals template:'home' limit:'20' %]
		[%param *header%]
			<hr />
			<div class="text-center">
				[%content_zone id:'new_arrivals_heading'/%]
			</div>
			<div class="slider-container">
				<div class="row row-slider">
		[%/param%]
		[%param *footer%]
				</div>
			</div>
		[%/param%]
	[%/new_arrivals%]
	[%top_sellers limit:'20' template:'home' %]
		[%param *header%]
			<hr />
			<div class="text-center">
				[%content_zone id:'top_sellers_heading-2'/%]
			</div>
			<div class="slider-container">
				<div class="row row-slider">
		[%/param%]
		[%param *footer%]
				</div>
			</div>
		[%/param%]
	[%/top_sellers%]
</div>
