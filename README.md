Crossknowledge - Content Provider Data Feed
===========================================

This resource is targeted at content providers wanted to integrate with our
content management system.


Format of the content
---------------------

At the moment, we accept these different formats:
* Static Files : pdf, docx, xlsx, images etc.
*  Video Files : mp4, with subtitles in srt format;
*  Scorm Packages : 1.2 and 2004.

Metadata and presentation
-------------------------

The metadata should be presented as an XML file. You'll find the XML Schema in this repository (catalog\_import.xsd)

### Presentation
```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalog>
	<provider>
		<name>CrossKnowledge Library</name>
		<description>Content from LCMS Content</description>
		<picture>http://example.ck/crossknowledge.gif</picture>
		<defaultThumbnail>
			<content>crossknowledge.gif</content>
		</defaultThumbnail>
	</provider>
	<contents>
		<content>
			<refId>OJMH390</refId>
			<refIdVersion>OJMH390_v1</refIdVersion>
			<title>How to Give a Constructive Feedback</title>
			<locale></locale>
			<summary>Feedback can help staff members to progress and develop their skills provided it is given in the right way. This session will show you how to identify common errors and the principles of constructive feedback.</summary>
			<type>Interactive</type>
			<subtype>Session</subtype>
			<runtime>scorm</runtime>
			<thumbnail></thumbnail>
			<url>http://path/to/object/OJMH390.zip</url>
			<tags>
				<tag>Skills Management</tag>
				<tag>Training</tag>
				<tag>Evaluation</tag>
				<tag>Learning</tag>
			</tags>
			<themes>
				<theme>Developing Autonomy</theme>
			</themes>
			<duration>30</duration>
			<audiences></audiences>
			<level>1</level>
			<objectives></objectives>
			<additionalData></additionalData>
		</content>
	</contents>
</catalog>
```

XML content description
------- 


|Field/Node|Type/Format|Size|Required|Description|
| :------- | :---- | :---: | :---: |:---|
|**catalog**                    |Main node||YES|
| &nbsp;&nbsp;**provider**                 |node||YES|Informations block about provider|
| &nbsp;&nbsp;&nbsp;&nbsp;name                       |text|||
| &nbsp;&nbsp;&nbsp;&nbsp;description                |text|256|YES|	Short description about company, content, etc|
| &nbsp;&nbsp;&nbsp;&nbsp;picture                    |absolute url|suggestion: 250px X 60px|YES|Path to logotipo/image. Eg: someurl.com/mylogo.png
| &nbsp;&nbsp;&nbsp;&nbsp;thumbnail                  ||||	Image which represent the provider, like logo, symbol, etc.
| &nbsp;&nbsp;**contents**                 |node||YES|
| &nbsp;&nbsp;&nbsp;&nbsp;content                    |node||YES|For each content
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;refId                    |text|45|YES|Reference ID. Must be unique for all versions of content. Eg: AB22 . The refid represents the content in all languages and versions available.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;refIdVersion             |text        |    45 |YES     | Reference ID Version. Represent version of content. Eg: AB22 English v1, AB22 Spanish v2, etc.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;firstPublicationDate     |date (YYYY-mm-dd) || No (highly recommended)|First publication date. Creation date to help versions control.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lastMofidificationDate 	|	date (YYYY-mm-dd)	||	No (highly recommended)	|	First publication date. Creation date to help versions control.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;title 					          |	text				||	YES						|	Do not must be unique, but highly recommended
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;subtitle 				        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;locale 					        |	text				||							|	Language of content. Better if uses the language-Country format. Eg: en-US, fr-FR, etc.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;description 				      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;summary 					        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;type						          |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;subtype					        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;runtime					        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;url						          |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;alternateUrl				      |	url					||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;thumbnail				        |	url					||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;audience					        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;objectives				        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;duration					        |	int					||							|	In minutes Eg. 10,20,etc.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;course					          |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**tags**					        |						  ||							|	One or more
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tag(1)					        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tag(n)					        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**themes**				        |						  ||							|	One or more themes, can be separated by comma(,). If the content have a categorization, this place can be used for it.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;theme(1)				        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;theme(n)				        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**authors**				      |						  ||							|	One or more
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;author					        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;firstname			      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lastname				      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;email				        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;jobtitle				      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;company				      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;phone				        |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;authorThumbnail		  |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;customGuid			      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;competencies			    |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;authorThumbnail		  |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**biographies**		  |						  ||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;biography			    |						  ||							|	One or more
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;locale			      |						  ||							|	Language of biography. Better if uses the language-Country format. Eg: en-US, fr-FR, etc.
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;biographyFull	  |						  ||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;biographyShort	  |						  ||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;additionalData			      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;videoSubtitles			      |						  ||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;subtitle (en-US)		    |	text				||							|	Eg: legend_en-US.srt
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;subtitle (fr-FR)		    |	text				||							|	Eg: legend_fr-FR.srt
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;audiences				        |						  ||							|	One or more audience, can be separated by comma (,). Eg: Leader, Senior manager, project manager, etc
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;audience (1)			      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;audience (2)			      |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;level					          |	int					|	  1,2 or 3  |	|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scoreinprogress			    |	text				||							|
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;detailedcontent			    |	text				||							|

How do I send my metadata and my content ?
--------------------------

We will provide you with an SFTP server where you will send the content and the metadata files.

### Naming Scheme

#### Catalog
The catalog should be created with the date of the creation in the name following this convention:

	catalog-YYYYmmddHHMMSS.xml

Example : catalog-20160403132400.xml for a catalog created on the 3rd of April 2016, at 1:24:00 pm. The hours need to be in the 24h format.
	
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

It's always better to use simplify the name of the assets to use only basic characters:
	[a-zA-Z0-9_\-\.]

How do I test my catalog.xml ?
------------------------------

We've included a simple python tool to test that

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



