# Coursera Downloader

@abstr_hyperlink @abstr_hyperlink @abstr_hyperlink @abstr_hyperlink @abstr_hyperlink 

  * Coursera Downloader
  * Introduction
  * Features
  * Disclaimer
  * Installation instructions 
    * Recommended installation method for all Operating Systems
    * Alternative ways of installing missing dependencies 
      * Alternative installation method for Unix systems
      * ArchLinux
      * Installing dependencies on your own
    * Docker
    * Windows
    * Create an account with Coursera
    * Running the script
    * Resuming downloads
  * Troubleshooting 
    * China issues
    * Found @abstr_number sections and @abstr_number lectures on this page
    * Download timeouts
    * Windows: proxy support
    * Windows: Failed to create process
    * SSLError: [Errno @abstr_number ] _ssl.c: @abstr_number : error: @abstr_number :SSL routines:SSL @abstr_number _READ_BYTES:sslv @abstr_number alert handshake failure
    * Alternative CDN for MathJax.js
  * Reporting issues
  * Filing an issue/Reporting a bug
  * Feedback
  * Contact



# Introduction

@abstr_hyperlink is arguably the leader in _massive open online courses_ (MOOC) with a selection of more than @abstr_number classes from @abstr_number different institutions @abstr_hyperlink . Generous contributions by educators and institutions are making excellent education available to many who could not afford it otherwise. There are even non-profits with "feet on the ground" in remote areas of the world who are helping spread the wealth (see the feedback below from @abstr_hyperlink ).

This script makes it easier to batch download lecture resources (e.g., videos, ppt, etc) for Coursera classes. Given one or more class names and account credentials, it obtains week and class names from the _lectures_ page, and then downloads the related materials into appropriately named files and directories.

Why is this helpful? A utility like @abstr_hyperlink can work, but has the following limitations:

@abstr_number . Video names have numbers in them, but this does not correspond to the actual order. Manually renaming them is a pain that is best left for computers. @abstr_number . Using names from the syllabus page provides more informative names. @abstr_number . Using `wget` in a for loop picks up extra videos which are not posted/linked, and these are sometimes duplicates.

Browser extensions like _DownloadThemAll_ is another possibility, but `coursera-dl` provides more features such as appropriately named files.

This work was originally inspired in part by @abstr_hyperlink by which I've downloaded many other good videos such as those from Khan Academy.

# Features

  * Support for all kinds of courses (i.e., "Old Platform"/time-based as well as "New Platform"/on-demand courses).
  * Intentionally detailed names, so that it will display and sort properly on most interfaces (e.g., @abstr_hyperlink or MX Video on Android devices).
  * Regex-based section (week) and lecture name filters to download only certain resources.
  * File format extension filter to grab resource types you want.
  * Login credentials accepted on command-line or from `.netrc` file.
  * Default arguments loaded from `coursera-dl.conf` file.
  * Core functionality tested on Linux, Mac and Windows.



# Disclaimer

`coursera-dl` is meant to be used only for your material that Coursera gives you access to download.

We do not encourage any use that violates their @abstr_hyperlink . A relevant excerpt:

> "[...] Coursera grants you a personal, non-exclusive, non-transferable license to access and use the Sites. You may download material from the Sites only for your own personal, non-commercial use. You may not otherwise copy, reproduce, retransmit, distribute, publish, commercially exploit or otherwise transfer any material, nor may you modify or create derivatives works of the material."

# Installation instructions

`coursera-dl` requires Python @abstr_number or Python @abstr_number and a free Coursera account enrolled in the class of interest. (As of February of @abstr_number , we test automatically the execution of the program with Python versions @abstr_number . @abstr_number , @abstr_number . @abstr_number , Pypy, @abstr_number . @abstr_number , @abstr_number . @abstr_number , and @abstr_number . @abstr_number ).

**Note:** We _strongly_ recommend that you use a Python @abstr_number interpreter ( @abstr_number . @abstr_number or later).

On any operating system, ensure that the Python executable location is added to your `PATH` environment variable and, once you have the dependencies installed (see next section), for a _basic_ usage, you will need to invoke the script from the main directory of the project and prepend it with the word `python`. You can also use more advanced features of the program by looking at the "Running the script" section of this document.

_Note:_ You must already have (manually) agreed to the Honor of Code of the particular courses that you want to use with `coursera-dl`.

