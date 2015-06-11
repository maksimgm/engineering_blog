CSS Precedence
===

##### Intro

CSS (Cascading Style Sheet), is a style sheet language of the internet. It   manipulates the deisgn and format of HTML. When I began learning CSS, it seemed like a very straight forward language, because of its ease in altering HTML. However, once I began replicating my first web page, it proved to be a challenge. I had no idea why my page was ignoring my CSS declarations. The challenge did not stem from my dearth of understanding how to write CSS source code. The challenge existed because I did not know CSS precedence. 

CSS precedence is simply the order of importance of certain selectors, their location in the style sheet, and their location int he HTML document. A better understanding of CSS precedence will lead to cleaner code and less vexation. Let's take a look at some factors which control CSS precedence:

* Specificity of Elements
* Internal style sheet v. External style v. Inline style
* !important tag


##### Specificity of Elements

Imagine you have an HTML document with id main-nav, and within that id you have an unordered list, with list elements e.g.

	<div id="main-nav">
		<ul>
			<li>About Us</li>
			<li>News</li>
			<li>Subscribe</li>
		</ul>
	</div>
	
Now let's style these elements:
	
	#main-nav ul{
		font-family: sans-serif;
	}
	
	#main-nav ul li{
		font-family: arial;
	}

As you may have noticed, there is a clear conflict between the font-family declarations. So, which one will CSS display on in our browser? CSS will display the more specific element. Since, `li` is nested inside of `ul`, arial will be displayed in our browser. 

The CSS standard follows the model that, more specific selectors take precedence over more general ones. Fortunatley, there is a specificity calculator to help us better understand this concept.

Specificty is calculated by counting different components of our CSS and expressing them in a form, (a,b,c,d). This will become clearer with an example e.g.

* Element, Pseudo Element: d = (0,0,0,1)
* Class, Pseudo class, Attribute: c = (0,0,1,0)
* Id: b = (0,1,0,0)
* Inline Style: a = (1,0,0,0)

Let's take at our first example and express its specificity using the calculator:

	#main-nav ul{
		font-family: sans-serif;
	}

	Specificity value: (0,1,0,1)


	#main-nav ul li{
		font-family: arial;
	}
	
	Specificity value: (0,1,0,2)
	
As you can see the latter has a higher priority than the former.

##### External, Internal, and Inline

There are three ways of applying styles to your page, orginized from most general most specific: External style sheets, Internal style sheets, and Inline styling. 

**External**

External style sheets are the most common form of styling, and the cleanest. Each HTML document must include a reference to the external style sheet:

HTML:

	<head>
	<link rel="stylesheet" type="text/css" href="style.css">
	</head>

CSS:

	#main-nav ul li{
		font-family: arial;
	}
	
This is the most conventional and put together form of applying styles. However, it is the least specific out of the three.

**Internal**

Internal style sheets are typically used if one part of the page has a unique style, however it is not very common. They are defined with a `<style>` element inside of the head section of an HTML [document](http://www.w3schools.com/css/css_howto.asp):


	<head>
	<style>
	#main-nav{
		background: blue;
	}
	
	li{
		font-family: sans-serif;
	}
	</style>
	</head>

If we were to use this example and the example in the **External** section, this would take precedence. i.e. the `font-family` of our page would be `sans-serif` not arial, because and internal style sheet is more specific than an external style sheet.
##### The X factor

!important tag

