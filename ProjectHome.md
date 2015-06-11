## Description ##
**sfdc-web2anything** is an opensource, community-contributed project to  help you **generate web forms for the _live collection/insertion of data in any standard or custom Salesforce.com object_**.

## Updates ##
_07-01-2009_ - I've uploaded an updated engine that will confirm on form submit if your PHP installation doesn't include the required [cURL extensions](http://php.net/curl); it also adds attachment support.
To update, if you don't want to re-run the entire procedure (see "Usage Instructions"), simply delete the engine/ and jquery/ folders from your webserver, clean your browser cache and re-download http://sfdc-web2anything.googlecode.com/svn/trunk/web2anything-engine-API14.zip then unzip its content (engine/, jquery/ and /uploads folders) back on your webserver.

## How does it work? ##
Follow the "Usage Instructions" to generate the webform, the config.inc.php file (which contains Salesforce.com credentials for API access) and download the PHP engine, then upload everything on your webserver. When a user visits/fills/submits the webform, a POST message is sent to the PHP engine file that connects to Salesforce.com (with the credentials specified in the config.inc.php file) and inserts the posted data.

The javascript for the generation of the webform is based on [jQuery](http://jquery.com) (with some help from one of its plugins, [selectboxes](http://www.texotela.co.uk/code/jquery/select/)) and uses your current Salesforce.com Session ID stored in your browser's cookies to query objects' and fields' properties via API thanks to [Salesforce.com AJAX Toolkit](http://www.salesforce.com/us/developer/docs/ajax/index.htm).

The PHP engine that takes care of inserting the posted data from the form to your Salesforce.com Organization is based on [sforce NuSOAP](http://sourceforge.net/project/showfiles.php?group_id=96634&package_id=166314), a modification of [NuSOAP](http://sourceforge.net/projects/nusoap/), _a set of PHP classes - no PHP extensions required - that allow developers to create and consume web services based on SOAP 1.1, WSDL 1.1 and HTTP 1.0/1.1_.

## Requirements ##
  * To create the form:
    * A Salesforce.com Edition with API access (typically EE, UE, DE)
    * Firefox 3, Safari 3, Chrome 0.3, Internet Explorer 7 (Internet Explorer would ideally need some fixes here and there)

  * To host the form and the PHP engine:
    * A webserver with PHP 4 or 5
      * cURL extension required
      * SOAP extensions NOT required

## Usage Instructions ##
  * Add a new bookmark to your browser's bookmarks toolbar with name "sfdc-web2anything" and location (URL) set to:
`javascript:(function(){if(document.getElementById('overlay_div'))return;loading=document.createElement('div');loading.setAttribute('id','overlay_div');loading.style.cssText='position:fixed;top:0;left:0;width:100%;height:100%;z-index:5000;color:#fff;background-color:#000;text-align:center;font-family:Arial;font-size:17px;padding-top:30px;opacity:.7;filter:alpha(opacity=70);';loading.innerHTML = '<p>Loading.. Please wait..</p>';document.body.appendChild(loading);var scriptElem=document.createElement('script');seed='http://sfdc-web2anything.googlecode.com/svn/trunk/web2anything.js';scriptElem.setAttribute('src',seed);scriptElem.setAttribute('type','text/javascript');scriptElem.setAttribute('id','web2X-script');document.getElementsByTagName('head')[0].appendChild(scriptElem)})();`
  * Login to your Salesforce.com Organization
  * While on the Salesforce Homepage, click on the "sfdc-web2anything" bookmark to launch the application
  * Follow the steps, make sure you read the documentation

## Screenshot ##
_web2anything form generator_

![http://phollaio.com/labs/web2x/sfdc-web2anything.gif](http://phollaio.com/labs/web2x/sfdc-web2anything.gif)

_Sample account form_

![http://phollaio.com/labs/web2x/generated-form.jpg](http://phollaio.com/labs/web2x/generated-form.jpg)

## To-do ##
  * ~~Add attachments support~~
  * ~~Client side form validation on user input (based on [jQuery](http://jquery.com) + [Validation](http://bassistance.de/jquery-plugins/jquery-plugin-validation/))~~