## Recommended installation method for all Operating Systems

From a command line (preferably, from a virtual environment), simply issue the command:
    
    
    pip install coursera-dl
    

This will download @abstr_hyperlink of the program from the @abstr_hyperlink along with _all_ the necessary dependencies. At this point, you should be ready to start using it.

If this does not work, because your Python @abstr_number version is too old (e.g. @abstr_number . @abstr_number . @abstr_number on Ubuntu @abstr_number . @abstr_number ), try:
    
    
    apt-get install python @abstr_number  python @abstr_number -pip
    pip @abstr_number  install coursera-dl
    

instead.

**Note @abstr_number :** We strongly recommend that you _don't_ install the package globally on your machine (i.e., with root/administrator privileges), as the installed modules may conflict with other Python applications that you have installed in your system (or they can interfere with `coursera-dl`). Prefer to use the option `--user` to `pip install`, if you need can.

**Note @abstr_number :** As already mentioned, we _strongly_ recommend that you use a new Python @abstr_number interpreter (e.g., @abstr_number . @abstr_number or later), since Python @abstr_number has better support for SSL/TLS (for secure connections) than earlier versions.  
If you must use Python @abstr_number , be sure that you have at least Python @abstr_number . @abstr_number . @abstr_number (later versions are OK).  
Otherwise, you can still use `coursera-dl`, but you will have to install the extra package `ndg-httpsclient`, which may involve compilation (at least on Linux systems).

## Alternative ways of installing missing dependencies

We strongly recommend that you consider installing Python packages with @abstr_hyperlink , as in it is the current @abstr_hyperlink , unless directed otherwise by one of the project members (for instance, when testing or debugging a new feature or using the source code directly from our git repository). If you are using `pip`, you can directly install all the dependencies from the requirements file using `pip install -r requirements.txt`.

### Alternative installation method for Unix systems

We strongly recommend that you install `coursera-dl` and all its dependencies in a way that does _not_ interfere with the rest of your Python installation. This is accomplished by the creation of a _virtual environment_ , or "virtualenv".

For the initial setup, in a Unix-like operating system, please use the following steps (create/adapt first the directory `/directory/where/I/want/my/courses`):
    
    
    cd /directory/where/I/want/my/courses
    virtualenv my-coursera
    cd my-coursera
    source bin/activate
    git clone https://github.com/coursera-dl/coursera-dl
    cd coursera-dl
    pip install -r requirements.txt
    ./coursera-dl ...
    

To further download new videos from your classes, simply perform:
    
    
    cd /directory/where/I/want/my/courses/my-coursera
    source bin/activate
    cd coursera-dl
    ./coursera-dl ...
    

We are working on streamlining this whole process so that it is as simple as possible, but to support older versions of Python and to cope with Coursera disabling SSLv @abstr_number , we have to take a few extra steps. In any case, it is _highly_ recommended that you always install the latest version of the Python interpreter that you can.

### ArchLinux

AUR package: @abstr_hyperlink 

### Installing dependencies on your own

**Warning:** This method is not recommended unless you have experience working with multiple Python environments.

You can use the `pip` program to install the dependencies on your own. They are all listed in the `requirements.txt` file (and the extra dependencies needed for development are listed in the `requirements-dev.txt` file).

To use this method, you would proceed as:
    
    
    pip install -r requirements.txt
    pip install -r requirements-dev.txt
    

The second line above should only be needed if you intend to help with development (and help is _always_ welcome) or if a maintainer of the project asks you to install extra packages for debugging purposes.

Once again, before filing bug reports, if you installed the dependencies on your own, please check that the versions of your modules are at least those listed in the `requirements.txt` file (and, `requirements-dev.txt` file, if applicable).

## Docker

If you prefer you can run this software inside Docker:

@abstr_code_section 

Or using netrc file:

@abstr_code_section 

The actual working dir for coursera-dl is /courses, all courses will be downloaded there if you don't specify otherwise.

## Windows

`python -m pip install coursera-dl`

Be sure that the Python install path is added to the PATH system environment variables. This can be found in Control Panel > System > Advanced System Settings > Environment Variables.

@abstr_code_section 

Or if you have restricted installation permissions and you've installed Python under AppData, add this to your PATH.

@abstr_code_section 

Coursera-dl can now be run from commandline or powershell.

## Create an account with Coursera

