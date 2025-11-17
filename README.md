# screenbot
ScreenBot 4.0 – The ultimate Windows automation tool with CLI commands, image recognition, OCR, and full system control.

<b>ScreenBot 4.0 - Advanced Windows Automation Framework</b>

Automate with Precision, Power, and Flexibility. ScreenBot 4.0 is a robust command-line interface (CLI) automation tool for Windows, designed to streamline repetitive tasks, enhance productivity, and enable complex automation workflows. Built for developers, IT professionals, gamers, and enterprises, ScreenBot 4.0 offers an intuitive yet powerful framework to automate mouse and keyboard interactions, image and text recognition, file operations, system monitoring, and web-based automation. With its extensive command set, modular scripting, and Professional version’s WebUI, ScreenBot 4.0 is the ultimate solution for Windows automation. Key Features: Versatile Automation: Control mouse, keyboard, windows, files, and system resources with a single tool.
Image & Text Recognition: Leverage computer vision and Tesseract OCR for dynamic GUI interactions.
Conditional Logic & Loops: Build intelligent workflows with if, else, and iterative constructs.
System Integration: Monitor CPU, RAM, disk usage, and manage application windows.
Web Fetching: Extract web content or download files with the fetcher utility, supporting JSON APIs and segmented downloads.
Custom Commands: Register user-defined commands for tailored automation.
Security: Password protection and guest mode for secure script execution.
WebUI (Professional): Remote automation, live desktop streaming, file browsing, and visual script building via a web interface.

 Table of Contents:
