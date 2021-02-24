# koha-layout2pagesdinde.pm
Print orders from koha library management system as german DIN formated letter.

# Installation
Copy the file layout2pagesdinde.pm in the folder "/usr/share/koha/lib/Koha/pdfformat/".

Then 2 changes are necessary.
1. koha needs to know that a new layout is available and allowed.
2. The new layout must be stored in the admin interface and made selectable.


## Make the layout available
You need to change the file: /usr/share/koha/intranet/cgi-bin/acqui/basketgroup.pl

Find the line:
my @valid_pdfformats = qw(pdfformat::layout3pages pdfformat::layout2pages pdfformat::layout3pagesfr pdfformat::layout2pagesde);

and change ist to 
my @valid_pdfformats = qw(pdfformat::layout3pages pdfformat::layout2pages pdfformat::layout3pagesfr pdfformat::layout2pagesde **pdfformat::layout2pagesdinde**);


## Make the layout selectable
You ned to change /usr/share/koha/intranet/htdocs/intranet-tmpl/prog/**xx-XX**/modules/admin/preferences/acquisitions.pref for every language (I.e. XX-XX for german de-DE)

Exeample for german language:
choices:
  pdfformat::layout2pages: Englisch, 2-seitig
  pdfformat::layout2pagesde: Deutsch, 2-seitig
  pdfformat::layout3pages: Englisch, 3-seitig
  pdfformat::layout3pagesfr: Französisch, 3-seitig
pref: OrderPdfFormat

must expanded to:
choices:
  pdfformat::layout2pages: Englisch, 2-seitig
  pdfformat::layout2pagesde: Deutsch, 2-seitig
  **pdfformat::layout2pagesdin: DIN(de), 2-seitig**
  pdfformat::layout3pages: Englisch, 3-seitig
  pdfformat::layout3pagesfr: Französisch, 3-seitig
pref: OrderPdfFormat

## Alternative installation
Alternatively, the file can be renamed to replace an existing file in the named directory. 
Then the package name must be adjusted in the first line.

package Koha::pdfformat::**layout2pagesdinde**
