# poutils

This project provides utility programs for .po file (gettext portable object file).

## potmerge

potmerge reads gettext portable object template data from the given files,
merges the entries by msgid,
and finally writes the resulting data to the standard output.
This utility program might be useful when you run xgettext for an individual source file.
