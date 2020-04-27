# abexpress-debugtool
This is the temporary home for the AB Express configuration checker tool. It looks for common issues with AB Express installations and configurations and provides suggested fixes. This site will always contain the latest version of the configuration checker tool.

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

### `Configured monitoring folder exists`
AB Express can be configured to monitor custom folders. This check will fail when AB Express has been configured in this manner, but the actual folder/directory does not exist on the system.

#### How to fix
Run the configuration checker tool and click on the failed check. The tool will show you a list of folders that have failed this check. Ensure that the listed folders exist on the system.

### `Network connection to REST API v1 and v2`
These checks verify that the system is able to make a network connection to the AB Express REST API servers. Being able to do so is critical for the successful operation of the AB Express service.

#### How to fix
Fixing this issue will likely require the assistance of the center's network IT team. If the network connection is being blocked, it could be due to one or more of the following issues:

- Blocked at the perimeter firewall
- Blocked by anti-malware software
- The center's network is not configured to trust the signing certificate authority of the AB Express TLS certificate

Please ask the center's network IT team to help enable external access to the AB Express REST API servers. You can send the following description to the center's network IT team and they will understand what to do:

`Please enable outbound or egress access to the abexpress-api.advancedbionics.com and dx-api.ironbox.app on TCP port 443`

### `System supports TLS 1.2 security protocol`
The AB Express service uses the transport-layer security (TLS) protocol version 1.2 for securely sending data. This is the industry standard and 1.2 is the minimum version supported. If the system does not appear to support this protocol, then this check will fail.

Often times a system will fail this check due to the following:
- Missing latest security patches
- Operating system is too old (TLS is automatically supported on Windows 8 and higher)
- It has been disabled by network administrators explicitly
- The minimum version of .NET Framework 4.6.1 is missing

#### How to fix
Fixing this issue will likely require the assistance of the center's network IT team. Please direct them to the following link:

[How to enable TLS on client machines](https://support.microsoft.com/en-us/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-default-secure-protocols-in-wi)