If you don't already have one, create a @abstr_hyperlink account and enroll in a class. See https://www.coursera.org/courses for the list of classes.

## Running the script

Run the script to download the materials by providing your Coursera account credentials (e.g. email address and password or a `~/.netrc` file), the class names, as well as any additional parameters:
    
    
    General:                     coursera-dl -u <user> -p <pass> modelthinking- @abstr_number
    

If you don't want to type your password in command line as plain text, you can use the script without `-p` option. In this case you will be prompted for password once the script is run.
    
    
    Without -p field:            coursera-dl -u <user> modelthinking- @abstr_number 
    Multiple classes:            coursera-dl -u <user> -p <pass> saas historyofrock @abstr_number - @abstr_number  algo- @abstr_number - @abstr_number 
    Filter by section name:      coursera-dl -u <user> -p <pass> -sf "Chapter_Four" crypto- @abstr_number 
    Filter by lecture name:      coursera-dl -u <user> -p <pass> -lf " @abstr_number . @abstr_number _" ml- @abstr_number - @abstr_number 
    Download only ppt files:     coursera-dl -u <user> -p <pass> -f "ppt" qcomp- @abstr_number - @abstr_number 
    Use a ~/.netrc file:         coursera-dl -n -- matrix- @abstr_number 
    Get the preview classes:     coursera-dl -n -b ni- @abstr_number 
    Specify download path:       coursera-dl -n --path=C:\Coursera\Classes\ comnetworks- @abstr_number 
    Display help:                coursera-dl --help
    
    Maintain a list of classes in a dir:
      Initialize:              mkdir -p CURRENT/{class @abstr_number ,class @abstr_number ,..classN}
      Update:                  coursera-dl -n --path CURRENT `\ls CURRENT`
    

**Note:** If your `ls` command is aliased to display a colorized output, you may experience problems. Be sure to escape the `ls` command (use `\ls`) to assure that no special characters get sent to the script.

Note that we _do_ support the New Platform ("on-demand") classes.

On *nix platforms, the use of a `~/.netrc` file is a good alternative to specifying both your username (i.e., your email address) and password every time on the command line. To use it, simply add a line like the one below to a file named `.netrc` in your home directory (or the @abstr_hyperlink , if you are using Windows) with contents like:
    
    
    machine coursera-dl login <user> password <pass>
    

Create the file if it doesn't exist yet. From then on, you can switch from using `-u` and `-p` to simply call `coursera-dl` with the option `-n` instead. This is especially convenient, as typing usernames (email addresses) and passwords directly on the command line can get tiresome (even more if you happened to choose a "strong" password).

Alternatively, if you want to store your preferred parameters (which might also include your username and password), create a file named `coursera-dl.conf` where the script is supposed to be executed, with the following format:
    
    
    --username <user>
    --password <pass>
    --subtitle-language en,zh-CN|zh-TW
    --download-quizzes
    #--mathjax-cdn https://cdn.bootcss.com/mathjax/ @abstr_number . @abstr_number . @abstr_number /MathJax.js
    # more other parameters
    

Parameter which is stored in the file will be overriden if it is again specified in your commandline script

**Note:** In `coursera-dl.conf`, all the parameters should not be wrapped with quotes.

## Resuming downloads

In default mode when you interrupt the download process by pressing `CTRL`+`C`, partially downloaded files will be deleted from your disk and you have to start the download process from the beginning. If your download was interrupted by something other than KeyboardInterrupt (`CTRL`+`C`) like sudden system crash, partially downloaded files will remain on your disk and the next time you start the process again, these files will be discarded from download list!, therefore it's your job to delete them manually before next start. For this reason we added an option called `--resume` which continues your downloads from where they stopped:
    
    
    coursera-dl -u <user> -p <pass> --resume sdn @abstr_number - @abstr_number
    

This option can also be used with external downloaders:
    
    
    coursera-dl --wget -u <user> -p <pass> --resume sdn @abstr_number - @abstr_number
    

*Note @abstr_number *: Some external downloaders use their own built-in resume feature which may not be compatible with others, so use them at your own risk.

*Note @abstr_number *: Remember that in resume mode, interrupted files **WON'T** be deleted from your disk.

**NOTE** : If your password contains punctuation, quotes or other "funny characters" (e.g., `<`, `>`, `#`, `&`, `|` and so on), then you may have to escape them from your shell. With bash or other Bourne-shell clones (and probably with many other shells) one of the better ways to do so is to enclose your password in single quotes, so that you don't run into problems. See @abstr_hyperlink for more information.