Free vs. Professional (#free-vs-professional)
Use Cases (#use-cases)
Installation (#installation)
Getting Started (#getting-started)
Core Features (#core-features)
WebUI (Professional) (#webui-professional)
Example Workflow (#example-workflow)
Documentation (#documentation)
Contributing (#contributing)
License (#license)
Support (#support)

 Why ScreenBot 4.0?
ScreenBot 4.0 combines simplicity with enterprise-grade functionality, making it ideal for both individual and team-based automation projects. Its key strengths include: Cross-Domain Automation: From GUI interactions to system monitoring, ScreenBot handles it all.
Dynamic UI Handling: Image-based targeting and OCR ensure compatibility with variable interfaces.
Extensibility: Register custom commands and integrate with external scripts or APIs.
Robust Error Handling: Configurable error management ensures reliable execution.
Remote Control (Professional): The WebUI enables browser-based automation, monitoring, and script building.
Active Development: Regular updates with new features and performance improvements.

Whether you're automating data entry, managing system resources, creating gaming macros, or orchestrating remote workflows, ScreenBot 4.0 delivers unmatched efficiency and precision. Free vs. Professional Feature
Free Version
Professional Version
Mouse & Keyboard Automation

Image & Text Recognition

Conditional Logic & Loops

File & Window Management

System Monitoring

Web Fetching (fetcher)

Security & Guest Mode

WebUI (Remote Control)

Live Desktop Streaming

File Browser Tab

Terminal & Script Builder

Multi-User Sessions

Advanced WebUI Configuration

Free Version: Perfect for individuals, developers, and hobbyists automating personal or small-scale tasks.
Professional Version: Tailored for enterprises and remote teams, with the WebUI enabling browser-based automation, multi-user support, and visual script building. Use CasesData Entry: Automate form filling or report generation.
GUI Automation: Click buttons, navigate menus, or test software UIs.
System Administration: Monitor resources and automate maintenance tasks.
Gaming Macros: Create scripts for repetitive in-game actions.
File Management: Organize files, automate backups, or batch process data.
Web Automation: Scrape websites or download files with fetcher.
Remote Automation (Professional): Manage tasks remotely with live desktop streaming and visual script building.

 Installation System Requirements OS: Windows 10 or 11 (64-bit)
RAM: 4 GB minimum (8 GB recommended)
Disk Space: 250 MB
Dependencies: .NET Framework 4 or later

Steps Download: 
ScreenBot 4.0  [(#screenbot4download)](https://github.com/Evic7/screenbot/releases/tag/v4.0)
ScreenBot 4.0 pro   [(#screenbotprodownload)](https://evandervictor.gumroad.com/l/screenbot)
Extract: Unzip to a directory and run the installation
Optional: Add the directory to your system’s PATH for CLI access.
Verify: Run screenbot4 --version to confirm installation.
Run Scripts: Create a .as script (e.g., myscript.as) and execute with screenbot4 run myscript.as, or modify default.as for automatic execution.

WebUI Setup (Professional)Check Version: Ensure webui4.exe is in your installation directory.
Launch WebUI: Run webui4.exe or webui4.exe start webui 127.0.0.1 4444.
Access: Open http://127.0.0.1:4444 in your browser (default credentials: admin/admin).
Configure: Use webuiconfig.exe to customize security, streaming, and user settings.

 Getting StartedCreate a Script: Write a .as file with commands (e.g., myscript.as).

! Move to coordinates (100, 200) at speed 5
move 100 200 5
! Type a greeting
keyBoard type 0.3 Hello, {{login}}!

Run the Script: Execute with screenbot4 run myscript.as.
Explore Commands: Use the Command Reference (#documentation) to build complex workflows.
WebUI (Professional): Launch webui4.exe and access the browser interface for remote control and script building.

 Core FeaturesMouse & Keyboard AutomationMouse: Move, click, drag, or scroll with coordinate-based or image-based commands.

move button.png 3
drag start.png end.png 3

Keyboard: Simulate text input, shortcuts, or special keys.

keyBoard type 0.3 {{login}}@example.com
keyBoard hold ctrl
keyBoard press c

Image & Text RecognitionImage Detection: Locate GUI elements with seeImage.

if seeImage login.png ?run click ?else msg Login button not found

OCR: Extract text from images or screens with readImage and readScreen.

readImage receipt.jpg useBlackWhite eng

Conditional Logic & Loops If/Else: Create dynamic workflows with logical operators.

if userInput Enter email ?cntn @gmail.com ?run msg Valid email!

Loops: Iterate over images or repeat commands.

eachOnScreen textfile.png ?run move {{imageX}} {{imageY}} 5

File & System ManagementFile Operations: Manage files with fileExist, readFile, writeFile, etc.

if fileExist data.txt ?run readFile data.txt ?else msg File not found

System Monitoring: Track CPU, RAM, and disk usage.

if getEnv ramFree ?lstn 1000 ?run msg Low memory warning!

Web FetchingFetcher Utility: Extract web content or download files.

fetcher -fetch ["url=https://example.com;parser=bs4;select=h1"]

SecurityPassword Protection: Secure scripts with setSecurityPassword and activateSecurity.
Guest Mode: Allow restricted command execution.

guestUser on

 WebUI (Professional)The Professional version introduces a WebUI, transforming ScreenBot into a remote automation powerhouse: Live Desktop Streaming: View your desktop in real-time via a browser.
File Browser: Browse and download files remotely.
Terminal: Execute ScreenBot commands from the browser.
Script Builder: Build scripts visually with a GUI interface.
Multi-User Support: Isolated sessions for concurrent users.
Configuration: Customize with webuiconfig.exe for security, streaming quality, and more.

Launch Example: 

webui4.exe start webui 192.168.1.10 8080 maxuser:3

Access: http://192.168.1.10:8080 (default credentials: admin/admin). Example Workflow: Web Form Submission 

! Reset environment
resetEnvironment

! Open browser
focusWindow Chrome
keyBoard type 0.2 https://example.com/login
keyBoard press enter
wait 5

! Check for login button
if seeImage login.png ?run click ?else msg Login button not found

! Enter credentials
keyBoard type 0.3 {{login}}
keyBoard press tab
keyBoard type 0.3 mypassword
keyBoard press enter

! Confirm login
if seeImage dashboard.png ?run msg Login successful! ?else msg Login failed

This script automates website login, demonstrating mouse, keyboard, image recognition, and GUI feedback. Key sections include: Command Reference: Detailed syntax for all commands (mouse, keyboard, image, file, etc.).
WebUI Guide: Setup and usage for the Professional WebUI.
Fetcher Utility: Web extraction and download instructions.
Examples: Sample scripts for common use cases.

 <b>Contributing: We welcome contributions to ScreenBot 4.0! </b>

<b>License: </b>ScreenBot 4.0 is licensed under the MIT License (LICENSE). The Free version is open for personal and commercial use, while the Professional version requires a one-time purchase for WebUI access.

Download Now: <br>

Free: [(#freedownload)](https://github.com/Evic7/screenbot/releases/tag/v4.0)  <br>

Pro: [(#prodownload)](https://evandervictor.gumroad.com/l/screenbot) 




