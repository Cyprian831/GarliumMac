## Graciously made by u/moomoohk on reddit

###### Adapted for github by @Cyprian01 

### For those people who had trouble installing Garlium on Mac (despite the simple instructions on https://xske.github.io/garlium/ )

Thought I'd put together a simple troubleshooter to improve your installation experience :)

For each line in the instructions I'll detail issues I came across and their fixes:

### sudo pip install virtualenv

You get:
```
Error: The directory '/Users/<user>/Library/Caches/pip/http' or its parent directory is not owned by the current user Fix: Add -H flag sudo -H pip install virtualenv
```
### virtualenv ./ --python=python3

You get:
`Error: ImportError: No module named virtualenv`

Fix:

Try this: `pip3 install virtualenv`

and then this: `pip3 install virtualenvwrapper`

### python3 setup.py install

You get:
`Error: TEST FAILED: /lib/python3.6/site-packages/ does NOT support .pth files`

Fix: Find your python3 install dir (which python3) and cut the path up to before the bin directory. Put the result into the file setup.cfg

For example, my which python3 for me returns /Library/Frameworks/Python.framework/Versions/3.6/bin/python3, so my setup.cfg contains:

[install]
prefix=/Library/Frameworks/Python.framework/Versions/3.6/

or You get:
`Error: [Errno 13] Permission denied: ...`

Fix: Prefix command with sudo -H (see below)

or You get: `Error: fatal error: 'openssl/aes.h' file not found`

Fix: `brew install pyenv`

Alternative fix: Run this instead `sudo -H env LDFLAGS="-L$(brew --prefix openssl)/lib" CFLAGS="-I$(brew --prefix openssl)/include" python3 setup.py install`

### python3 garlium
You get: `Error: Error: Could not import PyQt5 on Linux systems, you may try 'sudo apt-get install python3-pyqt5'`

Fix: `pip3 install pyqt5`

Hope this helps!

###### [Take me back to the hub!](https://cyprian831.github.io/Garlicoin/)
