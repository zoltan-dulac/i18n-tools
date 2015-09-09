# i18n-tools
Tools to help with your i18n/l10n projects.  Right now, this is specific to do English/French translations (since I live in Canada), but this repo will be updated to handle more than two locales.


## What's contained in this repo

Right now, this repo contains two executable files:

1. **xls2tab** - a shell script that will convert an Excel spreadsheet (or any other spredsheet that can be opened up by [LibreOffice](http://libreoffice.org) to a tab delimited file).
2. **xls2prop** - a shell script that will convert a specifically formatted spreadsheet to a [Java Property File](https://en.wikipedia.org/wiki/.properties) (again, this spreadsheet must be in a format readable by LibreOffice).  Right now, the format should be:

  | A | B | C | D | E | ... |
  | --- | --- | --- | --- | ---  | --- |
  | # all lines that begin with a '#' are ignored | | | |
  | # The row that begins with "# Locales" contains the locale names | | | |
  | # column A is the property variable name | | | |
  | # columns B and greater are the values in the different locales | | | |
  | | | | | |
  | # Locales | en_CA | fr_CA | ru_RU | ja_JP | ... |
  | form.header.name | Name | Nom | Имя | 名前 | ... |
  | form.header.address | Address | Addresse | Адрес | 住所 | ... |

  (Note: this format *will* change when this script supports more than two locales).  All rows that have a `#` as the first character in the `A` cell will act as a comment and will not be exproted to the property file.)
  
This repo also contains an `example` directory that contains an example spreadsheet and sample output from the spreadsheet.  The out `properties` file was created using the following command:

```
xls2prop example-spreadsheet.xls example
```

The first parameter is the name of the input spreadsheet.  The second parameter (`example`) is the prefix for the outfile names (in this case, the script will output the translations to `example_en.properties`	 and `example_fr.properties`).

## Dependencies

- [LibreOffice](http://libreoffice.org)
- a UNIX-like environment (if you are using Windows, you should be able to run this with [Cygwin](http://cygwin.com).

## Notes

- This repo will eventually work across operating systems, but right now it has only been tested under OSX.  If you are using this under another OS (e.g. Linux, Windows, etc), you should change xls2tab and change the `SOFFICE` variable to the location of the `soffice` binary on your machine.  I will eventually have the script autodetect this when I have done my cross-OS testing.
