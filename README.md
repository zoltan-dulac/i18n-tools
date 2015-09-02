# i18n-tools
Tools to help with your i18n/l10n projects.  Right now, this is specific to do English/French translations (since I live in Canada), but this repo will be updated to handle more than two locales.


## What's contained in this repo

Right now, this repo contains two files:

1. **xls2tab** - a shell script that will convert an Excel spreadsheet (or any other spredsheet that can be opened up by [LibreOffice](http://libreoffice.org) to a tab delimited file.
2. **xls2prop** - a shell script that will convert a specifically formatted spreadsheet to a [Java Property File](https://en.wikipedia.org/wiki/.properties) (again, this spreadsheet must be in a format readable by LibreOffice).  Right now, the format should be:

  | A | B | C |
  | --- | --- | --- |
  | Java Property name | English Copy | French Translation |

  (Note: this format *will* change when this script supports more than two locales).

## Dependencies

- [LibreOffice](http://libreoffice.org)
- a UNIX-like environment (if you are using Windows, you should be able to run this with [Cygwin](http://cygwin.com).

