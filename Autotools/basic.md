#  Autotools
- Autoconf
- Automake
- Libtool

# autoconf
- autoconf
- autoreconf
- autoheader
- autoscan
- autoupdate
- ifnames
- autom4te
## autoreconf
`configure.ac` file
`bootstrap.sh`
- -i    autoreconf will bootstrap a project into a distributable state by adding
        misssing files that are recomended or required by GNU for proper source
        projects. `ChangeLog`, `INSTALL`, `README`, `AUTHORS` so on
## autoheader
`config.h.in`
The utility generate a C/C++ compatible header fie template from various 
constructs in `configure.ac` file. 

When the end user executes config, the configuration script generates `config.h`
from `config.h.in`.
