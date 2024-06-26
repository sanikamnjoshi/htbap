# How to Remove an Error
[//]: # (Version:1.0.0)
I've intentionally separated the act of examining a program's execution from the act of fixing an error. But of course, debugging does also mean removing the bug. Ideally you will have perfect understanding of the code and will reach an ‘A-Ha!’ moment where you perfectly see the error and how to fix it. ==But since your program will often use insufficiently documented systems into which you have no visibility, this is not always possible. In other cases the code is so complicated that your understanding cannot be perfect.==

==In fixing a bug, you want to make the smallest change that fixes the bug. 🐞== You may see other things that need improvement; but don't fix those at the same time. Attempt to employ the scientific method of changing one thing and only one thing at a time. The best process for this is to be able to easily reproduce the bug, then put your fix in place, and then rerun the program and observe that the bug no longer exists. Of course, sometimes more than one line must be changed, but you should still conceptually apply a single atomic change to fix the bug.

> [!note] 🐞 aside
> the smallest, least hacky change, ideally

> [!quote] fixing a single bug with a single atomic change
> "*Attempt to employ the scientific method of changing one thing and only one thing at a time. \[...\] Of course, sometimes more than one line must be changed, but you should still conceptually apply a single atomic change to fix the bug.*"
> 
> think of this as the rule for commits in git. one commit should contain one logical change.

Sometimes, there are really several bugs that look like one. It is up to you to define the bugs and fix them one at a time. ==Sometimes it is unclear what the program should do or what the original author intended. In this case, you must exercise your experience and judgment and assign your own meaning to the code. Decide what it should do, and comment it or clarify it in some way and then make the code conform to your meaning.== This is an intermediate or advanced skill that is sometimes harder than writing the original function in the first place, but the real world is often messy. You may have to fix a system you cannot rewrite.

Next [How to Debug Using a Log](04-How-to-Debug-Using-a-Log.md)