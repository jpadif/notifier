# Notifier
A python script that notifies you via Pushbullet when an script has finished or a proccess has ended by monitoring its PID


## Configuration
### Create your own pushbullet Api key!
Go to [My Account](https://www.pushbullet.com/#settings/account). Clic on the button labeled as "Create Access Token" then replace "YourOwnApiKey" on notify file with your api key. 

```python
PUSH_BULLET_API_KEY = "YourOwnApiKey" # Replace this with your own key
PUSH_BULLET_API_URL = "https://api.pushbullet.com/v2/pushes"
NOTIFICATION_HEADER = "Script finished: "
...
```

### (Optional) Set your own default values! 
The variable `NOTIFICATION_HEADER` holds the title that the notification will use when a custom one is not specified using the flag `-t` or `--title`

And `NOTIFICATION_CONTENT` holds the default content that the notification will have. You can specify your own at run time with the flag `-c` or `--content`

```python
NOTIFICATION_HEADER = "Script finished: "
NOTIFICATION_CONTENT = "Has finished!!"
```

### Copy the script to your PATH
``` cp notify /usr/bin/ && chmod 755 /usr/bin/notify ```

## Usage
### Notify after a command finishes
Add `;notify` at the end of your lenghty command before executing it
```bash
$ lenghtyProccess; notify
```
`notify` will be executed after the first command and a notification will be sent.

*And if I forgot to add `; notify` after my command and it is already running? :(*

### Monitor an already running process and notify when it finishes 
Identify the PID of the process to monitor
```python
# You can identify a process using ps
ps aux |grep "lengthyProccess"

user  18873   0.0  0.0  2434840    752 s004  S+   11:46PM   0:00.00 lengthyProcess
```

The second number  (18873) is the PID, this is the number that identifies a currently running proccess. 

Use the flag `-p` to specify a running proccess by its PID
```
$ notify -p 18873
```

When the process ends a notification will be sent! MAGIC!




