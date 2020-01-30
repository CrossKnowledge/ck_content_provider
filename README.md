CrossKnowledge - Content Provider Data Feed
===========================================

This resource is for content providers in order to integrate with our
content management system.

Supported content formats
---------------------

* Audio in *mp3* format
* Downloadable documents: *pdf*, *docx*, *xlsx*, images, etc;
* Interactive content: SCORM packages(1.2 and 2004) and AICC packages, in *zip* format;
* Reading documents: *pdf*, *docx*, *doc*, *txt*;
* Video Files: *mp4* or *flv* format, with subtitles in *srt* or *vtt* format;
* External website URLs

**NOTE:**
* Multi SCO is not supported for SCORM content. In case you have a longer course, it should be splitted into multiple zip files with a single SCO.
* As the contents are imported in a CrossKnowledge learning path, it's not an issue.
* There are some conditions for the content, specially for SCORM, audios and videos. Click [here](https://developers.crossknowledge.com/third-party-prerequisites.html) to more information.

Metadata and presentation
-------------------------

The metadata should be presented as an XML file. You'll find the XML Schema [here](catalog_import.xsd).

You can check a example of a complete XML file [here](catalog_example.xml).

The encoding for XML file should be UTF-8 without BOM (Byte Order Map).

XML Description
---------------

This is the architecture of the XML:

| Node                                                          | Required | Allow Multiple Nodes | Details
| :-------                                                      | :----    | :---                 | :---
| catalog                                                       | YES      | NO                   | The main node
| catalog > provider [(see details here)](#providers)           | YES      | NO                   | The provider details
| catalog > contents [(see details here)](#contents)            | YES      | YES - content        | The contents of the specified provider

Each table above describes one node of XML.

#### Providers

| Field Name                |Type        | Required | Details
| :-------                  | :----      | :---     |:---  
| description               | text       | YES      | Short description about provider.
| name                      | text       | YES      | Name of the provider
| defaultThumbnail          | **node**   | YES      | [See details here](#default-thumbnail)
| picture                   | url        | YES      | Provider picture. <br/>**File type:** JPG or PNG (no transparency); <br/> **Resolution:** <br/> Widht: min 220px, max 719px; <br/> Height: min 60px, max 300px;

#### Contents

This node allows how much content you need, just define ``<content>`` for each one of them. There are some [notes](#supported-content-formats) that needs to be considered.

| Field Name                | Type     | Required | Details
| :-------                  | :----    | :---     |:---
| locale                    | text     | YES      | Language of content. Better if uses the language-Country format. Eg: en-US, fr-FR, pt-BR, etc. [See supported language codes](#supported-language-codes)
| refId                     | text     | YES      | refID stands for "Reference ID", which becomes the learning resource ID code. Must be unique for all versions of content. Eg: AB22 . The refId represents the content in all languages and versions available. Max size: 45.
| refIdVersion              | text     | YES      | refIdVersion stads for "Reference ID Version", which becomes the learning resource version ID code. Max size: 45
| runtime                   | text     | YES      | "CKLM_SCORM" => SCORM<br/> "CKLM_VIDEO" => Video<br/> "CKLM_AICC" => AICC <br/> "CKLM_FILE" => Reading document, PDF, Image, Office document<br/> "link_lo_guid" => website, URL<br/>See [Supported Content Formats](#supported-content-formats) for more information.
| subtype                   | text     | YES      | If the content is categorized, put category here
| title                     | text     | YES      | Unicity not required but highly recommended
| type                      | text     | YES      | "a" => Audio<br/>"d" => Document to download<br/>"p" => Image<br/>"i" => Interactive content (SCORM)<br/>"r" => Reading document<br/>"v" => Video<br/>"w" => website, URL
| url                       | text     | YES      | The URL of the content, preferred to be at high definition video. The content will be downloaded just once.
| additionalData            | text     | NO       | Additional information related to the content.
| alternateUrl              | url      | NO       | The URL of the content, preferred to be at low definition video. The content will be downloaded just once.
| archiveList               | int      | NO       | The content in the archive list is considered outdated and by default is no longer available for licenses. If the owner wants the content can be available again. Use 0 if the content isn't in archive list and 1 if it is.
| audience                  | text     | NO       | Eg: Leader, Senior Manager, Project Manager.
| authors                   | **node** | NO       | [See details here](#authors)
| blackList                 | int      | NO       | The content will not be available for the licenses use. Use 0 if the content isn't in black list and 1 if it is.
| duration                  | int      | NO       | The duration of the content, in minutes. Eg: 10, 20, 130.
| level                     | int      | NO       | Complexity level of the content:<br/>1 = novice<br/>2 = intemediate<br/>3 = advanced
| objectives                | text     | NO       | Content purpose or objective. Single paragraph, without break-lines.
| publicationDate           | date     | NO       | **Format: YYYY-mm-dd** / First publication date. Creation date to help versions control.
| publisher                 | text     | NO       | Name of the publisher of the contents.
| scoreinprogress           | text     | NO       | Content SCORM option to save progress score variable (value = Y or N, which means "Yes" or "No")
| subtitle                  | text     | NO       | The content's subtitle
| summary                   | text     | NO       | Explain this content. Single paragraph, without break-lines.
| summaryShort              | text     | NO       | Explain this content but in few words
| tags                      | **node** | NO       | [See details here](#tags)
| thumbnail                 | url      | NO       | Content thumbnail.<br/>**Format**: *PNG*, *JPG* or *SVG*.<br/>**Resolution**:<br/>Widht: min 220px, max 640px;<br/>Height: min 60px, max 300px;
| themes                    | **node** | NO       | [See details here](#themes)
| videoSubtitles            | **node** | NO       | [See details here](#video-subtitles)

#### Authors

This node allows as many nodes as needed, just define ``<author>`` for each learning resource.

**Important**: Fields inside *author* node should follow the order listed above

| Field Name      | Type     | Required | Details
| :-------        | :----    | :---     |:---
| lastName        | text     | YES      | The author's last name
| authorThumbnail | text     | NO       | Author thumbnail<br/>**Format**: *PNG*, *JPG* or *SVG*.<br/>**Resolution**:<br/>Widht: min 220px, max 640px;<br/>Height: min 60px, max 300px;
| biographies     | **node** | NO       | [See details here](#biographies)
| company         | text     | NO       | The author's company
| customGuid      | text     | NO       | Unique identifier for Author. If ommited, system create one based on provider and author names
| email           | text     | NO       | Author's email
| firstName       | text     | NO       | The author's first name
| jobTitle        | text     | NO       | Author's job title
| phone           | text     | NO       | Author's phone number for contact

#### Biographies

This node allows as many nodes as needed, just define ``<biography>`` for each author.

**Important**: Fields inside *biography* node should follow the order listed above

| Field Name      | Type     | Required | Details
| :-------        | :----    | :---     |:---
| locale          | text     | YES      | Language of biography. Max size: 5. [See supported language codes](#supported-language-codes)
| biographyShort  | text     | YES      | Few words about the author. Single paragraph, without break-lines.
| biographyFull   | text     | NO       | Describe with more details the biography. Single paragraph, without break-lines.

#### Default Thumbnail

| Field Name      | Type     | Required | Details
| :-------        | :----    | :---     |:---
| content         | url      | YES      | Image that represents the provider, like a logo or a symbol. <br> **File type:** JPG or PNG with 640px x 360px resolution.

#### Tags

This node allows as many nodes as needed, just define ``<tag>`` for each content.

| Field Name | Type  | Required | Details
| :-------   | :---- | :---     |:---
| tag        | text  | YES      | Metadata on a piece of content. A tag is a term that describes the content, by calling out related topics and synonyms for terms in the content title, for example. Content can have a wide set of tags.

#### Themes

This node allows as many nodes as needed, just define ``<theme>`` for each learning resource.

| Field Name | Type  | Required | Details
| :-------   | :---- | :---     |:---
| theme      | text  | YES      | This element can be used for a more detailed categorization using character ">". Eg: Main Theme > SubTheme > ...<br/> Metadata on a piece of content. A theme is one term that tries to summarize the content as a whole or call out the one topic that the content is about. Usually content does not have a lot of themes, mostly one, sometimes 2.

#### Video Subtitles

This node allows as many nodes as needed, just define ``<videoSubtitle>`` for each learning resource. Multiple language subtitles can be included.

| Field Name    | Type  | Required | Details
| :-------      | :---- | :---     |:---
| videoSubtitle | text  | YES      | Format: *SRT* or *VTT*.

How to send my metadata and my content
--------------------------

For uploading your content and metadata files, please request your CrossKnowledge contact. We can then decide to provide you with an SFTP server for you to use for uploading the files.

### Naming Scheme

#### Catalog

The catalog should be created with the date of the creation in the name following this convention:

 catalog-YYYYmmddHHMMSS.xml

**Example:** *catalog-20190321150659.xml* for a catalog created on the March 21th 2019 at 15:06:59.

Our system will process the files and put them in a backup directory afterwards.

#### Reference to the content

The references in the XML file should be relative to the position of the catalog.

If you have an directory structure like this

```
FTP/
    - catalog-20191104132400.xml
    - SCORM/
        - first_course.zip
        - second_course.zip
    - Img/
        - course_1_thumbnail.jpg
        - course_2_thumbnail.jpg
```

Then your catalog should look like that:

```xml
 ...
 <content>
  <title>Course 1 title here</title>
  <thumbnail>Img/course_1_thumbnail.jpg</thumbnail>
  <url>SCORM/first_course.zip</url>
  ...
 </content>
 <content>
  <title>Title of the Second course</title>
  <thumbnail>Img/course_2_thumbnail.jpg</thumbnail>
  <url>SCORM/second_course.zip</url>
  ...
 </content>
 ...
```

It's recommended to simplify the name of the assets to use only basic characters:
 [a-zA-Z0-9_\-\.]

Alternatively, an absolute URL (<http://domain/path/to/file.png>) can be provided for the following fields:

* Provider Picture
* Provider Thumbnail
* Content Url
* Content Thumbnail
* Author Thumbnail

**NOTE**: The URLs that specify images and documents will be downloaded and will not be requested anymore.
If you need to update this content, please update the URL and import again.

#### Supported Language codes

Our content management system support the following language codes:

> af-ZA am-ET ar-AE ar-BH ar-DZ ar-EG ar-IQ ar-JO ar-KW ar-LB ar-LY ar-MA ar-OM ar-QA ar-SA ar-SY ar-TN ar-YE as-IN ba-RU be-BY bg-BG bn-BD bn-IN bo-CN br-FR ca-ES co-FR cs-CZ cy-GB da-DK de-AT de-CH de-DE de-LI de-LU dv-MV el-GR en-AU en-BZ en-CA en-GB en-IE en-IN en-JM en-MY en-NZ en-PH en-SG en-TT en-US en-ZA en-ZW es-AR es-BO es-CL es-CO es-CR es-DO es-EC es-ES es-GT es-HN es-MX es-NI es-PA es-PE es-PR es-PY es-SV es-US es-UY es-VE et-EE eu-ES fa-IR fi-FI fo-FO fr-BE fr-CA fr-CH fr-FR fr-LU fr-MC fy-NL ga-IE gd-GB gl-ES gu-IN he-IL hi-IN hr-BA hr-HR hu-HU hy-AM id-ID ig-NG ii-CN is-IS it-CH it-IT ja-JP ka-GE kk-KZ kl-GL km-KH kn-IN ko-KR ky-KG lb-LU lo-LA lt-LT lv-LV mi-NZ mk-MK ml-IN mn-MN mr-IN ms-BN ms-MY mt-MT nb-NO ne-NP nl-BE nl-NL nn-NO oc-FR or-IN pa-IN pl-PL ps-AF pt-BR pt-PT rm-CH ro-RO ru-RU rw-RW sa-IN se-FI se-NO se-SE si-LK sk-SK sl-SI sq-AL sv-FI sv-SE sw-KE ta-IN te-IN th-TH tk-TM tn-ZA tr-TR tt-RU ug-CN uk-UA ur-PK vi-VN wo-SN xh-ZA yo-NG zh-CN zh-HK zh-MO zh-SG zh-TW zu-ZA

How to test my catalog.xml
--------------------------

This repository contains a simple python 2 tool to test it.

To use our tool you need to make sure that you have python-lxml installed. You can install using the following command:

```bash
pip install -r requirements.txt
```

Once you have the requirements installed you can check your datafeed like this:

```bash
python ./check.py my_catalog.xml
```
