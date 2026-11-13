Rebuild usb_modeswitch from RHEL 9 SRPMs
Many Realtek USB Wi-Fi adapters initially enumerate as a virtual CD-ROM drive (for Windows drivers) and require usb_modeswitch to flip into Wi-Fi mode. Since Red Hat removed usb_modeswitch and usb_modeswitch-data in RHEL 10, include these steps in your GitHub Pull Request or Issue description so other RHEL 10 users know how to get their USB dongle recognized.

    Install RPM build tools.
dnf install -y rpm-build dnf-utils gcc make libusb1-devel systemd-rpm-macros

Download the RHEL 9 source RPMs. Fetch usb_modeswitch and usb_modeswitch-data from CentOS Stream 9 or Rocky Linux 9 repositories.
rpmbuild --rebuild usb_modeswitch-*.el9.src.rpm
rpmbuild --rebuild usb_modeswitch-data-*.el9.src.rpm
dnf localinstall -y ~/rpmbuild/RPMS/x86_64/usb_modeswitch-*.el10.x86_64.rpm ~/rpmbuild/RPMS/noarch/usb_modeswitch-data-*.el10.noarch.rpm
