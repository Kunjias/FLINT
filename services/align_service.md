# align_service.py

latest commit comment from original repository:

```
Align service initial commit.

#   OBJECTIVE:
#	The purpose of this file is to implement a persistent subprocess that will maintain Bowtie2 running so that
#   it is available for alignment purposes without having to load the reference Index over an over again.
```

-line 46-61 (main function)
- `#   Open a pipe to the subprocess that will launch the Bowtie2 aligner.` \
- ` #   Dispatch the subprocess using STDIN as the input.` \
- `#   The Alignment Rate reported from Bowtie2 comes in through STDERR.`

``` Helper functions ```

- line 68-95 (format Bowtie2 command)
```
def getBowtie2Command():
    """
    Constructs a properly formatted shell Bowtie2 command by performing a simple lexical analysis using 'shlex.split()'.
    Returns:
        An array with the bowtie 2 command call split into an array that can be used by the popen() function.
    """
```

- line 100-118 (check if the 'end' of ouput has been reached)???
```
def validate_output(stringToValidate):
    """
    Function for determining if the 'end' of the output has been reached, for 'some' definition of 'end'. :)
    Args:
        stringToValidate:   The string that we'll be checking for the special flag that tells us 'this is the end'.
    Returns:
        True:   If the output string contains the flag.
        False:  If the output string is empty or if it does not contain the flag.
    """
 ```

-line 131-132 (App Initializer)
