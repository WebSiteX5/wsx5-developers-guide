# Getting started

## 1. ­ Get the Optional Object's UUID and skeleton
You can get your own Optional Object's id from your [developer page](http://answers.websitex5.com/profile/developer). There, follow the onscreen instructions to create a new Optional Object.
After creating the new Optional Object, you will be able to see its UUID and to install it in your copy of WebSite X5.

Once your object is installed, you can find its sources in the following path:
**C:\Users\\[User]\AppData\Local\Incomedia\WebSiteX5 v11 - [Edition]\PluginApps\\[UUID]**

Inside the Optional Object's folder you may find the following items:

* **manifest.xml**: mandatory, is the file containing all the code necessary to make your app work. All the informations you need to fill it are here, in the developer's guide.
* **localization.xml**: mandatory, it needs to contain at least the english localizationsfor the app, but it allows you to add more languages. It uses the same structure of the languages file of WebSite X5.
* **icon.png**: mandatory, is what will make your app recognized by the users and needs to be 32px*32px.
* **Resources folder**: optional, is necessary in case your app needs to use external files to work.

## 2. Define the user input fields
Before writing the code, you should plan your Optional Object user interface.
What kind of user input do you need? How many user inputs will you use? Do you need more tabs?
When these decisions are taken, fill the `Parameters` tag of the manifest.xml file accordingly to the instructions defined in the [manifest.xml](manifest-xml.md) and [User input fields](user-input-fields.md) sections.

## 3. Define the external files (Resources)
Once the UI has been defined, the next step is to decide if the app will need to use external files like javascript libraries (keeping in mind that jQuery is automatically included by WSX5), or custom css files.
If you need to do so, copy the required files inside the Resources folder of the app. Then link those files in the `Resources` tag of the manifest.xml file accordingly to the instructions you find int the [Resources Tag](manifest-xml.md#resources-tag) section.
Remember to add the correct path in the manifest.xml file, in case you use subfolders.

## 4. Define the output
Inside the `Output` tag you must define the HTML code that will be outputted in the site's page.
You can write plain HTML (or PHP).
To access to the user input fields values, refer to the [Output Tag](manifest-xml.md#output-tag) and [WSX5 Script](wsx5-script.md) sections.
You may want to discover the examples we uploded on [GitHub](http://www.github.com/websitex5): you can see how we built all the freeware Optional Objects you can find in WebSite X5.

## 5. Publish your Optional Object
Once your object is ready and you tested it, you can submit it to us and our developers will process it so all the users of WebSite X5 will be able to use your app on their projects.
For every question feel free to contact us on [Answers](http://answers.websitex5.com) and we will try to help you to develop your Objects.

We are looking forward to see your creations you want to share with the community.

Happy coding!
