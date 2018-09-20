OMERO User Help Guides
======================

**OME User Help Site**

The OME User Guides website consists of pages with user guides for clients or
workflows.

**Platform**

The web site is developed and maintained using Jekyll and GitHub.

The HTML, configuration, layout and CSS files are in this repository. The
zipped PDF archives of previous versions and other resources are available from the OME Downloads site:
[https://downloads.openmicroscopy.org/help/](https://downloads.openmicroscopy.org/help/)
in subfolders: pdfs, archives and resources.

**Editing Process**

Jekyll inserts the page content into the template held in the default layout
file and builds the site.

To do any editing or updating you will need to install and use Jekyll with any
dependencies required. Instructions are on the Jekyll site.

Once the Ruby gem and Jekyll are installed, the local server needs to be
started and set to watch for updates using:

    $ cd ome-help/
    $ jekyll serve --watch

You can then edit, add, commit and push as usual using your git repository.

When a file has been edited locally, the new version will be instantly visible
at:

[http://localhost:4000/ome-help/](http://localhost:4000/ome-help/)

**Jekyll version**

Jekyll 3 [changed the way layout metadata is handled](https://jekyllrb.com/docs/upgrading/2-to-3/#layout-metadata).
As of version 3.1.2, support for the former behaviour was withdrawn, breaking
the website menu and requiring a fix which was not backwards compatible.
Therefore, you should ensure you have Jekyll version 3.1.2+ to work with this
repository.

**GitHub**

Clone this repository and create a branch to use for your work. You should use
your local Jekyll server to review changes and when ready, commit and push to
your branch. Your changes will be viewable at
[https://your-github-username.github.io/ome-help/](https://your-github-username.github.io/ome-help/)
if you use 'gh-pages' as your
branch. If you do this, it is best to delete the cloned 'gh-pages'
branch from the main repo and then create your own which tracks the 'master'
branch. **Do not use your 'gh-pages' branch to track the 'gh-pages' branch
of the original repository as we will not accept PRs opened against this
branch.**

When work is complete and the changes pushed, a pull request should be opened
against the 'master' branch of the main repo. This will be picked up by the
OME CI system and the updated page will be viewable for review at
[https://help.staging.openmicroscopy.org/](https://help.staging.openmicroscopy.org/) once the build has been run.
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
appropriate field in default.html for: page title, menu ID,
description metadata and text and whether to display the Current OMERO Version number. 
Pages can be written in HTML or Markdown.
They have a short header and then the page content in the form:

    /---
    layout: default
    title: Getting Started with OMERO.insight
    menu-id: l1-quickstart
    description: Metadata header for each page.
    version:
        - yes
    redirect_from:
      - /old-page.html
    /---
    <page content>

These are used as follows:

- layout: indicates the .html layout file to be used for the page.
- title: appears in the banner at the top of the page.
- menu-id: indicates the level and place in the navigation structure.
- description: Metadata header for each page.
- version: flag to show/not show the OMERO version number bottom left in the page header banner.
- redirect_from: /name of page - allows redirect to this page from page that has been superceded/replaced by this one. 

**CSS**

Straight forward CSS and (very minimal) inline styling is used.

**Images**

The screenshots/other images for each section are generated from the
appropriate .graffle file (in resources/). The Omnigraffle canvas is exported
as a JPEG, 75% scaled, at 150 dpi.

The Omnigraffle files are named for the section in the style of the screenshot
image name - e.g. sharingData for the “Sharing Data” section and each canvas
named for the image identifier e.g. ScreenShot1. So the name of an image
generated from that canvas will be "sharingDataScreenShot1.jpg”.

A few canvases have different, selectable layers allowing a number of images
to be generated from the single canvas.

**Process to update for version changes**

The following elements need to be changed to the new version number:

For all:

- the index.html page (currently 1 occurrence in page text)
- the appropriate menu entry(s) in default.html (only number releases i.e. 5 -> 6)
- the version number in two screenshots in the relevant .graffle file -
  Downloads and Zips. Note: the version numbers are added as editable text in
  the Version 5.x Omnigraffle canvases. The new versions of the screenshots
  are saved with the same name over-writing the previous version.
- the new versions of the screenshots need to be placed in the images/ folder.

**Specific Version Pages**

For Version 5.x:

- getting-started-5.html - the title and the description in the page header +
Downloads and Zips screenshots
- importing-5.html - the title and the description in the page header +
Downloads and Zips screenshots
- index page - latest release version number (forth paragraph), and any
references in the “New Features” section

Links need to be updated in:

- resources.html - version number and size updated
- previous.html - links to previous version ZIP archive added (can be pasted from previous version listed in resources.html)

**Licensing**

© Copyright Open Microscopy Environment 2000 - 2018.
All material is covered by the
[Creative Commons Attribution 3.0 Unported License](https://creativecommons.org/licenses/by/3.0/).
You are free to share or adapt content as long as you credit the Open
Microscopy Environment. The exception to this is the screenshots and videos
which can only be used for non-commercial purposes.