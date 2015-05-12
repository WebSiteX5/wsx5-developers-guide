# WSX5Script
The WSX5Script code is an ECMAScript code which is run by WebSite X5 when the HTML/CSS code is built. The script output will be inserted where the script is.

The syntax to use is the same as JavaScript.
The script needs to be executed inside the <?wsx5 ?> tags (excpetion of the Hooks tag which do not require any particular tag).

Following global variables are accessible through code (further informations available on http://help.websitex5.com/api/pluginapps/):

parameters: each one has the properties indicated in the “Tag Parameters” paragraph. Further, everyone of them has these global methods and properties:
hide(): hides the field in the UI.
show(): shows the field in the UI.
visible: true if the field is visible in the UI.
enable(): abilitates the field in the UI.
disable(): disables the field in the UI.
enabled: true if the field is enabled in the UI.
resources: An object containing, for every ID, an object with following properties:
id: the ID specified in the manifest
name: name of the file
destination: path relative to the root of the website
document: has following methods:
write(string): writes a string in output
console
log(string): add a message in the developers console (tab visible when the app is in developer mode).
currentObject: has following properties:
id: id of the object
width: width of the object
l10n: Allows you to read a value of the localization.xml file and has following methods:
get(localizationId): returns the localization in the website language.
get(localizationId, defaultValue): returns the localization in the website language. If localizationId is not found, returns defaultValue.
get(localizationId, defaultValue, languageId): returns the localization in the specified language, returning defaultValue id localizationId is not found.
get_global(localizationId): returns the requested localization by taking it from the localization library of the UI of WebSite X5. It is always in the installation language of the software.
get_global(localizationId, DefaultValue): returns the requested localization by taking it from the localization library of the UI of WebSite X5. It is always in the installation language of the software. In case the localization is not present it will be used the default value.
As example, to have as output a value you added in the localization.xml you can use <?wsx5 document.write(l10n.get("Localization Key")) ?> where instead of Localization Key you add the Key used in the localization.xml file.

wsx5: has following properties
uiLanguageId: User Interface Language
contentLanguageId: Site Language
mode: ‘uipreview’, ‘preview’, ‘online’, according to the moment when the content is made
accessManagement: informations about the private area
shoppingCart: informations on the shopping cart
dataManagement: informations on the projects data