# Troubleshooting

If you have problems when downloading class materials, please try to see if one of the following actions solve your problem:

  * Make sure the class name you are using corresponds to the resource name used in the URL for that class: `https://www.coursera.org/learn/<CLASS_NAME>/home/welcome`

  * Have you tried to clean the cached cookies/credentials with the `--clear-cache` option?

  * Note that many courses (most, perhaps?) may remove the materials after a little while after the course is completed, while other courses may retain the materials up to a next session/offering of the same course (to avoid problems with academic dishonesty, apparently).   
  
In short, it is not guaranteed that you will be able to download after the course is finished and this is, unfortunately, nothing that we can help you with.

  * Make sure you have installed and/or updated all of your dependencies according to the `requirements.txt` file as described above.

  * One can export a Netscape-style cookies file with a browser extension ( @abstr_hyperlink , @abstr_hyperlink ) and use it with the `-c` option. This comes in handy when the authentication via password is not working (the authentication process changes now and then).

  * If results show @abstr_number sections, you most likely have provided invalid credentials (username and/or password in the command line or in your `.netrc` file or in your `coursera-dl.conf` file).

  * For courses that have not started yet, but have had a previous iteration sometimes a preview is available, containing all the classes from the last course. These files can be downloaded by passing the `--preview` parameter.

  * If you get an error like `Could not find class: <CLASS_NAME>`, then:

    * Verify that the name of the course is correct. Current class names in coursera are composed by a short course name e.g. `class` and the current version of the course (a number). For example, for a class named `class`, you would have to use `class- @abstr_number`, `class- @abstr_number` etc.
    * Second, verify that you are enrolled in the course. You won't be able to access the course materials if you are not officially enrolled and agreed to the honor course _via the website_.
  * If:

    * You get an error when using `-n` to specify that you want to use a `.netrc` file and,
    * You want the script to use your default netrc file and,
    * You get a message saying `coursera-dl: error: too few arguments`

Then you should specify `--` as an argument after `-n`, that is, `-n --` or change the order in which you pass the arguments to the script, so that the argument after `-n` begins with an hyphen (`-`). Otherwise, Python's `argparse` module will think that what you are passing is the name of the netrc file that you want to use. See issue # @abstr_number .

  * If your password has spaces, don't forget to write it using quotes.

  * Have you installed the right project ?   
  
**Warning** : If you installed the script using PyPi (pip) please verify that you installed the correct project. We had to use a different name in pip because our original name was already taken. Remember to install it using: @abstr_code_section 




## China issues

If you are from China and you're having problems downloading videos, adding " @abstr_number . @abstr_number . @abstr_number . @abstr_number d @abstr_number c @abstr_number hcgiwev @abstr_number .cloudfront.net" in the hosts file (/etc/hosts) and freshing DNS with "ipconfig/flushdns" may work (see https://github.com/googlehosts/hosts for more info).

## Found @abstr_number sections and @abstr_number lectures on this page

First of all, make sure you are enrolled to the course you want to download.

Many old courses have already closed enrollment so often it's not an option. In this case, try downloading with `--preview` option. Some courses allow to download lecture materials without enrolling, but it's not common and is not guaranteed to work for every course.

Finally, you can download the videos if you have, at least, the index file that lists all the course materials. Maybe your friend who is enrolled could save that course page for you. In that case use the `--process_local_page` option.

Alternatively you may want to try this Chrome extension: https://chrome.google.com/webstore/detail/coursera-materials-downlo/ijkboagofaehocnjacacdhdcbbcpilih

If none of the above works for you, there is nothing we can do.

## Download timeouts

Coursera-dl supports external downloaders but note that they are only used to download materials after the syllabus has been parsed, e.g. videos, PDFs, some handouts and additional files (syllabus is always downloaded using the internal downloader). If you experience problems with downloading such materials, you may want to start using external downloader and configure its timeout values. For example, you can use aria @abstr_number c downloader by passing `--aria` option:

@abstr_code_section 

And put this into aria @abstr_number c's configuration file `~/.aria @abstr_number /aria @abstr_number .conf` to reduce timeouts:

@abstr_code_section 

Timeout configuration for internal downloader is not supported.

## Windows: proxy support

If you're on Windows behind a proxy, set up the environment variables before running the script as follows:

