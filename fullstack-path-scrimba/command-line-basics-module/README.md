# Command Line Basics Notes

<!-- If note file have it's own folder, use './../readme.md' path to go one back. However if note file doesn't have it's own folder, you should use './readme.md' path to go one back. -->
* [Click here to go one back](./../readme.md).

* The directory named  'geography_game' is a little playground to interact with the command line.

## Some basic commands and operators 

* 'pwd', 'ls', 'cd', 'clear', '..', 'touch', 'mkdir', 
* 'rm'
    * -r -> If you tried to delete a non empty directory, use this instead of rmdir because you can't use that.
* rmdir
    * -r -> If the directory not empty, use this
* echo
    * '>' -> 'appends'. redirection operator.
    * echo 'Hello, world! > hello.txt
    It redirects the output inside of the hello.txt and overwrite on the existing data.
    * '>>' -> 'overrides'. append redirection operator. We also are using this like the redirection operator but with this operator, output was not overwritten but appended to the specified output file.
    * If the specified output file is not created before, echo command will realize and create that file.
* cat
    * cat hello.txt -> It shows the content of the hello.txt file
    * We also can use some operators with cat command too.
        * cat hello.txt > hello_copy.txt -> We also can redirect the output with our operator too. Cat command overwrites the hello.txt file content to the hello_copy.txt file.
    * Like how it happens for the echo, cat command also can create some files that does not exist in the first place.

## Notes from the 'Find files and directories' part
* Options are way us add more functionality to a command and change it's default behaviour. So, we use options to add additional functionality to a command.
* find [path] [option] [expression]
    * example: find . -name 'forest*'
    * The path defines where the search starts. All child elements are included in the search.
* There is short and long option syntax, short one with one dash, long one with two dash (and maybe with a bit detailed name). For example -r and --recursive options. -r and --recursive both are exact same option with the same functionality.
    * Many (but not all) options come in a both a long and a short version. Short one is more faster to type and long one is more readable. Other options are only exist in one single version, either short or long.
* A wildcard character is a symbol used in computing to represent one or more characters in a string, commonly used in searches and pattern matching. For our bash shell, an asterisk represent a wildcard character for us. 
* Paths
    * Relative file paths: example -> ../forests
    * Absolute file paths: example -> /Users/ajo/Coding/Scrimba/command_line/geography_game/forests
    * Current directory: .
    * Parent directory: ..
    * Home directory(Top level directory of the user account on the current device): ~ 
    * Root directory(Top level directory of the entire operating system): /
    * Note: Use the home and root directory with caution!

## Notes from the 'Aside: Kill a process' part
* To kill/terminate a process -> CTRL + C
* When to kill a process
    * If you're 'stuck' in an unfinished action, for instance due to a missing quotation mark.

## Notes from the 'Rename, Move & Copy' part
* Rename
    * mv [old_name] [new_name]
    * example: mv team_members.txt team.txt
    * Same syntax for files and directories. If I know right, directory is also a file in the essence.
* Move
    * mv [name] [new_location]
    * example: mv capitals.txt geography_game/cities
    * Same syntax for files and directories.
    * **Warning**: If the new location does not yet exist, 'mv' will rename the item instead of moving it. One small typo can cause different results for mv command as we understand.
* Copy
    * cp [original_name] [copy_name]
    * Copy file: cp team.txt team_backup.txt
    * Copy directory: cp -r cities cities_backup
        * Note: Recursive copying, using the '-r' option, means that every item at any level inside the directory is copied individually.

## Notes from the 'Search in files' part
* grep command
    * grep [pattern] [file(s)]
        * grep stands for -> (Global search) for a (regular expression) and (print matching lines). Global regular expression print for short.
        * grep by default gives all instances of the matched pattern we're looking for, as whole lines.
        * We can search in one file, in multiple files separated by spaces, or use the wildcard asterisk character.
    * grep [option] [pattern] [file(s)]
        * This example will show me the lines where 'name' string is found, with the line numbers: grep -n 'name' notes.md
    * Useful options:
        * Show line numbers: -n
        * Case insensitive: -i
        * Search recursively: -r
            * When we search recursively, we give a directory instead file(s) as the location(instead of [file(s)], [directory] comes). This cause grep to recursively look for the pattern in every file at any level in the directory we specified, including files that are in the sub directories.
            * example: grep -r ',' .
                * Output: Every line containing a comma from every file from either the current directory we specified or the subdirectories of it.

