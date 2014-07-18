Share annotations with smallURL
===============================

shareAnnotation.js is a plug in for [Annotatorjs](http://annotatorjs.org/) to add the possibility to share annotations with smallURL.
This plug works in two environments:
1- Modify the annotator editor, add a button where you can copy the url
2- If you put the URL in the browser, the plug-in creates the annotation in the document, you need a back end to make it work.

My backend is nodejs.

##Installation

To use the tool you need to use the [hashids.min.js](http://www.hashids.org/), in the lib folder, for the smallurl generator and the shareAnnotation.js in the source folder.

```html
 <script src="./lib/hashids.min.js"></script>
 <script src="./src/shareAnnotation.js"></script>
 ...
 <script>
     var host = 'http://localhost:3000';
	jQuery(function($) {
   
		...
	    var annotator = $('body').annotator({readOnly: true}).annotator().data('annotator');
	    $('body').annotator().annotator('addPlugin', 'ShareAnnotation',{http:host});
});
  </script>
```
Parameters:

Param: http: Host.

##Usage

After a new annotation, when you read a annotation a button appears in the bottom of the editor, this button allows you to copy a Small URL. After copy this URL you can paste it in the browser and read it in the document, without the edition, update and delete options.
ShareAnnotation plug in makes an ajax call to get the annotation, in json format, using Small URL, 
for example: when you put in the browser http://localhost:3000/annotation/share/3bK2D8jv, this plugin make a ajax call to http://localhost:3000/annotation/json/annotation/3bK2D8jv nodejs backend, in my case, and return a json object with the annotations, that is loaded for annotatorjs.




