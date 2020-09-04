# Metasnippet
Various Code and Command Snippets.

### Abbreviations
<details><summary>Click to collapse/fold.</summary><br/>
	
```code
E.g. --> "exempli gratia (Latin)" --> "for example" or "for the sake of example"
-------> Usages: I'll drive a new car, e.g., Lamborghini or Ferrari.
I.e. --> "id est (Latin)" --> "in other words" or "that is (to say)"
-------> Usages: I'll drive that new car, i.e., Lamborghini.
```
</details>

### Batch Script
<details><summary>Click to collapse/fold.</summary><br/>
	
```batch
:: Prints list of semicolon separated paths.
echo %path:;=&echo.%

```
</details>

### Kali Linux
<details><summary>Click to collapse/fold.</summary><br/>
	
```shell
# Post Installation.
sudo apt clean
sudo -- sh -c 'apt update && apt -y upgrade && apt -y full-upgrade && apt -y autoremove'

# [Re]set my password for Root user.
sudo passwd root

# Restore legacy Kali Root User Policy in v2020.1+.
sudo apt update && sudo apt install -y kali-grant-root

# Install Kali Linux main menu.
sudo apt install kali-menu -y

# Main menu customization.
# Get a new item 'Main Menu' in Usual applications >> Accessories
sudo apt install alacarte -y

# Fix broken Menu in Kali Linux.
sudo -- sh -c 'apt remove --purge kali-menu -y && apt clean'
sudo rm -rf .local/share/applications .config/menus
sudo reboot
sudo apt install kali-menu -y
```
</details>

### Laravel
<details><summary>Click to collapse/fold.</summary><br/>
	
* <b>Artisan Commands.</b> Useful Artisan commands.
* <i>Usages</i>: Execute the commands below from Laravel application directory.
```shell
# [Re]create config cache. Useful after any changes in '.env' file. If unable to 
# execute the command delete the "bootstrap/cache/config.php" file as fallback.
php artisan config:cache

# Clear Application Cache.
php artisan cache:clear

# Clear Route Cache.
php artisan route:clear

# Clear Configuration Cache.
php artisan config:clear

# Clear Compiled Views Cache.
php artisan view:clear
```

* <b>Clear Laravel Caches.</b> Clear Application/Route/Configuration/Views caches.
* <i>Usages</i>: Add the snippets below to "routes/web.php" file and call the URL from browser.
```php
// Clear Application Cache.
Route::get('/clear-cache', function() {
    Artisan::call('cache:clear');
    return "Application Cache is cleared!";
});
```
```php
// Clear Route Cache.
Route::get('/route-cache', function() {
    Artisan::call('route:clear');
    return "Route Cache is cleared!";
});
```
```php
// Clear Configuration Cache.
Route::get('/config-cache', function() {
    Artisan::call('config:clear');
    return "Configuration Cache is cleared!";
});
```
```php
// Clear Compiled Views Cache.
Route::get('/view-cache', function() {
    Artisan::call('view:clear');
    return "Compiled Views Cache is cleared!";
});
```

* <b>Application Debug Blacklist.</b> Hide the specific informations from debug page.
* <i>Usages</i>: Add the snippet below to "config/app.php" file.
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
</details>

### Linux (Debian-based)
<details><summary>Click to collapse/fold.</summary><br/>
	
```shell
## Change language to English US.
# First choose 'en_US.UTF-8' from supported locale list.
sudo dpkg-reconfigure locales

# Now change the current default locale.
sudo update-locale LANG=en_US.UTF-8

# Remove and purge a package.
sudo apt remove --purge <package-name>

# Install a package if not exist, Reinstall if exists.
sudo apt install --reinstall <package-name>

# Reboot/Restart.
"sudo shutdown -r now" OR "sudo reboot"
```
```shell
## Install "screenFetch" (Bash Screenshot Information Tool).
sudo apt install screenfetch
# Install "screenFetch" (Alternative) 
# Useful in error "awk: fatal: cannot open file `proc/fb' for reading".
sudo -- sh -c 'wget -O /usr/bin/screenfetch https://git.io/vaHfR && chmod +x /usr/bin/screenfetch'

```
</details>

### OpenVAS
<details><summary>Click to collapse/fold.</summary><br/>
	
```shell
# Issue Update/Download Feed.
# - rsync: failed to connect to feed.openvas.org (89.146.224.58): Connection refused (111)
# - rsync: failed to connect to feed.openvas.org (2a01:130:2000:127::d1): Cannot assign requested address (99)
#
# Fixing Update/Download Feed.
apt update && apt install iputils-ping
greenbone-nvt-sync --curl --verbose
```
</details>

### PHP
<details><summary>Click to collapse/fold.</summary><br/>
	
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

// Convert given path's separator '/' or '\' into the operating system's directory separator
// the server currently running on e.g., "\path\in\windows" >> "/path/in/linux".
// Usages: con_dirsep("/Replace/path/here")
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
</details>

### SSH Tweaks
<details><summary>Click to collapse/fold.</summary><br/>
	
```shell
##*Edit SSH server config file.
sudo nano /etc/ssh/sshd_config

#*Enable password authentication, uncomment.
#PasswordAuthentication yes

#*Enable root login, uncomment
#PermitRootLogin yes

#*Enable ssh key login, uncomment
#PubkeyAuthentication yes
#AuthorizedKeysFile .ssh/authorized_keys

