CrossKnowledge - Content Provider Data Feed
===========================================

This resource is for content providers in order to integrate with our
content management system.


Format of the content
---------------------
* Audio
* Downloadable documents: pdf, docx, xlsx, images;
* Interactive content, the SCORM packages : 1.2 and 2004;
* Reading documents;
* Video Files: mp4, with subtitles in srt format;
* Websites' URLs

Metadata and presentation
-------------------------
The metadata should be presented as an XML file. You'll find the XML Schema [here](blob/master/catalog_import.xsd).

### Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalog>
    <provider>
        <behaveLikeCrossKnowledge>true</behaveLikeCrossKnowledge>
        <description>Content from LCMS Content</description>
        <defaultThumbnail>
            <content>crossknowledge.gif</content>
        </defaultThumbnail>
        <name>CrossKnowledge Library</name>
        <picture>http://example.ck/crossknowledge.gif</picture>
    </provider>
    <contents>
        <content>
            <audiences></audiences>
            <description>This course will start out reviewing traditional CSS3 Layout, including flexbox, regions, and multicolumn layout. Then we will discuss WinJS controls that support additional UI layout options, including the ListView, SemanticZoom, and ViewBox controls.  We will see that the ListView displays items in grid or list layout, whereas the SemanticZoom supports zoom between two semantic levels, and the ViewBox allows for dynamically scaling single child element to fill available space without changing aspect ratio.</description>
            <locale>en-US</locale>
            <refId>OJMH390</refId>
            <refIdVersion>OJMH390_v1</refIdVersion>
            <summary>Feedback can help staff members to progress and develop their skills provided it is given in the right way. This session will show you how to identify common errors and the principles of constructive feedback.</summary>
            <summaryShort>Identify common errors and the principles of constructive feedback.</summaryShort>
            <title>How to Give a Constructive Feedback</title>
            <url>http://path/to/object/OJMH390.zip</url>
            <type>i</type>
            <subtype>Interactive</subtype>
            <runtime>CKLM_SCORM</runtime>
            <publicationDate>2014-02-14</publicationDate>
            <tags>
                <tag>Skills Management</tag>
                <tag>Training</tag>
                <tag>Evaluation</tag>
                <tag>Learning</tag>
            </tags>
            <thumbnail>img/8AI5.PNG</thumbnail>
            <themes>
                <theme>Developing Autonomy > Identifying the problem</theme>
            </themes>
            <duration>30</duration>
            <level>1</level>
            <authors>
                <author>
                    <firstName>Peter</firstName>
                    <lastName>Thorsteinson</lastName>
                    <authorThumbnail>img/thorsteinson.png</authorThumbnail>
                    <biographies>
                        <biography>
                            <locale>en-US</locale>
                            <biographyShort>Microsoft Expert</biographyShort>
                            <biographyFull>Peter Thornsteinson...</biographyFull>
                        </biography>
                    </biographies>
                </author>
            </authors>          
        </content>
    </contents>
