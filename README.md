# Metasnippet
Various Code and Command Snippets.

### Abbreviations
<details><summary>Click to collapse/fold.</summary><br/>
	
```code
E.g. --> "exempli gratia (Latin)" --> "for example" or "for the sake of example"
-------> Usages: I'll drive a new car, e.g., Lamborghini or Ferrari.
I.e. --> "id est (Latin)" --> "in other words" or "that is (to say)"
-------> Usages: I'll drive that new car, i.e., Lamborghini.

GUI ---> Graphical User Interface.
Output: Text, Window, Menu, Dialogue, Image, Audio, Video, Icon.
Input : Mouse, Keyboard, Voice, Gesture and other HW input.
--------------------------------
TUI ---> Text/Terminal User Interface.
Output: Text, Window, Menu, Dialogue.
Input : Mouse, Keyboard.
--------------------------------
CLI ---> Command Line Interface i.e. CUI (Console User Interface).
Output: Text.
Input : Keyboard.
	
PUP (Potentially Unwanted Products)
MVP (Minimum Viable Product).
AMPPS = Apache, MySQL/MongoDB/SQLite, PHP/Perl/Python and Softaculous (auto-installer) + SQLite, FTP [Cross Platform][Freemium Open-Source]
XAMPP = Apache, MySQL/MariaDB/SQLite and PHP/Pearl + phpMyAdmin + OpenSSL + FTP [Cross Platform][Free Open-Source]
WAMP = Windows, Apache, MySQL, and PHP + phpMyAdmin + MariaDB + Adminer + PhpSysInfo [Windows][Free]
MAMP = macOS, Apache/Nginx, PHP, Python, Perl or Ruby [macOS and Windows][Freemium Open-Source]
LAMP = Linux, Apache, MySQL, and PHP, Pearl, Python [Linux OS][Free Open-Source]
PODO (Plain Old Dart Object).
	
## User Log state form conventions.
Default : "Sign up"    == "Register"    == "Create an account"
Process : "Signing up" == "Registering" == "Creating an account"
Complete: "Signed up"  == "Registered"  == "Account created"
	
Default : "Sign in"   == "Log in"    == "Sign/Log into app"
Process : "Signing"   == "Logging"   == "Signing/Logging into app"
Complete: "Signed in" == "Logged in" == "Signed/Logged into app"

Default : "Sign out"    == "Log out"     == "Sign/Log out from app"
Process : "Signing out" == "Logging out" == "Signing/Logging out from app"
Complete: "Signed out"  == "Logged out"  == "Signed/Logged out from app"
	
## User Log state information.
Login/Signin detected/recorded.
	
```
</details>

### Bash Script
<details><summary>Click to collapse/fold.</summary><br/>
	
```console
# Execute a Remote script.
~$ curl -sL https://example.com/myscript.sh | bash -s
OR
~$ wget -qO- https://example.com/myscript.sh | bash -s

# Execute a Remote script with options/parameters/arguments.
~$ curl -sL https://example.com/myscript.sh | bash -s - <place the script's options/parameters/arguments here>
OR
~$ wget -qO- https://example.com/myscript.sh | bash -s - <place the script's options/parameters/arguments here>

```
</details>

### Batch Script
<details><summary>Click to collapse/fold.</summary><br/>
	
```batch
:: Prints list of semicolon separated paths.
echo %path:;=&echo.%

```
</details>
	
### Character Sets
<details><summary>Click to collapse/fold.</summary><br/>
	
