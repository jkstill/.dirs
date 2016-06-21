        Set up directory stack functions

 jks - 04/19/95 modified  to work in a reasonable manner
 jks - 08/21/95 modified to use Korn Shell arrays - much faster
 jks - 08/23/95 mkdir DIR_DIR if it does not exist
 jks - 12/26/97 compatible with bash 2.0

 these functions will allow you to create a set of directorys that
 can be saved to a file, and recalled to memory.  Once stored in memory
 ( in a Korn Shell array ) the list may be easily displayed.  You can jump
 to any directory with the g command by referring to its number. The list
 may be added to, deleted from, and saved back to a file

 example:

 to create a directory list that stores paths for the ctp forms modules

 cd /usr1av2/claims/ctpsrc/forms/src
 pushd
 cd ../usrdoc
 pushd
 cd ../isdoc
 pushd

 now enter 'dirs' or 'd' and you will see

 OLDPWD: /usr1av2/claims/ctpsrc/forms/usrdoc

 0       /usr1av2/claims/ctpsrc/forms/isdoc
 1       /usr1av2/claims/ctpsrc/forms/usrdoc
 2       /usr1av2/claims/ctpsrc/forms/src

 enter the following to save to file:
    saved ctpforms 'Source, User docs and Internal docs for CTP Oracle Forms'
    ( these are saved in $HOME/.dirs/<filename>

 now type 'cleardir'
 type 'd' to see that directories have been cleared
 type 'loadd ctpforms' a
 now type 'd' to see that directory set has been reloaded
 type 'g 1' to goto the /usr1av2/claims/ctpsrc/forms/usrdoc dir

 to load these functions automatically when you login, just make sure
 this file is in your home directory, and include this line in your
 .alias or .profile file.

 . <your home dir> /.dirs.pkg

 ex: . /usr1av2/jared/.dirs.pkg



###################################################

 Functions in dirs

 chkhome:  sets the HOME variable if not already set - used internally
 chkname:  sets the LOGNAME variable if not already set - used internally

 cleardir: resets the directory stack

 dirs: display current directory stack

 g: the 'goto dir' command - use with dir's number as displayed with 'dirs'

 gold: goto old; changes dir to OLDPWD

 loaddir: loads the specified directory stack file into the directory stack
          im memory.  if no file specified, loads '${HOME/.dirs/defdir'

 popd: pop the top directory off of the stack

 pushd: push the current directory onto the top of the directory stack

 rotd: rotate the directory stack; moves topmost dir to bottom of stack

 showdir: by itself, shows comment line ( first line ) from all files in
          the $HOME/.dirs directory.  when an argument is given, it will
          show the contents of specified directory stack file.
          ie. 'showdir ctpforms' would display the contents of our example
          file

 showalldir: shorcut command to show contents of all stack files

 savedir: saves the contents of the current directory stack to the named file.
          may optionally include a comment.
          if no filename is given, it will default to $HOME/.dirs/defdir
          if no comment is given, it defaults to 'created by savedir'
          if you resave the directory stack to a directory stack file that
          already exists, the current comment will be preserved, so there is
          no need to type it in again if you don't want to change it

          here are various forms of savedir:

          savedir
          this will save the current directory stack to $HOME/.dirs/defdir
          with the comment 'defdir - created by savedir'

          savedir ctpforms 'Source for Oracle forms'
          this will save the current directory stack to $HOME/.dirs/ctpforms
          with the comment 'ctpforms - Source for Oracle forms'

          if load the ctpforms directory stack and then add to it with
          'pushdir', you may use the command 'savedir ctpforms' to resave
          and the comment line will be preserved


poirot-jkstill-~/shell/dirs-09:46:06
> head -108 .dirs.pkg| cut -b3-

######################################################################
Set up directory stack functions

jks - 04/19/95 modified  to work in a reasonable manner
jks - 08/21/95 modified to use Korn Shell arrays - much faster
jks - 08/23/95 mkdir DIR_DIR if it does not exist
jks - 12/26/97 compatible with bash 2.0

these functions will allow you to create a set of directorys that
can be saved to a file, and recalled to memory.  Once stored in memory
( in a Korn Shell array ) the list may be easily displayed.  You can jump
to any directory with the g command by referring to its number. The list
may be added to, deleted from, and saved back to a file

example:

to create a directory list that stores paths for the ctp forms modules

cd /usr1av2/claims/ctpsrc/forms/src
pushd
cd ../usrdoc
pushd
cd ../isdoc
pushd

now enter 'dirs' or 'd' and you will see

OLDPWD: /usr1av2/claims/ctpsrc/forms/usrdoc

0       /usr1av2/claims/ctpsrc/forms/isdoc
1       /usr1av2/claims/ctpsrc/forms/usrdoc
2       /usr1av2/claims/ctpsrc/forms/src

enter the following to save to file:
   saved ctpforms 'Source, User docs and Internal docs for CTP Oracle Forms'
   ( these are saved in $HOME/.dirs/<filename>

now type 'cleardir'
type 'd' to see that directories have been cleared
type 'loadd ctpforms' a
now type 'd' to see that directory set has been reloaded
type 'g 1' to goto the /usr1av2/claims/ctpsrc/forms/usrdoc dir

to load these functions automatically when you login, just make sure
this file is in your home directory, and include this line in your
.alias or .profile file.

. <your home dir> /.dirs.pkg

ex: . /usr1av2/jared/.dirs.pkg



##################################################

Functions in dirs

chkhome:  sets the HOME variable if not already set - used internally
chkname:  sets the LOGNAME variable if not already set - used internally

cleardir: resets the directory stack

dirs: display current directory stack

g: the 'goto dir' command - use with dir's number as displayed with 'dirs'

gold: goto old; changes dir to OLDPWD

loaddir: loads the specified directory stack file into the directory stack
         im memory.  if no file specified, loads '${HOME/.dirs/defdir'

popd: pop the top directory off of the stack

pushd: push the current directory onto the top of the directory stack

rotd: rotate the directory stack; moves topmost dir to bottom of stack

showdir: by itself, shows comment line ( first line ) from all files in
         the $HOME/.dirs directory.  when an argument is given, it will
         show the contents of specified directory stack file.
         ie. 'showdir ctpforms' would display the contents of our example
         file

showalldir: shorcut command to show contents of all stack files

savedir: saves the contents of the current directory stack to the named file.
         may optionally include a comment.
         if no filename is given, it will default to $HOME/.dirs/defdir
         if no comment is given, it defaults to 'created by savedir'
         if you resave the directory stack to a directory stack file that
         already exists, the current comment will be preserved, so there is
         no need to type it in again if you don't want to change it

         here are various forms of savedir:

         savedir
         this will save the current directory stack to $HOME/.dirs/defdir
         with the comment 'defdir - created by savedir'

         savedir ctpforms 'Source for Oracle forms'
         this will save the current directory stack to $HOME/.dirs/ctpforms
         with the comment 'ctpforms - Source for Oracle forms'

         if load the ctpforms directory stack and then add to it with
         'pushdir', you may use the command 'savedir ctpforms' to resave
         and the comment line will be preserved