## Notes from the 'Replace content in files' part
* In the previous part, we learned how to find patterns in files, for instance how to find a specific text inside a specific file. I will now learn how to replace a pattern with another. Pattern terminology for us means a piece from a file that match in our search criteria.
* It can be quite a good strategy to first search for a pattern to if it even exist in your files. And then replace it with something else if you're not happy with it.
* Replacement basics
    * sed 's/pattern/replacement/' [filename]
        * sed command stands for 'stream editor'. Focus on how to use it and to understand, do not memorize the what they are stand for.
        * example: sed 's/,/:/' team*
            * This command finds all the files that starts with team. Then search for the comma character in it, this is our pattern. Then if finds any, it will replace with the colon character(but this will only reflect to the output, **file itself won't change, for the default behaviour**).
        * **Default behaviour**: 
            * Only the *first instance* of the search pattern in each line is replaced.
            * The file itself is *not modified*. Only the printed output contains the replacement
* Replacement options
    * sed 's/pattern/replacement/[option(s)]' [file]
    * example: sed 's/a/z/gI' team*
        * It looks at the current and subdirectories for the files start with team. If find any, it will look for the a character for every line that file has. Because of 'g' option, it will search for all instances but not the just first one on every line. And because of 'I' option, while searching, it will search case insensitive, that means it will search both 'a' and 'A'. After finding the instances, patterns, it will change them with 'z' character. And then it will show us the result as output and won't change the file itself.
        * Options used:
            * Case insensitive: -I
            * Global (i.e. all instances): -g
            * Note: The order doesn't matter: example -> -gI / -Ig
* About replacement output
    * Redirect output with redirection operator '>':
        * sed 's/,/:/' team* > colon_team.txt
            * We are not seeing any output because we redirected it to a file.
        * This is a more safer option than just go and modify the file itself. You have a second chance to look at your file with cat command for example and then examine and if everything is all right then go and delete the backup. This can prevent mistakes.
    * Modify file with an option of sed command:
        * sed -i 's/pattern/replacement/[option(s)]' [file]
            * this is for bash
        * sed -i '' 's/pattern/replacement/[option(s)]' [file]
            * this is for zsh

## Notes from the 'Count values in files' part
* Count basics
    * wc [filename]
        * wc is stand for 'word count'
        * As output, it will give us the how many line we have, how many words we have and how much byte that file has, it will also give the file name to us again.
* Count options
    * Lines: wc -l
    * Words: wc -w
    * Bytes: wc -c
    * Characters: wc -m
    * Note: Bytes and characters often have the same value in plain English text because 1 UTF-8 character = 1 byte.
    * Note: We can use the options together, order is not important. Output has it's own order of importance among the information it gives.

## Notes from the 'Sort file contents pt. 1'
* Sort file contents
    * sort [filename]
    * example: sort team_members.txt
        * The team_members.txt file is sorted alphabeticaly (A-Z) line by line.
* Sort options
    * sort [option] [filename]
    * Useful options:
        * Reverse(Z-A): -r
        * Numeric: -n
        * Note: By default, 'sort' treats everything as strings. Without the '-n' option, "11" comes before "2" because "11" string is at the beginning compare to "2" string.
* Remove duplicate lines
    * uniq [filename]
    * example: uniq team_members.txt
        * Any adjacent duplicates are removed
    * Note: To remove all duplicates, not just the adjacent ones, you have to first sort the file contents alphabetically.

## Notes from the 'Sort file contents pt. 2'
* We said that if we want to remove all the duplicates, we should sort and then remove, so, can we do both? Yes. Here it comes below.
* The pipe character: |
    * [cmd 1] | [cmd 2]
    * The pipe character takes the output of command one and turns that into an input for command 2.
    * example: sort team_members.txt | uniq
        * team_members.txt is sorted alphabetically, i.e. all duplicates are now adjacent.
        * The output of sort team_members.txt is passed as the input to uniq command with the help of pipe character
        * uniq removes duplicates from the sorted file, because we sorted, it removes all duplicates.
        * Note: Because of we passed an input to uniq command with pipe character, we are no longer specifying a file for the uniq command. What was the purpose of specifying a file for uniq command? We were actually giving an input by doing that, yeah! But now we already have our input. Therefore we are not specifying, and we didn't in our example so.
* Store output of sort and uniq
    * Default: Only the printed output is modified. The file itself stays unchanged.
    * Workaround: Redirect the output to a new file.
        * sort team_members.txt | uniq > sorted_team.txt
            * This stores the sorted team members in a new file called sorted_team.txt

## Additional Notes
* With cat command, I can see the contents of a file via the command line interface.
* With nano command, I can edit a file via cli. If a file I tried to edit is not created before, nano creates for me and then give me the edit interface.
* With touch command, I can create files from the command line. If I want to create a file and directly edit it, it would be faster to do that with nano than touch command.

### A Little Note
The notes above are from the scrimba course journey. But the code below is from a research and deep dive to the topics I wanted to learn more. I created the notes above in a process of active learning with course but below is came with research. Therefore I couldn't play with the text and create my own sentences as much. I could do that with focusing and giving my time more but it was easy to read and also write some text as note along the way. I did learn many things, picked informations and write them down there while reading. So it is right to say they are mostly comes from the resources below in a hand picked way, especially the POSIX part. I give my thanks to everyone helped to create that resources.

### What is a Linux Shell
* When a user logs in to the system or opens a console window, the kernel runs a new shell instance. The kernel is the heart of any operating system.
* It is responsible for the control management, and execution of processes, and to ensure proper utilization of system resources.
* A shell is a program that acts as an interface between a user and the kernel. It allows a user to give commands to the kernel and receive responses from it. Through a shell, we can execute programs and utilities on the kernel. Hence, at its core, a shell is a program used to execute other programs on our system.
#### Why do we need a Shell?
* Being able to interact with the kernel makes shells a powerful tool. Without the ability to interact with the kernel, a user cannot access the utilities offered by their machine's operating system.
### Different Types of Shells in Linux
* The Bourne Shell (denoted as **sh**)
    * Developed at AT&T Bell Labs by Steve Bourne
    * Regarded as the first UNIX shell ever.
    * It gained popularity because of its compact nature and high speeds of operation.
    * By default, it uses the prompt # for the root user and $ for the non-root users.
    * Complete path-name is /bin/sh and /sbin/sh.
    * It has some major drawbacks
        * Doesn't have in-built functionality to handle logical and arithmetic operations.
        * Cannot recall previously used commands.
        * Lacks comprehensive features to offer a proper interactive use.
* The GNU Bourne-Again Shell (denoted as **bash**)
    * Designed to be compatible with the Bourne shell(sh).
    * Incorporates useful features from different types of shells in Linux such as Korn shell and C shell.
    * Alow us to automatically recal previously used commands and edit them with help of arrow keys unlike the Bourne shell
    * Complete path-name is /bin/bash.
    * By default, it uses the prompt bash-VersionNumber# for the root user and bash-VersionNumber$ for the non-root users.
    * About portability:
        * Because Bash is the default shell on many Linux systems including multiple versions of Linux and the Mac operating system, Bash scripts are very portable. Bash scripts have also grown to be widely used, so they're more likely to function correctly without changes across multiple platforms. Overall, **this is one of the biggest advantages of Bash**.
* The C Shell (denoted as **csh**)
    * Created at the Universtiy of California by Bill Joy.
    * It was developed to include useful programming features like in-built support for arithmetic ops and a syntax similar to the C programming language.
    * After a while, they incorporated command history feature.
    * Another prominent feature of a C shell is "aliases".
    * Complete path-name for the C shell is /bin/csh. By default, it uses the prompt hostname# for the root user and hostname% for the non-root users.
* The Korn Shell (denoted as **ksh**)
    * Developed at AT&T Bell Labs by David Korn, to improve the Bourne Shell. Therefore The Korn shell is essentially a superset of the Bourne shell.
    * Allows in-built suppport for arithmetic operations while offering interactive features which are similar to the C shell.
    * Runs scripts made for the Bourne shell, while offering string, array and function manipulation similar to the C.
    * Supports scripts which were written for the C shell. Further, it is faster than most different types of shells in Linux, including the C shell. But every deep advantage has a downside with it. Read below to learn some of he disadvantages of Korn Shell. 
    * When it comes to complex scripting requirements, the Korn shell performs brilliantly unlike the Bash shell. It's also great in situations that require efficient power: data manipulation, advanced mathematics, process replacement. Like said before, Korn shell has an ability tto execute script tasks significantly faster(i.e. than the Bash shell), so it's useful for power users and users who require outstanding system performance.
    * About portability
        * Korn shell scripts often need to be modified when moved between systems for several reasons:
            * might not be accessible out of the box on various Linux platforms
            * non-portable high-level features
            * variety of versions, each with its own licensing rules
            * complicated to maintain consistent behavior across different systems
        * Thus, when using Korn shell scripts on multiple platforms, we should be aware of potential compatibility difficulties. Further, Korn documentation is scarce, so porting(making it portable) is made even more difficult.
    * Complete path-name for the Korn shell is /bin/ksh. By default, it uses the prompt # for the root user and $ for the non-root users.
* The Z Shell (denoted as **zsh**)
    * It is a sh shell extension with tons of improvements for customization. If you want a modern shell that has all the features a much more, the zsh shell might be what you're looking for.
    * Some noteworthy features of the z shell include:
        * Generate filenames based on given conditions
        * Plugins and theming support
        * Index of built-in functions
        * Command completion
* Wrapping Up:
    * Shells are one of, if not the most powerful tools available to a Linux user. Without shells, it is practically impossible for a person to utilise the features and functionality offered by the kernel installed on their system.
    * While we covered only the most commonly used types of shells in Linux, there are many other shell types worth exploring.


### What is POSIX? (shorthand for Portable Operating System Interface)
* It is an IEEE 1003.1 standard that defines the language interface between application programs (along with command line shells and utility interfaces) and the UNIX operating system.
* Compliance to the standard ensures when UNIX programs are moved from one UNIX platform to another. POSIX's focus is primarily on features from AT&T's System V UNIX (often referred to as SysV) and BSD UNIX.
    * SysV, is one of the earliest commercial versions of the Unix operating system, developed by AT&T and first released in 1983. It served a foundation for many Unix variants and introduced several key features that influenced later operating systems.
    * BSD, or Berkeley Software Distribution, is a Unix-like operating system that originated from the University of California, Berkeley, in the late 1970s. It has influenced many other operating systems, including FreeBSD, OpenBSD, and macOS, and is known for its permissive licensing and strong networking capabilities.
* A standard must be spelled out and followed by rules on how to achieve the goal of interoperability between operating systems. POSIX covers such things as: System Interfaces, and Commands and Utilities, Networking File Accesss, just to name a few, there is much more to POSIX than this.
* Why POSIX? 
    * In a word: **portability**
    * Over 60 years ago, programmers had to rewrite code completely if they wanted their software to run on more than one system. Portability became a feature in the mid-1960s, not through POSIX but in the mainframe arena, with the IBM's System/360 family of mainframe computers. Different models had their unique specializations, but the hardware was such that they could use the same operating system: OS/360.
    * Not only could the operating system run on different models, applications could run on them as well. Not only did this keep costs low, but it created computer systems, systems across a product line that could work together. It's all common today, networks and systems, but back then, this was a huge deal!
    * When UNIX came about, around the same timeü, it also showed promise in that it could operate on machines from different manufacturers. However, when UNIX started to fork into different flavors, porting(making it portable) code across these UNIX variants became difficult. The promise of UNIX portability was losing ground.
    * **To solve this portability issue, POSIX was formed in the 1980s**. The standard was defined based on AT&T's System V UNIX and BSD UNIX, the two biggest variants at the time. It's important to note that POSIX wasn't formed to control how the operating systems were built, any company was free to design their UNIX variant any way they pleased. POSIX was only concerned with how an application interfaces with the operating system. In programmer-speak, an interface is the method one program's code can communicate with another program. The interface expects Program A to provide a specific type of information to Program B. Likewise, Program A expects Program B to answer back with a specific type of data.
    * Without going into a lot of programmer-speak, for example I'll just say that the cat command makes a call to the operating system to fetch the file so cat can read it. cat reads it and then displays the file's contents on the screen. There is a lot of interplay between the application(cat) and the operating system. **How this interplay works is what POSIX was interested in**. If the interplay could be the same across the different UNIX variants, portability - regardless of operating system, manufacturer, and hardware - is regained. The specifics as to how all of this is accomplished is defined in the standard.
    * When code is compliant, it's easier to move to another system; very little code rewrite, if any, would be necessary. When code can work on different systems, the use of it expands. People using other systems can benefit from the use of the program. For those who are interested in the Linux sphere of compliance, much good information can be found at: [Linux Standard Base](https://refspecs.linuxfoundation.org/lsb.shtml).
    * Conclusion: The POSIX standard allows developers to create applications, tools, and platforms on many operating systems using much of the same code. It isn't a requirement, by any means, to write code according to the standard, but it does help, in a big way, when you want to port your code to other systems. Basically, POSIX is geared toward operating system designers and software developers, but as users of a system, we are affected by POSIX whether we may realize it or not. It is because of the standard that we are able to work on one UNIX or Linux system and bring that work over to another system and work on it with no hiccups. As users, we gain numerous benefits in usability and data re-use across systems.

## The Resources I used while learning and taking notes
* Scrimba fullstack path -> command line tools lessons
* Places that I researched from and learned somethings:
    * https://itsfoss.com/posix/
    * https://www.digitalocean.com/community/tutorials/what-is-bash
    * https://www.digitalocean.com/community/tutorials/different-types-of-shells-in-linux 
    * https://www.baeldung.com/linux/korn-vs-bash