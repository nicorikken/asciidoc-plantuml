# asciidoc-plantuml
Automatically exported from code.google.com/p/asciidoc-plantuml

# Wiki

## UFT_encoding

By default, PlantUML use the default charset of your platform, which may or may not be UTF-8, in such case the plugin will output wrong characters. The workaround is to add -charset UTF-8 parameter in acplantuml.py script. This would be:

        try:
            cmd = 'java -jar %s/plantuml.jar -charset UTF-8 -T%s -quiet "%s" > "%s"' % (
                  filter_path, self.options.format, infile, outfile)
            self.systemcmd(cmd)
        finally:
            os.chdir(saved_cwd)  

I will add encoding parameter in next release Issue1.

## SVG output to PDF
It is possible to have vector graphics in PDF. Take a look here (http://groups.google.com/group/asciidoc/msg/d28a5683d88eb108) for solution. It appears all you need is inkscape and dblatex > 0.3.2 (april 2011) installed.

It is now possible to use SVG in PDF with dblatex > 0.3.2 (april 2011). Inkscape is used as external tool to convert SVG into PDF.

For example, graphviz diagrams are converted into SVG, then inkscape is used to convert the SVG files into PDF files, then the PDF files are integrated as images into the PDF output by dblatex.

(This is part of imagedata.py, and not documented in the user manual yet)
http://dblatex.cvs.sourceforge.net/viewvc/dblatex/dblatex/lib/dbtexmf/core/imagedata.py?view=log

It is working pretty well.

## Usage
Introduction

You can add UML diagrams in your AsciiDoc document using [plantuml] block. PlantUML uses @startuml/@enduml lines, these lines will be automatically appended so you don't need to use them, but you can if you like to or if you copy your PlantUML code from somewhere else.

Filter available in download page contains it's own copy of PlantUML.jar. If you want to use your own PlantUML, please replace one in the zip file. 
