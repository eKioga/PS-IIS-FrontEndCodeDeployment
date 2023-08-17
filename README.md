<p align="center">
  <img src="https://imgur.com/9OSFZl1.jpeg" alt="Script GUI Screenshot">
</p>

<h3 align="center">PowerShell Deployment Script</h3>

<div align="center">

  [![Status](https://img.shields.io/badge/Status-Closed-red.svg)]() 
  [![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

---

<p align="center"> PowerShell script for deploying code to a Windows IIS server. 
</p>

## 📝 Table of Contents
- [About](#about)
- [Getting Started](#getting_started)
- [Built Using](#built_using)
- [Authors](#authors)
- [Acknowledgments](#acknowledgement)

## 🧐 About <a name = "about"></a>
I created this PowerShell script for production use at a previous employer of mine. I sanitized it for GitHub. Empowering developers with the ability to deploy their own code into production is the goal. 

It's designed for deploying front-end code to a Windows IIS server. From there, DFS would replicate it out to the rest of the web farms. After the script completes, it sends an email to a change management distribution list. The email describes which customer it updated to which version and includes the user account that executed the update. This ensures accountability with developers while keeping them agile.

## 🏁 Getting Started <a name = "getting_started"></a>
These instructions will get walk you through the process of executing this script in your environment.

### Prerequisites
- A newer version of PowerShell is highly recommended. 
- Ensure that Set-ExecutionPolicy is configured for the host running the script.
	- If you're unfamiliar with "Set-ExecutionPolicy", click [here](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.3#-executionpolicy ) to review it's documentation.
- Locate the variables within the script (see example below) and update them to reflect your environment.

Example Variables: 
```
$destination = "\\WebServer01\inetpub"
$deploymentDirectory = "\\DeployServer01\deployments\WEB\QA\"
$messageFrom = "operations@company.com"
$messageTo = "changeMangamentSystem@company.com"
$messageBody = "Updated WEB for $instanceName to $webVersion <br>by $env:username <br><br>Per $tpURL"
$smtpServer = "emailServer.company.local"
```

### Executing the Script
How to use the script, step by step.

1. Copy "PS-IIS-FrontEndCodeDeployment.ps1" to your local workstation.
	- Depending on your Execution Policy, it may be simpler to copy the code itself into a new text file on your local workstation, then change the extension to .ps1.
2. Run the script by right-clicking on the .ps1 file and then choose "Run with Powershell".
   	- You can also open the script file using Windows PowerShell ISE. I recommend this for approach for easy testing and debugging.

#### Once the "Web Deployment" interface appears, do the following:
1. **Web Instance**: Enter the customer instance that will receive the update.
2. **Web Version**: Enter the code version.
3. **TP URL**: Add link to the TargetProcess page describing this customer deployment.
4. Click the **Enter button** to begin deployment.
<p align="center">
  <img src="https://i.imgur.com/OhViH97.jpeg" alt="Script text box examples">
</p>

**Note**: After clicking the "Enter" button, a blue screen will pop-up printing out the status of each step the script is executing. If the script fails, take a look at the last step it tried to execute and start investigating there.

#### If you see the text "Deployment Complete!" in the bottom text box, this signifies that the script has ran successfully.
<p align="center">
  <img src="https://i.imgur.com/SqXvHHe.jpeg" alt="Script results example">
</p>

## ⛏️ Built Using <a name = "built_using"></a>
- [VS Code](https://vuejs.org/) - My favorite IDE
- [Windows PowerShell ISE](https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise?view=powershell-7.3) - IDE (For easy functions in isolation)
- [Obsidian](https://obsidian.md) - Markup Editor (My favorite tool for notes!)

## ✍️ Authors <a name = "authors"></a>
- [Eric Post](https://github.com/eKioga) - Idea & work

## 🎉 Acknowledgments <a name = "acknowledgement"></a>
- A big thank you to all the devs that had me working late nights and weekends jump scaring me with code drop requests. Thank you for helping me find the motivation to write this script.
