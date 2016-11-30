# DevOps-SpecialMilestone

Team Members:

1. Ayush Gupta - agupta25@ncsu.edu
2. Nishtha Garg - ngarg@ncsu.edu
3. Shivam Gulati - sgulati2@ncsu.edu

The project used for the milestone is the same as Milestone 3 at

```
https://github.com/shivamgulati1991/m3base
```

### Diet Monkey

Shrink resources available on server.

1. We run the script shrink.js which shrinks the allocated memory of the server if the utilization is less.
2. It connects to the digital ocean droplets and reduced the memory.
3. The scipt can be run as
```
node shrink.js
```

![Screencast](https://github.com/shivamgulati1991/DevOps-SpecialMilestone/blob/master/Screens/1.gif)

### Restart Monkey

Restart server. Check if services properly restarted.

1. We run the shell script restart.sh which initiates the server restart.
  ```
  sh restart.sh
  ```
2. It first calls the file reboot.js which reboots the server.
  ```
  echo "Preparing to reboot server"
  #call reboot script to reboot
  node reboot.js
  ```
3. Next, we induce a 30 second delay in the script so the server is back up fully.
  ```
  echo "Getting services back up"
  #30 seconds delay to allow for server to back up
  sleep 30
  ```
4. Further, it runs the restartplaybook.yml file using ansible to get the application back up.
  ```
  #playbook to run the application back
  ansible-playbook -i inventory restartplaybook.yml
  ```
5. Since our application runs on port 3000, to check if our service is back up, we use the netstat command as below.
  ```
  netstat -anp 2> /dev/null | grep :3000
  ```
6. We can see that the node application is running on the same.

![Screencast](https://github.com/shivamgulati1991/DevOps-SpecialMilestone/blob/master/Screens/2.gif)
