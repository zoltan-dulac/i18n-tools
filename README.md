# z4n
Tools to help with your i18n/l10n projects using [Java .properties files](https://en.wikipedia.org/wiki/.properties). The name is a bad joke based on the author's name, [Zoltan](http://www.useragentman.com).


## What's contained in this repo

This package contains the following BASH scripts.

1. **removeEntitiesInProp** - a shell script that will take a *.properites file and convert all the property values to UTF-8.  This conversion applies to [numeric entities](https://en.wikipedia.org/wiki/Numeric_character_reference), [named entities](https://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references) and ['\u'-escaped Unicode characters](https://mathiasbynens.be/notes/javascript-escapes#unicode). It also cleans up the formatting of the property name and value by putting one (and only one) space before and after the = symbol separating the two.  
2. **xls2tab** - a shell script that will convert an Excel spreadsheet (or any other spredsheet that can be opened up by [LibreOffice](http://libreoffice.org) to a tab delimited file).
3. **xls2prop** - a shell script that will convert a specifically formatted spreadsheet to a [Java Property File](https://en.wikipedia.org/wiki/.properties) (again, this spreadsheet must be in a format readable by LibreOffice).  Right now, the format should be:

  | A | B | C | D | E | ... |
  | --- | --- | --- | --- | ---  | --- |
  | # all lines that begin with a '#' are ignored | | | |
  | # The row that begins with "# Locales" contains the locale names | | | |
  | # column A is the property variable name | | | |
  | # columns B and greater are the values in the different locales | | | |
  | # Locales | en_CA | fr_CA | ru_RU | ja_JP | ... |
  | form.header.name | Name | Nom | Имя | 名前 | ... |
  | form.header.address | Address | Addresse | Адрес | 住所 | ... |
  
  Things to keep in mind:
  
  1. All rows that have a `#` as the first character in the `A` cell will act as a comment and will not be extracted to the property file.)
  2. The row that is an a cell labelled "# Locales" will contain the locales to be translated to.  I usually use [IETF language tags](https://en.wikipedia.org/wiki/IETF_language_tag) for the locale names, but you can technically use whatever strings you want.

  This repo also contains an `example` directory that contains an example spreadsheet and sample output from the spreadsheet. The resultant `properties` file was created using the following command:

```
xls2prop example-spreadsheet.xls example
```

The first parameter is the name of the input spreadsheet.  The second parameter (`example`) is the prefix for the outfile names (in this case, the script will output the translations to `example_en_CA.properties`, `example_fr_CA.properties`, `example_ru_RU.properties` and `example_ja_JP.properties`).

## Dependencies

- [LibreOffice](http://libreoffice.org)
- [uni2ascii](http://billposer.org/Software/uni2ascii.html)
- a UNIX-like environment (if you are using Windows, you should be able to run this with [Cygwin](http://cygwin.com)).

## Notes

- These scripts have been tested under OSX and Microsoft  Windows using Cygwin.  It should work using Linux with no modifications (please log an issue at https://github.com/zoltan-dulac/i18n-tools/ if there are any issues).
