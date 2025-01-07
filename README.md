# General

First of all, this material is related to **my personal studies** of [this bootcamp](https://www.googleadservices.com/pagead/aclk?sa=L&ai=DChcSEwj86amcg-SKAxU1kO4BHbIPN5AYABAAGgJkeg&ae=2&aspm=1&co=1&ase=2&gclid=Cj0KCQiAvvO7BhC-ARIsAGFyToW3p41_9ygY24uxgC2hnUoLaYhdKHe3S6doZJcGm-OZsydJ8PCGS4IaAgvFEALw_wcB&ohost=www.google.com&cid=CAESVeD2E80a1M2CDTlusoXXXt9p6_vHqv-TwY7XGzxypvH9IT4PWUp4yt9VPL2qeDYwMgDKKe2kK_X_3a1Gjz9-WJTiADRDUJSuEZX0FBZyD83PnHCPw-8&sig=AOD64_1g8HATRzeM824qM0M4bIqNjWclXQ&q&nis=4&adurl&ved=2ahUKEwin1qCcg-SKAxX9G7kGHdwoBekQ0Qx6BAgQEAE) on DIO platform. This material is **NOT** free to reproduce. I ask you to please access the DIO course. Here I only put **my** notes.


We can have one **app service** for several **web apps**. Is like to have one web server for several web apps.

![Azure app service - general](images/azure-app-service-general.png)

![Deploy on app service](images/deploy-on-app-service.png)


# Instalation of AZ CLI

I followed [these instructions](https://learn.microsoft.com/pt-br/cli/azure/install-azure-cli-linux?pivots=apt) to install AZ CLI


# Login in

I executed:

```
az login
```

Then a browser window was open. I logged in. But the authentication was failed. The passed reason was due to MFA.

To solve, in the same previous browser window, I logged (and confirmed with the code that was sent to my email). Then it was necessary to execute `az login` again and then in the next attemp the authentication through browser window (opened with the command `az login`) was successfull.


# Cloning a simple website Github repository

I executed these command:

```
mkdir webapp01
cd webapp01
git clone git@github.com:Azure-Samples/html-docs-hello-world.git
```

With these commands I created the directoty structure **webapp01 -> html-docs-hello-world -> website files (css, js, img ...)**


# Seeing my resource groups

I executed this command:

```
az group list --query "[].{id:name}" 
```


# Creating the app

Please execute this command:

```
 az webapp up -g DefaultResourceGroup-EUS -n apphtml01x --html --region us-east-01
```

An **empty** app will be created.

This command didn't work due a limitation related to a resource group or a region. I saw correctly the resource groups available with the previous command, ok?

I tried also to create a resource group in [Azure portal](http://portal.azure.com), but this attempt didn't work too.


# Uploading the app

Please execute the previous command again.


# Updating the app

After making a change in the HTML as exampĺe, teacher executed again the previous command.


# Getting the URL of the app

The URL was showed in the output of the command to upload or update the app:

![URL of the app](images/url-of-the-app.png)


# Versioning the app

I versioned the Azure app passed by the teacher without the original .git diretory to avoid problems on vesioning. But is the same of the git repository that I cloned before (as documented in this document).


# Configuring an app

You can configure several things of an app in the Azure Portal:

![configuring an app](images/configuring-an-app.png)

You configure there several things, ce3retificates as exampĺe.

If you wanna using websockets, you have a specific configuration about this thing.


# General observations

Teacher said that is common paths generating problems. Paths related to paths of the files.

You have also an option in the Azure Portal (inside the app details) to see the logs of the app. You have to enable logs in the app to see the logs.

In the next image you can see a change in the consumption of some resource related to the app:

![consumption change](images/seeing-the-change-in-the-consumption-of-the-app.png)

Teacher said that the log retention time is 30 days and if you try to extend this period, this action involves costs.

You have several configurations and options to be done om the Azure Portal. Like

- Load test;
- See metrics;
- An area to configure blocks;
- An area to see quotes;
- An area to see application insigths.

Related to scale horizontal and vertical, the options in the portal are:

![configuring scaling](images/configuring-scaling.png)

Is cool to access the Azure Portal, access the area related to the app and see all the options.

In the time teacher recorded the course, the screen to configure autoscaling was:

![configuring autoscale](images/configuring-autoscale.png)

More autoscaling settings:

![more autoscalling settings](images/more-autoscaling-settings.png)

Teacher said that general things can be observed every 5 minutes, but to memory his advice is to observe on each 3 minutes.

And you also can configure the scaling to be based on a specific date.


# Seeing the logs

You can see the logs in the area related to the app in the Azure Portal an also in the CLI with this command:

```
az webapp log tail --name <name_of_the_app> --resource-group <name_of_the_resource_group> --level verbose
```


# Configuring a certificate

By default the app running in the default subdomain of the domain **azurewebsite.net** already have a certificate, but if you change the domain you can configure a certificate for this new domain in this area:

![Configuring a certificate](images/configuring-a-certificate.png)

Teacher said that is sufficient to only configure the certificate in the area related to the previous image. You can also put the certificate in a keyvault and configure it. On adding a certificate you have an option to import a certificate from a keyvault.

Teacher said that the certificate **.cert** you can import directly and the certificate **.pfx** you have to put it in a keyvault.


# Dimensioning

You can make available more instances of the app based on a specific date like black friday or some resources, like measuring the CPU consumption and making new instances available on hitting 80% of the CPU consumption.


# Scaling

Also in Azure Portal you can configure horizontal and vertical scaling:

![Configuring scaling](images/configuring-scaling.png)