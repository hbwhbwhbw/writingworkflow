# Summary

This is a guide to the tools I use to make research and writing easier. My initial goal was to have a system I could use to keep track of a growing library of PDF documents, easily organized and accessible from multiple devices. I also wanted to minimize the time I spent formatting citations while I wrote. This system allows me to access my research and writing from a work computer, home computer, or tablet, to keep annotations and notes in a centralized repository, and to largely* avoid the painful task of bluebooking.

*not entirely

## Hardware

I use a 2015 Macbook Pro and a 2020 iPad Air. I do the vast majority of my writing on the Macbook and the vast majority of my reading of articles and other PDF documents on the iPad. I read books mostly in hard copy but occasionally on my Kobo ereader.

## Software

I combine Zotero (a reference manager), Scrivener (a very robust word processor), Dropbox (cloud storage), Pandoc (a tool that transforms documents), and plain text Markdown files (for notetaking). I also use Hazel (an automated organizing tool) to set rules for certain kinds of downloads that don't go into my Zotero library.

## Research

Confession: I am a PDF hoarder. I download lots and lots of PDFs; mostly law review articles, but lots of scholarship in other disciplines as well.  The longer I've been writing and doing research, the more I realized that I needed a robust reading practice, and that it was helpful to have a disciplined note-taking system to synthesize what I was reading. I do not read everything I download, and I definitely don't read them as soon as I download them.

Enter Zotero, which allows me to amass an enormous library of PDFs, store them in a Dropbox repository accessible across platforms and devices, and automatically rename and reorganize them. For information on how I configure Zotero to do this, see below.

Zotero isn't perfect; the browser support for Westlaw* is nonexistent, and for SSRN it's just bad. It works okay, but not great, for legal cases in Google Scholar. But for scholarship I access through a library database such as HeinOnline, JStor, etc., I can simply click the Zotero browser extension and it automatically downloads the article with all the associated metadata, renames the file, and sticks it in a subfolder organized by author and date. I also use Zotero to keep track of links to news articles relevant to my research.

This means I mostly download law review articles from HeinOnline; Zotero's browser support is very good for Hein, and I can be sure that the pagination is correct. I use JStor and other databases for scholarship in other fields.

I don't keep everything in Zotero. I download reports, letters, and SSRN preprints to my downloads folder, and use Hazel to automatically move those items into designated folders within Dropbox.

*I am curious whether Zotero plays better with Casetext, but I have not yet tried it. If Casetext had decent Zotero-readable metadata associated with legal decisions, it would be a gamechanger for me.

## Notetaking

