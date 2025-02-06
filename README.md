Here’s the updated README with your author information included:

---

# Website Change Monitor

This Python script monitors a website for changes and plays an alert sound when a change is detected. It is designed to continuously check the website at a specified interval and notify the user when the content changes.

---

## Features

- **Continuous Monitoring**: Checks the website every second (or a custom interval) for changes.
- **Change Detection**: Detects changes in the website's content by comparing SHA-256 hashes.
- **Alert Sound**: Plays an annoying sound when a change is detected.
- **Graceful Exit**: Handles `Ctrl+C` to exit the program cleanly.
- **Error Handling**: Robust error handling for network requests, parsing, and sound playback.
- **Persistent State**: Saves the last detected hash to a file for comparison across runs.

---

## Requirements

- Python 3.6 or higher
- Required Python libraries:
  - `requests`
  - `beautifulsoup4`
  - `pygame`

---

## Installation

1. Clone or download the repository.
2. Install the required Python libraries:

   ```bash
   pip install requests beautifulsoup4 pygame
   ```

3. Place an audio file named `annoying_sound.mp3` in the same directory as the script. This file will be played when a change is detected.

---

## Configuration

Modify the following variables in the script to customize its behavior:

- `url`: The URL of the website to monitor.
- `check_interval`: The time interval (in seconds) between checks. Default is `1` second.
- `sound_file`: The path to the sound file to play when a change is detected. Default is `annoying_sound.mp3`.
- `headers`: HTTP headers to mimic a real browser.

Example:

```python
url = 'https://admission.1337.ma/candidature/check-in'
check_interval = 1  # Check every second
sound_file = 'annoying_sound.mp3'
```

---

## Usage

1. Run the script:

   ```bash
   python monitor.py
   ```

2. The script will start monitoring the website. It will print a dot (`.`) for each check to indicate progress.

3. When a change is detected, the script will print `CHANGE DETECTED! Playing alert sound.` and play the sound file.

4. Press `Ctrl+C` to exit the script gracefully.

---

## How It Works

1. **Fetch Website Content**: The script fetches the HTML content of the specified URL using the `requests` library.
2. **Extract JSON Data**: If the website contains a `<script id="__NEXT_DATA__">` tag, the script extracts and monitors the JSON data inside it. Otherwise, it monitors the entire HTML content.
3. **Generate Hash**: A SHA-256 hash is generated for the extracted content.
4. **Compare Hashes**: The script compares the current hash with the previously saved hash.
5. **Notify on Change**: If the hashes differ, the script plays an alert sound and updates the saved hash.
6. **Repeat**: The script continues monitoring at the specified interval.

---

## Notes

- **Respect Website Policies**: Avoid setting the `check_interval` too low (e.g., less than 5 seconds) to prevent overloading the server or violating the website's terms of service.
- **Error Handling**: The script handles network errors, parsing errors, and sound playback errors gracefully.
- **Persistent State**: The last detected hash is saved in `previous_hash.txt` to ensure changes are detected across script runs.

---

## Example Output

```
Starting website monitor. Press Ctrl+C to exit.
........
CHANGE DETECTED! Playing alert sound.
........
```

---

## License

This project is open-source and available under the [MIT License](LICENSE).

---

## Author

**Boutrig Mouhamed**  
- GitHub: [moboutrig](https://github.com/moboutrig)  
- Email: [eetops207@gmail.com](mailto:eetops207@gmail.com)  

Feel free to contribute or report issues!  

--- 

Let me know if you need further adjustments! 😊
