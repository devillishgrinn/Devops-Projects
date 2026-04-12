Project: https://roadmap.sh/projects/dummy-systemd-service

Step-1: Create a script that acts as the core of the service and defines it's functionality using command: **sudo nano ~/dummy.sh(your service-name.sh)** and enter the following: 
    #!/bin/bash
    while true; do
      echo "Dummy service is running..." >> /var/log/dummy-service.log
      sleep 10
    done

Step-2: Give it execution permission using command: **chmod +x ~/dummy.sh**

Step-3: Create a Service in folder /etc/systemd/system/ using command: **sudo nano /etc/systemd/system/dummy.service** and enter the following details in it: 

**[Unit]**
    Description=Dummy App Service  //label
    After=network.target	 //start after network is up

**[Service]**
    ExecStart=/home/ubuntu/dummy.sh //app path
    Restart=always  //restart no matter what
    RestartSec=3   // wait 3 seconds before restarting
    User=root      //run as root
    StandardOutput=journal  //logs output to journal
    StandardError=journal   //logs Errors to journal 

**[Install]**
    WantedBy=multi-user.target  //start as boot

Step-4: Reload the systemd using command: **sudo systemctl daemon-reexec**

Step-5: Reload the daemon using command: **sudo systemctl daemon-reload**

Step-6: Start the dummy-service using command: **sudo systemctl start dummy**

Step-7: Check status of dummy-service using command: sudo systemctl status dummy
