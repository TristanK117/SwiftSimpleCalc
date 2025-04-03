# SimpleCalc

## Greetings!
This homework is designed to force you to exercise your knowledge of the Swift programming language. This homework does not involve iOS in any way. It uses the Playground feature of XCode to allow you to interactively write Swift code--the compiler will constantly check your code in the background.

In this exercise, you will implement a pair of functions that do some simple mathematical calculations.

## To get started...
... you must first obtain a copy of the source. You do that by cloning this repository. Two options are available to you:

1. **Fork this repository.** From the GitHub repository web page, click "Fork" in the upper-right. This will create a copy of this repository in your own GitHub account. From there do a `git clone` from your own copy of the GitHub repository. (If you are unsure of the clone syntax, open the new repository in your account from the web, and click the green "Code" button--it will offer the correct syntax to use.)

2. **Clone and re-home this repository.** Open a "Command Prompt" or "Terminal" instance and use:

        git clone https://github.com/tedneward/INFO449-SwiftSimpleCalc

    ... to do the deed. This will also create a local copy of the project on your machine in a directory called `INFO449-SwiftSimpleCalc`. You will also need to "re-home" your local copy so it points to your own GitHub account; you can do this by creating a repository of this same name (`INFO449-SwiftSimpleCalc`) in your GitHub account and then executing `git remote set-url origin https://github.com/[your-ID]/INFO449-SwiftSimpleCalc.git`. (Needless to say, it's a lot easier to fork the repo.)

    In order to store your changes to your own GitHub account, you need to create a new repository on GitHub (call it `INFO449-SwiftSimpleCalc`), and then change the project's settings to point to that new repository as the remote origin.

        git remote set-url origin https://github.com/[your-ID]/INFO449-SwiftSimpleCalc.git

    Note, this will appear to succeed whether you got the syntax of the URL correct or not, so do a quick push to make sure it all worked correctly:

        git push

    Git will ask you for your username and password, then (if everything was done correctly), it will upload the code to the new repository, and this is your new "home" for this project going forward. Verify the files are there by viewing your GitHub project through the browser.


## To work on the code...
To open this project in XCode, fire up XCode itself, then File|Open the `SimpleSwift.playground` file.

> Interesting side note: In truth the Playground is not a file, but a directory that pretends to be a file. This is a common trick in the macOS/iOS world. If you look at it Finder, it will appear to be a single file; if you look at it from Terminal, however, you can navigate "into" the file and view its contents. In the case of Playgrounds, the actual code is stored in `Contents.swift`. As it turns out, this is also how executables ("bundles") work in both iOS and macOS.

When you make changes to the playground, be sure to commit the entire directory contents (`git add SimpleSwift.playground; git commit -m "Change message"`) and push the contents up to the GitHub server (`git push`). We will never see your changes if you do not push to the server!

**NOTE:** Your grade for this assignment (and all future assignments) will be based on what we see in the GitHub repository, and nothing else. A basic rule of this course: **If it isn't in GitHub, it doesn't exist.**

## Your tasks
You are to implement two `calculate` functions, each of which take `Strings` are expected to perform the calculations intended. This is designed to make you comfortable with converting Strings to other values--a common task in mobile applications, when obtaining input from the user--for further processing. One of the functions takes an array of Strings, expecting each "part" of the calculation expression to be each be in its own String (such as "2" "+" "2"), and the second expects a single String containing the entire expression ("2 + 2").

You should make sure your calculate method can handle the following kinds of input:

* `calculate(["2", "+", "2"])`: This should return 4
* `calculate(["2", "-", "2"])`: This should return 0
* `calculate(["2", "/", "2"])`: This should return 1
* `calculate(["2", "%", "2"])`: This should return 0
* `calculate(["2", "*", "2"])`: This should return 4

For those who aren't aware of it, the "%" operator is called the "modulo" operator, and it is the "remainder" result in an integer division that does not divide equally. Thus, `5 % 2` is 1 (5 divided by 2 is 2 remainder 1), `10 % 3` is 1 (10 divided by 3 is 3 remainder 1) and `4 % 2` is 0 (4 divided by 2 is 2 remainder 0).

The `calculate` method also needs to support a few other less-traditional expressions as well:

* `calculate(["1", "2", "3", "4", "5", "count"])`: This should return a count of all the number arguments, which in this case will be 5.
* `calculate(["1", "3", "2", "avg"])`: This should return the average of the numbers, which is all of the values added up (1 + 3 + 2) and divided by the number of arguments (3).
* `calculate(["5", "fact"])`: This should calculate the factorial of the single number passed in, which is that number multiplied by each number below it. 5-factorial is 5 * 4 * 3 * 2 * 1, or 120.

For this latter set of operations, it is safe to assume that `["count"]` (no additional arguments) is 0, `["avg"]` is also 0, and `["fact"]` is 0. `["1", "fact"]` should return 1, and `["0", "fact"]` should also return 1. (Yes, 0-factorial is 1. True story.)

## Running the Playground
The Playground should be configured to compile automatically; if it is not, look at the icon in the lower-left corner. If you do a long-click (click-and-hold) on that button, it will pop up a menu asking whether you want the Playground to compile automatically or manually.

> (Sometimes XCode can get confused about your code while you are writing it, and earlier versions of XCode always compiled in the background, leading to XCode to be constantly in a state of confusion and requiring XCode to be restarted to clear out the confusion. This gives you the choice.)

## Extra credit
You can earn two extra credit points as part of this assignment. These are described here, but will require you to uncomment the blocks of code for each in order to run them.

#### Implement `calculate` to handle negative numbers
What happens when somebody puts a "-" in front of one of those numbers? (This can easily turn into some edge-case nightmares, such as "2 - - 2" trying to figure out where those negative signs go; for our purposes, assume that there will never be a space between a negative sign and the number if it is going to be a negative number.)

#### Implement `calculate` to handle floating-point numbers
What happens when we want to multiply .5 by .5? In that particular case, we need two new flavors of `calculate` that return Double values, instead of Int; implement a version of `caculate` for each form (one taking a String array, the other taking a String, just as we did above) that deal with floating-point values.

