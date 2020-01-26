# Metasnippet
Code Snippets of various languages written or collected by Metaspook.

### PHP
```php
// Escape PHP string in HTML.
// Usages: html_escape("Replace string/variable here")
function html_escape($string){ return '<pre>'.$string.'</pre>';}

// Escape PHP string in JavaScript.
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
```
