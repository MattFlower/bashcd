Intro
=====

bashcd is a collection of tools meant to make navigating the command line a bit easier.  The following commands are included:

<b>fcd &lt;dirname&gt;</b>

Recurses subdirectories using the find command in order to find a directory.  This is probably the most reliable of the methods
I provide to recurse subdirectories, but there is one complication -- if you have a particularly large subtree, it may be slow.

<b>filecd &lt;filename&gt;</b>

Switch to the directory which contains the identified file.  For example, if you were in the home directory and if you had a 
file named /home/mflower/code/opensource/README.md, typing "filecd README.md" would switch to the /home/mflower/code/opensource
directory.

<b>dcd &lt;directory alias&gt;</b>

Dcd keeps an internal list of directory aliases.  For example, if you wanted to keep a directory alias for the 
/home/mflower/code/opensource directory, I would type dcd -a opensource from that directory.  In the future, typing 
dcd opensource would switch me to that directory.  dcd -l gives you a list of all current aliases.
Type dcd -h for further details.

<b>lcd &lt;dirname&gt;</b>

Similar to fcd, except not limited to only subdirectories.  Lcd can switch to any directory on your machine which is currently
in the locate database.  This is great if you have a well updated located database. 

<b>mcd &lt;dirname&gt;</b>

Very similar to lcd except that it is specific to mac.  It uses the mdfind command line utility which uses the underlying 
indexing that happens constantly on the mac.  

<b>ucd &lt;dirname&gt;</b>

Switch to a parent directory of the current directory.  For example, if the current directory is /home/mflower/code/opensource, 
you could use ucd home to switch to the /home directory.

Installation
============
Copy the file https://raw.github.com/MattFlower/bashcd/master/bashcd to a local file called .bashcd in your root directory.
Add the following line to your .profile, .bashrc, or .bash_profile.  

> source .bashcd

Once you restart your terminal bashcd will be automatically initialized.  If you wish to try it out without installing it 
permanently, you can type "source <path to your .bashcd file>" (without the < and > marks).

If you have problems with scripts complaining about dcd after doing this, consider wrapping the source in a check to make sure
you are in an interactive shell:


    if [[ $- == *i* ]]; then
        source .bashcd
    fi

Documentation
=============
All commands have a help file built into them.  Type the command and press enter to see the help.  I've also copied these
help files into the wiki: <https://github.com/MattFlower/bashcd/wiki>

Features
========
All of the above features have bash completion built in.  After you have typed the name of the command, hit the tab key for
completion.

If there are multiple completions for the command you have entered, bashcd will show a list of potential directories to go to.  
For example:

<pre>
/Users/mflower/code/code/a $ ucd code
 
Please choose a directory to change to
--------------------------------------
  1. /Users/mflower/code 
  2. /Users/mflower/code/code 

Your choice: 1

/Users/mflower/code $
</pre>

