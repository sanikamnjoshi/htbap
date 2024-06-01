# How to Debug Using a Log
[//]: # (Version:1.0.0)
*Logging* is the practice of writing a system so that it produces a sequence of informative records, called a log. *Printlining* is just producing a simple, usually temporary, log. Absolute beginners must understand and use logs because their knowledge of programming is limited; system architects must understand and use logs because of the complexity of the system. ==The amount of information that is provided by the log should be configurable, ideally while the program is running. 🏃== In general, logs offer three basic advantages:

- Logs can provide useful ==information about bugs that are hard to reproduc==e (such as those that occur in the production environment but that cannot be reproduced in the test environment).
- Logs can provide ==statistics and data relevant to performance, such as the time passing between statements==.
- When configurable, logs allow general information to be captured in order to debug unanticipated specific problems without having to modify and/or redeploy the code just to deal with those specific problems.

> [!question] 🏃 log configuration
> how to make logging configurable-while-running?

==The amount to output into the log is always a compromise between information and brevity.== Too much information makes the log expensive and produces ==*scroll blindness*==, making it hard to find the information you need. ==Too little information and it may not contain what you need.== For this reason, making what is output configurable is very useful. ==Typically, each record in the log will identify its position in the source code, the thread that executed it if applicable, the precise time of execution, and, commonly, an additional useful piece of information, such as the value of some variable, the amount of free memory, the number of data objects, etc.== These log statements are sprinkled throughout the source code, particularly at major functionality points and around risky code. Each statement can be assigned ==a level 🪵== and will only output a record if the system is currently configured to output that level. You should design the log statements to address problems that you anticipate. Anticipate the need to measure performance.

> [!note] 🪵 excursus: logging in python
> in python, log levels are used to indicate the severity or importance of messages logged by an application. the `logging` module in python provides several built-in log levels, each represented by an integer value. these levels help developers categorize log messages and control the verbosity of logging output. the standard log levels are:
> 1. `DEBUG` (10): detailed information, typically of interest only when diagnosing problems. used for lower-level system information.
> 2. `INFO` (20): confirmation that things are working as expected. general information about the application's execution.
> 3. `WARNING` (30): an indication that something unexpected happened, or indicative of some problem in the near future (e.g., ‘disk space low’). the software is still working as expected.
> 4. `ERROR` (40): due to a more serious problem, the software has not been able to perform some function.
> 5. `CRITICAL` (50): a very serious error, indicating that the program itself may be unable to continue running.
> 
> here's a quick example of how to use these log levels in python:
> 
> ```python
> import logging
> 
> # configure logging
> logging.basicConfig(level=logging.DEBUG)
> 
> # log messages with different severity levels
> logging.debug("This is a debug message")
> logging.info("This is an info message")
> logging.warning("This is a warning message")
> logging.error("This is an error message")
> logging.critical("This is a critical message")
> ```
> 
> in this example, `logging.basicConfig(level=logging.DEBUG)` sets the logging threshold to `debug`, meaning all messages with a severity level of `debug` and above will be output. adjusting the log level can help filter out less severe messages as needed.
> 
> some languages may additionally include a `trace` level, which `logging` in python does not include. it is typically used for very detailed debugging information, often more fine-grained than `debug`.

If you have a permanent log, printlining can now be done in terms of the log records, and some of the debugging statements will probably be permanently added to the logging system.

Next [How to Understand Performance Problems](05-How-to-Understand-Performance-Problems.md)
