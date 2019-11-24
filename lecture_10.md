# Lecture 10: Vulnerability finding with fuzzing, exploits

## Why to find software vulnerabilities?

Some software vulnerabilities can be exploited by the attacker (not all of them, usually only a small amount is exploitable). If a software contains a bu, attackers can carry out

- Denial of Service attacks (DoS)
- Remote code execution

**This is a huge risk!**

## Exploit sources
- Exploit database (https://www.exploit-db.com/)
- Metasploit framework
- Github
- Darkweb

- Developing your own exploits?
    - It is a time consuming task, the success rate can be low,  but effect can be enormous
    - A Proof of Concept should be created and warn the software producer

## Example of a software vulnerability exploitation process
The very fist step of the attack was to exploit the software vulnerability.

- The attacker sends the exploit to the target (dropper)
- The victim service executes the payload the payload / the victim opens the file that contains the exploit with the payload
- The executed payload downloads a Command and Control (C&C) client malware
- The C&C client connects to the C&C server to receive commands how to carry out the malicious activity
- The infected system can send screen captures, local files to the C&C server or simple spread itself

## What are the steps of exploit development

- Finding the vulnerability (e.g with fuzzing), the application crashes
- Find the reason of the crash (reverse engineering the code)
- Decide whether the control flow can be redirected or not
- Decide how and where to place the payload (e.g on the stack, in the heap)
- Bypass the mitigation (DEP, ASLR, sandboxing, etc)
- Create a working version of the exploit (proof of concept)

### Example - Stack overflow

Reason of crash: to long input
Control flow redirection: yes, by overwriting the return address of the stack frame
Payload place: On the stack after the *ret* together with the vulnerability exploitation
DEP bypass: ROP
ASLR bypass: memory leak, non PIE module

## How to find software vulnerabilities

- Accidentally
    E.g my PDF reader keeps crashing for the same input.
- AV tools
    AV tools cane report suspicious activity such as a port is opened, a suspicious registry entry is created.
- Source code analysis
    Looking for patterns that can reflect vulnerabilities
- Binary code static analysis
    Reverse engineering or advanced specific solutions
- Binary coe dynamic analysis
    E.g the angr framework
- Fuzzing


## Fuzzing
Fuzzing or fuzz testing as an qutomated software testing techinque that invloves providing invalid, unexpected or random data as inputs to the computer program. The program is then monitored for any sign of error (exceptions such as crashes, failing built-in code assertions or memory leaks)

How does the program accept input?
- File format fuzzing
    Invalid files are created and opened by the application (e.g a PDF file for a PDF reader)
- Protocol fuzzing or network based fuzzing
    The input is provided through network protocols (e.g HTTP requests are sent with the wrong format)

### How to create invalid input

- Mutation based input generation
    Using existing input to create slightly different versions
- Format description based input generation
    The format is described, the input is created using this format
- Response based input generation
    The input is based on the received response


#### Mutation based fuzzing

- The input is created based on existing valid input
- Mutations of input are made without the knowledge of the structure of the input (e.g random)
- Requires little setup time
- The success is based on the mutation algorithm
- Mutation can mess up the file format and prevent int to be process (e.g file checksums)

#### Format description (generation) based fuzzing

- The file format of the protocol is described
    variables, variable locations and relations
- Very time consuming to describe the input format (e.g the PDF reference is 1310 pages)
- All combinations can be created theoretically

