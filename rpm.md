# preparation
> sudo dnf install -y rpm-build rpmdevtools

# e.g.
```bash
# prepare the build dirs
# fist kind -- by basic command
mkdir rpmbuild
cd rpmbuild/
mkdir -p RPMS/noarch SOURCES SPECS SRPMS

# second kind -- by specific command
rpmdev-setuptree
# in reality, we won't be using the SRPMS directory
```

# preamble
consit of much of the information you see with command
> rpm -qi [package name]
- each datum is a single line

# %description
The `%description` section of the spec file contains a description of the RPM
package.

# %prep
The `%prep` section is a script that is the first one executed during the build
process. This script is not executed during the installation of the package.
