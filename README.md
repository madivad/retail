# retail
## tail -f on a folder adding new files after implementation

I called this re(-)tail because it's like creating a whole new instance of tail without actually invoking it. 

The premise of this is for monitoring a folder where new logs can be added and will be picked up by this command.

## Usage:
quite simply, command followed by folder name, eg

    $ retail ~/logs

this will monitor all files that appear in the log directory under the users home directory.

## todo:
Well, there's a few things to do namely:
- gracefully handle a file that are no longer present
- gracefully handle non text/ASCII based files 
- limit to files of a particular type
- incorporate tail lengths (all lines, the last X lines etc)
- port this to OS X
- port this to Windows
- give me some ideas?

## Special note:
***I did not write this. This is not my code***  

I have published this [with permission](http://serverfault.com/a/542580/322904) because it has become EXTREMELY useful to me and I will eventually make some changes to make it more suitable for my needs. But for right now, it works PERFECTLY. In fact, I will gladly hand this repo over to Jack if he so desires, alternatively, feel free to pull and push any changes as you see fit. You, [Sir Jack](http://serverfault.com/users/142829/jack), have answered an age old question that has been unanswered at the command line level (so far as I've determined).

My use case scenario is I have a script that monitors a local device and reports it's value every second. That script appends the new value to an existing file based on the date. When the date increments, the filename changes. This filename would not exist when the `tail` was initially run. Hence, `retail` and it's like invoking a new tail every time it comes around adding new files as required. 

A quick and simple test is to invoke the command on a directory:

    $ retail logs

then after the file has been running returning existing logs files, insert a line to a current file. For example. I have a log file based on date that includes a time and values. Before do something that will inflence the results, I `echo` a note to the log:

    $ echo "# starting microwave" >> 20160515.power.log
    
I then start the device. (obviously I'm using it in a power monitoring situation).

Feel free to enhance this in any way you see fit. 

Cheers!
