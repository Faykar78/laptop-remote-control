# Laptop Remote Control

A Bluetooth-based remote control system consisting of an Android app and a laptop server application that allows you to control your laptop's volume, brightness, and system functions.

## Components

1. Android App (`android-remote/`)
   - Controls volume and brightness
   - System controls (shutdown, restart, sleep, lock)
   - Bluetooth connection management
   - Modern Material Design UI

2. Laptop Server (`laptop-server/`)
   - Python-based Bluetooth server
   - Cross-platform support (Windows, macOS, Linux)
   - System command execution
   - Volume and brightness control

## Setup Instructions

### Laptop Server Setup

1. Install Python 3.7 or higher
2. Install required packages:
   ```bash
   cd laptop-server
   pip install -r requirements.txt
   ```

3. Additional setup by operating system:

   #### Windows
   - Install Visual C++ build tools
   - Run PowerShell as administrator for system commands

   #### macOS
   ```bash
   brew install brightness
   ```

   #### Linux
   ```bash
   sudo apt-get install python3-bluetooth
   sudo apt-get install libbluetooth-dev
   sudo apt-get install python3-dev
   ```

4. Start the server:
   ```bash
   python laptop_remote_server.py
   ```

### Android App Setup

1. Open the `android-remote` project in Android Studio
2. Enable Bluetooth permissions in your Android device settings
3. Build and install the app:
   ```bash
   ./gradlew assembleDebug
   adb install app/build/outputs/apk/debug/app-debug.apk
   ```

## Usage

1. Start the laptop server
2. Open the Android app
3. Click "Connect to Laptop" to establish Bluetooth connection
4. Use the controls:
   - Slide volume control to adjust system volume
   - Slide brightness control to adjust screen brightness
   - Use system control buttons for shutdown, restart, etc.

## Permissions Required

### Android App
- Bluetooth
- Bluetooth Admin
- Bluetooth Connect

### Laptop Server
- System administration (for brightness and volume control)
- Bluetooth access

## Troubleshooting

1. Bluetooth Connection Issues
   - Ensure Bluetooth is enabled on both devices
   - Check if devices are paired
   - Restart both the server and the app

2. System Control Issues
   - Ensure proper permissions are granted
   - Run laptop server with administrator/sudo privileges

3. Volume/Brightness Control Issues
   - Check system permissions
   - Verify hardware support
   - Check system logs for errors

## Security Considerations

- The application uses a specific UUID for Bluetooth communication
- System commands require proper authentication
- Connection is limited to paired devices
- Commands are validated before execution

## Development

### Android App Structure
```
android-remote/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/laptopremote/
│   │   │   │   └── MainActivity.kt
│   │   │   └── res/layout/
│   │   │       └── activity_main.xml
│   │   └── AndroidManifest.xml
│   └── build.gradle
└── build.gradle
```

### Laptop Server Structure
```
laptop-server/
├── laptop_remote_server.py
└── requirements.txt
```

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License.

## Support

For support, please open an issue in the GitHub repository.
