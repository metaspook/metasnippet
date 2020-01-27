# Metasnippet
Code Snippets of various languages written or collected by Metaspook.

### PHP
```php
// Escape string value for use in HTML.
// Usages: html_escape("Replace string/variable here")
function html_escape($string){ return '<pre>'.$string.'</pre>';}

// Escape string value for use in XML.
// Usages: html_escape("Replace string/variable here")
function xml_escape($value){ return htmlspecialchars(preg_replace('#[\x00-\x08\x0B\x0C\x0E-\x1F]+#','',$value),ENT_QUOTES);}

// Escape string value for use in JavaScript.
// Usages: js_escape("Replace string/variable here")
function js_escape($string){ return str_replace("\n", '\n', str_replace('"', '\"', addcslashes(str_replace("\r", '', (string)$string), "\0..\37'\\")));}

// Escape the ANSI Escape Characters.
// Usages: ansi_escape("Replace string/variable here")
function ansi_escape($string){ return preg_replace('#\\x1b[[][^A-Za-z]*[A-Za-z]#', '', $string);}

// Returns 'true/false' if running under Windows OS or not.
// Usages: is_windows() == true
//       : IS_WINDOWS == true
function is_windows(){ return ('\\' === DIRECTORY_SEPARATOR) ? true : false; }; define('IS_WINDOWS', is_windows());

// String sorting callback function for 'array_filter' function.
// Usages: array_filter($arr, 'string_sort')
function string_sort($var){ return (strlen($var) && is_string($var)); }

// Convert directory separator into running OS's.
// Usages: con_dirsep("Replace path here")
function con_dirsep($string){ return str_replace(['\\', '/'], DIRECTORY_SEPARATOR, $string); }

// Convert given string's URLs to links.
// Usages: url_2_link("Here is an example url: http://example.com")
function url_2_link($string){ 
    function u2l_callback($matches){ return '<a href="'.htmlspecialchars($matches[1]).'">'.$matches[1].'</a>';}
    return preg_replace_callback("#(\bhttps?://\S+\b)#",'u2l_callback',$string);
}
```
