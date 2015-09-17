# jquery.fold
A utility plugin for content folding.  Replaces an element with a placeholder comment so that it can be easily restored later.

# Why do you need this plugin?
Manual folding can be a bit brittle when you have to rely on things like `$('#original-parent').append($element)` or `$('#original-sibling').before($element)`.  Use this plugin to make your markup a little less brittle.  `.fold()` will do the same thing as `.detach()` but will leave an HTML comment so that you can restore the element to the original spot, without relying on the context/sibling context.

#To fold:
```
$('#element').fold();
```

#To unfold:
```
$('#element').fold('restore');
```


#Example of using with [Harvey](http://harvesthq.github.io/harvey/)
```
var $primaryNav = $('.primary-nav'),
	$mobileNavContainer = $('.mobile-nav-container');

Harvey.attach('screen and (max-width: 767px)', {
  on: function() {
    $primaryNav.fold().appendTo($mobileNavContainer);
  },
  off: function() {
    $primaryNav.fold('restore');
  }
});
```