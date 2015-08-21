# TopFloor-Functions
Basic functions used by many Top Floor modules.

See https://github.com/martin-wessel-topfloor/TopFloor-Functions/wiki for more information

## tf_functions_load_json
Loads JSON file named $module.json, using a file saved anywhere in the active theme directory and if not found using $module.json saved anywhere in the calling module directory.  The file is parsed with PHP's json_decode command (as an array) and then saved using drupal's variable_set command as an array under the $module_settings key.  No error checking other then file availability
and well formed JSON is performed.  

Standard comments are supported (and will be removed before conferting to JSON):
* Use /* ... */ to comment a block
* Use // to comment to the end of a line

See: http://php.net/manual/en/function.json-decode.php 

See: https://api.drupal.org/api/drupal/includes%21bootstrap.inc/function/variable_set/7

> #### param string module
> The name of the module that needs JSON loaded. Do not include the file extension
> 
> #### return bool
> * False indicates that there was an error loading the JSON,
> * True indicates that the JSON file was loaded, parsed, and saved

## tf_functions_make_interchange
Creates an <img> tag formatted to work with Foundation's Interchange Javascript library.  This creates a responsive image in a theme using Foundation.

See: http://foundation.zurb.com/docs/components/interchange.html

> #### param string image_uri
> the path to the image using Drupal's URI format; usually the URI element in Drupal image array
>
> #### param string large_style
> The machine name of the image style that will be used to generate an image that will be used at Foundation's large size and above
>
> #### param string medium_style
> The machine name of the image style that will be used to generate an image that will be used at Foundation's medium size
>
> #### param string small_style
> The machine name of the image style that will be used to generate an image that will be used at Foundation's small size
> 
> #### return string
> A properly formatted <img> tag that includes all the Foundation Interchange markup.

## tf_functions_add_js
Provides a wrapper for drupal_add_js.  Note that it will only look for a  file named $module.js but will do so in both the module and current theme. Loads Javascript using a file saved anywhere in the active theme directory  and if not found using $module.js saved anywhere in the calling $module directory.

See: https://api.drupal.org/api/drupal/includes%21common.inc/function/drupal_add_js/7

> #### param string module
> The name of the module that needs Javascript loaded.  Do not include the extension.  This will be converted to $data paramater for drupal_add_js
>
> #### param array options
> This will be passed as the $options parameter for drupal_add_js.  See the documentation for that function for valid values.
>
> #### return array
> The current array of JavaScript files, settings, and in-line code, including Drupal defaults, anything previously added with calls to drupal_add_js(), and this function call's additions.

## tf_functions_add_css
Provides a wrapper for drupal_add_css.  Note that it will only look for a file named $module.css but will do so in both the module and current theme. Loads CSS styles using a file saved anywhere in the active theme directory and if not found using $module.css saved anywhere in the calling $module directory.

See: https://api.drupal.org/api/drupal/includes%21common.inc/function/drupal_add_css/7

> #### param string module
> The name of the module that needs Javascript loaded.  Do not include the extension.  This will be converted to $data paramater for drupal_add_css.
>
> #### param array options
> This will be passed as the $options parameter for drupal_add_css.  See the documentation for that function for valid values.
>
> #### return array
> An array of queued cascading stylesheets

## _tf_functions_get_file_path
An internal function that when given a module name and file type, searches the active theme and module folder for a file named $module.$type.   Returns file path for a file saved anywhere in the active theme directory and if not found saved anywhere in $module. directory.

**Used by**
* tf_functions_load_json
* tf_functions_add_js
* tf_functions_add_css

TODO: This might make more sense as a public function that can be used by other modules.

> #### param string module
> The name of the module, used as the base file name
> 
> #### param string type
> The type of file to search for, used as the file extension
> 
> #### return string
> The path to the file, or FALSE if no file was found.
