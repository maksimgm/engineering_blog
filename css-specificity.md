CSS Precedence
===

##### Intro

CSS (Cascading Style Sheet), is the style sheet language of the internet. It manipulates the design and format of an HTML document. When I began learning CSS, it seemed like a very simple language because of its easy syntax. However, once I began replicating web page, it proved to be an exasperating challenge. The challenge did not stem from my dearth of understanding CSS syntax. The challenge persisted because I did not know CSS precedence. 

CSS precedence is, simply, the order of importance of certain selectors, their location in the style sheet, and their location in the HTML document. A better understanding of CSS precedence will lead to cleaner code and less vexation. Let's take a look at the different factors that control CSS precedence:

* Specificity of Elements
* Internal style sheet vs. External style vs. Inline style
* !important tag


##### Specificity of Elements

Imagine you have an HTML document with `id` `main-nav`, and within that id you have an `unordered list`, with some list elements e.g.

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

As you may have noticed, there is a clear conflict between the font-family declarations. So, which one will CSS display on in our browser? CSS will display the more specific declaration. Since, `li` is nested inside of `ul`, Arial will be displayed in our browser. 

The CSS standard follows the model that more specific selectors take precedence over more general ones. Fortunately, there is a specificity calculator to help us better understand this concept.

Specificity is calculated by counting the different components of your CSS and expressing them in a form, (a,b,c,d). e.g.

* Element, Pseudo Element: d = (0,0,0,1)
* Class, Pseudo class, Attribute: c = (0,0,1,0)
* Id: b = (0,1,0,0)
* Inline Style: a = (1,0,0,0)

Let's take a look at our first example and express its specificity using the calculator:

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

There are three ways of applying styles to your page, organized from most general most specific: External style sheets, Internal stylesheets, and Inline styling. 

**External Style Sheet**

External style sheets are the most common and cleanest  form of styling. Every HTML document must include a reference to the external style sheet:

HTML:

	<head>
		<link rel="stylesheet" type="text/css" 
		href="style.css">
	</head>

CSS:

	#main-nav ul li{
		font-family: arial;
	}
	
This is the most conventional and put together form of applying styles. However, it is the least specific out of the three.

Furthermore, if for some reason you have multiple style sheets, then the latter style sheet will take precedence over the former:

HTML:

	<head>
		<link rel="stylesheet" type="text/css" 
		href="style.css">
		<link rel="stylesheet" type="text/css" 
		href="styleTwo.css">
	</head>

style.css:

	#main-nav ul li{
		font-family: arial;
	}

styleTwo.css

	#main-nav ul li{
		font-family: times;
	}
	
In conclusion, the `font-family` of our page will be `times`, because *styleTwo.css* succeeds style.css. Therefore, *styleTwo.css* is more specific. 

**Internal Style Sheet**

Internal style sheets are typically used if one part of the page has a unique style, however it is not very common. They are defined with a `style` element inside of the head section of an HTML document [CSS How To...](http://www.w3schools.com/css/css_howto.asp):


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

If we were to compare this example to the example in the **External** section then, this would take precedence. i.e. the `font-family` of our page would be `sans-serif` not arial, because and internal style sheet is more specific than an external style sheet.

**Inline Styles**

An inline style is typically used to apply a unique style to a specific element on the page. This method of styling is very discouraged, because it mixes content with presentation, which leads to disorganized code. Use this method seldomly.

To use inline styles, add a style attribute to the relevant tag. The style attribute can contain any CSS property. [CSS How To...](http://www.w3schools.com/css/css_howto.asp)

	<li style="font-family:times new roman;">About Us</li>
	
In conclusion, **Inline** styling will override the other two forms of styling.

##### The Important Tag

An `!important` declaration provides the author the ability give more value to a declaration than it naturally has. Here is a code example that will clearly demonstrate how `!important` declarations affect your style:

	#main-nav ul{
		font-family: sans-serif !important;
	}
	
	#main-nav ul li{
		font-family: arial;
	}

As you may have guessed, the `font-family` of our list elements will be sans-serif, not arial, even though arial is more specific. The `!important` declaration partially disproves the specificity rules. I say partially, because if we insert an `!important` declaration into an **Inline** style element than it will still take precedence over the `!important` declaration in our **External** style sheet:

*External Stylesheet*
	
	#main-nav li{
		font-family: sans-serif !important;
	}
	
*Inline*

	<li style="font-family:times new roman !important;">About Us</li>
	
As you may have guessed the `font-family` of our list element will be, times new roman, because an *Inline* style sheet takes precedence over an *External* style sheet.

**When Should `!important` Declarations Be Used?**

The`!important` declaration should **not be used unless they are absolutely necessary** after all other options have been exhausted. Do not be one of those individuals who use `!important` declarations out of laziness, to avoid debugging your code, or to rush through a project. This is a bad habit, because you are disrupting the natural flow of rules. The reason specificity exists in CSS is to make sure that certain elements take precedence over others. The `!important` declarations throws  those rules out of the window, and allows the user to declare which elements are more important.

The `!important` declaration allows users with special needs to place emphasis on specific CSS syntax that will aid their ability to access content. Additionally, the `!important` declaration can also be used to override urgent problems. However, this should only be a temporary fix, until a better solution is found.

##### Conclusion

This piece covered everything you need to know about CSS precedence, including, the specificity of elements, the specificity of different style sheets/styles, and the `!important` declaration. Hopefully, this piece taught you about the importance of CSS precedence. Thus, resulting  in producing best style sheet possible. 


