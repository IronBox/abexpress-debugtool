# abexpress-debugtool
This is the temporary home for the AB Express configuration checker tool. It looks for common issues with AB Express installations and configurations and provides suggested fixes.

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
The configuration checker tool 

### `Product key is valid`
This check analyzes the configured product key from the registry to ensure that is a valid key. If a key has not been entered via the administrator Configuration tool or has been tampered with directly in the registry, this check will fail.

#### How to fix
Use the Admin Configuration Tool to enter a valid product key. You can obtain a key by signing into [www.abproportal.com](https://www.abproportal.com).


### `Workstation name is configured`
Each AB Express requires a workstation name. It can be anything, such as the name of the computer (recommended). This is entered in using the administrator configuration tool.

#### How to fix
Use the Admin Configuration Tool to enter a valid workstation name key.

#### `Center name is configured`
AB Express requires a center name to be configured. This should be the 



