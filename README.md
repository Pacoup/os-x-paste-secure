# OS X Paste Secure

Past Secure is a small script for OS X shamelessly ~~stolen~~ borrowed from this [StackExchange thread](http://apple.stackexchange.com/questions/79986/why-cant-i-paste-into-the-password-dialog-when-mounting-an-encrypted-disk-image) which allows you to paste in OS X's annoying “secure” dialog boxes (e.g. for that one long ssh key passphrase you want to setup for the first time).

1. Open **Script Editor** and save the following script somewhere on your computer:

    ```AppleScript
    tell application "System Events" to tell process "SecurityAgent"
        set value of text field 1 of window 1 to (the clipboard)
        click button 1 of group 1 of window 1
    end tell
    ```
2. Run the application which generates the secure dialog you cannot paste into

3. Copy the password you want to paste in (e.g. from LastPass)

4. Open the **Terminal** and run the following command:

    ```Bash
    $ osascript <~/path/to/your/script>
    ```
    
    The first time you run this script, the system may ask you to enable access to assistive devices for Terminal. Do this by open **Security & Privacy** from **Preferences**, and in the **Privacy** tab, under **Accessibility**, activate the checkbox next to **Terminal.app**.

5. The password should be pasted in the dialog box
