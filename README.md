# Custom Page List

by Heiner Gassen  
<https://github.com/hgassen/custom-page-list>

Based on the work of

* Philipp Urlich (somatonic): PageListImageLabel  
<https://github.com/somatonic/PageListImageLabel>
* Adam Spruijt (adamspruijt): PageListBetterLabels  
<https://github.com/adamspruijt/PageListBetterLabels>


## Introduction

Custom Page List is a module for ProcessWire 2.2+, <http://processwire.com>. 
It lets you easily customize the page list (tree) in the admin section.


## Features

* Customize styles and separators used in the page list
* Display custom labels for each field
* Display image thumbnails
* Display formatted dates
* Display info from related models (e.g. title field of related pages)
* Display on/off checkbox as "Yes/No" (ready for translation)
* Define output filter(s) for each field


## Installation

Copy the folder MarkupCustomPageList to /site/modules. Install via the modules management page in ProcessWire.

Requires the core module ProcessPageList that is installed by default.


## Configuration

As usual, you define the fields to display in the page list on the settings page of the core module ProcessPageList.

MarkupCustomPageList tries to make as few assumptions as possible about the way you want to display your page list.
Here are some of them -- if needed, we might make them configurable in a future version.

* The first field to display is considered the primary field. Only its value is displayed (not its name).
* All other fields are considered secondary fields.
* If an image field is defined, the thumbnail of the image is displayed at the beginning of the line (in front of the primary field).
* If an image field with several images is defined, only the first image is displayed.
* If several image fields are defined, only the (first) image of the first field is displayed

On the module's settings page, you can configure the following options:

* Set class names for primary and secondary fields. The default classes are defined in the module's CSS file.
* Set separators
* Set image options
* Set datetime format for "created" and "modified" fields. (For all other datetime fields, the output format is taken from the field's definition.)
* Show an additional link to edit the template associated with a page (superuser only)
* Set custom parameters (see next section)


## Custom parameters

Custom parameters allow you to do the following:

* Display a field label or not
* Replace the standard field label with your own
* Set output filters for each field value

Custom parameters for each field have the following format (everything must be on one line):

	fieldname=new fieldname|filtername1=filter value1|filtername2=filter value2 ...
	
Parameter name and values are separated by "=", parameters are separated by "|".


### First parameter: fieldname=new fieldname

Replace the default label (field name) by your own label:
    
	template.name=Template
	
Leave new fieldname empty to display no fieldname at all:

	template.name=
	

### All other parameters: filtername=filter value

Right now, there are two output filters available:

The **truncate** filter truncates the field value after a given number of characters and appends an ellipsis (...).

	truncate=25

The **style** filter applies the given style(s) to the field value:

	style=color:#cc3333;font-weight:bold
	
A complete line with custom parameters might look like this:

	body=Content|truncate=25|style=color:#cc3333;font-weight:bold
	
It would show the first 25 characters of the body field (labeled "Content") in bold style and red color.


## Download

Source code is available at <https://github.com/hgassen/custom-page-list>.


## License

CustomPageList is distributed under the GNU/GPL v2. See the included file `LICENSE.txt` for more information.


## Version History

Version 1.0.3 - January 27, 2013

* Fix for Fieldtype Page if specific field is requested

Version 1.0.2 - January 26, 2013

* Delete generated thumbs of type cropimage if parent image is deleted

Version 1.0.1 - Janaury 25, 2013

* Change generated thumbnail names to comply with PW best practice

Version 1.0 - January 21, 2013

* Initial release

