# Using EC2Rescue for Windows Server GUI<a name="ec2rw-gui"></a>

EC2Rescue for Windows Server can perform the following analysis on an offline instance:


| Option | Description | 
| --- | --- | 
| Diagnose and Rescue | EC2Rescue for Windows Server can detect and address issues with the following service settings: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2rw-gui.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2rw-gui.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2rw-gui.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2rw-gui.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2rw-gui.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2rw-gui.html) | 
| Restore | Perform one of the following actions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2rw-gui.html) | 
| Capture Logs | Allows you to capture logs on the instance for analysis\. | 

EC2Rescue for Windows Server can collect the following data from active and offline instances:


| Item | Description | 
| --- | --- | 
| Event Log | Collects application, system, and EC2Config event logs\. | 
| Memory Dump | Collects any memory dump files that exist on the instance\. | 
| EC2Config File | Collects log files generated by the EC2Config service\. | 
| EC2Launch File | Collects log files generated by the EC2Launch scripts\. | 
| SSM Agent File | Collects log files generated by SSM Agent\. | 
| Sysprep Log | Collects log files generated by the Windows System Preparation tool\. | 
| Driver SetupAPI Log | Collects Windows SetupAPI logs \(setupapi\.dev\.log and setupapi\.setup\.log\)\. | 
| Registry | Collects SYSTEM and SOFTWARE hives\. | 
| System Information | Collects MSInfo32\. | 
| Boot Configuration | Collects HKEY\_LOCAL\_MACHINE\\BCD00000000 hive\. | 
| Windows Update Log | Collects information about the updates that are installed on the instance\.  Windows Update logs are not captured on Windows Server 2016 and later instances\.  | 

## Video Walkthrough<a name="ec2rescue-walkthrough"></a>

Brandon shows you how to use the Diagnose and Rescue feature of EC2Rescue for Windows Server:

[![AWS Videos](http://img.youtube.com/vi/Apc6u2II5JA/0.jpg)](http://www.youtube.com/watch?v=Apc6u2II5JA)

## Analyzing an Offline Instance<a name="ec2rescue-offline"></a>

The **Offline Instance** option is useful for debugging boot issues with Windows instances\.

**To perform an action on an offline instance**

1. From a working Windows Server instance, download the [EC2Rescue for Windows Server](https://s3.amazonaws.com/ec2rescue/windows/EC2Rescue_latest.zip?x-download-source=docs) tool and extract the files\.
**Note**  
You can run the following PowerShell command to download EC2Rescue without changing your Internet Explorer Enhanced Security Configuration \(ESC\):  

   ```
   PS C:\> Invoke-WebRequest https://s3.amazonaws.com/ec2rescue/windows/EC2Rescue_latest.zip -OutFile $env:USERPROFILE\Desktop\EC2Rescue_latest.zip
   ```
This command will download the EC2Rescue \.zip file to the desktop of the currently logged in user\.

1. Stop the faulty instance, if it is not stopped already\.

1. Detach the EBS root volume from the faulty instance and attach the volume to a working Windows instance that has EC2Rescue for Windows Server installed\.

1. Run the EC2Rescue for Windows Server tool on the working instance and choose **Offline Instance**\.

1. Select the disk of the newly mounted volume and choose **Next**\.

1. Confirm the disk selection and choose **Yes**\.

1. Choose the offline instance option to perform and choose **Next**\.

The EC2Rescue for Windows Server tool scans the volume and collects troubleshooting information based on the selected log files\.

## Collecting Data from an Active Instance<a name="ec2rescue-active"></a>

You can collect logs and other data from an active instance\.

**To collect data from an active instance**

1. Connect to your Windows instance\.

1. Download the [EC2Rescue for Windows Server](https://s3.amazonaws.com/ec2rescue/windows/EC2Rescue_latest.zip?x-download-source=docs) tool to your Windows instance and extract the files\.
**Note**  
You can run the following PowerShell command to download EC2Rescue without changing your Internet Explorer Enhanced Security Configuration \(ESC\):  

   ```
   PS C:\> Invoke-WebRequest https://s3.amazonaws.com/ec2rescue/windows/EC2Rescue_latest.zip -OutFile $env:USERPROFILE\Desktop\EC2Rescue_latest.zip
   ```
This command will download the EC2Rescue \.zip file to the desktop of the currently logged in user\.

1. Open the EC2Rescue for Windows Server application and accept the license agreement\.

1. Choose **Next**, **Current instance**, **Capture logs**\.

1. Select the data items to collect and choose **Collect\.\.\.**\. Read the warning and choose **Yes** to continue\.

1. Choose a file name and location for the ZIP file and choose **Save**\.

1. After EC2Rescue for Windows Server completes, choose **Open Containing Folder** to view the ZIP file\.

1. Choose **Finish**\.