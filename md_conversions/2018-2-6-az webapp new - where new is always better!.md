---
title: "az webapp new - where new is always better!"
author_name: Ahmed Elnably
layout: post
hide_excerpt: true
---
      [Ahmed Elnably](https://social.msdn.microsoft.com/profile/Ahmed Elnably)  2/6/2018 2:31:20 PM  ### This blog post has old info, the new version is [here](http://blogs.msdn.microsoft.com/appserviceteam/2018/03/22/renaming-our-new-command-to-up/).

 The App Service team have been hard at work creating a new experimental create and deploy experience for [Azure App Service.](https://azure.microsoft.com/en-us/services/app-service/) We released a new [Azure CLI extension](https://docs.microsoft.com/en-us/cli/azure/azure-cli-extensions-overview?view=azure-cli-latest) that adds a new command called **new **(have you seen what we did there!?). The new command (**Which is currently in Preview**) enables the user to create and deploy their Node.js or .NET Core app using a single command. For Node.js we check for the existence of a **package.json** file in the code root path to indicate it is a Node.js app. For .NET Core we check for the existence of a ***.csproj** file with **netcoreapp **as the** TargetFramework** [caption id="attachment\_7095" align="alignnone" width="586"][![]({{ site.baseurl }}/media/2018/02/newCLI-1024x669.gif)]({{ site.baseurl }}/media/2018/02/newCLI.gif) Click on the gif to see the command in action[/caption] In the case of Node.js app the command does the following:  2. Create a new resource group (in Central US, you can use the --location to change the region)
 4. Create a new Linux single VM small App Service plan in the Standard SKU (in Central US)
 6. Create a Linux webapp
 8. Deploy the content of the current working directory to the webapp using [Zip Deployment](https://blogs.msdn.microsoft.com/appserviceteam/2017/10/16/zip-push-deployment-for-web-apps-functions-and-webjobs/)
  In the case of .NET Core app the command does the following:  2. Create a new resource group (in Central US, you can use the --location to change the region)
 4. Create a new free Windows App Service plan (in Central US)
 6. Create a Windows webapp
 8. Deploy the content of the current working directory to the webapp using [Zip Deployment](https://blogs.msdn.microsoft.com/appserviceteam/2017/10/16/zip-push-deployment-for-web-apps-functions-and-webjobs/)
  To Install the Azure CLI tools refer to their [documentation](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest). To Install the extension: az extension add --name webapp To update the extension with the latest fixes and new languages support (Current version is 0.1.0): az extension update --name webapp To know what the command will do without creating anything: az webapp new --name [app name] --location [optional Azure region name] --dryrun [caption id="attachment\_7115" align="alignnone" width="626"][![]({{ site.baseurl }}/media/2018/02/dryrun-1024x592.gif)]({{ site.baseurl }}/media/2018/02/dryrun.gif) Click to see --dryrun in action[/caption] To use the new command: az webapp new --name [app name] --location [optional Azure region name] To update your app content - Just rerun the command you used to create the app (including the --location argument): az webapp new --name [app name] --location [optional Azure region name] To submit feedback or submit an issue please open an issue in the [Azure CLI extensions Github Project page](https://aka.ms/webapp-extension-issues). Road Map - also tracked [here](https://aka.ms/webapp-extension-issues):  2. Add better support to update the app with new changes
 4. Add more languages to the supported list
 6. Add support to [Azure Functions](https://azure.microsoft.com/en-us/services/functions/)
        