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
 
	```<?xml version="1.0" encoding="UTF-8"?>
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
	      <refIdVersion>OJMH390</refIdVersion>
	      <title>How to Give a Constructive Feedback</title>
	      <locale></locale>
	      <summary>Feedback can help staff members to progress and develop their skills provided it is given in the right way. This session will show you how to identify common errors and the principles of constructive feedback.</summary>
	      <type>Interactive</type>
	      <subtype>Session</subtype>
	      <runtime>scorm</runtime>
	      <thumbnail></thumbnail>
	      <url>http://path/to/object/OJMH390.zip</url>
	      <tags>
		<tag>SKILLS_MANAGEMENT</tag>
		<tag>TRAINING</tag>
		<tag>EVALUATION</tag>
		<tag>LEARNING</tag>
	      </tags>
	      <themes>
		<theme>DEVELOPING_AUTONOMY</theme>
	      </themes>
	      <duration>30</duration>
	      <audiences></audiences>
	      <level>1</level>
	      <objectives></objectives>
	      <additionalData></additionalData>
	    </content>
    </contents>```

Content
-------
<table class="wikitable">
<tr>
<th> Field
</th>
<th> Type
</th>
<th> Size
</th>
<th> Required
</th>
<th> Description
</th></tr>

<tr>
<td>
<dl><dt>provider</dt></dl>
</td>
<td>
</td>
<td>
</td>
<td>
</td>
<td>
<p>Informations block about content provider
</p>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd>name</dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> Provider name (Comercial name)
</td></tr>

<tr>
<td>
<dl><dd><dl><dd>description</dd></dl></dd></dl>
</td>
<td> text
</td>
<td> 256
</td>
<td>
</td>
<td> Short description about company, content, etc
</td></tr>

<tr>
<td>
<dl><dd><dl><dd>picture</dd></dl></dd></dl>
</td>
<td> text
</td>
<td> suggestion: 250px X 60px
</td>
<td>
</td>
<td> Path to logotipo/image. Eg: someurl.com/mylogo.png
</td></tr>

<tr>
<td>
<dl><dd><dl><dd>thumbnail</dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> Image which represent the provider, like logo, symbol, etc.
</td></tr>

<tr>
<td>
<dl><dt>contents</dt></dl>
</td>
<td>
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dt><dl><dd><dl><dd>content</dt></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>refId</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td> 45
</td>
<td> YES
</td>
<td> Reference ID. Must be unique for all versions of content. Eg: AB22 . The refid represents the content in all languages and versions available.
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>refIdVersion</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td> 45
</td>
<td> YES
</td>
<td> Reference ID Version. Represent version of content. Eg: AB22 English v1, AB22 Spanish v2, etc.
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>firstPublicationDate</dd></dl></dd></dl></dd></dl>
</td>
<td> date (YYYY-mm-dd)
</td>
<td>
</td>
<td> No (highly recommended)
</td>
<td> First publication date. Creation date to help versions control.
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>lastMofidificationDate</dd></dl></dd></dl></dd></dl>
</td>
<td> date (YYYY-mm-dd)
</td>
<td>
</td>
<td> No (highly recommended)
</td>
<td> Content Release date. Versions control. If no possible, set refIdVersion to tell us about the content version.
</td></tr>
<tr>
<td>
<dl><dd><dl><dd><dl><dd>title</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td> YES
</td>
<td> Do not must be unique, but highly recommended
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>subtitle</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>locale</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> Language of content. Better if uses the language-Country format. Eg: en-US, fr-FR, etc.
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>description</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>summary</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>type</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> Url, PDF, Scorm, etc.
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>subtype</dd></dl></dd></dl></dd></dl>
</td>
<td> texte
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>url</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>alternateUrl</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>thumbnail</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>audience</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>objectives</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>duration</dd></dl></dd></dl></dd></dl>
</td>
<td> int
</td>
<td>
</td>
<td>
</td>
<td> mins
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>course</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dt><dl><dd><dl><dd><dl><dd>tags</dt></dl></dd></dl></dd></dl></dd></dl>
</td>
<td>
</td>
<td>
</td>
<td>
</td>
<td> One or more tags, can be separated by comma(,)
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>tag<sub>1</sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>tag<sub>n</sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dt><dl><dd><dl><dd><dl><dd>themes</dt></dl></dd></dl></dd></dl></dd></dl>
</td>
<td>
</td>
<td>
</td>
<td>
</td>
<td> One or more themes, can be separated by comma(,). If the content have a categorization, this place can be used for it.
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>theme<sub>1</sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>theme<sub>n</sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dt><dl><dd><dl><dd><dl><dd>authors</dt></dl></dd></dl></dd></dl></dd></dl>
</td>
<td>
</td>
<td>
</td>
<td>
</td>
<td> One or more authors, can be separated by comma (,)
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>author</dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td>
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>firstname</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>lastname</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>email</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>jobtitle</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>company</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>phone</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>authorThumbnail</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>customGuid</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd><dl><dd>competencies</dd></dl></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>additionalData</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dt><dl><dd><dl><dd><dl><dd>videoSubtitles</dt></dl></dd></dl></dd></dl></dd></dl>
</td>
<td>
</td>
<td>
</td>
<td>
</td>
<td> One or more subtitles, can be separated by comma(,)
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>subtitle <sub>en-US<sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> Eg: legend_en-US.srt
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>subtitle <sub>fr-FR<sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> Eg: legend_fr-FR.srt
</td></tr>

<tr>
<td>
<dl><dt><dl><dd><dl><dd><dl><dd>audiences</dt></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> One or more audience, can be separated by comma (,). Eg: Leader, Senior manager, project manager, etc
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>audience<sub>1</sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd><dl><dd>audience<sub>n</sub></dd></dl></dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>level</dd></dl></dd></dl></dd></dl>
</td>
<td> int
</td>
<td> 1, 2 or 3
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>scoreinprogress</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td>
</td></tr>

<tr>
<td>
<dl><dd><dl><dd><dl><dd>detailedcontent</dd></dl></dd></dl></dd></dl>
</td>
<td> text
</td>
<td>
</td>
<td>
</td>
<td> Eg: Management strategy
</td></tr>

</table>

How do I test my catalog.xml ?
------------------------------

We've included a simple python tool to test that

### Requirements

To use our tool you need to make sure that you have python-lxml installed:

	$> pip install -r requirements.txt

### Check my catalog

Once you have the requirements installed you can check your datafeed like this:

	$> python ./check.py my_catalog.xml


