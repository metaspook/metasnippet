# Metasnippet
Code Snippets of various languages written or collected by Metaspook.

### PHP
```php
// Escape string value for use in HTML.
// Usages: html_escape("Replace string/variable here")
function html_escape($str){ return '<pre>'.$str.'</pre>';}

// Escape string value for use in XML.
// Usages: html_escape("Replace string/variable here")
function xml_escape($str){ return htmlspecialchars(preg_replace('#[\x00-\x08\x0B\x0C\x0E-\x1F]+#','',$str),ENT_QUOTES);}

// Escape string value for use in JavaScript.
// Usages: js_escape("Replace string/variable here")
function js_escape($str){ return str_replace("\n", '\n', str_replace('"', '\"', addcslashes(str_replace("\r", '', (string)$str), "\0..\37'\\")));}

// Escape the ANSI Escape Characters.
// Usages: ansi_escape("Replace string/variable here")
function ansi_escape($str){ return preg_replace('#\\x1b[[][^A-Za-z]*[A-Za-z]#', '', $str);}

// Returns 'true/false' if running under Windows OS or not.
// Usages: is_windows() == true
//       : IS_WINDOWS == true
function is_windows(){ return ('\\' === DIRECTORY_SEPARATOR) ? true : false; }; define('IS_WINDOWS', is_windows());

// String sorting callback function for 'array_filter' function.
// Usages: array_filter($arr, 'string_sort')
function string_sort($var){ return (strlen($var) && is_string($var)); }

// Convert directory separator into running OS's.
// Usages: con_dirsep("Replace path here")
function con_dirsep($str){ return str_replace(['\\', '/'], DIRECTORY_SEPARATOR, $str); }

// Convert given string's URLs to links.
// Usages: url_2_link("Here is an example url: http://example.com")
function url_2_link($str){ 
    function u2l_callback($matches){ return '<a href="'.htmlspecialchars($matches[1]).'">'.$matches[1].'</a>';}
    return preg_replace_callback("#(\bhttps?://\S+\b)#",'u2l_callback',$str);
}

// Convert given word or phrase into valid HTML ID.
// Usages: text_2_id("Replace Text for ID")
function text_2_id($text, $prepend = null, $delimiter = '-'){
    $text = strtolower($text); $id = preg_replace('/\s/', $delimiter, $text);
    $id = preg_replace('/[^\w\-]/', '', $id); $id = trim($id, $delimiter);
    $prepend = (string) $prepend;
    return !empty($prepend) ? join($delimiter, array($prepend, $id)) : $id;
}

// Extended stripping out of string from HTML tags.
// Usages: strip_tags_ext($str, $allowableTags = '', $fallbackStr = '')
//       : $str (string) – The string to be stripped of HTML formatting.
//       : $allowableTags (string) – The string of tags to allow when stripping tags.
//       : $fallbackStr (string) – The string to be used as a fallback.
function strip_tags_ext($str, $allowableTags = '', $fallbackStr = ''){
    $str = strip_tags($str, $allowableTags);
    $str = str_replace('&nbsp;', '', $str);
    if (preg_match('/^\s*$/', $str)) return $fallbackStr;
    return $str;
}

// Replace newlines with paragraph tags in a block of text.
// Usages: text_2_paragraph("Replace text string/variable here")
function text_2_paragraph($str){return str_replace('<p></p>','','<p>'.preg_replace('#([\r\n]\s*?[\r\n]){2,}#','</p>$0<p>',$str).'</p>');}
```