</catalog>
```

XML Description
------- 
This is the architecture of the XML:

| Node                                                          | Required | Allow Multiple Nodes | Details                        |
| :-------                                                      | :----    | :---                 | :---                               
| catalog                                                       | YES      | NO                   | The main node |
| catalog > provider [(see details here)](#providers)           | YES      | NO                   | The provider details |
| catalog > contents [(see details here)](#contents)            | YES      | YES - content        | The contents of the specified provider |
| catalog > contents > content > audiences                      | YES      | YES - audience       | Describe the audiences of the content |
| catalog > contents > content > videoSubtitles                 | YES      | YES - videoSubtitle  | Describe the subtitles of videos |
| catalog > contents > content > tags                           | NO       | YES - tag            | Describe the tags of the content |
| catalog > contents > content > themes                         | NO       | YES - theme          | Describe the themes for the content |
| catalog > contents > content > authors                        | NO       | YES - author         | Describe the themes for the content |
| catalog > contents > content > authors > author > biographies | NO       | YES - biography      | Set information about the author ||

Each table above describes one node of XML.

#### Providers

| Field Name                |Type        | Size | Required | Details 
| :-------                  | :----      | :--- | :---     |:---  
| behaveLikeCrossKnowledge  | boolean    |      | YES      | 
| description               | text       | 256  | YES      | Short description about company, content, etc |
| name                      | text       |      | YES      | Name of the provider
| picture                   | url        |      | YES      | Absolute or relative url. To relative url, the url should be relative to this XML. Eg. XML url: http://somesite.com/PATH_TO_XML/catalog.xml, the url for this image should be PATH_TO_XML/someimage.png. 
| defaultThumbnail          | **node**   |      | YES      | [See details here](#default-thumbnail)
| thirdPartyContract        | boolean    |      | NO       | Default: true
| thirdPartyOffer           | boolean    |      | NO       | Default: true


#### Contents

This node allows how much content you need, just define ``<content>`` for each one of them.

| Field Name                | Type     | Size | Required | Details
| :-------                  | :----    | :--- | :---     |:---   
| audiences                 | **node** |      | YES      | [See details here](#audiences)
| description               | text     |      | YES      | 
| locale                    | text     |      |	YES      | Language of content. Better if uses the language&nbsp;Country format. Eg: en&nbsp;US, fr&nbsp;FR, etc.
| refId                     | text     | 45   | YES      | Reference ID. Must be unique for all versions of content. Eg: AB22 . The refId represents the content in all languages and versions available.
| refIdVersion              | text     | 45   | YES      | Reference ID Version. Represent version of content. Eg: AB22 English v1, AB22 Spanish v2...
| summary                   | text     |      | YES      |
| summaryShort              | text     |      | YES      |
| title                     | text     |      | YES      | Unicity not required but highly recommended
| url                       | text     |      | YES      |
| additionalData            | text     |      | NO       |
| alternateUrl              | url      |      | NO       |
| archiveList               | int      |      | NO       | Accept: 0 or 1. Default: 1
| authors                   | **node** |      | NO       | [See details here](#authors)
| blackList                 | int      |      | NO       | Accept: 0 or 1. Default: 1
| course                    | text     |      | NO       |
| detailedcontent           | text     |      | NO       |
| duration                  | int      |      | NO       | In minutes. Eg: 10, 20, 130..
| level                     | int      | 1    | NO       | Accepted: 1, 2 or 3
| linkedActionTips          | **node** |      | NO       | [See details here](#linked-action-or-essential-tips)
| linkedEssential           | **node** |      | NO       | [See details here](#linked-action-or-essential-tips)
| objectives                | text     |      | NO       |
| publicationDate           | date     |      | NO       | **Format: YYYY-mm-dd** / First publication date. Creation date to help versions control.
| publisher                 | text     |      | NO       | 
| runtime                   | text     |      | NO       | Accepted: "CKLM_SCORM" => Scorm<br/> "CKLM_FILE" => Reading document, PDF, Image, DOC<br/> "link_lo_guid" => Website, url
| scoreinprogress           | text     |      | NO       | 
| subtitle                  | text     |      | NO       | 
| subtype                   | text     |      | NO       | If the content is categorized, put category here
| tags                      | **node** |      | NO       | [See details here](#tags)
| thumbnail                 | url      |      | NO       | Absolute or relative url. To relative url, the url should be relative to this XML. Eg: with this XML URL(http://somesite.com/PATH_TO_XML/catalog.xml), the URL for this image should be "PATH_TO_XML/content_thumbnail/someimage.png"
| themes                    | **node** |      | NO       | [See details here](#themes)
| type                      | text     |      | NO       | Accepted: "a" => Audio, "d" => Document to download, "p" => Image, "i" => Interactive content (Scorm), "r" => Reading document, "v" => Video, "w" => Website, Url
| videoSubtitles            | **node** |      | NO       | [See details here](#video-subtitles)


#### Audiences

This node allows you describe how much audiences you need, just define ``<audience>`` for each one of them.

| Field Name      | Type     | Size | Required | Details
| :-------        | :----    | :--- | :---     |:---
| audience        |	text     |      | YES      | Eg: Leader, Senior Manager, Project Manager...


#### Authors

This node allows you describe how much authors you need, just define ``<author>`` for each one of them.

| Field Name      | Type     | Size | Required | Details
| :-------        | :----    | :--- | :---     |:---
| lastName		  |	text	 |      | YES      |
| authorThumbnail |	text	 |      | NO       | Absolute or relative url. To relative url, the url should be relative to this XML. with this XML URL(http://somesite.com/PATH_TO_XML/catalog.xml), the URL for this image should be "PATH_TO_XML/content_thumbnail/someimage.png"
| biographies     |	**node** |      | NO       | [See details here](#biographies)
| company         |	text	 |      | NO       |
| competencies    |	text	 |      | NO       |
| customGuid      |	text	 |      | NO       |
| email           |	text	 |      | NO       |
| firstName       |	text	 |      | NO       |
| jobTitle		  |	text	 |      | NO       |
| phone           |	text	 |      | NO       |


#### Biographies

This node allows you describe how much biographies you need, just define ``<biography>`` for each one of them.

| Field Name      | Type     | Size | Required | Details
| :-------        | :----    | :--- | :---     |:---
| locale          |	text     | 5    | YES      | Language of biography. Should be in this format: language-COUNTRY. Eg: en-US, fr-FR
| biographyShort  |	text     | 0    | YES      |
| biographyFull   |	text     |      | NO       |


#### Default Thumbnail

| Field Name      | Type     | Size | Required | Details
| :-------        | :----    | :--- | :---     |:---
| content         |	url      |      | YES      | Image which represent the provider, like a logo or a symbol. There is no limit to the thumbnail size, but we recommend a proportional image to 640x320px and follow same rule of picture. 


#### Linked Action or Essential Tips

This node allows you describe how much tips you need, just define ``<code>`` for each one of them.

| Field Name      | Type     | Size | Required | Details
| :-------        | :----    | :--- | :---     |:---
| code            |	text     |      | YES      |


#### Tags

This node allows you describe how much tags you need, just define ``<tag>`` for each one of them.

| Field Name | Type  | Size | Required | Details
| :-------   | :---- | :--- | :---     |:---
| tag        | text  |      | YES      |


#### Themes

This node allows you describe how much themes you need, just define ``<theme>`` for each one of them.

| Field Name | Type  | Size | Required | Details
| :-------   | :---- | :--- | :---     |:---
| theme      | text  |      | YES      | This element can be used for a more detailed categorization using character ">". Eg: Main Theme > SubTheme > ...


#### Video Subtitles

This node allows you describe how much themes you need, just define ``<videoSubtitle>`` for each one of them.

| Field Name    | Type  | Size | Required | Details
| :-------      | :---- | :--- | :---     |:---
| videoSubtitle | text  |      | YES      | Eg: legend_en-US.srt


How to send my metadata and my content
--------------------------

We will provide you with an SFTP server where you will send the content and the metadata files.

### Naming Scheme

#### Catalog
The catalog should be created with the date of the creation in the name following this convention:

	catalog-YYYYmmddHHMMSS.xml

**The hours need to be in the 24h format.**

Example : catalog-20160403132400.xml for a catalog created on the 3rd of April 2016, at 1:24:00 pm.
	
Our system will process the files and put them in a backup directory afterwards.

#### Reference to the content

The references in the XML file can be either absolute (http://domain/path/to/file.png) or relative to the position of the catalog file. If you have an directory structure like this
	FTP/
		- catalog-20160403132400.xml
		- Scorm/
			- first_course.zip
			- second_course.zip
		- Img/
			- course_1_thumb.jpg
			- course_2_thumb.jpg

Then your catalog should look like that:
```xml
	...
	<content>
		<title>Course 1 title here</title>
		<thumbnail>Img/course_1_thumb.jpg</thumbnail>
		<url>Scorm/first_course.zip</url>
		...
	</content>
	<content>
		<title>Title of the Second course</title>
		<thumbnail>Img/course_2_thumb.jpg</thumbnail>
		<url>Scorm/second_course.zip</url>
		...
	</content>
	...
```

It's recommended to use simplify the name of the assets to use only basic characters:
	[a-zA-Z0-9_\-\.]

**NOTE**: The URLs that specify images and documents will be downloaded and will not be requested anymore. If you need to update this content, please update the URL and import again.

How to test my catalog.xml
------------------------------

We've included a simple python tool to test it.

### Requirements

To use our tool you need to make sure that you have python-lxml installed:
```bash
pip install -r requirements.txt
```

### Check my catalog

Once you have the requirements installed you can check your datafeed like this:
```bash
python ./check.py my_catalog.xml
```
