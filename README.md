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
| + **provider**                 |node||YES|Informations block about provider|
| + + name                       |text|||
| + + description                |text|256|YES|	Short description about company, content, etc|
| + + picture                    |absolute url|suggestion: 250px X 60px|YES|Path to logotipo/image. Eg: someurl.com/mylogo.png
| + + thumbnail                  ||||	Image which represent the provider, like logo, symbol, etc.
| + **contents**                 |node||YES|
| + + content                    |node||YES|For each content
| + + + refId                    |text|45|YES|Reference ID. Must be unique for all versions of content. Eg: AB22 . The refid represents the content in all languages and versions available.
| + + + refIdVersion             |text        |    45 |YES     | Reference ID Version. Represent version of content. Eg: AB22 English v1, AB22 Spanish v2, etc.
| + + + firstPublicationDate     |date (YYYY-mm-dd) || No (highly recommended)|First publication date. Creation date to help versions control.
| + + + lastMofidificationDate 	|	date (YYYY-mm-dd)	||	No (highly recommended)	|	First publication date. Creation date to help versions control.
| + + + title 					          |	text				||	YES						|	Do not must be unique, but highly recommended
| + + + subtitle 				        |	text				||							|
| + + + locale 					        |	text				||							|	Language of content. Better if uses the language-Country format. Eg: en-US, fr-FR, etc.
| + + + description 				      |	text				||							|
| + + + summary 					        |	text				||							|
| + + + type						          |	text				||							|
| + + + subtype					        |	text				||							|
| + + + runtime					        |	text				||							|
| + + + url						          |	text				||							|
| + + + alternateUrl				      |	url					||							|
| + + + thumbnail				        |	url					||							|
| + + + audience					        |	text				||							|
| + + + objectives				        |	text				||							|
| + + + duration					        |	int					||							|	In minutes Eg. 10,20,etc.
| + + + course					          |	text				||							|
| + + + **tags**					        |						  ||							|	One or more
| + + + + tag(1)					        |	text				||							|
| + + + + tag(n)					        |	text				||							|
| + + + **themes**				        |						  ||							|	One or more themes, can be separated by comma(,). If the content have a categorization, this place can be used for it.
| + + + + theme(1)				        |	text				||							|
| + + + + theme(n)				        |	text				||							|
| + + + **authors**				      |						  ||							|	One or more
| + + + + author					        |	text				||							|
| + + + + + firstname			      |	text				||							|
| + + + + + lastname				      |	text				||							|
| + + + + + email				        |	text				||							|
| + + + + + jobtitle				      |	text				||							|
| + + + + + company				      |	text				||							|
| + + + + + phone				        |	text				||							|
| + + + + + authorThumbnail		  |	text				||							|
| + + + + + customGuid			      |	text				||							|
| + + + + + competencies			    |	text				||							|
| + + + + + authorThumbnail		  |	text				||							|
| + + + + + **biographies**		  |						  ||							|
| + + + + + + biography			    |						  ||							|	One or more
| + + + + + + + locale			      |						  ||							|	Language of biography. Better if uses the language-Country format. Eg: en-US, fr-FR, etc.
| + + + + + + + biographyFull	  |						  ||							|
| + + + + + + + biographyShort	  |						  ||							|
| + + + additionalData			      |	text				||							|
| + + + videoSubtitles			      |						  ||							|
| + + + + subtitle (en-US)		    |	text				||							|	Eg: legend_en-US.srt
| + + + + subtitle (fr-FR)		    |	text				||							|	Eg: legend_fr-FR.srt
| + + + audiences				        |						  ||							|	One or more audience, can be separated by comma (,). Eg: Leader, Senior manager, project manager, etc
| + + + + audience (1)			      |	text				||							|
| + + + + audience (2)			      |	text				||							|
| + + + level					          |	int					|	  1,2 or 3  |	|
| + + + scoreinprogress			    |	text				||							|
| + + + detailedcontent			    |	text				||							|



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


