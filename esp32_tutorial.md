---
layout: page
title: ESP32C5 Start-up Tutorial
permalink: /project/esp32tutorial
---
## Recommended Resources

For more details on ESP32-C5 and related tools, check out the following resources:

|      Content      |                                                      Source                                                       | Recommendation |
| :---------------: | :---------------------------------------------------------------------------------------------------------------: | :------------: |
|   ESP-IDF Tool    |                                  [GitHub](https://github.com/espressif/esp-idf)                                   |      ***       |
| ESP-NOW Protocol  | [Documentation](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c5/api-reference/network/esp_now.html) |      ***       |
|  ESP32-C5 Guide   |        [Get Started](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c5/get-started/index.html)        |      ***       |
|      ESP-DSP      |                                  [GitHub](https://github.com/espressif/esp-dsp)                                   |       **       |
| VSC IDF Extension |                          [GitHub](https://github.com/espressif/vscode-esp-idf-extension)                          |       *        |

> We highly recommend using the ESP-IDF tools rather than Arduino. The lab and project tutorials are based on ESP-IDF tools.

## Getting Started with ESP32-C5

### Step 1: Install ESP-IDF

The **ESP-IDF (IoT Development Framework)** is the official programming guide for **ESPRESSIF ESP32-C5**. Follow the step-by-step installation process tailored to your operating system. It is recommended to install ESP-IDF under the default path (`~` or `/Users/yourusername/`).

**Installation Guide**: [ESP32-C5 Getting Started](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c5/get-started/index.html)

To simplify usage, create an alias for `export.sh` by following these steps:

1. Open your shell profile file (`.profile`, `.bashrc`, `.zshrc`, etc.) and add the following line:

    ```bash
    alias get_idf='. $HOME/esp/esp-idf/export.sh'
    ```

2. Apply the changes by restarting your terminal or running:

    ```bash
    source ~/.bashrc  # Or replace with your profile file
    ```

3. Now, you can quickly load the ESP-IDF toolchain by typing:

    ```bash
    get_idf
    ```

### Step 2: Run the Blinking LED Example

Once ESP-IDF is installed, test it by running the **blinking LED** example.

1. Navigate to the ESP directory and copy the example project:

    ```bash
    cd ~/esp
    cp -r $IDF_PATH/examples/get-started/blink .
    cd blink
    ```

2. Set the target device:

    ```bash
    idf.py --preview set-target esp32c5
    ```

3. Identify the device port:

    - Check the port by running:

      ```bash
      ls /dev/cu*
      ```
    - On macOS, it typically appears as `/dev/cu.usbmodem1101`.

4. Build the firmware:

    ```bash
    idf.py build
    ```

    If there are no errors, the build will generate firmware binary `.bin` files.

5. Flash the firmware to your ESP32-C5:

    ```bash
    idf.py -p /dev/cu.usbmodem1101 flash  # Replace with your actual port
    ```

6. Monitor the output to confirm the LED is blinking:

    ```bash
    idf.py -p /dev/cu.usbmodem1101 monitor  # Replace with your actual port
    ```

Once you see the LED blinking, you have successfully set up your ESP32-C5!