```code
+---------+----------CHARACTER-SETS-----------+
| special | !"#$%&'()*+,- ./:;<=>?@[\]^_`{|}~ |
| upper   | ABCDEFGHIJKLMNOPQRSTUVWXYZ        |
| lower   | abcdefghijklmnopqrstuvwxyz        |
| number  | 0123456789                        |
+---------+-----------------------------------+
```
</details>
	
### Dart lang
<details><summary>Click to collapse/fold.</summary><br/>
	
#### Type Systems Chart v0.2
```code
                 * Type Systems Chart v0.2 *
                 ===========================       © Metaspook
 +--Annotations-+-------------------Details-------------------+
 | void         | Type omitted, value can't be used           |
 | Never        | Throw exception/abort/expression never run  |
 |              +-----------------Reset-Value-----------------+
 | Null         | No object, 'null' as value                  |
 + Object       | Any T, no instance member and 'null'        |
 |_ String      | String: UTF-16 code or text inside "" or '' |
 |_ num         | int/double, no instance member              |
 |  |_ int      | Numbers: 64-bit Integer                     |
 |  |_ double   | Num.ers: 64-bit Floating point, int         |
 |_ bool        | Booleans: 'true' and 'false'                |
 |_ Iterable<T> | List/Set, no instance member +----Element---+
 |  |_ List <T> | List of [val,ues]            | List         |
 |  |_ Set  <T> | Set of {unique,values}       | Set          |
 |_ Map   <T,T> | Map of {key:value} pairs     | Map          |
 +-Inferrers-+  |                              |              |
 |  dynamic  |  | Any T, nonexistent instance  | List/Set/Map |
 +-----------+--+ member allowed.              |              |
 |  var      |  | Static T, same T             | List/Set/Map |
 |  final T  |  | Static T, set once.          | List/Set/Map |
 |  const T  |  | Static T, set once at        +--------------+
 +-----------+  | defining only, compile-time constant.       |
 | Future<T>    | Future type (asynchronous expression)       |
 | Stream<T>    | Stream type (asynchronous expression)       |
 +--------------+---------------------------------------------+
 | Priority--> const T > final T > T > var > object > dynamic |
 +------------------------------------------------------------+
 | [T]ypes : Named T declaration of class/typedef/enum.       |
 | Return T: Future, Stream and all types in Annotations.     |
 | Nullable: Types in Annotations are nullable as T?          |
 | Fields  : Variables declared in Class.                     |
 | Methods : Class functions, getter and setter               |
 | Members : Class constructor/field/methods/operator         |
 | Property: Field-like Class member constructs               |
 +------------------------------------------------------------+
```
	
#### Function Cheats
```code
 /// Function Cheats ///                          © Metaspook
 
 funcName(parameters) {expressions...};            // Defining
 |______||__________| |______________|
   Name      Head           Body
  ______  _________
 |      ||         |
 funcName(arguments);                              // Calling
 funcName(function as argument);                   // Callback
funcName(parameters) { expressions... };           // Named
funcName(parameters) => expression;                // Named Arrow
(parameters) { expressions... };                   // Anonymous
(parameters) => expression;                        // Anonymous Arrow (Lambda)
funcName(parameters) { ... funcName(parameters) }; // Recursion
```
	
#### Parameter Cheats
```code
 /// Parameter Cheats ///                      © Metaspook

({required parameter})                    // Named Required
({parameter = initialValue})              // Named Optional
(parameter)                               // Positional Required
([parameter = initialValue])              // Positional Optional
(positionalParameter, {namedParameter})   // Hybrid Parameters
```
	
#### Built-in types
```code
1. Data Types        |   2. Collections
---------------------+----------------------
Type       Keyword       Type        Keyword
----       -------       ----        -------
String     String        Map         Map
Boolean    bool          Iterable    Iterable
Number     num           |_ List     List
|_ Integer int           |_ Set      Set
|_ Double  double
```
	
#### Solutions
```dart
// navigate to first route and remove all previous.
Navigator.of(context).popUntil((Route route) => route.isFirst),

// navigate to first route and remove all previous (named). (not tested)
Navigator.of(context).popUntil(ModalRoute.withName('/root'));

// resize widgets with no width/height property.
Transform.scale( scale: 2.0, child: <target widget here> )
	
// override setState to check if widget is mounted.
@override
void setState(fn) {
  if (mounted) super.setState(fn);
}
```
	
#### Conditional Statement
```dart
void main() {
  // var inNum = 3.5;
  // var inNum = "3";
  var inNum = 3;

  // If conditional flow 1.
  if (inNum is int) {
    print('This is Integer');
  } else if (inNum is double) {
    print('This is double');
  } else if (inNum is String) {
    print('This is String');
  } else {
    print('This is another type or no number');
  }

  // If conditional flow 2.
  if (inNum.runtimeType == int) {
    print('This is Integer');
  } else if (inNum.runtimeType == double) {
    print('This is double');
  } else if (inNum.runtimeType == String) {
    print('This is String');
  } else {
    print('This is another type or no number');
  }

  // Ternary conditional flow 1.
  inNum is int
      ? print('This is Integer')
      : inNum is double
          ? print('This is double')
          : inNum is String
              ? print('This is String')
              : print('This is another type or no number');

  // Ternary conditional flow 2.
  inNum.runtimeType == int
      ? print('This is Integer')
      : inNum.runtimeType == double
          ? print('This is double')
          : inNum.runtimeType == String
              ? print('This is String')
              : print('This is another type or no number');

  // Switch conditional case.
  switch (inNum.runtimeType) {
    case int:
      print('This is Integer');
      break;
    case double:
      print('This is double');
      break;
    case String:
      print('This is String');
      break;
    default:
      print('This is another type or no number');
      break;
  }
}
```
	
</details>
	
### Data Structures
<details><summary>Click to collapse/fold.</summary><br/>
	
```code
Stack => LIFO (Last In First Out)
 4 
