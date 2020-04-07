# HCL Mainframe Tools

HCL Mainframe Tools is a set of utilities that extend the functionality of Zowe Explorer.

The extension includes the following:

* Run REXX execs
* Submit jobs by specifying Data set name or from in open editors
* Terse PACK or UNPACK data sets or members
* Transmit or receive data sets ready for easy archiving 
* Receive XMIT files from Desktop
* List the System SVC List
* List System variables
* Run console commands
* Deploy the HCL Mainframe tools backend to mainframe

**Note:** The Zowe Explorer is powered by [Zowe CLI](https://zowe.org/home/). 

## Contents

* [Software Requirements](#software-requirements)
* [Create a Zowe CLI z/OSMF profile](#create-a-zowe-cli-zosmf-profile)

## Software Requirements

Ensure that you meet the following prerequisites before using the extension:

* Installed [Node.js](https://nodejs.org/en/download/) v8.0 or later.
* Configured TSO/E address space services, z/OS data set and file REST interface, and z/OS jobs REST interface. For more information, see [z/OS Requirements](https://docs.zowe.org/stable/user-guide/systemrequirements-zosmf.html#z-os-requirements).
* Zowe CLI `zosmf` profile.

**Notes:**

* You can use your existing Zowe CLI `zosmf` profiles that are created with the Zowe CLI v.2.0.0 or later.
* Zowe CLI `zosmf` profiles that are created in Zowe Explorer can be interchangeably used in the Zowe CLI.

### Create a Zowe CLI z/OSMF profile

See the [Zowe Explorer](https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe) documentation for profile creation details.

### Installation

The HCL Mainframe Tools requires a backend application to be installed to use the included commands.
The installation can be done with the following steps:

#### Step 1: Install the HCL Mainframe Tools Extension

#### Step 2: Deploy the HCL Tools Backend Exec

* Open the Command Palette, and type "Deploy Hcl Tools Backend Rexx Exec", and select the command to run it
* Choose the Mainframe profile to deploy the rexx exec to
* Specify the name of the data set that will hold the "HCLREXX" backend exec; this data set will be created if it does not exist. This value will be used whenever the HCL Tools backend is invoked.
* If the HCLREXX member exists, choose "yes" to overwrite the old member.

![Deploy backend Rexx Exec](images/docs-deploy-rexx-exec.gif?raw=true "Deploy backend Rexx Exec")

#### Step 3:  Deploy the HCL Tools Backend Program
* Open the Command Palette, and type "Deploy Hcl Tool Backend Program", select the command to run it
* Choose the Mainframe profile to deploy the backend program to
* Specify a temporary data set to hold the backend program terse Packed archive; you will be asked to re-allocate this data set if it already exists.
* Specify a data set to hold the unpacked XMIT format data set.
* Specify a data set to hold the HCL Tools backend program.
* The backend program will be uploaded to the mainframe, and installed to the specified location.

#### Installation Verification
* After deploying the HCL Tools backend, installation can be verified by running the  [Display HCL Tools Backend Version](#data-sets) command. Installation is successful if the backend version is displaysed.

### Advanced Configuration

You can modify HCL Mainframe Tools preferences in the extension `Setting` in the following ways:

* **Dummy Output Class** You can specify which output class should be used when running HCL Mainframe Tools backend utilities. By default class 'Z' is used a dummy class.

* **Enable Telemetry** HCL mainframe tools gathers high level anonymous usage information for quality improvement purposes. This telemetry can be turned off if desired.

* **HCL Backend Exec Data Set Name** The data set where the HCL Tools Rexx backend while be located. If this does not exist it will be created for you. A PDSE with Fixed Block 80 byte or larger records is required.

* **HCL Backend Program Library data set Name** The PDSE data set where the HCL Program object will reside. This data set will be created by the backend deployment command.

* **Log Level** The extension log level can be changed if required. If you encounter a problem when using HCL mainframe Tools please set the log level to "all" prior to reproducing the problem; after set the log level back to default.

* **Console Commands Config** New commands can be added or the default commands customized by editing the "label" value of commands.

<br /><br />

## Sample use cases

Review the following use cases to understand how to use HCL Mainframe Tools.

* [Data Sets](#data-sets)
* [Extras](#extras)

---

### Data Sets

You can use the following functionalities when interacting with the Zowe Explorer data set tree:

* **Display HCL Tools Backend Version**: You can check which version of the HCL Tools backend is installed on your mainframe.
* **List SVCs**: You can see the system SVC list including the numbers, addresses and names of both standard and ESR SVC entries.
* **List System Variables**: You can see the current values of many system ( REXX) variables, including Operating System and Hardware information.

* **Copy data set Name** and **Copy Member Name**: You can easily copy the label of a data set or member to system clipboard.
* **Run as Exec**: You can run REXX execs from data set or members and see exec output.
* **Terse Pack data sets and or members**: You can use AMATERSE to PACK data sets or membrs for simplied file transfers of binary or test files.
* **Terse Unpack**: You can use AMATERSE to UNPACK Terse data sets.

#### Display HCL Tools Backend Version

1. Navigate to the Zowe Explorer tree.
2. Open the **DATA SETS** Bar.
3. Select the profile that you want to see the backend version of
4. Right Click and choose **Display HCL Tools Backend Version**
The backend version is displayed as a Information Message in the Noficiation Area.

<br /><br />

#### List SVCs

1. Navigate to the Zowe Explorer tree.
2. Open the **DATA SETS** Bar.
3. Select the profile that you want to List SVCs of
4. Right Click and choose **List SVCs**
The System SVC information is displayed in a read-only editor.

<br /><br />

#### List System Variables

1. Navigate to the Zowe Explorer tree.
2. Open the **DATA SETS** Bar.
3. Select the profile that you want to List System Variables of
4. Right Click and choose **List System Variables**
The System variables are displayed in a read-only editor.

<br /><br />

#### Copy data set or member Name

1. Navigate to the Zowe Explorer tree.
2. Open the **DATA SETS** Bar.
3. Select a profile which is displaying a data set search pattern.
4. Select the desired data set or member.
5. Right Click and choose **Copy data set name** or **Copy member name**.
The resource name is placed on the system clipboard.

<br /><br />

#### Run as Exec

1. Navigate to the Zowe Explorer tree.
2. Open the **DATA SETS** Bar.
3. Select a profile which is displaying a data set search pattern.
4. Select the desired EXEC data set or member.
5. Right Click and choose **Run as Exec**
6. If needed specify an argument string for the exec, or press enter to run with no arguments
The exec is run and the output is displayed.

<br /><br />

#### Terse Pack data sets and or members

1. Navigate to the Zowe Explorer tree.
2. Open the **DATA SETS** Bar.
3. Select a profile which is displaying a data set search pattern.
4. Select the desired data set or member
5. Right Click and choose **Terse: Pack select data set**
6. Specify the output terse file name
The selected file is packed and the output is displayed.

<br /><br />

#### Terse Unpack

1. Navigate to the Zowe Explorer tree.
2. Open the **DATA SETS** Bar.
3. Select a profile which is displaying a data set search pattern.
4. Select the desired data set or member
5. Right Click and choose **Terse: unpack select data set**
The selected file is unpacked and the output is displayed.

<br /><br />

---

### Extras

* **Show all available Commands**: You can get an overview of all the commands included in HCL Mainframe Tools; including the situations when the commands can be invoked.

* **Submit a Batch Job**: You can submit a batch job by specifying the full data set name. The job appears in the Zowe Explorer Jobs tree.

* **Run Console Commands**: You can easily run a number of console commands by choosing from a list. You can easily change the default commands or add new commands in HCL Mainframe Tools Settings, for example, the following could be added to "list OUTCLASS definitions":

```json
"mainframetools.consoleCommandsConfig": [
    ...
        {
            "label": "$D OUTCLASS",
            "description": "List OUTCLASS defintions"
        },
    ...
```

where "label"  is the command to execute and "description"  the human readable description of the command.


![Add new Console Commands](images/add-console-command.gif?raw=true "Add new Console Commands")


* **Receive an XMIT file from Workstation**: You can use this command to upload and receive an XMIT format file from your workstation to the mainframe.

* **Create an XMIT format data set =**: You can use this command to "XMIT" a PDSE or other kind of data set to an XMIT format data set. The resulting file can be downloaded to a workstation or easily sent to another mainframe system.

* **Receive an XMIT file on mainframe**: You can use this command to "RECEIVE" an XMIT format data set. For example, you might need to do this if you have copied an XMIT file from another mainframe and wish to extract it.


#### Show all available Commands

1. Open the Command Palette
2. Type 'Mainframe Tools Show all', select the command to run it
A table of all available HCL Tools commands is displaysed including the contexts in which each can be used

<br /><br />

#### Submit a Batch Job

1. Open the Command Palette
2. Type 'Mainframe Tools Submit job', select the command to run it
3. Choose the desired profile
4. Specify the name of the data set and member containing the desired job, press enter to submit the job
The Job number appears in the Notification area

<br /><br />

#### Run Console Commands

1. Open the Command Palette
2. Type 'mainframe tools run a console command', select the command to run it
3. Choose the desired profile
4. Select the command you wish to issue, or "custom command" if you wish to run a different command
5. Press Enter to run the command
The output from the command appears in the HCL Tools Ouyput terminal

<br /><br />

#### Receive an XMIT file from Workstation

1. Open the Command Palette
2. Type 'Mainframe Tools Upload and receive an XMIT file from workstation', select the command to run it
3. Choose the desired profile
4. Navigate to and select the local XMIT file using the file selection dialog, Click open
5. Specify the remote XMIT data set name and the remote 'receive' data set name, press enter
The data set is uploaded to the mainframe ane then Received into the specified data set

<br /><br />

#### Create an XMIT format data set =

1. Open the Command Palette
2. Type 'Mainframe Tools Create an XMIT format data set', select the command to run it
3. Choose the desired profile
4. Specify the data set to be converted to XMIT format
5. Specify the output data set name
The data set is transmitted to the specified output data set and the result displayed

<br /><br />

#### Receive an XMIT file on mainframe

1. Open the Command Palette
2. Type 'Mainframe Tools receive xmit', select the command to run it
3. Choose the desired profile
4. Specify the data set to be received
5. Specify the destination data set name
The data set is received into the specified destation and the result displayed

<br /><br />
