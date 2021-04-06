## OpenSCAP (Open Security Content Automation Protocol)

## Scanning against STIGs
CentOS 8
```bash
# Build and run the container
make go

# View security profiles
ls -1 /usr/share/xml/scap/ssg/content/ssg-*-ds.xml 
oscap info /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml

# Scan
oscap xccdf eval --profile xccdf_org.ssgproject.content_profile_stig --results-arf /home/arf.xml --report /home/report.html /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml
```

UBI 7
```bash
# Build from source
yum install wget -y
version=1.3.4
wget https://github.com/OpenSCAP/openscap/releases/download/${version}/openscap-${version}.tar.gz
tar -xzpf openscap-${version}.tar.gz
cd openscap-${version}
mkdir -p build
yum install cmake dbus-devel GConf2-devel libacl-devel libblkid-devel libcap-devel libcurl-devel libgcrypt-devel libselinux-devel libxml2-devel libxslt-devel libattr-devel make openldap-devel pcre-devel perl-XML-Parser perl-XML-XPath perl-devel python-devel rpm-devel swig bzip2-devel gcc-c++ libyaml-devel xmlsec1-devel xmlsec1-openssl-devel
cd build/
cmake ../
make
make install
```

## Todo
- UBI containers are unable to find OpenSCAP package
- Unable to find CentOS 8 SCAP content
- Run OpenSCAP within its own container and "target" other containers
    - https://github.com/OpenSCAP/openscap/blob/maint-1.3/docs/manual/manual.adoc#scanning-remote-and-virtual-machines-or-containers

## References
https://www.open-scap.org/getting-started/

https://github.com/OpenSCAP/openscap
https://github.com/OpenSCAP/openscap/blob/maint-1.3/docs/manual/manual.adoc
https://github.com/ComplianceAsCode/content
