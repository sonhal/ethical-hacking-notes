# Software fuzzing

## Types of fuzzing with their characteristics

Fuzzing or fuzz testing is an automated software testing technique
that involves providing invalid, unexpected, or random data as inputs to a computer program.

#### How the program accepts the input?
- File format fuzzing: invalid files are created and opened by the
application (e.g. invalid pdf file is opened by a pdf reader)

- Protocol fuzzing or network based fuzzing: the input is provided
through network protocols (e.g. http request is sent with a wrong
format)

####  How the input is created

- Mutation based input generation
    Using existing input to create slightly different versions
- Format description based input generation
    The format is described, the input is created using the format
- Response based input generation
    The input is based on the received response (interactive generation)

## The steps of exploit writing

- Finding the vulnerability (e.g with fuzzing)
 the application crashes
- Find the reason of the crash (reverse engineer the code)
- Decide whether the control flow can be redirect or not
- Decide how and where to place the payload (on the stack, in the heap with spraying)
- Bypass all the mitigations (DEP, ASLR, sandboxing, etc)
- Create a working version of the exploit (proof of concept)


## Exploit sources

Metasploit framework
Github
Dark web
Exploit databases
Developing your own exploits