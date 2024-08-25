---
share: true
created: 2023-10-24T18:26
updated: 2024-08-18T15:05
---
I want to call a another script from a Python script, and the shell running it is either PowerShell on Windows, or Bash on Ubuntu. How should I construct such a code?

# Attempt 1: Using a simple `ls` command

The code running for Bash is:
```python
command = 'ls'
subprocess.Popen(command).wait() 
```
And the code running for PowerShell is:
```python 
command = 'pwsh -c ls'
subprocess.Popen(command).wait() 
```

Therefore I come up with this script that runs successfully in both shells:
```python
pproc_name = psutil.Process(os.getppid()).name()
is_power_shell = bool(re.fullmatch('pwsh|pwsh.exe|powershell.exe', pproc_name))

if is_power_shell:
    env = 'pwsh -c '
else:
    env = ''

command = env + 'ls'
subprocess.Popen(command).wait() 
```
<sub>Code from https://stackoverflow.com/a/55598796/3416774</sub>

# Attempt 2: Using my real case command
This works on PowerShell:
```python
import os, psutil, subprocess, re

pproc_name = psutil.Process(os.getppid()).name()
is_power_shell = bool(re.fullmatch('pwsh|pwsh.exe|powershell.exe', pproc_name))

if is_power_shell:
    env = 'pwsh -c '
else:
    env = ''

command = env + 'deno run --allow-all main.ts'
subprocess.Popen(command).wait()
```

However it gives this error on Bash:
```python
Traceback (most recent call last):
  File "/home/test.py", line 12, in <module>
    subprocess.Popen(command).wait() 
  File "/usr/lib/python3.10/subprocess.py", line 969, in __init__
    self._execute_child(args, executable, preexec_fn, close_fds,
  File "/usr/lib/python3.10/subprocess.py", line 1845, in _execute_child
    raise child_exception_type(errno_num, err_msg, err_filename)
FileNotFoundError: [Errno 2] No such file or directory: 'deno run --allow-all main.ts'
```

To fix this I have to add `shell=True` to the subprocess function.
