# Autopsy

Autopsy is an open-source and powerful digital forensics platform. Several features within Autopsy have been developed by the Department of Homeland Security Science and Technology funding. 

Both SIFT and Kali have 2.24 by default installed. And that was not good enough for some of the more current challenges. Installing 4.20 at the time of writing resulted in a dead GUI, to do with encapsulating Java runtime internals in Java 17. But I'll post my notes on installing it, because in the future that may be solved.

Looking forward, I see the same SEVERE UI error reported for Java 18 for several applications already using it. So, I may do it all again, but now with the latest version of autopsy and sleuthkit running Java 16.

## Installing autopsy 4.20

### Prerequisites

Existing sleuthkit conflicts. Remove it.
 
```text                                                                               
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ sudo apt remove --auto-remove sleuthkit -y
[sudo] password for kali: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  kali-linux-headless libtsk19 sleuthkit
...
```

Run [linux_macos_install_scripts/install_prereqs_ubuntu.sh](https://github.com/sleuthkit/autopsy/blob/develop/linux_macos_install_scripts/install_prereqs_ubuntu.sh):

```text                                                                               
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ ./install_prereqs_ubuntu.sh 
Turning on all repositories for apt...
Installing all apt dependencies...
Hit:1 http://ftp.belnet.be/pub/kali/kali kali-rolling InRelease
Get:2 http://ftp.belnet.be/pub/kali/kali kali-rolling/contrib Sources [78.3 kB]
...
Processing triggers for kali-menu (2023.3.3) ...
Autopsy prerequisites installed.
Java 17 instllation: 
java-1.17.0-openjdk-amd64      1711       /usr/lib/jvm/java-1.17.0-openjdk-amd64
                                                                               
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ java -version
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
openjdk version "17.0.8" 2023-07-18
OpenJDK Runtime Environment (build 17.0.8+7-Debian-1)
OpenJDK 64-Bit Server VM (build 17.0.8+7-Debian-1, mixed mode, sharing)
```

### Install sleuthkit

```text                                                                              
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ wget -O /tmp/sleuthkit-java_4.12.0-1_amd64.deb https://github.com/sleuthkit/sleuthkit/releases/download/sleuthkit-4.12.0/sleuthkit-java_4.12.0-1_amd64.deb
--2023-08-03 02:14:27--  https://github.com/sleuthkit/sleuthkit/releases/download/sleuthkit-4.12.0/sleuthkit-java_4.12.0-1_amd64.deb
Resolving github.com (github.com)... 140.82.121.4
Connecting to github.com (github.com)|140.82.121.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
...
Saving to: ‘/tmp/sleuthkit-java_4.12.0-1_amd64.deb’

/tmp/sleuthkit-java 100%[===================>]  10.93M  8.99MB/s    in 1.2s    

2023-08-03 02:14:29 (8.99 MB/s) - ‘/tmp/sleuthkit-java_4.12.0-1_amd64.deb’ saved [11460436/11460436]
                                                                               
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ sudo apt install /tmp/./sleuthkit-java_4.12.0-1_amd64.deb -y
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'sleuthkit-java' instead of '/tmp/./sleuthkit-java_4.12.0-1_amd64.deb'
The following additional packages will be installed:
  libc3p0-java libsqlite3-dev
Suggested packages:
  liblog4j1.2-java sqlite3-doc
The following NEW packages will be installed:
  libc3p0-java libsqlite3-dev sleuthkit-java
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
...
Setting up sleuthkit-java (4.12.0-1) ...
Processing triggers for libc-bin (2.37-5) ...
```

### Install autopsy
 
```text                                                                               
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ wget -O /tmp/autopsy-4.20.0.zip https://github.com/sleuthkit/autopsy/releases/download/autopsy-4.20.0/autopsy-4.20.0.zip
--2023-08-03 02:15:20--  https://github.com/sleuthkit/autopsy/releases/download/autopsy-4.20.0/autopsy-4.20.0.zip
Resolving github.com (github.com)... 140.82.121.4
Connecting to github.com (github.com)|140.82.121.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
...
Saving to: ‘/tmp/autopsy-4.20.0.zip’

/tmp/autopsy-4.20.0 100%[===================>]   1.03G  8.45MB/s    in 2m 4s   

2023-08-03 02:17:25 (8.50 MB/s) - ‘/tmp/autopsy-4.20.0.zip’ saved [1106980836/1106980836]
                                                                             
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ unzip /tmp/autopsy-4.20.0.zip -d /tmp/
Archive:  /tmp/autopsy-4.20.0.zip
   creating: /tmp/autopsy-4.20.0/
   ...
  inflating: /tmp/autopsy-4.20.0/platform/update_tracking/org-openide-windows.xml  
  inflating: /tmp/autopsy-4.20.0/unix_setup.sh  
                                                                                    
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ cd /tmp/autopsy-4.20.0                  
                                                                                
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ ls
autopsy       etc       LICENSE-2.0.txt              README.txt
bin           harness   linux_macos_install_scripts  Running_Linux_OSX.md
CoreTestLibs  icon.ico  NEWS.txt                     unix_setup.sh
docs          java      platform
```
    
### Configuring autopsy
     
```text
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ ./unix_setup.sh
zsh: permission denied: ./unix_setup.sh
                                                                                
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ chmod +x unix_setup.sh

                                                 
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ ./unix_setup.sh 
---------------------------------------------
Checking prerequisites and preparing autopsy:
---------------------------------------------
/tmp/autopsy-4.20.0 /tmp/autopsy-4.20.0
Checking for PhotoRec...found in /usr/bin
Checking for Java...ERROR: JAVA_HOME environment variable must be defined.
                                                                                
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")
                                                                                
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ echo $JAVA_HOME
/usr/lib/jvm/java-17-openjdk-amd64
                                                                                
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ export JAVA_HOME
                                                                                
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.20.0]
└─$ ./unix_setup.sh       
---------------------------------------------
Checking prerequisites and preparing autopsy:
---------------------------------------------
/tmp/autopsy-4.20.0 /tmp/autopsy-4.20.0
Checking for PhotoRec...found in /usr/bin
Checking for Java...found in /usr/lib/jvm/java-17-openjdk-amd64
Checking for Sleuth Kit Java bindings...found in /usr/share/java
Copying sleuthkit-4.12.0.jar into the autopsy directory...done
/tmp/autopsy-4.20.0

Application is now configured. You can execute bin/autopsy to start it
```                                                                     

### Move it

```text
┌──(kali㉿kali-blue)-[/tmp]
└─$ sudo mv /tmp/autopsy-4.20.0 /opt/

┌──(kali㉿kali-blue)-[/tmp]
└─$ sudo ln -s /opt/autopsy-4.20.0/bin/autopsy /usr/local/bin/autopsy

┌──(kali㉿kali-blue)-[/tmp]
└─$ chmod +x /usr/local/bin/autopsy
```

## Clean up

```text
┌──(kali㉿kali-blue)-[/tmp]
└─$ rm /tmp/sleuthkit-java_4.12.0-1_amd64.deb /tmp/autopsy-4.20.0.zip
```

### Finally running it (Not)

#### Theme engine

    (java:5640): Gtk-WARNING **: 02:58:02.016: Unable to locate theme engine in module_path: "adwaita",

Solve with:

```text
sudo apt install gnome-themes-extra
```

#### SecurityManager warning

```text
WARNING: A terminally deprecated method in java.lang.System has been called
WARNING: System::setSecurityManager has been called by org.netbeans.TopSecurityManager (file:/opt/autopsy-4.20.0/platform/lib/boot.jar)
WARNING: Please consider reporting this to the maintainers of org.netbeans.TopSecurityManager
WARNING: System::setSecurityManager will be removed in a future release
```

This is just a [warning regarding JEP411](https://openjdk.org/jeps/411), and can be ignored.

#### No working UI

```text
Aug 03, 2023 3:10:00 AM org.netbeans.ProxyURLStreamHandlerFactory register
SEVERE: No way to find original stream handler for jar protocol
java.lang.reflect.InaccessibleObjectException: Unable to make field transient java.net.URLStreamHandler java.net.URL.handler accessible: module java.base does not "opens java.net" to unnamed module @6b162892
	at java.base/java.lang.reflect.AccessibleObject.checkCanSetAccessible(AccessibleObject.java:354)
	at java.base/java.lang.reflect.AccessibleObject.checkCanSetAccessible(AccessibleObject.java:297)
	at java.base/java.lang.reflect.Field.checkCanSetAccessible(Field.java:178)
	at java.base/java.lang.reflect.Field.setAccessible(Field.java:172)
	at org.netbeans.ProxyURLStreamHandlerFactory.register(ProxyURLStreamHandlerFactory.java:59)
	at org.netbeans.JarClassLoader.<clinit>(JarClassLoader.java:117)
	at org.netbeans.MainImpl.execute(MainImpl.java:153)
	at org.netbeans.MainImpl.main(MainImpl.java:60)
	at org.netbeans.Main.main(Main.java:58)
```

This is a more serious permissions issue to do with [Java Module System and NetBeans Platform Applications](https://cwiki.apache.org/confluence/display/NETBEANS/Java+Module+System+and+NetBeans+Platform+Applications) and [encapsulating the Java runtime internals](https://blogs.oracle.com/javamagazine/post/a-peek-into-java-17-continuing-the-drive-to-encapsulate-the-java-runtime-internals).

## Usage

Before diving into Autopsy and analysing data, there are a few steps to perform; such as identifying the data source and what Autopsy actions to perform with the data source. 

Basic workflow:

* Create/open the case for the data source to investigate
* Select the data source to analyse
* Configure the ingest modules to extract specific artefacts from the data source
* Review the artefacts extracted by the ingest modules
* Create the report

To prepare a new case investigation, you need to create a case file from the data source. When you start Autopsy, there will be three options. You can create a new case file using the "New Case" option. Once you click on the "New Case" option, the Case Information menu opens, where information about the case is populated.

* Case Name: The name you wish to give to the case
* Base Directory: The root directory that will store all the files specific to the case (the full path will be displayed)
* Case Type: Specify whether this case will be local (Single-user) or hosted on a server where multiple analysts can review (Multi-user)
