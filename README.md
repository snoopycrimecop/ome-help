OMERO User Help Guides
======================

**OME User Help Site**

The OME User Guides website consists of pages with user guides for clients or
workflows.

**Workflow**

The standard workflow is to write and layout sections in Word using images
generated from annotated screenshots in Omnigraffle. A PDF is then generated
from the Word document and an HTML page constructed using the text from the
Word document.

**Platform**

The web site is developed and maintained using Jekyll and GitHub.

The HTML, configuration, layout and CSS files are in this repository. The
PDFs, zipped PDF archives of previous versions and the Word and Omnigraffle
resources are in the main OME Downloads repository:
[http://downloads.openmicroscopy.org/help/](http://downloads.openmicroscopy.org/help/)
in subfolders: pdfs, archives and resources.

To do any editing or updating you will need to install and use Jekyll with any
dependencies required. Instructions are on the Jekyll site.

**GitHub**

Clone this repository and create a branch to use for your work. You should use
your local Jekyll server to review changes and when ready, commit and push to
your branch. Your changes will be viewable at
http://your-github-username.github.io/ome-help/ if you use 'gh-pages' as your
branch. If you do this, it is best to delete the cloned 'gh-pages'
branch from the main repo and then create your own which tracks the 'master'
branch. **Do not use your 'gh-pages' branch to track the 'gh-pages' branch
of the original repository as we will not accept PRs opened against this
branch.**

When work is complete and the changes pushed, a pull request should be opened
against the 'master' branch of the main repo. This will be picked up by the
OME CI system and the updated page will be viewable for review at
[http://help.staging.openmicroscopy.org/](http://help.staging.openmicroscopy.org/) once the build has been run.
The PR will be posted in the OME stand-up document for review.

**Web Site Structure**

The structure is as follows:

- the raw HTML pages for processing (the ones that are edited)
- images/ - images used in chapters and logos etc.
- _layout/default.html - provides the menu order, the page layout and the headers for the pages
- _includes/navigation.html - provides the code for constructing the menu
- js/ - contains the Javascript files for the site
- css/ - contains the CSS files
- config.yml - YAML configuration file
- 404.html - a custom error page that redirects to the home page

Once you have built the site locally your git repository will also have:

- _site/ - containing the generated HTML pages etc. for serving

**Navigation and Menus**

The navigation bar and menu items are in default.html. The menu is hard-coded
because this is the only way to maintain the desired order with Jekyll.

**Page Files**

Individual files for the pages contain the variables to be inserted in the
appropriate field in default.html for: page title, menu ID, PDF name and
description metadata and text. Pages and can be written in HTML or Markdown.
They have a short header and then the page content in the form:

/---
layout: default
title: Getting Started with OMERO.insight Version 5.0.3
menu-id: l1-quickstart
pdfs:
    - getting-started-5.pdf
description: Metadata header for each page.
/---
<page content>

**CSS**

Straight forward CSS and (very minimal) inline styling is used.

**Editing Process**

Jekyll inserts the page content into the template held in the default layout
file and builds the site.

Once the Ruby gem and Jekyll are installed, the local server needs to be
started and set to watch for updates using:

$ jekyll serve --watch

You can then edit, added, commit and push as usual using your git repository.

When a file has been edited locally, the new version will be instantly visible
at:

http://localhost:4000/ome-help/

Once changes have been pushed to your 'gh-pages' branch, they take a short
time to build, and then will be visible on GitHub at:

[http://your-github-username.github.io/ome-help/](http://your-github-username.github.io/ome-help/)

**Notes on Current Workflow**

The Word and Omnigraffle files for the sections are all in the /resources folder at:
[http://downloads.openmicroscopy.org/help/](http://downloads.openmicroscopy.org/help/)

**Images**

The screenshots/other images for each section are generated from the
appropriate .graffle file (in resources/). The Omnigraffle canvas is exported
as a JPEG, 75% scaled, at 150 dpi. In the Word document the images are
generally resized to 16 cm width (if required) and centred. A small minority
are scaled down further to balance them with other images.

The Omnigraffle files are named for the section in the style of the screenshot
image name - e.g. sharingData for the “Sharing Data” section and each canvas
named for the image identifier e.g. ScreenShot1. So the name of an image
generated from that canvas will be "sharingDataScreenShot1.jpg”.

A few canvases have different, selectable layers allowing a number of images
to be generated from the single canvas.

**Word Documents**

The Word documents have hidden text below each image identifying the image,
size and alignment in Markdown syntax. In most cases bold type is also
indicated in hidden text - **Text**. This helps when marking up the text from
the Word document in HTML.

**PDFs**

The PDFs for each section are generated from the appropriate .doc file for
that chapter (in resources/)

**Process to update for version changes**

The following elements need to be changed to the new version number:

For all:

- the index.html page (currently 3 occurrences in page text)
- the appropriate menu entry(s) in default.html
- the “title:" in relevant HTML pages - getting-started-5.html and 
  importing-5.html or getting-started-4.html and importing-4.html
- the heading in the relevant Word .doc file
- the version number in two screenshots in the relevant .graffle file -
  Downloads and Zips. Note: the version numbers are added as editable text in
  the Version 5.x Omnigraffle canvases. The new versions of the screenshots
  are saved with the same name over-writing the previous version.
- the new versions of the screenshots need to be placed in the images/ folder.
- new versions of the PDF need to be generated
- a new ZIP archive file for all the PDFs for that version generated i.e one
for  5.x or one for 4.4.x (with the appropriate sections for the  new versions
included).
- the previous version ZIP archive file becomes the reference archive for that
version - linked to from the ”Previous” page.

Note:
Only the OMERO client and related workflow PDFs are included in this archive.
Other PDFs such as virtual-microscope.pdf and editor.pdf are not included in
the archive, so copies of previous versions should be archived as appropriate.

**Specific Version Pages**

For Version 5.x:
getting-started-5.html - the title and the description in the page header +
Downloads and Zips screenshots
importing-data-4.html- the title and the description in the page header

For Version 4.4.x:
getting-started-4.html- the title and the description in the page header +
Downloads and Zips screenshots
importing-data-4.html- the title and the description in the page header

index page - latest release version number (forth paragraph), and two
references in the “New Features” section

Links need to be updated in:

resources.html - version number and size updated
previous.html - links to previous version ZIP archive added

**Licensing**

© Copyright Open Microscopy Environment 2000 - 2014.
All material is covered by the
[Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/).
You are free to share or adapt content as long as you credit the Open
Microscopy Environment. The exception to this is the screenshots and videos
which can only be used for non-commercial purposes.