---   ^   
 3    |
---  pop
 2   push
---   |
 1    v
---
 0 | 1 | 2 | 3 | 4
 <- dequeue  <-enqueue
Queue => FIFO (First In First Out)
```
</details>
	
### Terminology
<details><summary>Click to collapse/fold.</summary><br/>
	
```code
std -> standard
err -> error
io  -> input output
lib -> library

Standard streams
----------------
stdin  -> standard input
stdout -> standard output
stderr -> standard error

+---------------+---------------+
| Text terminal |    Process    |
+---------------+---------------+
|  Keyboard     +--> stdin      |
|               |               |
|  Display   <--+ stdout/stderr +
+---------------+---------------+
```
</details>
	
### Drivers/Runtimes/SDK
<details><summary>Click to collapse/fold.</summary><br/>
	

```console
# Vulkan (check runtime informations).
# In Windows latest NVIDIA driver excluded "Vulkan RT Library" from the "Programs and Features" and made built-in.
# Anyone can verify which Vulkan runtime is installed by entering following command.
vulkaninfo

```
</details>


### Git Snippet
<details><summary>Click to collapse/fold.</summary><br/>
	
```code

Repository: Git is a repository, storage, or a location where every piece of code is stored.
Fork: It means copying the code from one’s repository to yours.
Upstream: The party which owns the code from where you have cop
origin

    The default upstream repository
https://github.com/njnareshjoshi/articles/blob/master/useful-git-commands/UsefulGitCommands.md
https://dzone.com/articles/introduction-to-git-flow
https://dzone.com/refcardz/getting-started-git
 git worktree list   
repo        = Short form of "Repository"
REPO_NAME   = Name of a Repository like "30DaysOfFlutter"
REMOTE_URL  = https://github.com/metaspook/30DaysOfFlutter.git
REMOTE_NAME = A named REMOTE_URL (Default REMOTE_NAME is "origin")
BRANCH      = A branch name (Default BRANCH is "main")
Fetch       = Get updated existing files
Merge       = Get updated all files
COMMIT_ID   = A identifier of commit's SHA hash like "4626de3"
TAG         = Tag name of a commit like "v1.0"
MESSAGE     = A message like "This is my first commit"
N           = Number
DIRECTORY   = A directory path
FILE        = A file path
USER        = An username like "metaspook"
EMAIL       = An email address like "metaspook@gmail.com"
<>          = Place Here
[]          = Optional
#           = Comments

REMOTE ---------------------- LOCAL ---------------------------------------------
Commits <- Upstream branch <- Remote-tracking branch <--> Commits <- Local branch
           dev                origin/dev                             dev
PROCESS: Initialization (once) -> Modification-> Staging -> Committing -> Pushing

working tree Staging tracked files

1. Create a working directory with a REPO_NAME
2. Make working directory as local repo by initializing git on it.
3. Create new files edit them or folder and edit them
4. 

# Configuration
git config -l                               # list all config keys and values
git config --global user.name "<USER>"      # set the username
git config --global user.email "<EMAIL>"    # set the email
git config --global credential.helper cache # cache your login credentials

# Add, Clone and Initialize repos
git remote add [<REMOTE_NAME>] <REMOTE_URL>            # Add a remote repo.
git remote rename <OLD_REMOTE_NAME> <NEW_REMOTE_NAME>  # Rename a remote repo.
git remote remove <REMOTE_NAME>                        # Remove a remote repo.
git remote -v                                          # List added remote repos.
git clone [-b <BRANCH>] <REMOTE_URL> [DIRECTORY]       # Clone a remote repo.
git init [-b <BRANCH>] [DIRECTORY]                     # Initialize a local repo

# Staging & Committing
git add <FILE[*].. AND/OR DIRECTORY[*]..>  # staging Single or Multiple or wildcarded.
git add [-A] [.] [--dry-run]               # staging All of current directory or test dry-run.
git reset                                  # restore to last commit 
git reset --hard                           # restore to last commit , new staged file gone.
git commit [--amend] [-a] [-m="<MESSAGE>"] # commit changes, '--amend' modify last commit, '-a' staging modified/deleted files.
git reset --hard HEAD~                     # delete last commit, restore to previous.
git reset --hard <COMMIT_ID>               # delete all before and restore to specific commit.
git push <REMOTE_NAME> +HEAD               # push last commit deletion/modification to remote.
git push <REMOTE_NAME> +<BRANCH>           # push all commit deletion/modification to remote.

