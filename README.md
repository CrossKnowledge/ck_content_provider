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


How do I test my catalog.xml ?
------------------------------

We've included a simple python tool to test that

### Requirements

To use our tool you need to make sure that you have python-lxml installed:

	$> pip install -r requirements.txt

### Check my catalog

Once you have the requirements installed you can check your datafeed like this:

	$> python ./check.py my_catalog.xml



