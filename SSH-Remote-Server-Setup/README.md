**Project: https://roadmap.sh/projects/ssh-remote-server-setup**
# SSH-Remote-Server-Setup: 
Steps to setup SSH to the remote server:

Step-1: Create a AWS Instance and start Instance

Step-2: Open CLI and enter commmand which Generates a new ssh keys using "ed25519" alogrithm with label "test-ssh-key" in folder $HOME/.ssh/: 
                                _**ssh-keygen -t ed25519 -C "test-ssh-key" -f ~/.ssh/test-ssh-key **_ 

Step-3: Go to the server/AWS Instance and run command: **_nano ~/.ssh/authorized-keys_** and paste the pubblic key here

Step-4: Give /.ssh folder 700 permission and .ssh/authorized-keys 600 permission using: _**chmod 700 /.ssh **_ and _**chmod 600 /.ssh/authorized-keys**_

Step-5: Use commmand to connect to server: _**ssh ~/.ssh/test-ssh-key <username>@<ip-address>**_

**Configure ssh to an alias(say my-server):**

Step-6: Create a new file "config" in /.ssh folder and write/define the following fields in it:

    Host my-server #your alias
        HostName xxx.xx.xx.xx #Your Public IPv4 address #<Note: Create a Elastic Ip in AWS as Public Ip changes after every Instance's Start & Stop>
        User ubuntu #Username
        IdentityFile ~/.ssh/test-ssh-key #path to the public-key

Step:7: Connect to server using command: _**ssh my-server**_


                                            