@abstr_code_section 

Related discussion: @abstr_hyperlink 

## Windows: Failed to create process

In `C:\Users\<user>\AppData\Local\Programs\Python\Python @abstr_number - @abstr_number \Scripts` or wherever Python installed (above is default for Windows) edit below file in idle: (right click on script name and select 'edit with idle in menu)

@abstr_code_section 

from

@abstr_code_section 

to

@abstr_code_section 

(add quotes). This is a known pip bug.

Source: @abstr_hyperlink @abstr_hyperlink 

## SSLError: [Errno @abstr_number ] _ssl.c: @abstr_number : error: @abstr_number :SSL routines:SSL @abstr_number _READ_BYTES:sslv @abstr_number alert handshake failure

This is a known error, please do not report about this error message! The problem is in **YOUR** environment. To fix it, do the following:

@abstr_code_section If the error remains, try installing coursera-dl from github following this instruction: https://github.com/coursera-dl/coursera-dl#alternative-installation-method-for-unix-systems

If you still have the problem, please read the following issues for more ideas on how to fix it: @abstr_hyperlink @abstr_hyperlink @abstr_hyperlink 

This is also worth reading: https://urllib @abstr_number .readthedocs.io/en/latest/security.html#insecureplatformwarning

## Alternative CDN for `MathJax.js`

When saving a course page, we enabled `MathJax` rendering for math equations, by injecting `MathJax.js` in the header. The script is using a cdn service provided by @abstr_hyperlink . However, that url is not accessible in some countries/regions, you can provide a `--mathjax-cdn <MATHJAX_CDN>` parameter to specify the `MathJax.js` file that is accessible in your region.

# Reporting issues

Before reporting any issue please follow the steps below:

@abstr_number . Verify that you are running the latest version of the script, and the recommended versions of its dependencies, see them in the file `requirements.txt`. Use the following command if in doubt:
    
    
        pip install --upgrade coursera-dl
    

@abstr_number . If the problem persists, feel free to @abstr_hyperlink in our bugtracker, please fill the issue template with _as much information as possible_.

# Filing an issue/Reporting a bug

When reporting bugs against `coursera-dl`, please don't forget to include enough information so that you can help us help you:

  * Is the problem happening with the latest version of the script?
  * What operating system are you using?
  * Do you have all the recommended versions of the modules? See them in the file `requirements.txt`.
  * What is the course that you are trying to access?
  * What is the precise command line that you are using (feel free to hide your username and password with asterisks, but leave all other information untouched).
  * What are the precise messages that you get? Please, use the `--debug` option before posting the messages as a bug report. Please, copy and paste them. Don't reword/paraphrase the messages.



# Feedback

I enjoy getting feedback. Here are a few of the comments I've received:

  * "Thanks for the good job! Knowledge will flood the World a little more thanks to your script!"   
Guillaume V. @abstr_number / @abstr_number / @abstr_number 

  * "Just wanted to send you props for your Python script to download Coursera courses. I've been using it in Kenya for my non-profit to get online courses to places where internet is really expensive and unreliable. Mostly kids here can't afford high school, and downloading one of these classes by the usual means would cost more than the average family earns in one week. Thanks!"   
Jay L., @abstr_hyperlink @abstr_number / @abstr_number / @abstr_number 

  * "I am a big fan of Coursera and attend lots of different courses. Time constraints don't allow me to attend all the courses I want at the same time. I came across your script, and I am very happily using it! Great stuff and thanks for making this available on Github - well done!"   
William G. @abstr_number / @abstr_number / @abstr_number 

  * "This script is awesome! I was painstakingly downloading each and every video and ppt by hand -- looked into wget but ran into wildcard issues with HTML, and then.. I came across your script. Can't tell you how many hours you've just saved me :) If you're ever in Paris / Stockholm, it is absolutely mandatory that I buy you a beer :)"   
Razvan T. @abstr_number / @abstr_number / @abstr_number 

  * "Thanks a lot! :)"   
Viktor V. @abstr_number / @abstr_number / @abstr_number 




# Contact

Please, post bugs and issues on @abstr_hyperlink . Send other comments to Rogério Theodoro de Brito (the current maintainer): rbrito@ime.usp.br (twitter: @abstr_hyperlink ) or to John Lehmann (the original author): first last at geemail dotcom (twitter: @abstr_hyperlink ).