## Localizations

An Optional Object may be localized using the localizations.xml file prodived with the object.

The file format is the same used for the languages of WebSite X5.

It is obligatory to fill in at least the English localization in the file. 

To access the localizations from the manifest.xml file, add the l10n-id attribute to the xml element you want to localize.
The l10n-id attribute must contain a localization id that was previously specified in the localization.xml file using the <Key> tag as reported in the following example.

```xml
<?xml version="1.0" encoding="utf-8"?>
<WebsiteX5LanguagesLibrary xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <Languages>
	<Language>
	 	<Code><![CDATA[EN]]></Code>
	 	<Name><![CDATA[English]]></Name>
	 	<WritingDirection><![CDATA[LeftToRight]]></WritingDirection>
	 	<Localizations>
		   	<Localization>
		     	<Key>my-first-localizazion-id</Key>
		     	<Value>First sentence</Value>
		   	</Localization>
		   	<Localization>
		     	<Key>my-second-localizazion-id</Key>
		     	<Value>Second sentence</Value>
		   	</Localization>
	 	</Localizations>
	</Language>
	<Language>
		<Code><![CDATA[IT]]></Code>
	 	<Name><![CDATA[Italian]]></Name>
	 	<WritingDirection><![CDATA[LeftToRight]]></WritingDirection>
	 	<Localizations>
		   	<Localization>
		     	<Key>my-first-localizazion-id</Key>
		     	<Value>Prima frase</Value>
		   	</Localization>
		   	<Localization>
		     	<Key>my-second-localizazion-id</Key>
		     	<Value>Seconda frase</Value>
		   	</Localization>
	 	</Localizations>
	</Language>
 </Languages>
</WebsiteX5LanguagesLibrary>
```