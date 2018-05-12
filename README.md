# How to Create an Emergency Administrator Account

So you tried changing your username [or something] and you were the only admin on your account, and now you have no admin access to your own mac [this happened to me].

What do you do?

This is how you create an admin account by using the Setup Assistant, as a last-ditch way of getting access to your computer again.

## Disclaimer

This is just a transcript of an article I used to fix this issue, when I foolishly decided to change my User directory name. Nothing was changed except I lost my admin privileges...

The original article can be found [here].(http://www.theinstructional.com/guides/how-to-re-run-the-os-x-setup-assistant)

## Steps

This is what you'll need to do to remedy this:

- Restart mac into **Single-User Mode**
- Delete `.AppleSetupDone` file
- Reboot
- Create temp admin user
- Give yourself admin privileges
- Delete temp admin user
- Have a cup of tea / coffee

## Why Delete `.AppleSetupDone`

This file is created by the system upon initial setup; this means that when you delete it, on system start when it doesn't find it, the system thinks it's the initial setup and will run the Setup Assistant.

This tool has root access and can create administrator users, without having to reset any old passwords; that is why I tried this instead of booting into safemode or otherways of fixing this issue.

After creating your temp admin, the file will be regenerated and thus there is no harm in deleting the file.

## Single User Mode

Start by restarting your mac while holding <kbd>command</kbd> + <kbd>s</kbd> to boot into **Single User Mode**. You should see a black command line with a bunch of text.

First you want to run a command to ensure there are not problems in the file system. [there should be no issues]

`/sbin/fsck -fy`

Next you want to mount the file system so you can modify things within it.

`/sbin/mount -uw /`

Now we delete the file:

`rm /var/db/.AppleSetupDone`

>_Or if you're scared of messing up like I >was, you can use this command to rename the >file instead:_
>
>`mv /var/db/.AppleSetupDone >/var/db/.AppleSetupDoneOLD`

Type `reboot` to restart the computer. You may see a log in screen [I think if you have your hard drive encrypted]; if you do, type in your password.

After this you should see the Setup Assistant interface; go through it and create a user. Go to **System Preferences** and click the lock icon [bottom left]. Next, select the checkbox to give administrator rights to your user account; you should get a popup saying a restart is required.

Restart.

Now you can delete the admin account you created, or keep it incase you may need it. Go have a cup of tea / coffee and relax. No more need to worry.