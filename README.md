# TopFloor-Functions
Basic functions used by many Top Floor modules

## tf_functions_load_json
Loads JSON file named $module.json, using a file saved anywhere in the active theme directory and if not found using $module.json saved anywhere in the calling module directory.  The file is parsed with PHP's json_decode command and then saved using drupal's variable_set command as an array under the $module_settings key.  No error checking other then file availability
and well formed JSON is performed.

## tf_functions_make_interchange
Creates an <img> tag formatted to work with Foundation's Interchange Javascript library.  This creates a responsive image in a theme using Foundation.

See: http://foundation.zurb.com/docs/components/interchange.html

## tf_functions_add_js
Provides a wrapper for drupal_add_js.  Note that it will only look for a  file named $module.js but will do so in both the module and current theme. Loads Javascript using a file saved anywhere in the active theme directory  and if not found using $module.js saved anywhere in the calling $module directory.

See: https://api.drupal.org/api/drupal/includes%21common.inc/function/drupal_add_js/7

## tf_functions_add_css
Provides a wrapper for drupal_add_css.  Note that it will only look for a file named $module.css but will do so in both the module and current theme. Loads CSS styles using a file saved anywhere in the active theme directory and if not found using $module.css saved anywhere in the calling $module directory.

See: https://api.drupal.org/api/drupal/includes%21common.inc/function/drupal_add_css/7

## _tf_functions_get_file_path
An internal function that when given a module name and file type, searches the active theme and module folder for a file named $module.$type.   Returns file path for a file saved anywhere in the active theme directory and if not found saved anywhere in $module. directory.

Used by tf_functions_load_json, tf_functions_add_js, tf_functions_add_css

TODO: This might make more sense as a public function that can be used by other modules.
