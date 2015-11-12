# jquery.input-allow v0.1
*by Jason Yung - [http://callmejay.com](http://callmejay.com "http://callmejay.com")*

 A [jQuery](http://jquery.com) plugin that provides lightweight unobtrusive real-time regEx filtering for individual characters entered into input fields.  

### Basic Usage
Simply use the **allow** attribute on any **input** tag to specify a regEx to filter by. 

	<input class="digits-only" type="text" allow="[0-9]"/>

	<input class="alpha-only" type="text" allow="[a-z]"/>
	
	<input class="special-only" type="text" allow="[\-!@#$%\^&*()_+=\:;<>]"/>

### Dynamic Content Support
The plugin uses `$('body').delegate(...)` to bind its core handlers to any and every **input** tag that has an **allow** attribute defined, including those added dynamically:

	$('body').append("<input type='text' allow='[a-z]'>"); //works out of the box!

### Events
Each character entered into a filtered input field is compared to some regEx:

- If a character matches, the **input** element will trigger an **input-allow.pass** event
- If a character does not match, the **input** element will trigger an **input-allow.fail** event

To bind a handler to these events, you can use `on` or `delegate`:

	$('input[allow]').on('input-allow.fail', function(event) {
		event.target.css('background','red'); //bad input - color the input red
	}

	// dynamic content support
	$('body').delegate('input-allow.pass', 'input[allow]',function(event){
		event.target.css('background','green'); //good input - color the input green
	})	

### Known Issues
- Edge cases were not really considered.

### Roadmap
TODO