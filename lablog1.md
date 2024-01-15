# Lab Report 1

## Instructions
>Lab Report 1 - Remote Access and FileSystem (Week 1)
>You’ll submit a lab report by writing a blog post about the basic filesystem commands we learned today. You should create the post, like we just described using Github Pages. The lab report is due Tuesday, January 16 by 10pm. See the FAQ below for common questions, including how to add images and what to submit to Gradescope.
>
>For each of the commands cd, ls, and cat, and using the workspace you created in this lab:
>
>* Share an example of using the command with no arguments.
>* Share an example of using the command with a path to a directory as an argument.
>* Share an example of using the command with a path to a file as an argument.
> So that's 9 total examples (3 for each command). For each, include:
>
>1. A screenshot or Markdown code block showing the command and its output
>2. What the working directory was when the command was run
>3. A sentence or two explaining why you got that output (e.g. what was in the filesystem, what it meant to have no arguments).
>4. Indicate whether the output is an error or not, and if it's an error, explain why it's an error.
>You will upload your submission by publishing the page on Github Pages, then printing the page to PDF and uploading to the Lab Report 1 assignment on Gradescope.
>
>Note: Make sure to use backticks ` around keywords such as commands, file names, paths, etc. to make them show up as code like cd.

**Let's start with working from the ~ directory.**

### Example of command with no arguments:
* `cd` does nothing and outputs nothing as it does not change any directory. This is not an error. (Still in the `~` directory)\
* `ls` prints `lecture1` as it lists the files and folders in the current working directory. Without doing any changes in directory, the commandline stays in the ~ directory, which encompasses `lecture1`. This is not an error. (`~` directory)\
* `cat` by itself opens a line where if you enter anything into the terminal it echoes what is written. For example, after entering `cat` in the terminal, a new line pops up and when if I enter `practice!` into the terminal, it prints out `practice!`. You can use this to create small text files through the terminal, by typing `cat > file.txt` then the text that you would type would be created into that file. This is not an error. (Still in the `~` directory)\

### Example of using the command with a path to a directory as an argument:
* `cd lecture1` changes the terminal directory into the directory `lecture1`. It doesn't output anything, because it's job is to change the directory. Now we are in the `lecture1` directory, this is not an error.
* `ls messages` prints out `en-us.txt  es-mx.txt  ja.txt  zh-cn.txt` which are the files that are in the directory of messages (`ja.txt` is the japanese translation of hello world that I created). Now that we are in the `lecture1` directory, the terminal can access the directory of messages which allows it to list out all those files. This is not an error.
* `cat messages` prints out `cat: messages: Is a directory` because there isn't really anything for the terminal to concatenate. This is not an error, and we are still in the `lecture1` directory.

### Example of using the command with a path to a file as an argument
* `cd Hello.java` prints out an error `bash: cd: Hello.java: Not a directory` because `cd` is only used to change directories, and `Hello.java` is a file. If you try to change directories into a file, it won't work because a file isn't a directory and does not have any contents of other files within it. We are still in the `lecture1` directory, and this is an error because you cannot change directories into a file.
* `ls Hello.class` prints out `Hello.class` and effectively echoes the file name. This is because it lists out files within a directory that you input it to, similar to cat, but without combining the contents of a file. When you input a file as an argument, it lists out that file. So inputting `Hello.class` would simply print out the only file, and that is `Hello.class`. We are in the `lecture1` directory and this is not an error.
* `cat Hello.java README` prints out 
```
import java.io.IOException; // starting from this line, this is the contents of the Hello.java file
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}To use this program: // starting from this line, this is the contents of the README file

javac Hello.java
java Hello messages/en-us.txt`
```
   The command I just entered combines (or concatenates) the `Hello.java` file and the `README` files, then prints it out, which is why it printed out the contents of both of those files. It can print out any amount of files when specified. We are still in the `lecture1` directory, and this is not an error.

