Leftronic API Documentation
===========================

What is Leftronic?
------------------

[Leftronic](https://beta.leftronic.com) makes powerful dashboards for business intelligence.

* Colorful and interactive data visualizations
* Templates to get you started right away
* Drag-and-drop editor makes it easy for anyone to create a powerful dashboard, customized to their needs
* Integration with Google Analytics, Twitter, Chartbeat, Zendesk, Basecamp, Pivotal Tracker, Facebook, and more to come!
* Dashboards can be protected or shared with a shortened URL
* Powerful API's for Javascript, PHP, Python, Ruby, and Java
* Python Package and Ruby Gem

Technical Notes
---------------

We also suggest checking out our [API](https://beta.leftronic.com/api) page. While the most detailed documentation is here, it has JSON and CURL examples in addition to a test form to send data to your custom widgets.

Authentication is handled by your API access key. We strongly encourage you to keep this key private. If you're logged in, your key can be found on our [API](https://beta.leftronic.com/api) page. If you plan on using one of our API libraries, you will find instructions below on how to set your access key.

All API requests are made by sending a POST request to https://beta.leftronic.com/customSend with a properly formatted JSON packet. We do not support XML.

Current API version is 1.0.

Getting Started
---------------

If you haven't already, create an account at https://beta.leftronic.com/accounts/login.

Get your API access key from the API overview page at https://beta.leftronic.com/api.

We recommend checking out our [Tutorials](https://beta.leftronic.com/tutorials) to familiarize yourself with your dashboard.

Javascript
----------

*Note*: Because Javascript is rendered by the browser, your API access key will be clearly visible in plain text. We recommend using our PHP, Python, or Ruby API libraries. If you need to use the Javascript API and have concerns about abuse or misuse of your private key, please feel free to send us an email at <support@leftronic.com>.

Start by downloading the most recent version of our Javascript API at https://github.com/sonofabell/leftronic/blob/master/api_javascript.js.

### Dependencies

This library uses [jQuery](http://jquery.com) for POST requests. Either [download jQuery](http://jquery.com/download) or look at [instructions](http://code.google.com/apis/libraries/devguide.html#jquery) to load from Google's CDN.

```javascript
<script type="text/javascript" src="your/path/jquery.min.js"></script>
```

Edit the file, adding your API key here:

```javascript
var accessKey = "YOUR_ACCESS_KEY";
```

Add the file to the header of your web pages with the appropriate path linking to the location of your file:

```javascript
<script type="text/javascript" src="your/path/api_javascript.js"></script>
```

Here are some example functions to push to your dashboard. Be sure you have configured the correct widgets to accept custom data points. Also, be sure that you have entered your API access key correctly.

Let's start with pushing a number to a widget.

```javascript
pushNumber("yourNumberStream", 14600);
```

Now we'll push some geographic coordinates to a map widget. You can use either the U.S. or world map widgets. The first coordinate (37.8) is the latitude and the second coordinate (-122.6) is the longitude. If your request is successful, you should see a data point appear on San Francisco, California.

```javascript
pushGeo("yourGeoStream", 37.8, -122.6);
```

Here's how you push a title and message to a text feed widget.

```javascript
pushText("yourTextStream", "This is my title.", "Hello World!");
```

Let's push an array of names and values to a leaderboard widget. Be sure to create the array first (you may call it whatever you'd like). Be careful to use the proper syntax. Next, push the array to your widget.

```javascript
var leaderArray = [{"name": "Johnny", "value": 84}, {"name": "Jamie", "value": 75}, {"name": "Lance", "value": 62}];

pushLeaderboard("yourBoardStream", leaderArray);
```

Similar to the last example, let's push a list of items to a list widget. Same rules as last time.

```javascript
var listArray = [{"listItem": "Elizabeth"}, {"listItem": "Marshall"}, {"listItem": "Claire"}, {"listItem": "Nolan"}];

pushList("yourListStream", listArray);
```

PHP
---

Start by downloading the most recent version of our PHP API at https://github.com/sonofabell/leftronic/blob/master/api_php.php.

### Dependencies

This API library uses "json_encode()" which requires [PHP](http://php.net/downloads.php) 5.2.0 or greater.

Create a class instance with your API key. Feel free to name it whatever you'd like.

```php
$update = new Leftronic("YOUR_ACCESS_KEY");
```

Here are some example functions to push to your dashboard. Be sure you have configured the correct widgets to accept custom data points. Also, be sure that you have entered your API access key correctly.

Let's start with pushing a number to a widget.

```php
$update->pushNumber("yourNumberStream", 14600);
```

Now we'll push some geographic coordinates to a map widget. You can use either the U.S. or world map widgets. The first coordinate (37.8) is the latitude and the second coordinate (-122.6) is the longitude. If your request is successful, you should see a data point appear on San Francisco, California.

```php
$update->pushGeo("yourGeoStream", 37.8, -122.6);
```

Here's how you push a title and message to a text feed widget.

```php
$update->pushText("yourTextStream", "This is my title.", "Hello World!");
```

Let's push an array of names and values to a leaderboard widget. Be sure to create the array first (you may call it whatever you'd like). Be careful to use the proper syntax. Next, push the array to your widget.

```php
$leaderArray = array(array("name" => "Johnny", "value" => 84), array("name" => "Jamie", "value" => 75), array("name" => "Lance", "value" => 62));

$update->pushLeaderboard("yourBoardStream", $leaderArray);
```

Similar to the last example, let's push a list of items to a list widget. Same rules as last time.

```php
$listArray = array(array("listItem" => "Elizabeth"), array("listItem" => "Marshall"), array("listItem" => "Claire"), array("listItem" => "Nolan"));

$update->pushList("yourListStream", $listArray);
```

Python
------

**_Note_**: We also have a Leftronic Python Package that offers the same functionality. You can download it on [Github](https://github.com/sonofabell/leftronic-python) or on the [Python Package Index](http://pypi.python.org/pypi/leftronic).

Start by downloading the most recent version of our Python API at https://github.com/sonofabell/leftronic/blob/master/api_python.py.

### Dependencies

[urllib2](http://docs.python.org/library/urllib2.html) and [JSON](http://docs.python.org/library/json.html).

```python
import urllib2
import json
```

Import the file. Your location may vary.

```python
from api_python import Leftronic
```

Create a class instance with your API key. Feel free to name it whatever you'd like.

```python
update = Leftronic("YOUR_ACCESS_KEY")
```

Here are some example functions to push to your dashboard. Be sure you have configured the correct widgets to accept custom data points. Also, be sure that you have entered your API access key correctly. *Note*: The first argument passed to the functions ("update" in these examples) is the name of your class instance.

Let's start with pushing a number to a widget.

```python
Leftronic.pushNumber(update, "yourNumberStream", 14600)
```

Now we'll push some geographic coordinates to a map widget. You can use either the U.S. or world map widgets. The first coordinate (37.8) is the latitude and the second coordinate (-122.6) is the longitude. If your request is successful, you should see a data point appear on San Francisco, California.

```python
Leftronic.pushGeo(update, "yourGeoStream", 37.8, -122.6)
```

Here's how you push a title and message to a text feed widget.

```python
Leftronic.pushText(update, "yourTextStream", "This is my title.", "Hello World!")
```

Let's push an array of names and values to a leaderboard widget. Be sure to create the array first (you may call it whatever you'd like). Be careful to use the proper syntax. Next, push the array to your widget.

```python
leaderArray = [{"name": "Johnny", "value": 84}, {"name": "Jamie", "value": 75}, {"name": "Lance", "value": 62}]

Leftronic.pushLeaderboard(update, "yourBoardStream", leaderArray)
```

Similar to the last example, let's push a list of items to a list widget. Same rules as last time.

```python
listArray = [{"listItem": "Elizabeth"}, {"listItem": "Marshall"}, {"listItem": "Claire"}, {"listItem": "Nolan"}]

Leftronic.pushList(update, "yourListStream", listArray)
```

Ruby
----

**_Note_**: We also have a Leftronic Ruby Gem that offers the same functionality. You can download it on [Github](https://github.com/sonofabell/leftronic-ruby) or on [RubyGems](https://rubygems.org/gems/leftronicapi).

Start by downloading the most recent version of our Ruby API at https://github.com/sonofabell/leftronic/blob/master/api_ruby.rb.

### Dependencies

[RubyGems](http://rubygems.org/pages/download), [Curb](http://rubygems.org/gems/curb), and [JSON](http://rubygems.org/gems/json). We recommend installing them with the [RubyGems](http://rubygems.org/pages/download) installer.

```ruby
require 'rubygems'
require 'curb'
require 'json'
```

Import the file. Your location may vary.

```ruby
require 'api_ruby'
```

Create a class instance with your API key. Feel free to name it whatever you'd like.

```ruby
update = Leftronic.new("YOUR_ACCESS_KEY")
```

Here are some example functions to push to your dashboard. Be sure you have configured the correct widgets to accept custom data points. Also, be sure that you have entered your API access key correctly.

Let's start with pushing a number to a widget.

```ruby
update = Leftronic.pushNumber("yourNumberStream", 14600)
```

Now we'll push some geographic coordinates to a map widget. You can use either the U.S. or world map widgets. The first coordinate (37.8) is the latitude and the second coordinate (-122.6) is the longitude. If your request is successful, you should see a data point appear on San Francisco, California.

```ruby
update = Leftronic.pushGeo("yourGeoStream", 37.8, -122.6)
```

Here's how you push a title and message to a text feed widget.

```ruby
update = Leftronic.pushText("yourTextStream", "This is my title.", "Hello World!")
```

Let's push an array of names and values to a leaderboard widget. Be sure to create the array first (you may call it whatever you'd like). Be careful to use the proper syntax. Next, push the array to your widget.

```ruby
leaderArray = Array[{"name" => "Johnny", "value" => 84}, {"name" => "Jamie", "value" => 75}, {"name" => "Lance", "value" => 62}]

update = Leftronic.pushLeaderboard("yourBoardStream", leaderArray)
```

Similar to the last example, let's push a list of items to a list widget. Same rules as last time.

```ruby
listArray = Array[{"listItem" => "Elizabeth"}, {"listItem" => "Marshall"}, {"listItem" => "Claire"}, {"listItem" => "Nolan"}]

update = Leftronic.pushList("yourListStream", listArray)
```

Java
----

Our Java API was created by Webmetrics and is available at https://github.com/webmetrics/leftronic-java.

At this time we do not offer support for our Java API but we have tested it, and it works.

Feedback and Issues
-------------------

If you notice any bugs or other issues, submit a patch or send us a pull request. You can also send us an email at <support@leftronic.com>.
