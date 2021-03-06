# Microsoft AL application add-on and localization extensions for Microsoft Dynamics 365 Business Central
Welcome to the ALAppExtension repository!

This repo is a platform for Microsoft and our vibrant partner channel and community to work together to develop apps in the AL language and enable the general extensibility of Microsoft Dynamics 365 Business Central.

We’re working to make the core application thinner, more extensible, and easier to localize by extracting more and more of our application business logic into add-on and localization apps. As we go, we’ll publish the source code for the apps in this repo. The apps are open for contributions and can serve as starting point for verticalizations or just as samples for developing apps.

Microsoft will publish the contributions to the code in this repo on AppSource, and they’ll ship in upcoming releases of [Microsoft Dynamics 365 Business Central](https://dynamics.microsoft.com/en-us/business-central), where you’ll get to enjoy the effect of your contributions.

## Types of engagements
There are a couple of ways to engage with us here:  
  
* You can grab the code and contribute to the published apps. For more information, see the _Contributing_ section below.  
* If you’re building your own app and need something specific from us, like an event, you can help improve the general extensibility of the business logic. For more information, see the _Extensibility requests_ section below.

### Extensibility requests
The following are the types of requests you can submit to unblock your app:  

* Add new integration events – Get the event you need to hook-in to a process.  
* Change function visibility – For example, make a public function external or a similar change so you can call it from your extension and reuse the business logic.  
* Replace Option with Enum – Replace a specific option with an enum that supports your extension. The new type enum is extensible, but all code was written for non-extensible options.  
* Extensibility enhancements – Request changes in the application code that will improve extensibility.  
  
We’ll have a look at your request, and if we can we’ll implement it asap. If we can’t we’ll let you know and briefly explain why not. When that happens, don’t be discouraged. Go back to the drawing board, see if you can work it out, and then come back and submit another request.

## Contributing
This project welcomes contributions and suggestions.  Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## How to get started
1. Become familiar with development in AL. For more information, see https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-get-started.  
2. Choose the sandbox option that's right for you. For more information, see https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-sandbox-overview.  
3. Clone the repository where Microsoft extensions are available : https://github.com/Microsoft/ALAppExtensions.  
4. Objects are in the Microsoft ID range, which means you cannot upload the app to your sandbox. For the app to work you must renumber the object IDs (for more information, see https://blogs.msdn.microsoft.com/nav/2018/04/05/business-central-object-ranges/).  
    
    You can renumber objects in several ways. The following steps describe one of them.  
    
	1. Get the RenumberNavObjectIds tool from https://github.com/NAVDEMO/RenumberNavObjectIds.  
    2. Clone the project and open it in Visual Studio 2015. Build the project, and you are off to a good start.  
    3. Run the following PowerShell Script in PowerShell ISE:  
       ```
       Import-module "C:\...\RenumberObjectIds.dll"  
	   $RenumberList = @{}  
	   0..1000 | % { $RenumberList += @{ (1800+$_) = (80000+$_) } }  
	   0..20 | % { $RenumberList += @{ (136630+$_) = (82000+$_) } }  
		 
	   Renumber-NavObjectIds -SourceFolder "C:\...\C52012DataMigration\" -DestinationFolder "C:\...\C52012DataMigrationReID" -RenumberList $RenumberList -Verbose  
       ```
5. In Visual Studio Code, connect to your sandbox (follow the steps in the documentation that step 2 refers to) and open the C:\...\C52012DataMigrationReID folder. Now you are ready to go. You can modify the code and build your extension.  
6. To submit your changes, create a new branch. Remember to revert the change of IDs, and then create a pull request.  

## See Also
[FAQ](FAQ.md)