# Banching
git branch <BRANCH>                      # Creat a new Branch, need commits
git checkout [-b] <BRANCH>               # Switch to a Branch, new by '-b'
git branch -a                            # List local and remote branches
git branch -r                            # List remote-tracking branches
git branch -u [<REMOTE_NAME>/<BRANCH>]   # Add current to remote-tracking branches
git branch -d <BRANCH>                   # Delete local branch use '-D' instead of '-d' to force.
git push <REMOTE_NAME> -d <BRANCH>       # Delete remote branch
git branch -rd <BRANCH>                  # Delete local and remote-tracking branch
git fetch [<REMOTE_NAME> <BRANCH>] [-all] # Fetch remote repo changes to current/specific/all branches.
## Merge local/remote branch changes to current branch or test dry-run or abort merge conflict.
git merge [<BRANCH>] [<REMOTE_NAME>/<BRANCH>] [--dry-run] [--abort]
git pull [<REMOTE_NAME> <BRANCH>] [-all]  # Fetch and merge remote repo changes to current/specific/all branches.
## Push current/specific/all branch to remote, upstream '-u' first time.
git push [-u] [<REMOTE_NAME>] [<BRANCH>] [-all]
## Branch renamig process
git branch -M [<OLD_BRANCH>] <NEW_BRANCH>       # Rename an old or current to new
git push <REMOTE_NAME> :refs/heads/<OLD_BRANCH> # Delete old remote branch (safe)
git branch --unset-upstream <OLD_BRANCH>        # Unset old from upstream
git push -u <REMOTE_NAME> <NEW_BRANCH>          # Push new branch and set upstream

# Tagging
git tag                                          # List all local tags 
git tag show <TAG>                               # Details of a commit's tag
git tag <TAG> [<COMMIT_ID>]                      # Create a tag for historical mark point 
git tag <TAG> [<COMMIT_ID>] -af [-m="<MESSAGE>"] # Create a tag for release mark point.
git tag –d <TAG> 	                             # Remove local tag
git push <REMOTE_NAME> :refs/tags/<TAG>          # Remove remote tag (safe)
## Tag renaming process
git tag -d <OLD_TAG>                                     # Get the OLD_COMMIT_ID from output
git tag <NEW_TAG> <OLD_COMMIT_ID> [-af] [-m="<MESSAGE>"] # Create a new tag with OLD_COMMIT_ID
git push --tags                                          # Push all tags to remote
git push <REMOTE_NAME> :refs/tags/<OLD_TAG>              # Remove remote tag (safe)
git ls-remote --tags <REMOTE_NAME>                       # List all remote tags

# Git Patch
### Email-formatted (with author, date and message) or unformatted patch file like
### "0001-commit-message.patch" from changes to reuse portability and share with other developer.
## Patch Generation.
git diff > <FILE>.patch                                       # All unstaged file changes to a unformatted patch file.
git format-patch [-<N>] [<COMMIT_ID>] [-o <DIRECTORY>]        # From All/Specific/Last N'th Commits to patch files per commit.
git format-patch [-<N>] [<COMMIT_ID>] --stdout > <FILE>.patch # From All/Specific/Last N'th Commit to a single patch file
## Patch Application.
git apply --stat file.patch                                  # pre-application stats.
git apply --check file.patch                                 # pre-application error check
git apply patch_file.patch                                   # patch application
git diff                                                     # post-application review changes
git add -A                                                   # post-application staging changes
git commit -m="<MESSAGE>"                                    # post-application commit changes
git am < file.patch                                          # patch application, staging and commit.
git reset --hard HEAD~                                       # Restore the pre-application state.

# Status, Logs, & Misc.
git status                                   # State of the working directory and the staging area. 
git log --oneline --graph --decorate --all   # Nice graph of all commit's log
git log -p [<COMMIT_ID>]                     # A commit's history and file changes
git log --stat [<COMMIT_ID>]                 # Number of Modified files and lines.
git restore <FILE>                           # Restore unstaged file modification.
git restore --staged                         # Restore to staged file unstaged state
git rm <FILE>                                # remove tracked files
git mv <OLD_FILE> <NEW_FILE>                 # rename/move tracked files
git diff                                     # All unstaged file changes from last commit.
git diff [<FILE>]                            # All/Specific unstaged file changes from last commit.
git diff [<COMMIT_ID>]                       # Changes from specific commit to last commit or staged changes.
git diff [<OLD_COMMIT_ID>] [<NEW_COMMIT_ID>] # Changes from specific commit to specific commit.

