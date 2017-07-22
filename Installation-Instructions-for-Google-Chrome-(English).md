XX-Net is an Open-Source project for securing your internet connection. The tool works well for most browsing activity in China. There are four high-level steps
1. Install XX-Net Proxy source code from Github
1. Setup Chrome Certificates
1. Deploy a new Google API Server
1. (Optional) Install SwitchyOmega to enable 1-click VPN

# Step One: Install XX-Net Proxy
1. Download Source code from https://codeload.github.com/XX-net/XX-Net/zip/3.3.1
1. Unzip contents of folder to any location. Make sure you remember the location, you'll need this later
1. Double-click start.vbs or start.bat to start.
1. A dialog box may appear. If it is in Chinese, the dialog box is asking if you want to put a desktop shortcut to XX-net. A desktop shortcut will make it easy to use in the future, so I recommend adding the desktop shortcut.
1. You will be prompted for administrator privileges (this is required to install the security certificates that are used to access HTTPS websites). Click Agree.
1. Once the installation is complete and the process is started, your default browser will open to the main Proxy Configuration page. Keep this page open, you will need it soon.
1. A tray icon will appear in the lower right on the desktop. You can use this to access the commonly used Functions of XX-Net


At this point, you may begin browsing google and other websites that are usually blocked in Internet Explorer. However, Chrome may have some security settings that mean you cannot browse in Google Chrome just yet. In addition, video streaming is unavailable at this point since you are using the default free proxy server provided by XX-net. Video streaming is blocked to reduce the amount of traffic going through this server. We'll fix this shortly.


# Step Two: Set up browser security certificates
1. In your Chrome Browser, Go to Chrome://settings
1. Scroll to bottom of settings and click "Show Advanced Settings"
1. Click Manage Certificates
1. Go to the "Trusted Root Certificates" tab
1. Click Import
1. Navigate to the folder which you unzipped the XX-net Source Code to
1. Find CA.crt stored in the location \XX-Net-3.2.7\data\age_proxy
1. Complete the wizard, accepting all default options


At this point, Chrome is now fully functional, with the exception of video streaming. The next step is to create our own proxy server(s) provided by Google APIs. Each server provides 1GB of traffic each day, so set up the appropriate amount of servers based on your estimate of usage.

# Step Three: Deploy a new Google API Server
1. Go to https://console.developers.google.com/
1. Sign-in using a gmail account (create a separate one if you prefer)
1. In the top right – click create a project and give project a name "e.g. VPNServer". Take note of the project ID (just below the project name), you'll need this later
1. (Optional) You can choose to specify a location where your Google APIs Server is deployed. It is strongly recommended to choose a location in North Asia, e.g. Hong Kong/Japan/Korea/Singapore so that you can maximize performance.
1. (Optional) Click Show advanced options
1. (Optional) Choose a App Engine region
1. Click Create
1. Wait a few minutes for the deployment to complete (you will receive a notification in the top-right)
1. Each server provides 1GB access per day, if you think you need more than this, deploy multiple servers using steps 3-7 above, taking note of each project ID
1. Open the tab you left open in Step 1.6 or navigate to http://localhost:8085/
1. On the left hand panel Click Deploy server
1. Type in your Project ID from Google (multiple project IDs separated by |)
1. Click Start to deploy
1. You will have to sign in to Google using the user name and password used in step 3.2
1. Once deployment is complete, Click Configuration
1. Type in your Project ID from Google (multiple project IDs separated by |)
1. Click Save

Congratulations! You should now be ready to rock and roll!

# (Optional) Step Four: Install SwitchyOmega for One-click on and off
One tool to make switching between VPN and non-VPN super simple is SwitchyOmega add on for Chrome. To add SwitchyOmega to your Chrome Browser follow these few simple steps:
1. Download SwitchyOmega from here https://github.com/XX-net/XX-Net/tree/master/SwitchyOmega
1. When the download is complete, drag the SwitchyOmega file into a new tab in Google Chrome. This will open the tab to download and install SwitchyOmega.
1. Download and Install Chrome Proxy Add-on
1. On the left hand side panel, open Settings>Import/Export
1. Click restore from file 
1. Find OmegaOptions.bak in XX-Net-3.2.7\SwitchyOmega
1. Click Apply Changes

Now that you are finished installing these useful tools, you now have a free and secure browsing environment that you can use to unlock the entire internet.