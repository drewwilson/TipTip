TipTip

Copyright 2010 Drew Wilson

http://www.drewwilson.com
http://code.drewwilson.com/entry/tiptip-jquery-plugin

Version 1.3   -   Updated: Mar. 23, 2010

This Plug-In will create a custom tooltip to replace the default
browser tooltip. It is extremely lightweight and very smart in
that it detects the edges of the browser window and will make sure
the tooltip stays within the current window size. As a result the
tooltip will adjust itself to be displayed above, below, to the left 
or to the right depending on what is necessary to stay within the
browser window. It is completely customizable as well via CSS.

This TipTip jQuery plug-in is dual licensed under the MIT and GPL licenses:
http://www.opensource.org/licenses/mit-license.php
http://www.gnu.org/licenses/gpl.html

-------------------------------------------------------------------

This is modified version of TipTip

What's New:

* All callback functions when called, "this" refers to the element that is applied the TipTip and also receive an argument which is an object with the some useful values.

    { holder: tiptip_holder, content: tiptip_content, arrow: tiptip_arrow, options: opts }

* The option "content" can also be a callback function that must return a string or HTML. This callback function will be called every time the tooltip is shown. Very useful for ajax generated tooltips. For example:

	$j('#my-element').tipTip({

	  maxWidth: 600,
	  defaultPosition: 'right',
	  content: function (e) {
		  $.ajax({ url: 'myJsonWebService.php', success: function (response) {
			  e.content.html(response); // the var e is the callback function data (see above)
		  });
		  return 'Please wait...'; // We temporary show a Please wait text until the ajax success callback is called.
	  }

	});

* If "enter" and "exit" callback function return false, then the tooltip won't be shown or hidden respectively.

* Added option "afterEnter" which is a callback function that is called after a tooltip is shown.

* Added option "afterExit" which is a callback function that is called after a tooltip is hidden.

* Fixed option "maxWidth" so that it is applied each time a tooltip is shown. It seems that using the cssClass option (see below) is a better way to do this.

* Added option "cssClass" which is applied to the tiptip holder before shown. You can apply more than one css classes by seperating them with a space character (see also jQuery.addClass).

* Added methods to "show", "hide" or "destroy" a TipTip. For example:

	$('#my-element').tipTip({ content: 'Hello world!' }); // We apply a tooltip with the text Hello world! on #my-element $('#my-element').tipTip('show'); // This will programmatically show the applied TipTip without the need to hover over the element. $('#my-element').tipTip('hide'); // we hide it $('#my-element').tipTip('destroy'); // and then we destroy it which means the element #my-element no won't have a TipTip applied.

* The option "activation" can have the value "manual". In this case no events will be applied to the element and the developer will be responsible to show or not the tooltip. But you can always use the show and hide methods to show or hide the tooltip ;-)

* Created an alternate look & feel for TipTip, you can use it by setting the option "cssClass" to "alternative".