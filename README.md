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
    	</contents>
    </catalog>```

Content
------- 

How do I test my catalog.xml ?
------------------------------

We've included a simple python tool to test that

### Requirements

To use our tool you need to make sure that you have python-lxml installed:

	$> pip install -r requirements.txt

### Check my catalog

Once you have the requirements installed you can check your datafeed like this:

	$> python ./check.py my_catalog.xml


