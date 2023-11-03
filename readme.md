# Edith, a template for minimal editions
## C21 Editions Project, jointly funded by the Irish Research Council and UKRI-AHRC (grant numbers IRC/W001489/1 and AH/W001489/1)
### Edith is inspired by [Ed](https://minicomp.github.io/ed/). The technical foundation is [CETEIcean](https://github.com/TEIC/CETEIcean).
### [Town by Annemarie Ní Churreáin & Rich Gilligan using this very repository](https://mkrzmr.github.io/town/)

#### Introduction
The aim of Edith is to provide an easy-to-use and sustainable template for digital editions.
Easy-to-use means anybody can copy or download this repository, change a few files and links and have their own digital edition. Basic knowledge of HTML will be enough to get started.
Sustainable means the edition is a flat-file system and does not rely on complex-to-maintain frameworks. All that is is needed is a HTML5 browser and client-side JavaScript. Because of this simplicity, the edition can be hosted free of cost here on GitHub, or on any other web hosting provider with minimal system requirements.
The edition is also sustainable in that it is easy to archive (simply download all files in this repository) and reproduce. 

#### How to get started
1. Download or copy this repository.
2. Locate the "xml" folder. This is where your xml files will go. You do not need to make any changes to the files (See the technical section below), as long as your files are TEI-compliant they should work without modifications.
3. Locate the "poetry" folder - rename the folder as you like -. In this folder, find the "template.html" file. Now all you need to do is to change the link on line 12 `../xml/LinkToYourXmlHere.xml` so that it links to one of your xml files in the "xml" folder.
4. Save the template.html under a new name.
5. Repeat this process for each xml file you want to include in your edition.
6. Now, change the links in the index.html file to create a menu that links to the html files you created in step 5.
7. Finally, deploy to GitHub-Pages or any plain web server of your choice. On Linux, simply run `npx http-server -c-1` on the main folder to spin up a local server for testing and troubleshooting.

#### Customize the rendering of your XML files
Any TEI-element used in the source file will be converted into an HTML-element with the prefix "tei-". For example, the TEI element <lg> will become `tei-lg`. The supplied CSS file has default rules to style most of the commonly used elements, but it is easy to add or modify rules. 

#### Background
While the original [Ed](https://minicomp.github.io/ed/) is a Jekyll theme and uses Markdown to edit texts, [CETEIcean](https://github.com/TEIC/CETEIcean) uses JavaScript to transform an XML-Document into an HTML-Document. 
The created HTML output is then styled with CSS. This leads to a series of advantages for scholarly use, beyond the simplicity mentioned in the introduction:
* No change to the XML files is needed. This is probably the biggest advantage for scholarly use. The files do not need to be re-created in Markdown or changed in any way.
* Using CSS to control layout gives a lot of flexibility. Our template should cover most TEI-compliant texts, and additional styling can easily be applied. For example, some of the texts in this edition feature multiple levels of indentation and     extra      word     space. An xslt transformation approach could only achieve this through changing the source file. In this template, content and representation are clearly divided.
* Because we are effectively working in HTML, it is easy to add "extra" content alongside the encoded text, without touching the XML file. For example, the "return" button used in this template is just a few lines of HTML and CSS. In the same way, a footer or other content can easily be added on.

#### Adding features
This template was deliberately kept simple to increase accessibility. A few ideas came up during the work on this edition, that are added here as pointers for anyone looking to expand their edition:
1. Display the TEI-header information.
Using CSS, most of the header information is hidden using `display:none`. Change this to `display:block` to show as much or as little of the header elements as you need. CETEIcean uses custom JS behaviours to show or hide the entire header, but Edith manages the page rendering through CSS alone. 

2. Having a Faksimile or scan alongside the transcription.
Recommended to add the information to the XML file in a <div>

>           <figure>
>                            <graphic url="/town/town.jpeg" xml:id="sample1"/>
>                            <p>[Title Page Verso Image]</p>
>          </figure>


Then use CSS to align the <figure> element with the rest of the text.

3. Add public annotations.
Easiest to use would be a public tool such as (Hypothes.is)[https://web.hypothes.is/]. Include the JS snippet to your HTML pages to enable annotations.

4. Automatically build the menu.
This was tried, but ultimately would have made the template more complex with little gain for most users. If you are looking to automatically update the menu, it is probably best to use PHP. Beware this will make your setup more complex.