# Backup & Restore
## Backup repo from a old REMOTE_URL
git clone --mirror <REMOTE_URL> <REPO_NAME>/.git
cd <REPO_NAME>
git config --unset core.bare
git reset --hard
## Restore repo to a new REMOTE_URL
git push --mirror <REMOTE_URL>

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

### Linux OS
<details><summary>Click to collapse/fold.</summary><br/>
	
+ <details>
    <summary>Generic Distro</summary><br/>
	
    * <b>GitHub Desktop - The Linux Fork</b>
    * <i>Installation</i>: [https://github.com/shiftkey/desktop](https://github.com/shiftkey/desktop)
+ <details>
    <summary>Debian-based</summary><br/>
	
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

  ## Install "Midnight Commander".
  # A TUI based Visual File Manager.
  sudo apt install mc
  
  ## Install "ZSH shell".
  sudo apt install -y zsh zsh-syntax-highlighting zsh-autosuggestions
  # Default ZSH configuration.
  cp /etc/skel/.zshrc ~/
  # Instant switch to ZSH.
  zsh
  # Set ZSH as default shell (a reboot may require to replace bash properly).
  chsh -s /bin/zsh
  ```
+ <details>
    <summary>Kali Linux</summary><br/>
  
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
</details>
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
// Change browser's URL
// Usages: browser_url("Replace full url or like 'file.php' here")
function browser_url($url){ echo("<script>history.replaceState({},'','$url');</script>");}

// Escape string value for use in HTML.
// Usages: html_escape("Replace string/variable here")
function html_escape($str){ return '<pre>'.htmlspecialchars($str).'</pre>';}

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
// Usages: url2link("Here is an example url: http://example.com")
function url2link($str){ 
    function u2l_callback($matches){ return '<a href="'.htmlspecialchars($matches[1]).'">'.$matches[1].'</a>';}
    return preg_replace_callback("#(\bhttps?://\S+\b)#",'u2l_callback',$str);
}

// Convert given word or phrase into valid HTML ID.
// Usages: text2id("Replace Text for ID")
function text2id($text, $prepend = null, $delimiter = '-'){
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
// Usages: text2paragraph("Replace text string/variable here")
function text2paragraph($str){return str_replace('<p></p>','','<p>'.preg_replace('#([\r\n]\s*?[\r\n]){2,}#','</p>$0<p>',$str).'</p>');}

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
    fclose($pipes[2]);$code = proc_close($process);
    return '<pre>'.htmlspecialchars($output).'</pre>';
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
![Alt text](https://forums.virtualbox.org/styles/prosilver/imageset/vbox_footer_logo.png?raw=true)
<table ><tbody ><tr><td><details ><summary><b>Click to collapse/fold 👈</b>
</summary>
<h6>Linux/Mac/Windows</h6>

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
<h6>Linux</h6>

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
<h6>Windows</h6>

```batch
:: Fix error "VERR_NEM_VM_CREATE_FAILED"
:: causing by WSL2, Memory integrity etc.
:: ! Restart PC to take effect after command.
bcdedit /set hypervisorlaunchtype off
```

```batch
:: Use this command first or go to directory where
:: Virtualbox installed befor using 'VBoxManage' command.
pushd "%PROGRAMFILES%\Oracle\VirtualBox"
```
</details></td></tr></tbody>
</table>

### Windows
<details><summary>Click to collapse/fold.</summary><br/>
	
```batch
:: Get a CMD prompt during Windows installation.
Press Shift + F10
```

```pwsh
# Creates a virtual disk (VHD/VHDX) snapshot.
Checkpoint-IscsiVirtualDisk -OriginalPath "D:\VHDs\DB.vhdx"
Checkpoint-IscsiVirtualDisk -OriginalPath "D:\VHDs\DB.vhdx" -Description "Before database merge" -ComputerName "fssvr.contoso.com"
```
```pwsh
# Test mode in windows 10+ let user test Microsoft unsigned applications.
# Run below commands in CMD/PowerShell as Administrator and reboot your system.

# Remove test mode watermark.
# Disable test mode.
# Enable Driver Signature Enforcement.
bcdedit -set TESTSIGNING OFF

# Enable test mode (adds a watermark).
# Disable Driver Signature Enforcement.
bcdedit -set TESTSIGNING ON
```
</details>

### WSL (Windows Subsystem for Linux)
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
