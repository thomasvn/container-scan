## OpenSCAP (Open Security Content Automation Protocol)

## Scanning against STIGs
Fedora 34
```bash
# Build and run the container
make go

# View security profiles
ls -1 /usr/share/xml/scap/ssg/content/ssg-*-ds.xml 
oscap info /usr/share/xml/scap/ssg/content/ssg-fedora-ds.xml

# Scan
profile=xccdf_org.ssgproject.content_profile_ospp
stream=/usr/share/xml/scap/ssg/content/ssg-fedora-ds.xml
oscap xccdf eval --profile $profile --results-arf /home/arf.xml --report /home/report.html $stream

# Generate a fix
oscap xccdf generate fix --template urn:xccdf:fix:script:sh --profile $profile --output /home/remed2script.sh --fetch-remote-resources --skip-valid $stream
```

CentOS 8
(NOTE: CentOS [does not currently have a STIG](https://github.com/ComplianceAsCode/content/issues/3743))
```bash
# Build and run the container
make go

# View security profiles
ls -1 /usr/share/xml/scap/ssg/content/ssg-*-ds.xml 
oscap info /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml

# Scan
oscap xccdf eval --profile xccdf_org.ssgproject.content_profile_stig --results-arf /home/arf.xml --report /home/report.html /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml
```

<!--
NOTE: Working with UBI often means dealing with RedHat subscription hurdles and yum repo limitations

UBI 7
```bash
# Download the package and install
curl -O http://mirror.centos.org/centos/8-stream/AppStream/x86_64/os/Packages/openscap-scanner-1.3.4-5.el8.x86_64.rpm
yum install --downloadonly openscap-scanner-1.3.4-5.el8.x86_64.rpm
```

UBI 7
```bash
# BUILD FROM SOURCE
# Clone Repo
yum install -y git
git clone --recurse-submodules https://github.com/OpenSCAP/openscap.git
cd openscap

# Install dependencies
yum install -y cmake dbus-devel GConf2-devel libacl-devel libblkid-devel libcap-devel libcurl-devel libgcrypt-devel libselinux-devel libxml2-devel libxslt-devel libattr-devel make openldap-devel pcre-devel perl-XML-Parser perl-XML-XPath perl-devel python-devel rpm-devel swig bzip2-devel gcc-c++ libyaml-devel xmlsec1-devel xmlsec1-openssl-devel

cd build/
cmake ../
make
make install
```
-->


## Todo
- UBI find a way to download OpenSCAP.
- Run OpenSCAP within its own container and "target" other containers
    - https://github.com/OpenSCAP/openscap/blob/maint-1.3/docs/manual/manual.adoc#scanning-remote-and-virtual-machines-or-containers


## References
- https://www.open-scap.org/getting-started/
- https://github.com/OpenSCAP/openscap
- https://github.com/OpenSCAP/openscap/blob/maint-1.3/docs/manual/manual.adoc
- https://github.com/ComplianceAsCode/content
- https://access.redhat.com/articles/4238681