# Restart the ssh service.
"sudo systemctl restart ssh" OR "sudo service --full-restart sshd"
```
</details>

### VirtualBox
<details><summary>Click to collapse/fold.</summary><br/>
	
```shell
### VirtualBox Guest Additions.
#
## Pre-Installation.
# 1. Select VM >> Settings >> >> Storage >> If no CD-ROM device add a new.
# 2. Start VM >> In VM's window menu 'Devices' >> 'Insert Guest Additions CD Image'
# 3. Enter either of the following commands. (second one for legacy distros.)
sudo -- sh -c 'apt update && apt -y upgrade && apt -y full-upgrade && apt -y autoremove'
sudo -- sh -c 'apt-get update && apt-get upgrade -y && apt-get full-upgrade -y && apt-get autoremove -y'

## Installation on GUI/Normal Debian-like.
# Go to CD-ROM folder Enter the following command then reboot to take effect.
sudo ./VBoxLinuxAdditions.run

## Installation on GUI/Normal Debian-like (Alternative).
# Enter first of the following commands, if VirtualBox-Guest-* package's version
# matches with VirtualBox's then enter the second. Once done, reboot to take effect.
apt search virtualbox-guest
for X in dkms utils x11; do sudo apt install -y virtualbox-guest-$X; done

## Installation on GUI-less/Terminal on Debian-like.
# Enter the following commands. Once done, reboot to take effect.
for X in build-essential dkms linux-headers-generic linux-headers-$(uname -r); do sudo apt install -y $X; done
sudo mkdir -p /mnt/cdrom
sudo mount /dev/cdrom /mnt/cdrom
cd /mnt/cdrom
sudo ./VBoxLinuxAdditions.run --nox11

## Installation on GUI-less/Terminal on Debian-like (Alternative).
# Enter first of the following commands, if VirtualBox-Guest-* package's version
# matches with VirtualBox's then enter the second. Once done, reboot to take effect.
apt search virtualbox-guest
for X in dkms utils; do sudo apt install -y virtualbox-guest-$X; done

## Get the Version on Debian-like.
/usr/sbin/VBoxService --version

## Get List of available VirtualBox-Guest packages.
apt search virtualbox-guest

## Get List of installed VirtualBox-Guest packages.
dpkg -l | grep virtualbox-guest
```

```batch
:: WINDOWS: Fix error "VERR_NEM_VM_CREATE_FAILED"
:: causing by WSL2, Memory integrity etc.
:: ! Restart PC to take effect after command.
bcdedit /set hypervisorlaunchtype off
```

```batch
:: WINDOWS: Use this command first or go to directory where
:: Virtualbox installed befor using 'VBoxManage' command.
pushd "%PROGRAMFILES%\Oracle\VirtualBox"
```
```shell
## Enable SSH to Guest VM (Windows/Mac/Linux).
## Guest VM >> Settings >> Network >> Advanced >> Port Forwarding button. (Alternative).
VBoxManage modifyvm "Your VM Name" --natpf1 "SSH,tcp,127.0.0.1,2522,10.0.2.15,22"
# Verify the rule.
VBoxManage showvminfo "Your VM Name" | grep 'Rule'
# Connect using the following from Host.
ssh -p 2522 <login>@127.0.0.1

# Change the UUID of Virtual Disk
VBoxManage internalcommands sethduuid "/var/vdisks/myDisk1.vdi"

# Clone VDI Disk
VBoxManage clonevdi myDisk1.vdi cloneDisk.vdi

# Enable Nested VT-x/AMD-V for Intel VT-x supported CPU.
VBoxManage modifyvm "Your VM Name" --nested-hw-virt on

# Enable Unrestricted Guest Execution for Intel VT-x supported CPU.
VBoxManage modifyvm "Your VM Name" --vtxux on
```
</details>

### Windows
<details><summary>Click to collapse/fold.</summary><br/>
	
```batch
:: Get a CMD prompt during Windows installation.
Press Shift + F10
```
</details>

### Windows Subsystem for Linux (WSL)
<details><summary>Click to collapse/fold.</summary><br/>
	
```batch
:: WSL 1
:: Requirements: Windows 10

:: Enable WSL 1
:: ! Restart PC to take effect after command.
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

:: Set WSL 1 as default version next Linux will install on.
wsl --set-default-version 1
```

```batch
:: WSL 2
:: Requirements: Windows 10 Version 2004+ Build 19041+

:: Enable WSL 2
:: ! Restart PC to take effect after command.
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

:: Set WSL 2 as default version next Linux will install on.
wsl --set-default-version 2
```

```batch
:: Lists all 'Linux Distro Names', 'Status' and 'WSL versions'.
"wsl --list --verbose" OR "wsl -l -v"

:: Change the WSL versions of any Linux Installation.
:: <distribution name> = Desired distro's name.
:: <versionNumber>     = Desired WSL version '1' or '2'.
wsl --set-version <distribution name> <versionNumber>
```

```pwsh
## Windows Defender exclusion for WSL distros. (performance+)
# Download the script from here:
# https://gist.github.com/noelbundick/9c804a710eb76e1d6a234b14abf42a52
# Enter the following conmmands respectively from an
# administrative PowerShell prompt where the script exists.
$POLVAR = (Get-ExecutionPolicy)
Set-ExecutionPolicy RemoteSigned -force
./excludeWSL.ps1
Set-ExecutionPolicy $POLVAR -force
```
</details>
