# Android-LogMailer
This is a bash script that grabs the system log from an android device connected to the machine, checks for errors in the last hour then sends an automated mail with the error(s) to a specified mailing list on finding them.
It is designed to be executed as a cron job every hour.

Note: This script is a base which you can build upon. For example, you can make some changes to make it capture the logs related to the app you are testing by modifying the logcat command on line 4 or a specific error you are tracking by modifying the regex variable on line 9.



#### Prerequisites:
1. Android SDK is installed with platform-tools directory added to the path
2. Debugging is enabled on your android device from the developer options.
3. The connected device trusts the machine.
4. Email is configured in the environment (https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/)
5. Change example@mail.com in the script to the email list you want to send the automated mail to


#### Steps:
1. Download the script
2. Execute the following from the same path of the script(you can copy it to any path that is added to the path environment variable)
  
  ```
  chmod +x logmail
  sudo cp logmail /usr/local/bin
  ```
3. Use gnome-schedule and configure the script to run every hour or execute crontab -e and add the following line to the file and save
  
  ```
  0 * * * * logmail
  ```