- Zettelkasten - I am playing around with using a Zettelkasten system to keep track of more abstract notes. I keep notes in plain text files (one note per file) and use [Obsidian](https://obsidian.md/) to visualize the links between them.
- Annotating PDFs
  - I use PDFExpert on the iPad to mark up PDFs.
  - When I'm done, I extract the annotations to Zotero and tag the item as "read."
  - All the highlights and  margin notes I've made get pulled into a separate annotations entry linked to the original item that is then searchable within my Zotero database.

## Writing

I use Scrivener for writing. I find myself playing too much with formatting in Word, and I don't like having to scroll up and down to the relevant sections of an article when I'm in the editing process. I like the modular approach of Scrivener. I also like being able to store primary source documents (e.g., securities disclosures, draft legislation, etc.) in the "research" folder of a particular project. When I present a piece at a workshop, I also keep my presentation notes and any feedback in Scrivener.

## Nerd content starts here!!

I write in what is called "pandoc flavored markdown." [Inspired by Dave Smith](https://davepwsmith.github.io/academic-scrivener-howto/), I set up Scrivener to look like a "plain text" editor.

## Citations

As Dave Smith documents, you can use Zotero to copy "quick cites" and paste into Scrivener when you're citing. I use [Smith's script](https://github.com/davepwsmith/zotpick-applescript) to launch a "quick citation picker" window within Scrivener.

### Zotero setup

1. Install Zotero for desktop, as well as relevant browser plugins (the support for Heinonline is particularly good).
2. Install the Zotfile plugin. There are two options for storing your Zotero files - as attachments locally stored within Zotero, or as links to documents stored elsewhere. I chose the latter, and use a Dropbox folder to store all my Zotero PDFs.
   - I organize my Dropbox folder by author, and within that by publication year. (I do this by ticking the box in Zotfile Preferences that says "Use subfolder defined by" and fill in "/%a/%y")
   - If you already have a giant folder of PDFs, you can drag them into Zotero and it will extract information from them (not perfectly, but works pretty well for articles downloaded from library databases).

  If you have a giant folder of SSRN downloads, I cannot help you with that. In my opinion, it's best just to start a new system moving forward rather than agonizing over everything that already exists. Onward!

   - In Zotfile preferences>>Renaming rules, untick "Use Zotero to Rename." I use what I think is the default format: {%a_}{%y_}{%t}, which yields a renamed file: Jackson_Foucault Welles_2015_Hijacking #MYNYPD.pdf.

## Set up your bibliography file.

3. Install Betterbibtex plugin.
2. In Preferences>>Better BibTex>>Citation Key Format, update all citekeys to [auth:lower][year]
3. Go to File>>Export library. Choose Betterbiblatex format. Tick "keep updated." Export to Dropbox/Markdown or wherever you want to keep your Zotero library.
4. In Zotero, set Preferences >> Better BibTeX >> Automatic export >> Automatic export: On change. This keeps the .bib file updated with any new references that you add in Zotero.

## Set up your stylesheets.

7. I use a slightly tweaked version of bluebook-law-review.csl, it works better for me than juris-m's indigobook for law review style.

# STOP HERE IF YOU DON'T WANT TO MESS WITH MARKDOWN, PANDOC, OR AUTOMATING YOUR CITATIONS.

If you stop here, congratulations! You just set yourself up with a nice library that is organized by author and year, accessible from multiple devices, and can be used to keep all your notes on readings in searchable form! If you want to try to automate your citations and formatting using pandoc, read on.

8. Download [zotpick-pandoc](https://github.com/davepwsmith/zotpick-applescript/blob/master/zotpick-pandoc%20for%20Scrivener.applescript) and compile it as an application.

6. Under Scrivener Preferences>>General>>Citations, choose [zotpick-pandoc](https://github.com/davepwsmith/zotpick-applescript/blob/master/zotpick-pandoc%20for%20Scrivener.applescript) as bibliography manager.
   1. troubleshooting zotpick: got error that it didn't have ability to send keystrokes, had to tweak in Privacy>Accessibility settings
   2. Tweaked script to generate square brackets
         ```set theReference to do shell script "/usr/bin/curl 'http://127.0.0.1:23119/better-bibtex/cayw?format=pandoc&brackets=true' 2>/dev/null; exit 0"```

6. Cmd-Y in Scrivener launches quick citation picker, which generates citekeys.

## Compiling

11. Compile your Scrivener draft to Multimarkdown: File>>Compile>>select: Compile for: Multimarkdown. Under settings, **uncheck "Convert rich text to Markdown" box.**

12. Use pandoc to convert to .docx format.

    - Use tweaked version of bluebook-law-review.csl saved in /dropbox/markdown. ^[~/Desktop/repos/csl/bluebook-law-review.csl.]

    ```
    sh pandoc filename.md --bibliography ~/Dropbox/repos/zotero.bib
    --csl ~/Dropbox/repos/csl/bluebook-law-review.csl
    --reference-doc template.docx
    -o filename.docx; open filename.docx
    ```

13. You can create a docx with your preferred styles and use that as a template to define Word styles (headings, typeface, etc.)

#### Documentation I found helpful
https://www.simonlindgren.com/notes/2019/11/15/setup-for-writing-in-markdown-citing-with-zotero-and-publishing-with-pandoc

https://davepwsmith.github.io/academic-scrivener-howto/

https://pandoc.org/MANUAL.html
