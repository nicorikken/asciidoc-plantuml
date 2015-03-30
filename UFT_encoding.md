By default, PlantUML use the default charset of your platform, which may or may not be UTF-8, in such case the plugin will output wrong characters.
The workaround is to add -charset UTF-8 parameter in acplantuml.py script.
This would be:

```
        try:
            cmd = 'java -jar %s/plantuml.jar -charset UTF-8 -T%s -quiet "%s" > "%s"' % (
                  filter_path, self.options.format, infile, outfile)
            self.systemcmd(cmd)
        finally:
            os.chdir(saved_cwd)  
```

I will add encoding parameter in next release [Issue1](http://code.google.com/p/asciidoc-plantuml/issues/detail?id=1).