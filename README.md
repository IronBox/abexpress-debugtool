# abexpress-debugtool
This is the temporary home for the AB Express configuration checker tool. It looks for common issues with AB Express installations and configurations and provides suggested fixes.

![Tool screenshot](tool-screenshot.png)


## Installation and Usage
This site is packaged with the latest version of the AB Express configuration tool, to get the tool:

1. Click on the green **Clone or download** button on the top-right
2. Select **Download ZIP**
3. Unzip the ZIP archive into a folder on the system that you troubleshooting AB Express on
4. Run **ABExpressConfigCheckerTool.exe**
5. Click the Run button to start configuration checking

Any check that has failed will be shown in red. Click on any failed check to view the suggested fix for the detected issue.

### Requirements
- .NET Framework 4.6.1+ (this should be already installed on almost all Windows machines)




## Automated Checks
The configuration checker tool checks for the following common issues. Please note that the fix for all of the following will require administrative privileges on the system.

### `Product key is valid`
This check analyzes the configured product key from the registry to ensure that is a valid key. If a key has not been entered via the administrator configuration tool or has been tampered with directly in the registry, this check will fail.

#### How to fix
Use the administrator configuration tool to enter a valid product key. You can obtain a key by signing into [www.abproportal.com](https://www.abproportal.com).


### `Workstation name is configured`
Each AB Express requires a workstation name. It can be anything, such as the name of the computer (recommended). This is entered in using the administrator configuration tool.

#### How to fix
Use the administrator configuration tool to enter a valid workstation name.

### `Center name is configured`
AB Express requires a center name to be configured. This should be the name of the health care provider, such as "UCLA

#### How to fix
Use the administrator configuration tool to enter a center name.

### `Windows service installed`
This check verifies that the AB Express Windows service is installed on the system.

#### How to fix
Install or re-install AB Express

### `Windows service is running`
This check verifies that the AB Express Windows service is installed on the system and running.

#### How to fix
There are a few ways to restart the Windows service (note that administrator privileges is required for all fix methods):

__Method 1 (Windows UI, Recommended)__
1. Press the Windows key
2. Run "services.msc".
3. Right click on the service named **AB Express Client Service** and click Start


__Method 2 (Command prompt, advanced)__
1. Open a command prompt
2. Enter the following command to start the AB Express service `sc start abexpressclient`


### `Windows service is configured to automatically start`
The AB Express service needs to be configured to automatically start when the system starts.

#### How to fix
To fix this, do the following (requires administrator privileges):

1. Press the Windows key
2. Run "services.msc".
3. Right click on the service named **AB Express Client Service** and select Properties.
4. Change the **Startup Type** to **Automatic**
5. Start the service if it is not already started

### `Agent has been configured`
This check verifies that the AB Express service has been configured with the administration tool.

#### How to fix
Use the administrator configuration tool to fully configure the AB Express service.


