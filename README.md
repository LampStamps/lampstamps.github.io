<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.1.3/dist/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">

<div class="col-xs-12">
	[%breadcrumb%]
		[%PARAM *header%]
			<ul class="breadcrumb" itemscope itemtype="http://schema.org/BreadcrumbList" role="navigation" aria-label="Breadcrumb">
				<li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem">
					<a href="[@config:home_url@]" itemprop="item"><span itemprop="name">Home</span></a>
					<meta itemprop="position" content="0" />
				</li>
		[%/PARAM%]
		[%PARAM *body%]
			<li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem">
				<a href="[@url@]" itemprop="item"><span itemprop="name">[@name@]</span></a>
				<meta itemprop="position" content="[%calc [@count@] + 1 /%]" />
			</li>
		[%/PARAM%]
		[%PARAM *footer%]
			</ul>
		[%/PARAM%]
	[%/breadcrumb%]
	<h1 class="page-header">[@content_name@]</h1>
	<p class="text-muted">
		[%IF [@content_author@]%]
			Author: [@content_author@] &nbsp;
		[%/IF%]
		[%if [@date_posted@] != 0000-00-00 00:00:00%]
			Date Posted:[%FORMAT type:'date'%][@date_posted@][%/FORMAT%]&nbsp;
		[%/IF%]
	</p>
	[%if ![@form:pgnum@] OR [@form:pgnum@] eq '1'%]
		<p>
			[@content_short_description1@]
			[@content_short_description2@]
			[@content_short_description3@]
		</p>
	[%/if%]
</div>
[%load_template file:'cms/includes/sidebar.template.html'/%]
<img src="[%asset_url type:'content' id:'[@content_id@]' default:'[@config:imageurl@]/pixel.gif'/%]" class="img-responsive" alt="[@name@] main image"/>
<img src="[%asset_url type:'content' thumb:'alt_1' id:'[@content_id@]' default:'[@config:imageurl@]/pixel.gif'/%]"  class="img-responsive" alt="[@name@] image"/>
[%advert type:'text' template:'carousel' limit:'10' ad_group:''%]
	[%param *header%]
		<section id="homepageCarousel" class="carousel slide" aria-label="Banner Images">
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
		</section>
		<hr>
	[%/param%]
	[%param *ifempty%]
	[%/param%]
[%/advert%]
[%advert type:'product' limit:'8' template:'' ad_group:''%]
	[%param *header%]
		<section class="row" aria-label="Featured Products">
	[%/param%]
	[%param footer%]
		</section>
		<hr>
	[%/param%]
[%/advert%]
[%if ![@form:pgnum@] OR [@form:pgnum@] eq '1'%]
	<section class="n-responsive-content" aria-label="Description">
		[%parse%]
			[@content_description1@]
			[@content_description2@]
			[@content_description3@]
			[@content_wufoo_form@]
		[%/parse%]
	</section>
[%/if%]
[%thumb_list type:'content' content_type:'' template:'' limit:'20'%]
	[%param *footer%]
		<ul class="pagination" role="navigation" aria-label="Pagination Navigation">
			[%paging limit:'3'%]
				[%param *previous_page%]<li><a href="[@URL@]" aria-label="Go Back 1 Page">Previous Page</a></li>[%/param%]
				[%param *goback_pages%]<li><a href="[@URL@]" aria-label="Go To Page [@PAGE@]">[@PAGE@]</a></li>[%/param%]
				[%param *current_page%]<li class="active"><a href="[@URL@]" aria-label="Current Page">[@PAGE@]</a></li>[%/param%]
				[%param *gonext_pages%]<li><a href="[@URL@]" aria-label="Go To Page [@PAGE@]">[@PAGE@]</a></li>[%/param%]
				[%param *next_page%]<li><a href="[@URL@]" aria-label="Go Forward 1 Page">Next Page</a></li>[%/param%]
			[%/paging%]
		</ul>
	[%/param%]
[%/thumb_list%]
[%thumb_list type:'products' template:'' limit:'[@config:related_limit@]'%]
	[%param header%]
		<hr>
		<section class="row" aria-label="Products">
	[%/param%]
	[%param footer%]
		</section>
	[%/param%]
