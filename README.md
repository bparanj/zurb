http://foundation.zurb.com/sites/docs/v/5.5.3/applications.html

Create a new Rails 5 project.

We will use zurb-foundation 4.3.2 with Rails 5.

```
rails new zurb
```

Create a product resource.

```
rails g scaffold product name price:decimal --skip-stylesheets
```

Migrate the database.

```
rails db:migrate
```

Add:

```ruby
gem 'zurb-foundation'
```

to Gemfile. Run bundle. Install zurb foundation.

```
rails g foundation:install
```

Say yes to overwrite application.html.erb. Define the route for the home page.

```ruby
root 'products#index'
```

Go to `http://localhost:3000`.

Add about us sidebar:

```html
<body>
  <div class="row">
    <div class="large-8 columns">
      <%= yield %>
    </div>
    <div class="large-4 columns">
      <h2>About Us</h2>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
      quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
      consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
      cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
      proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    </div>
  </div>
  <%= javascript_include_tag "application" %>
</body>
```

The about us collapses if the width is reduced.


Add navigation bar:

```rhtml
<nav class="top-bar">
  <ul class="title-area">
    <li class="name">
      <h1><%= link_to "Awesome Store", products_path %></a></h1>
    </li>
  </ul>
  <section class="top-bar-section">
    <ul class="right">
      <li class="divider"></li>
      <li><%= link_to "Browse Products", products_path %></li>
      <li class="divider"></li>
      <li><%= link_to "Price List" %></li>
      <li class="divider"></li>
      <li><%= link_to "Contact Us" %></li>
      <li class="divider"></li>
      <li><%= link_to "Cart" %></li>
    </ul>
  </div>
</nav>
```

to the layout file. The layout file will now look like this:

```rhtml
<!DOCTYPE html>
<!-- paulirish.com/2008/conditional-stylesheets-vs-css-hacks-answer-neither/ -->
<!--[if lt IE 7 ]> <html class="ie6" lang="en"> <![endif]-->
<!--[if IE 7 ]>    <html class="ie7" lang="en"> <![endif]-->
<!--[if IE 8 ]>    <html class="ie8" lang="en"> <![endif]-->
<!--[if IE 9 ]>    <html class="ie9" lang="en"> <![endif]-->
<!--[if (gt IE 9)|!(IE)]><!--> <html lang="en"> <!--<![endif]-->
  <head>
  	<meta charset="utf-8" />
  	<!-- Uncomment to make IE8 render like IE7 -->
  	<!-- <meta http-equiv="X-UA-Compatible" content="IE=7" /> -->
  	<!-- Set the viewport width to device width for mobile -->
  	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
  	<title>Zurb Example</title>
  	<%= stylesheet_link_tag    "application" %>
  	<%= javascript_include_tag "vendor/custom.modernizr" %>
    <%= csrf_meta_tags %>
  </head>
  <body>
	<nav class="top-bar">
	  <ul class="title-area">
	    <li class="name">
	      <h1><%= link_to "Awesome Store", products_path %></a></h1>
	    </li>
	  </ul>
	  <section class="top-bar-section">
	    <ul class="right">
	      <li class="divider"></li>
	      <li><%= link_to "Browse Products", products_path %></li>
	      <li class="divider"></li>
	      <li><%= link_to "Price List" %></li>
	      <li class="divider"></li>
	      <li><%= link_to "Contact Us" %></li>
	      <li class="divider"></li>
	      <li><%= link_to "Cart" %></li>
	    </ul>
	  </div>
	</nav>
    <div class="row">
      <div class="large-8 columns">
        <%= yield %>
      </div>
      <div class="large-4 columns">
        <h2>About Us</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
        cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
        proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
    </div>
    <%= javascript_include_tag "application" %>
  </body>
</html>
```

Add:

```css
$topbar-bg: #212D48 !default;
```

to `foundation_and_overrides.scss`. Reload the page. Now the background color is changed.

Style the button in index.html.erb:

```rhtml
<%= link_to 'New Product', new_product_path, class: "button radius" %>
```

Change form partial:

```rhtml
<div class="row">
  <div class="small-3 columns">
    <%= f.label :name, class: "right inline" %>
  </div>
  <div class="small-9 columns">
    <%= f.text_field :name %>
  </div>
</div>
<div class="row">
  <div class="small-3 columns">
    <%= f.label :price, class: "right inline" %>
  </div>
  <div class="small-9 columns">
    <%= f.text_field :price %>
  </div>
</div>
<div class="row">
  <div class="small-9 small-offset-3 columns">
    <%= f.submit %>
  </div>
</div>
```

Reload the new product page. 

Tooltip

Add:

```rhtml
title: 'Price in USD', data: { tooltip: true }
```

to price field so that it looks like this:

```rhtml
<%= f.label :price, class: "right inline", title: 'Price in USD', data: { tooltip: true } %>
```

Reload the new product page. Now, if you hover over the Price label, you will see the tooltip.


Episode 417 upgraded to Rails 5 and zurb-foundation 4.3.2.

Railscast version : zurb-foundation (4.2.2)


