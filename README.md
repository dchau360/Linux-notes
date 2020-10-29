# Linux-notes
To change the password in our example, we just execute this one command:

# echo "linuxpassword" | passwd --stdin linuxuser
on modern Linux. (Thanks to DAVID for this tip)

or

# echo -e "linuxpassword\nlinuxpassword" | passwd linuxuser
This can also be put into one bash script or executed on remote node by the ssh command.

For example, we can change the password of linuxuser on a batch of servers (100 servers: 10.1.0.1 to 10.1.0.100) by:

# for ((i=1;i<=100;i++)); do \
ssh 10.1.0.$i 'echo -e "linuxpassword\nlinuxpassword" | passwd linuxuser'; \
done;
Even further, we can create one user and set its initial password remotely by:

# ssh remoteserver \
'useradd newuser; echo -e "passwdofuser\npasswdofuser" | passwd newuser'
If you want to update your own password as a normal user, you may use

$ echo -e "your_current_pass\nlinuxpassword\nlinuxpassword" | passwd
