## Notetaking
- Zettelkasten - I am playing around with using a Zettelkasten system to keep track of more abstract notes.
- Annotating PDFs
  - I use PDFPen (?) on the iPad to mark up PDFs.
  - When I'm done, I extract the annotations to Zotero.
  - I also convert the notes to their own markdown file and save them.

## Writing

## Citation management
### Zotero
1. Install Zotero for desktop, as well as relevant browser plugins (the support for Heinonline is particularly good).
2. Install Zotfile. There are two options for storing your Zotero files - as attachments locally stored within Zotero, or as links to documents stored elsewhere. I chose the latter, and use a Dropbox folder to store all my Zotero PDFs.
   - I organize my Dropbox folder by author, and within that by publication year.
   - If you already have a giant folder of PDFs, you can drag them into Zotero and it will extract information from them.
   -
2. Install Betterbibtex plugin.
2. update all citekeys to authyear
3. export library in Betterbiblatex format to dropbox/Markdown. tick "keep updated."
4. In Zotero, set Preferences >> Better BibTeX >> Automatic export >> Automatic export: On change. This keeps the .bib file updated with any new references that you add in Zotero.
5. Set [zotpick-pandoc](https://github.com/davepwsmith/zotpick-applescript/blob/master/zotpick-pandoc%20for%20Scrivener.applescript) as citation manager in Scrivener
   1. troubleshooting zotpick: got error that it didn't have ability to send keystrokes, had to tweak in Privacy>Accessibility settings
   2. Tweaked script to generate square brackets
         ```set theReference to do shell script "/usr/bin/curl 'http://127.0.0.1:23119/better-bibtex/cayw?format=pandoc&brackets=true' 2>/dev/null; exit 0"```

6. Cmd-Y in Scrivener launches quick citation picker, which generates citekeys.

## Compiling

1. Compile to Multimarkdown: **uncheck "Convert rich text to Markdown" box.**
2. Use pandoc to convert to .docx format.

    - Use tweaked version of bluebook-law-review.csl saved in /dropbox/markdown. ^[~/Desktop/repos/csl/bluebook-law-review.csl.]

    ``` sh pandoc filename.md --bibliography zotero.bib
    --csl ~/Desktop/repos/csl/bluebook-law-review.csl
    --reference-doc template.docx
    -o filename.docx; open filename.docx
    ```

  3. Use reference doc to define Word styles

#### documentation
https://www.simonlindgren.com/notes/2019/11/15/setup-for-writing-in-markdown-citing-with-zotero-and-publishing-with-pandoc
