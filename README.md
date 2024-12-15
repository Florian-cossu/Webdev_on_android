# Developement on android terminal

## Prerequisites

-   Have an alternative appstore such as F-droid
-   Have [Termux](https://f-droid.org/packages/com.termux/) installed
-   Have a code editor installed. I personally use [Acode](https://github.com/Acode-Foundation/Acode)
-   Have a good keyboard tailored for developement. I personally use [Unexpected Keyboard](https://play.google.com/store/apps/details?id=juloo.keyboard2)

# Simple projects

For simple projects you may just create some local html that you want to try on your local browser.
Doing so is fairly simple:

1. Create the folder that will contain your html code
2. Next open termux
3. Enable storage access `termux-setup-storage`
4. Update termux and then set up apache and php on your device:

    - `pkg update && pkg upgrade`
    - `pkg install apache2 php`
    - `nano /data/data/com.termux/files/usr/etc/apache2/httpd.conf`

5. Find the line starting with DocumentRoot and update it to point to your directory. For example:

    ```DocumentRoot "/storage/emulated/0/your_path_to_folder"
    <Directory "/storage/emulated/0/your_path_to_folder">
        AllowOverride All
        Require all granted
    </Directory>
    ```

6. Start Apache:

-   `apachectl start`

7. Termux local storage:

-   `cd /storage/emulated/0/your_path_to_folder`
-   `php -S localhost:8000`

8. visit: localhost:8000/path/to/file.php

# Node JS

1. Create a folder on your device and create a basic JS script. For example one looking like this:

`console.log("Test node JS successful")`

2. Next install node.js `pkg install nodejs`
3. Next use `cd` to move to your node js project folder (Reminder that if you created it on your internal storage it'll probably be located under `/storage/emulated/0/your_path_to_folder`)
4. Once you navigated to your project folder's root using `cd` you cqn run `npm init`
5. Finally run `node filename.js` and you should be good.