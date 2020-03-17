# Metasnippet
Code Snippets of various Languages/Commands written or collected by Metaspook.

### PHP
```php
// Escape string value for use in HTML.
// Usages: html_escape("Replace string/variable here")
function html_escape($str){ return '<pre>'.$str.'</pre>';}

// Escape string value for use in XML.
// Usages: xml_escape("Replace string/variable here")
function xml_escape($str){ return htmlspecialchars(preg_replace('#[\x00-\x08\x0B\x0C\x0E-\x1F]+#','',$str),ENT_QUOTES);}

// Escape string value for use in JavaScript.
// Usages: js_escape("Replace string/variable here")
function js_escape($str){ return str_replace("\n", '\n', str_replace('"', '\"', addcslashes(str_replace("\r", '', (string)$str), "\0..\37'\\")));}

// Escape the ANSI Escape Characters.
// Usages: ansi_escape("Replace string/variable here")
function ansi_escape($str){ return preg_replace('#\\x1b[[][^A-Za-z]*[A-Za-z]#', '', $str);}

// Returns 'true/false' if running under Windows OS or not.
// Usages: is_windows() == true
//       : IS_WINDOWS == true       // Optional
function is_windows(){ return ('\\' === DIRECTORY_SEPARATOR) ? true : false; }; 
define('IS_WINDOWS', is_windows()); // Optional

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

// Returns current user's home directory of running system in obfuscated way.
// Usages: echo get_home_dir();
function get_home_dir(){
    $rkrp = str_rot13('rkrp'); if (function_exists($rkrp)) {
		return ('\\' === DIRECTORY_SEPARATOR) ? $rkrp("echo %USERPROFILE%") : $rkrp("echo ~");
	} else return ('\\' === DIRECTORY_SEPARATOR) ? getenv("USERPROFILE") : getenv("HOME");
}

// Returns 'true/false' if given string is a valid 'md5' hash.
// Usages: is_md5('fae8a9257e154175da4193dbf6552ef6') === true;
function is_md5($var =''){ return preg_match('/^[a-f0-9]{32}$/', $var) ? true : false ;}

// Returns 'true/false' if given string is a valid 'sha256' hash.
// Usages: is_sha256('a91069147f9bd9245cdacaef8ead4c3578ed44f179d7eb6bd4690e62ba4658f2') === true;
function is_sha256($var =''){ return preg_match('/^[a-f0-9]{64}$/', $var) ? true : false ;}

// Alternate command execution on system and returns output.
// Useful where functions exec, passthru, shell_exec and system aren't enabled but proc_open is.
// Usages: run_cmd('whoami');
//       : run_cmd("echo $variable");
function run_cmd($cmd) {
    $descriptors = [0 => ['pipe', 'r'],1 => ['pipe', 'w'],2 => ['pipe', 'w']];
    $process = proc_open($cmd.' 2>&1', $descriptors, $pipes);
    if (!is_resource($process)) die("Can't execute command.");
    fclose($pipes[0]);$output = stream_get_contents($pipes[1]);
    fclose($pipes[1]);$error = stream_get_contents($pipes[2]);
    fclose($pipes[2]);$code = proc_close($process);return $output;
}

```

### Batch Script
```batch
:: Prints list of semicolon separated paths.
echo %path:;=&echo.%

```

### VirtualBox
```batch
:: In Windows use this command first.
pushd "%PROGRAMFILES%\Oracle\VirtualBox"
```
```shellscript
# Change the UUID of Virtual Disk
VBoxManage internalcommands sethduuid "/var/vdisks/myDisk1.vdi"

# Clone VDI Disk
VBoxManage clonevdi myDisk1.vdi cloneDisk.vdi

# Enable Nested VT-x/AMD-V for Intel VT-x supported CPU.
VBoxManage modifyvm "Your VM Name" --nested-hw-virt on
```

### Kali Linux
```shell
# [Re]set my password for Root user.
sudo passwd root

# Restore legacy Kali Root User Policy in v2020.1+.
sudo apt update && sudo apt install -y kali-grant-root
```

### Laravel
* Application Debug Blacklist [add below code to "/laravel/config/app.php" file.]
```php
/*
    |--------------------------------------------------------------------------
    | Application Debug Blacklist
    |--------------------------------------------------------------------------
    |
    | When an exception is uncaught and the APP_DEBUG environment variable is 
    | true, the debug page will show all environment variables and their 
    | contents. In some cases you may want to obscure certain variables.
    |
    */

    'debug_blacklist' => [
        '_ENV' => [
            'APP_KEY',
            'DB_PASSWORD',
            'REDIS_PASSWORD',
            'MAIL_PASSWORD',
        ],

        '_SERVER' => [
            'APP_KEY',
            'DB_PASSWORD',
            'REDIS_PASSWORD',
            'MAIL_PASSWORD',
        ],

        '_POST' => [
            'password',
        ],
    ],
```
