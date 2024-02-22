# vimrc configuration file
A file that contains initialization commands is called a "vimrc" file.
Each line in a vimrc file is executed as an Ex command line.  It is
sometimes also referred to as "exrc" file.  They are the same type of
file, but "exrc" is what Vi always used, "vimrc" is a Vim specific
name.  Also see |vimrc-intro|.

### Places for your personal initializations:

 | OS         | path                                                       | 
 | --         | --                                                         | 
 | Unix       | $HOME/.vimrc or $HOME/.vim/vimrc                           | 
 | MS-Windows | $HOME/\_vimrc, $HOME/vimfiles/vimrc or $VIM/\_vimrc        | 
 | Amiga      | s:.vimrc, home:.vimrc, home:vimfiles:vimrc  or $VIM/.vimrc | 
 | Haiku      | $HOME/config/settings/vim/vimrc                            | 

The files are searched in the order specified above and only the first
one that is found is read.

RECOMMENDATION: Put all your Vim configuration stuff in the
$HOME/.vim/ directory ($HOME/vimfiles/ for MS-Windows). That makes it
easy to copy it to another system.

If Vim was started with "-u filename", the file "filename" is used.
All following initializations until 4. are skipped. $MYVIMRC is not
set.
"vim -u NORC" can be used to skip these initializations without
reading a file.  "vim -u NONE" also skips loading plugins.  |-u|

If Vim was started in Ex mode with the "-s" argument, all following
initializations until 4. are skipped.  Only the "-u" option is
interpreted

### evim.vim 

 a. If vim was started as |evim| or |eview| or with the |-y| argument, the
script $VIMRUNTIME/evim.vim will be loaded.
### system-vimrc 

 b. For Unix, MS-Windows, VMS, Macintosh and Amiga the system vimrc file
is read for initializations.  The path of this file is shown with the
":version" command.  Mostly it's "$VIM/vimrc".  Note that this file is
ALWAYS read in 'compatible' mode, since the automatic resetting of
'compatible' is only done later.  Add a ":set nocp" command if you
like.  For the Macintosh the $VIMRUNTIME/macmap.vim is read.

  ##### VIMINIT .vimrc \_vimrc EXINIT .exrc \_exrc $MYVIMRC

 c. Five places are searched for initializations.  The first that exists
is used, the others are ignored.  The $MYVIMRC environment variable is
set to the file that was first found, unless $MYVIMRC was already set
and when using VIMINIT.
I   The environment variable VIMINIT (see also |compatible-default|) (\*)
    The value of $VIMINIT is used as an Ex command line.
II  The user vimrc file(s):

 | -                                 | -                | 
 | --                                | --               | 
 | "$HOME/.vimrc"                    | (for Unix) (\*)  | 
 | "$HOME/.vim/vimrc"                | (for Unix) (\*)  | 
 | "s:.vimrc"                        | (for Amiga) (\*) | 
 | "home:.vimrc"                     | (for Amiga) (\*) | 
 | "home:vimfiles:vimrc"             | (for Amiga) (\*) | 
 | "$VIM/.vimrc"                     | (for Amiga) (\*) | 
 | "$HOME/\_vimrc"                   | (for Win32) (\*) | 
 | "$HOME/vimfiles/vimrc"            | (for Win32) (\*) | 
 | "$VIM/\_vimrc"                    | (for Win32) (\*) | 
 | "$HOME/config/settings/vim/vimrc" | (for Haiku) (\*) | 

Note: For Unix and Amiga, when ".vimrc" does not exist,
"\_vimrc" is also tried, in case an MS-DOS compatible file
system is used.  For MS-Windows ".vimrc" is checked after
"\_vimrc", in case long file names are used.
Note: For Win32, "$HOME" is checked first.  If no "\_vimrc" or
"\.vimrc" is found there, "$VIM" is tried.  See |$VIM| for when
	$VIM is not set.
* The environment variable EXINIT.
  The value of $EXINIT is used as an Ex command line.
* The user exrc file(s).  Same as for the user vimrc file, but with
  "vimrc" replaced by "exrc".  But only one of ".exrc" and "\_exrc" is
   used, depending on the system.  And without the (\*)!
*  The default vimrc file, $VIMRUNTIME/defaults.vim.  This sets up
   options values and has "syntax on" and "filetype on" commands,
   which is what most new users will want.  See |defaults.vim|.

If the 'exrc' option is on (which is NOT the default), the current
directory is searched for three files.  The first that exists is used,
the others are ignored.
- The file ".vimrc" (for Unix, Amiga) (\*) "\_vimrc" (for Win32) (\*)
- The file "\_vimrc" (for Unix, Amiga) (\*) ".vimrc" (for Win32) (\*)
- The file ".exrc"  (for Unix, Amiga) "\_exrc"  (for Win32)

(\*) Using this file or environment variable will cause 'compatible' to be
off by default.  See |compatible-default|.

Note: When using the |mzscheme| interface, it is initialized after loading
the vimrc file.  Changing 'mzschemedll' later has no effect.

