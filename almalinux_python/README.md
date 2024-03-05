# AlmaLinux (latest) with Python example

This example contains an Apptainer "definition" file [`alma_python.def`](./alma_python.def) which builds a container with the latest version of AlmaLinux (at time of writing 9.3), and a virtualenv with Numba and which runs the Numba enabled [Python Example](https://github.com/UCL-RITS/pi_examples/tree/master/python3_numba_pi_dir).

This can be built on Myriad without being `root`!

## Instructions:

Clone this repository onto your home area on Myriad (other RC systems are available). Change directory to this directory and then add Apptainer to your environment:

```shell
$ module load apptainer
```

This will set up some temporary directories - for example a cache directory in your Scratch space.

### Build:

```
$ apptainer build --fakeroot alma_python.sif alma_python.def
INFO:    User not listed in /etc/subuid, trying root-mapped namespace
INFO:    The %post section will be run under fakeroot
WARNING: 'nodev' mount option set on /run/user/55052, it could be a source of failure during build process
INFO:    Starting build...
Getting image source signatures
Copying blob sha256:28130cb29ede9c7eb632516608f6be44c01d736736eb9f03846fb16c819426ae
Copying config sha256:0b005789c921fe92059e0844745a0daa0b7b592e51d763102b83a77c2850f159
Writing manifest to image destination
Storing signatures
2024/03/05 12:33:21  info unpack layer: sha256:28130cb29ede9c7eb632516608f6be44c01d736736eb9f03846fb16c819426ae
2024/03/05 12:33:21  warn xattr{usr/bin/write} ignoring ENOTSUP on setxattr "user.rootlesscontainers"
2024/03/05 12:33:21  warn xattr{/run/user/55052/uccaoke_apptainerbuild/build-temp-2419102521/rootfs/usr/bin/write} destination filesystem does not support xattrs, further warnings will be suppressed
INFO:    Copying ./pi.py to /pi.py
INFO:    Running post scriptlet
+ chmod 644 /pi.py
+ dnf update -y
AlmaLinux 9 - AppStream                         4.6 MB/s | 9.1 MB     00:01    
AlmaLinux 9 - BaseOS                            7.0 MB/s | 4.7 MB     00:00    
AlmaLinux 9 - Extras                             47 kB/s |  17 kB     00:00    
Dependencies resolved.
================================================================================
 Package              Architecture Version                   Repository    Size
================================================================================
Upgrading:
 gnutls               x86_64       3.7.6-23.el9_3.3          baseos       1.0 M
 libxml2              x86_64       2.9.13-5.el9_3            baseos       746 k
 openssl              x86_64       1:3.0.7-25.el9_3          baseos       1.2 M
 openssl-libs         x86_64       1:3.0.7-25.el9_3          baseos       2.1 M
 python3              x86_64       3.9.18-1.el9_3.1          baseos        25 k
 python3-libs         x86_64       3.9.18-1.el9_3.1          baseos       7.3 M
 python3-rpm          x86_64       4.16.1.3-27.el9_3         baseos        64 k
 rpm                  x86_64       4.16.1.3-27.el9_3         baseos       485 k
 rpm-build-libs       x86_64       4.16.1.3-27.el9_3         baseos        87 k
 rpm-libs             x86_64       4.16.1.3-27.el9_3         baseos       306 k
 rpm-sign-libs        x86_64       4.16.1.3-27.el9_3         baseos        19 k
 sqlite-libs          x86_64       3.34.1-7.el9_3            baseos       619 k
 tzdata               noarch       2024a-1.el9               baseos       430 k

Transaction Summary
================================================================================
Upgrade  13 Packages

Total download size: 14 M
Downloading Packages:
(1/13): openssl-3.0.7-25.el9_3.x86_64.rpm       9.9 MB/s | 1.2 MB     00:00    
(2/13): libxml2-2.9.13-5.el9_3.x86_64.rpm       6.0 MB/s | 746 kB     00:00    
(3/13): gnutls-3.7.6-23.el9_3.3.x86_64.rpm      8.2 MB/s | 1.0 MB     00:00    
(4/13): python3-3.9.18-1.el9_3.1.x86_64.rpm     719 kB/s |  25 kB     00:00    
(5/13): python3-rpm-4.16.1.3-27.el9_3.x86_64.rp 3.6 MB/s |  64 kB     00:00    
(6/13): openssl-libs-3.0.7-25.el9_3.x86_64.rpm   19 MB/s | 2.1 MB     00:00    
(7/13): rpm-build-libs-4.16.1.3-27.el9_3.x86_64 7.7 MB/s |  87 kB     00:00    
(8/13): rpm-libs-4.16.1.3-27.el9_3.x86_64.rpm    11 MB/s | 306 kB     00:00    
(9/13): rpm-sign-libs-4.16.1.3-27.el9_3.x86_64. 2.3 MB/s |  19 kB     00:00    
(10/13): sqlite-libs-3.34.1-7.el9_3.x86_64.rpm   20 MB/s | 619 kB     00:00    
(11/13): rpm-4.16.1.3-27.el9_3.x86_64.rpm       3.3 MB/s | 485 kB     00:00    
(12/13): tzdata-2024a-1.el9.noarch.rpm           18 MB/s | 430 kB     00:00    
(13/13): python3-libs-3.9.18-1.el9_3.1.x86_64.r  28 MB/s | 7.3 MB     00:00    
--------------------------------------------------------------------------------
Total                                            20 MB/s |  14 MB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Upgrading        : openssl-libs-1:3.0.7-25.el9_3.x86_64                  1/26 
  Upgrading        : sqlite-libs-3.34.1-7.el9_3.x86_64                     2/26 
  Upgrading        : rpm-4.16.1.3-27.el9_3.x86_64                          3/26 
  Upgrading        : rpm-libs-4.16.1.3-27.el9_3.x86_64                     4/26 
  Upgrading        : rpm-build-libs-4.16.1.3-27.el9_3.x86_64               5/26 
  Upgrading        : rpm-sign-libs-4.16.1.3-27.el9_3.x86_64                6/26 
  Upgrading        : tzdata-2024a-1.el9.noarch                             7/26 
  Upgrading        : python3-3.9.18-1.el9_3.1.x86_64                       8/26 
  Upgrading        : python3-libs-3.9.18-1.el9_3.1.x86_64                  9/26 
  Upgrading        : python3-rpm-4.16.1.3-27.el9_3.x86_64                 10/26 
  Upgrading        : openssl-1:3.0.7-25.el9_3.x86_64                      11/26 
  Upgrading        : libxml2-2.9.13-5.el9_3.x86_64                        12/26 
  Upgrading        : gnutls-3.7.6-23.el9_3.3.x86_64                       13/26 
  Cleanup          : python3-rpm-4.16.1.3-25.el9.x86_64                   14/26 
  Cleanup          : openssl-1:3.0.7-24.el9.x86_64                        15/26 
  Cleanup          : rpm-build-libs-4.16.1.3-25.el9.x86_64                16/26 
  Cleanup          : rpm-sign-libs-4.16.1.3-25.el9.x86_64                 17/26 
  Cleanup          : rpm-4.16.1.3-25.el9.x86_64                           18/26 
  Cleanup          : rpm-libs-4.16.1.3-25.el9.x86_64                      19/26 
  Cleanup          : python3-3.9.18-1.el9_3.x86_64                        20/26 
  Cleanup          : python3-libs-3.9.18-1.el9_3.x86_64                   21/26 
  Cleanup          : tzdata-2023c-1.el9.noarch                            22/26 
  Cleanup          : openssl-libs-1:3.0.7-24.el9.x86_64                   23/26 
  Cleanup          : sqlite-libs-3.34.1-6.el9_1.x86_64                    24/26 
  Cleanup          : libxml2-2.9.13-4.el9.x86_64                          25/26 
  Cleanup          : gnutls-3.7.6-23.el9.x86_64                           26/26 
  Running scriptlet: rpm-4.16.1.3-27.el9_3.x86_64                         26/26 
  Running scriptlet: gnutls-3.7.6-23.el9.x86_64                           26/26 
  Verifying        : gnutls-3.7.6-23.el9_3.3.x86_64                        1/26 
  Verifying        : gnutls-3.7.6-23.el9.x86_64                            2/26 
  Verifying        : libxml2-2.9.13-5.el9_3.x86_64                         3/26 
  Verifying        : libxml2-2.9.13-4.el9.x86_64                           4/26 
  Verifying        : openssl-1:3.0.7-25.el9_3.x86_64                       5/26 
  Verifying        : openssl-1:3.0.7-24.el9.x86_64                         6/26 
  Verifying        : openssl-libs-1:3.0.7-25.el9_3.x86_64                  7/26 
  Verifying        : openssl-libs-1:3.0.7-24.el9.x86_64                    8/26 
  Verifying        : python3-3.9.18-1.el9_3.1.x86_64                       9/26 
  Verifying        : python3-3.9.18-1.el9_3.x86_64                        10/26 
  Verifying        : python3-libs-3.9.18-1.el9_3.1.x86_64                 11/26 
  Verifying        : python3-libs-3.9.18-1.el9_3.x86_64                   12/26 
  Verifying        : python3-rpm-4.16.1.3-27.el9_3.x86_64                 13/26 
  Verifying        : python3-rpm-4.16.1.3-25.el9.x86_64                   14/26 
  Verifying        : rpm-4.16.1.3-27.el9_3.x86_64                         15/26 
  Verifying        : rpm-4.16.1.3-25.el9.x86_64                           16/26 
  Verifying        : rpm-build-libs-4.16.1.3-27.el9_3.x86_64              17/26 
  Verifying        : rpm-build-libs-4.16.1.3-25.el9.x86_64                18/26 
  Verifying        : rpm-libs-4.16.1.3-27.el9_3.x86_64                    19/26 
  Verifying        : rpm-libs-4.16.1.3-25.el9.x86_64                      20/26 
  Verifying        : rpm-sign-libs-4.16.1.3-27.el9_3.x86_64               21/26 
  Verifying        : rpm-sign-libs-4.16.1.3-25.el9.x86_64                 22/26 
  Verifying        : sqlite-libs-3.34.1-7.el9_3.x86_64                    23/26 
  Verifying        : sqlite-libs-3.34.1-6.el9_1.x86_64                    24/26 
  Verifying        : tzdata-2024a-1.el9.noarch                            25/26 
  Verifying        : tzdata-2023c-1.el9.noarch                            26/26 

Upgraded:
  gnutls-3.7.6-23.el9_3.3.x86_64           libxml2-2.9.13-5.el9_3.x86_64        
  openssl-1:3.0.7-25.el9_3.x86_64          openssl-libs-1:3.0.7-25.el9_3.x86_64 
  python3-3.9.18-1.el9_3.1.x86_64          python3-libs-3.9.18-1.el9_3.1.x86_64 
  python3-rpm-4.16.1.3-27.el9_3.x86_64     rpm-4.16.1.3-27.el9_3.x86_64         
  rpm-build-libs-4.16.1.3-27.el9_3.x86_64  rpm-libs-4.16.1.3-27.el9_3.x86_64    
  rpm-sign-libs-4.16.1.3-27.el9_3.x86_64   sqlite-libs-3.34.1-7.el9_3.x86_64    
  tzdata-2024a-1.el9.noarch               

Complete!
+ dnf install -y 'dnf-command(config-manager)'
Last metadata expiration check: 0:00:03 ago on Tue Mar  5 12:33:30 2024.
Dependencies resolved.
================================================================================
 Package                     Arch      Version                  Repo       Size
================================================================================
Installing:
 dnf-plugins-core            noarch    4.3.0-11.el9_3.alma.1    baseos     36 k
Installing dependencies:
 dbus-libs                   x86_64    1:1.12.20-8.el9          baseos    151 k
 python3-dateutil            noarch    1:2.8.1-7.el9            baseos    287 k
 python3-dbus                x86_64    1.2.18-2.el9             baseos    132 k
 python3-dnf-plugins-core    noarch    4.3.0-11.el9_3.alma.1    baseos    246 k
 python3-six                 noarch    1.15.0-9.el9             baseos     36 k
 python3-systemd             x86_64    234-18.el9               baseos     83 k

Transaction Summary
================================================================================
Install  7 Packages

Total download size: 970 k
Installed size: 2.9 M
Downloading Packages:
(1/7): dnf-plugins-core-4.3.0-11.el9_3.alma.1.n 1.4 MB/s |  36 kB     00:00    
(2/7): dbus-libs-1.12.20-8.el9.x86_64.rpm       2.5 MB/s | 151 kB     00:00    
(3/7): python3-dbus-1.2.18-2.el9.x86_64.rpm     2.6 MB/s | 132 kB     00:00    
(4/7): python3-dateutil-2.8.1-7.el9.noarch.rpm  3.1 MB/s | 287 kB     00:00    
(5/7): python3-six-1.15.0-9.el9.noarch.rpm      2.1 MB/s |  36 kB     00:00    
(6/7): python3-systemd-234-18.el9.x86_64.rpm    4.8 MB/s |  83 kB     00:00    
(7/7): python3-dnf-plugins-core-4.3.0-11.el9_3. 4.2 MB/s | 246 kB     00:00    
--------------------------------------------------------------------------------
Total                                           2.1 MB/s | 970 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : python3-systemd-234-18.el9.x86_64                      1/7 
  Installing       : python3-six-1.15.0-9.el9.noarch                        2/7 
  Installing       : python3-dateutil-1:2.8.1-7.el9.noarch                  3/7 
  Installing       : dbus-libs-1:1.12.20-8.el9.x86_64                       4/7 
  Installing       : python3-dbus-1.2.18-2.el9.x86_64                       5/7 
  Installing       : python3-dnf-plugins-core-4.3.0-11.el9_3.alma.1.noarc   6/7 
  Installing       : dnf-plugins-core-4.3.0-11.el9_3.alma.1.noarch          7/7 
  Running scriptlet: dnf-plugins-core-4.3.0-11.el9_3.alma.1.noarch          7/7 
  Verifying        : dbus-libs-1:1.12.20-8.el9.x86_64                       1/7 
  Verifying        : dnf-plugins-core-4.3.0-11.el9_3.alma.1.noarch          2/7 
  Verifying        : python3-dateutil-1:2.8.1-7.el9.noarch                  3/7 
  Verifying        : python3-dbus-1.2.18-2.el9.x86_64                       4/7 
  Verifying        : python3-dnf-plugins-core-4.3.0-11.el9_3.alma.1.noarc   5/7 
  Verifying        : python3-six-1.15.0-9.el9.noarch                        6/7 
  Verifying        : python3-systemd-234-18.el9.x86_64                      7/7 

Installed:
  dbus-libs-1:1.12.20-8.el9.x86_64                                              
  dnf-plugins-core-4.3.0-11.el9_3.alma.1.noarch                                 
  python3-dateutil-1:2.8.1-7.el9.noarch                                         
  python3-dbus-1.2.18-2.el9.x86_64                                              
  python3-dnf-plugins-core-4.3.0-11.el9_3.alma.1.noarch                         
  python3-six-1.15.0-9.el9.noarch                                               
  python3-systemd-234-18.el9.x86_64                                             

Complete!
+ dnf config-manager --set-enabled crb
+ dnf install -y epel-release
AlmaLinux 9 - CRB                               3.7 MB/s | 2.5 MB     00:00    
Last metadata expiration check: 0:00:01 ago on Tue Mar  5 12:33:35 2024.
Dependencies resolved.
================================================================================
 Package               Architecture    Version            Repository       Size
================================================================================
Installing:
 epel-release          noarch          9-5.el9            extras           18 k

Transaction Summary
================================================================================
Install  1 Package

Total download size: 18 k
Installed size: 25 k
Downloading Packages:
epel-release-9-5.el9.noarch.rpm                 738 kB/s |  18 kB     00:00    
--------------------------------------------------------------------------------
Total                                            55 kB/s |  18 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : epel-release-9-5.el9.noarch                            1/1 
  Running scriptlet: epel-release-9-5.el9.noarch                            1/1 
Many EPEL packages require the CodeReady Builder (CRB) repository.
It is recommended that you run /usr/bin/crb enable to enable the CRB repository.

  Verifying        : epel-release-9-5.el9.noarch                            1/1 

Installed:
  epel-release-9-5.el9.noarch                                                   

Complete!
+ dnf install -y python3 python3-pip python3-virtualenv
Extra Packages for Enterprise Linux 9 - x86_64   20 MB/s |  20 MB     00:01    
Last metadata expiration check: 0:00:03 ago on Tue Mar  5 12:33:38 2024.
Package python3-3.9.18-1.el9_3.1.x86_64 is already installed.
Dependencies resolved.
================================================================================
 Package                   Arch        Version             Repository      Size
================================================================================
Installing:
 python3-pip               noarch      21.2.3-7.el9        appstream      1.7 M
 python3-virtualenv        noarch      20.21.1-1.el9       epel           202 k
Installing dependencies:
 python3-distlib           noarch      0.3.2-1.el9         epel           192 k
 python3-filelock          noarch      3.7.1-1.el9         epel            24 k
 python3-platformdirs      noarch      2.5.4-1.el9         epel            31 k
 python3-wheel-wheel       noarch      1:0.36.2-8.el9      crb             42 k
Installing weak dependencies:
 libxcrypt-compat          x86_64      4.4.18-3.el9        appstream       88 k
 python3-setuptools        noarch      53.0.0-12.el9       baseos         839 k

Transaction Summary
================================================================================
Install  8 Packages

Total download size: 3.1 M
Installed size: 15 M
Downloading Packages:
(1/8): libxcrypt-compat-4.4.18-3.el9.x86_64.rpm 2.1 MB/s |  88 kB     00:00    
(2/8): python3-wheel-wheel-0.36.2-8.el9.noarch. 4.7 MB/s |  42 kB     00:00    
(3/8): python3-distlib-0.3.2-1.el9.noarch.rpm   1.8 MB/s | 192 kB     00:00    
(4/8): python3-filelock-3.7.1-1.el9.noarch.rpm  3.9 MB/s |  24 kB     00:00    
(5/8): python3-platformdirs-2.5.4-1.el9.noarch. 4.3 MB/s |  31 kB     00:00    
(6/8): python3-virtualenv-20.21.1-1.el9.noarch. 5.8 MB/s | 202 kB     00:00    
(7/8): python3-setuptools-53.0.0-12.el9.noarch. 3.7 MB/s | 839 kB     00:00    
(8/8): python3-pip-21.2.3-7.el9.noarch.rpm      4.4 MB/s | 1.7 MB     00:00    
--------------------------------------------------------------------------------
Total                                           1.8 MB/s | 3.1 MB     00:01     
Extra Packages for Enterprise Linux 9 - x86_64  1.6 MB/s | 1.6 kB     00:00    
Importing GPG key 0x3228467C:
 Userid     : "Fedora (epel9) <epel@fedoraproject.org>"
 Fingerprint: FF8A D134 4597 106E CE81 3B91 8A38 72BF 3228 467C
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-9
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : python3-platformdirs-2.5.4-1.el9.noarch                1/8 
  Installing       : python3-filelock-3.7.1-1.el9.noarch                    2/8 
  Installing       : python3-distlib-0.3.2-1.el9.noarch                     3/8 
  Installing       : python3-wheel-wheel-1:0.36.2-8.el9.noarch              4/8 
  Installing       : python3-setuptools-53.0.0-12.el9.noarch                5/8 
  Installing       : libxcrypt-compat-4.4.18-3.el9.x86_64                   6/8 
  Installing       : python3-pip-21.2.3-7.el9.noarch                        7/8 
  Installing       : python3-virtualenv-20.21.1-1.el9.noarch                8/8 
  Running scriptlet: python3-virtualenv-20.21.1-1.el9.noarch                8/8 
  Verifying        : libxcrypt-compat-4.4.18-3.el9.x86_64                   1/8 
  Verifying        : python3-pip-21.2.3-7.el9.noarch                        2/8 
  Verifying        : python3-setuptools-53.0.0-12.el9.noarch                3/8 
  Verifying        : python3-wheel-wheel-1:0.36.2-8.el9.noarch              4/8 
  Verifying        : python3-distlib-0.3.2-1.el9.noarch                     5/8 
  Verifying        : python3-filelock-3.7.1-1.el9.noarch                    6/8 
  Verifying        : python3-platformdirs-2.5.4-1.el9.noarch                7/8 
  Verifying        : python3-virtualenv-20.21.1-1.el9.noarch                8/8 

Installed:
  libxcrypt-compat-4.4.18-3.el9.x86_64                                          
  python3-distlib-0.3.2-1.el9.noarch                                            
  python3-filelock-3.7.1-1.el9.noarch                                           
  python3-pip-21.2.3-7.el9.noarch                                               
  python3-platformdirs-2.5.4-1.el9.noarch                                       
  python3-setuptools-53.0.0-12.el9.noarch                                       
  python3-virtualenv-20.21.1-1.el9.noarch                                       
  python3-wheel-wheel-1:0.36.2-8.el9.noarch                                     

Complete!
+ virtualenv /runtime
created virtual environment CPython3.9.18.final.0-64 in 283ms
  creator CPython3Posix(dest=/runtime, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(extra_search_dir=/usr/share/python3-wheels,download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/root/.local/share/virtualenv)
    added seed packages: pip==21.2.3, setuptools==53.0.0, wheel==0.36.2
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator
+ source /runtime/bin/activate
++ '[' /runtime/bin/activate = /.post.script ']'
++ deactivate nondestructive
++ unset -f pydoc
++ '[' -z '' ']'
++ '[' -z '' ']'
++ hash -r
++ '[' -z '' ']'
++ unset VIRTUAL_ENV
++ '[' '!' nondestructive = nondestructive ']'
++ VIRTUAL_ENV=/runtime
++ '[' linux-gnu = cygwin ']'
++ '[' linux-gnu = msys ']'
++ export VIRTUAL_ENV
++ _OLD_VIRTUAL_PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
++ PATH=/runtime/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
++ export PATH
++ '[' -z '' ']'
++ '[' -z '' ']'
++ _OLD_VIRTUAL_PS1=
++ '[' x '!=' x ']'
+++ basename /runtime
++ PS1='(runtime) '
++ export PS1
++ alias pydoc
++ true
++ hash -r
+ pip install --upgrade pip
Requirement already satisfied: pip in /runtime/lib/python3.9/site-packages (21.2.3)
Collecting pip
  Downloading pip-24.0-py3-none-any.whl (2.1 MB)
Installing collected packages: pip
  Attempting uninstall: pip
    Found existing installation: pip 21.2.3
    Uninstalling pip-21.2.3:
      Successfully uninstalled pip-21.2.3
Successfully installed pip-24.0
+ pip install numba
Collecting numba
  Downloading numba-0.59.0-cp39-cp39-manylinux2014_x86_64.manylinux_2_17_x86_64.whl.metadata (2.7 kB)
Collecting llvmlite<0.43,>=0.42.0dev0 (from numba)
  Downloading llvmlite-0.42.0-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (4.8 kB)
Collecting numpy<1.27,>=1.22 (from numba)
  Downloading numpy-1.26.4-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (61 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 61.0/61.0 kB 6.2 MB/s eta 0:00:00
Downloading numba-0.59.0-cp39-cp39-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (3.7 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 3.7/3.7 MB 20.2 MB/s eta 0:00:00
Downloading llvmlite-0.42.0-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (43.8 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 43.8/43.8 MB 28.3 MB/s eta 0:00:00
Downloading numpy-1.26.4-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (18.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 18.2/18.2 MB 28.5 MB/s eta 0:00:00
Installing collected packages: numpy, llvmlite, numba
Successfully installed llvmlite-0.42.0 numba-0.59.0 numpy-1.26.4
INFO:    Adding runscript
INFO:    Creating SIF file...
INFO:    Build complete: alma_python.sif

```

### Run:

```shell
$ apptainer run alma_python.sif 
Calculating PI with:
  10000000 slices
Obtained value of PI: 3.141592653589731
Time taken: 0.34809374809265137 seconds
```

If you don't want Apptainer to automount your home directory (arguably a terrible idea from a security perspective), you can create a fake one as a subdirectory of your home directory e.g.

```shell
$ mkdir home
$ apptainer run -H $(pwd)/home alma_python.sif 
Calculating PI with:
  10000000 slices
Obtained value of PI: 3.141592653589731
Time taken: 0.34809374809265137 seconds
```