[%/thumb_list%]
[%IF [@content_allow_reviews@]%]
<div class="dropdown">
	<button class="btn btn-default btn-xs dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown" aria-expanded="true">
		Share: <i class="fa fa-facebook-square text-facebook" aria-hidden="true"></i>
		<i class="fa fa-twitter-square text-twitter" aria-hidden="true"></i>
		<i class="fa fa-pinterest-square text-pinterest" aria-hidden="true"></i>
		<span class="caret"></span>
	</button>
	<ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
		<li role="presentation"><a class="js-social-share" role="menuitem" tabindex="-1" href="//www.facebook.com/sharer/sharer.php?u=[%url_encode%][@url@][%/url_encode%]"><i class="fa fa-facebook-square text-facebook" aria-hidden="true"></i> Facebook</a></li>
		<li role="presentation"><a class="js-social-share" role="menuitem" tabindex="-1" href="//twitter.com/intent/tweet/?text=[%url_encode%][@content_name@][%/url_encode%]&amp;url=[%url_encode%][@url@][%/url_encode%]"><i class="fa fa-twitter-square text-twitter" aria-hidden="true"></i> Twitter</a></li>
		<li role="presentation"><a class="js-social-share" role="menuitem" tabindex="-1" href="//www.pinterest.com/pin/create/button/?url=[%url_encode%][@url@][%/url_encode%]&amp;description=[%url_encode%][@content_name@][%/url_encode%]"><i class="fa fa-pinterest-square text-pinterest" aria-hidden="true"></i> Pinterest</a></li>
	</ul>
</div>
<a id="comments"></a><hr />
[%thumb_list type:'content_reviews' limit:'5'%]
	[%param filter_1%][@CONTENT_ID@][%/param%]
	[%param *header%]
		<h3>Comments ([@reviews@])</h3>
	[%/param%]
	[%param *body%]
		<div itemprop="review" itemscope itemtype="http://schema.org/Review">
			<blockquote>
				<h4 itemprop="name"><i>[%nohtml%][@title@][%/nohtml%]</i></h4>
				<div>
					<strong>[%if [@reviewname@]%]By: <span itemprop="author">[@reviewname@]</span> on [%/ if%]<meta itemprop="datePublished" content="[%FORMAT type:'date'%][@insert_date@][%/FORMAT%]">[%FORMAT type:'date'%][@insert_date@][%/FORMAT%]</strong>
				</div>
				<span itemprop="description">[%nohtml%][@review@][%/nohtml%]</span>
				[%IF [@review_response@]%]
					<br /><br />
					<blockquote>
						<span class="review_response text-muted"><strong><i>[@config:website_name@] Response</i></strong><br /> [%nohtml%][@review_response@][%/nohtml%]</span>
					</blockquote>
				[%/IF%]
			</blockquote> <hr />
		</div>
	[%/param%]
[%/thumb_list%]
<h3>Leave a comment</h3>
<form name="edit_review" method="post" role="form" action="[%URL page:'account' type:'write_contentreview'%][%/URL%]">
	<fieldset>
		<input type="hidden" name="fn" value="confirm">
		<input type="hidden" name="item" value="[@content_id@]">
		<input type="hidden" name="checked_terms_and_conditions" value="1">
		<input type="hidden" name="rating_value" id="rating_value" value="5"/>
		<div class="form-group">
			<label for="review_title">Title For Comment</label>
			<input class="form-control" type="text" name="review_title" id="review_title" value="[%nohtml%][@form:review_title@][%/nohtml%]" required/>
		</div>
		<div class="form-group">
			<label for="review_text">Your Comment</label>
			<textarea name="review_text" id="review_text" rows="10" class="form-control" required>[%nohtml%][@form:review_text@][%/nohtml%]</textarea>
		</div>
		[%ajax_loader%]
			[%if ![@user:username@] or [@user:username@] eq 'noreg'%]
				<div class="form-group">
					<label for="customername">Your Name</label>
					<input class="form-control" type="text" name="customername" id="customername" value="[%nohtml%][@form:customername@][%/nohtml%]" required/>
				</div>
				<div class="form-group">
					<label for="emailaddress">Your Email Address</label>
					<input class="form-control" size="70" type="email" name="emailaddress" id="emailaddress" value="[%nohtml%][@form:emailaddress@][%/nohtml%]" required/>
				</div>
			[%/if%]
		[%/ajax_loader%]
		<p>
			<button type="submit" class="btn btn-success" />Post Comment</button>
		</p>
		<p class="text-muted">Comments have to be approved before showing up</p>
	</fieldset>
</form>
[%/if%]
</div>
