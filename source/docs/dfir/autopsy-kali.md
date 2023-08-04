# Autopsy on Kali

Autopsy is an open-source and powerful digital forensics platform. Several features within Autopsy have been developed by the Department of Homeland Security Science and Technology funding. If you want to get to work quickly, and do not insist on trying to get version 4 working in Linux, use the given defaults. Or set up [Autopsy 4 on a Windows VM](autopsy-windows.md).

Both SIFT and Kali have 2.24 by default installed. And that was not good enough for some of the more current challenges. Installing 4.20 at the time of writing resulted in a dead GUI, to do with encapsulating Java runtime internals in Java 17. Looking forward, I see the same SEVERE UI error reported for Java 18 for several applications which are already using it. And using JDK 16 will not be trivial. The only release available in Debian 10 is OpenJDK 11. Debian 11 has OpenJDK 17. Both of these are releases with long-term support. 

So I tried for OpenJDK 11, autopsy-4.17.0 and sleuthkit-java_4.10.2-1_amd64.deb. That works. And posted my notes on installing Autopsy 4.20 on JDK 17 below it, because in the future the GUI problem may be solved, and then these notes become useful.

## Installing Autopsy 4.17

### Prerequisites

Run [install_prereqs_ubuntu.sh](https://github.com/sleuthkit/autopsy/blob/develop/linux_macos_install_scripts/install_prereqs_ubuntu.sh) and add:

```text
┌──(kali㉿kali-blue)-[~]
└─$ sudo apt -y install openjdk-11-jdk openjdk-11-jre
[sudo] password for kali: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  openjdk-11-jdk-headless openjdk-11-jre-headless
...
Setting up openjdk-11-jdk-headless:amd64 (11.0.20~7-1) ...
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/rmic to provid
e /usr/bin/rmic (rmic) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jaotc to provi
de /usr/bin/jaotc (jaotc) in auto mode
Setting up openjdk-11-jre:amd64 (11.0.20~7-1) ...
Setting up openjdk-11-jdk:amd64 (11.0.20~7-1) ...
                                                                                
┌──(kali㉿kali-blue)-[~]
└─$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-17-openjdk-amd64/bin/java   1711      auto mode
  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java   1111      manual mode
  2            /usr/lib/jvm/java-17-openjdk-amd64/bin/java   1711      manual mode

Press <enter> to keep the current choice[*], or type selection number: 1
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/java to provide /usr/bin/java (java) in manual mode
                                                                                                                                            
┌──(kali㉿kali-blue)-[~]
└─$ java -version
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
openjdk version "11.0.20-ea" 2023-07-18
OpenJDK Runtime Environment (build 11.0.20-ea+7-post-Debian-1)
OpenJDK 64-Bit Server VM (build 11.0.20-ea+7-post-Debian-1, mixed mode, sharing)
```

### Remove conflicting sleuthkit

```text
┌──(kali㉿kali-blue)-[~]
└─$ cd Downloads 
                                                                                                                                   
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

### Install sleuthkit

```text
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ wget -O /tmp/sleuthkit-java_4.10.2-1_amd64.deb https://github.com/sleuthkit/sleuthkit/releases/download/sleuthkit-4.10.2/sleuthkit-java_4.10.2-1_amd64.deb
--2023-08-03 11:20:10--  https://github.com/sleuthkit/sleuthkit/releases/download/sleuthkit-4.10.2/sleuthkit-java_4.10.2-1_amd64.deb
Resolving github.com (github.com)... 140.82.121.3
Connecting to github.com (github.com)|140.82.121.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/2562873/18b1bc80-8ba8-11eb-83c5-19c343833937?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20230803%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230803T102010Z&X-Amz-Expires=300&X-Amz-Signature=2190994dc759f71e008df9dbc3a586e241beb0fb063481f2408ed38f6238d7d7&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=2562873&response-content-disposition=attachment%3B%20filename%3Dsleuthkit-java_4.10.2-1_amd64.deb&response-content-type=application%2Foctet-stream [following]
--2023-08-03 11:20:10--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/2562873/18b1bc80-8ba8-11eb-83c5-19c343833937?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20230803%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230803T102010Z&X-Amz-Expires=300&X-Amz-Signature=2190994dc759f71e008df9dbc3a586e241beb0fb063481f2408ed38f6238d7d7&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=2562873&response-content-disposition=attachment%3B%20filename%3Dsleuthkit-java_4.10.2-1_amd64.deb&response-content-type=application%2Foctet-stream
Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.109.133, 185.199.108.133, 185.199.111.133, ...
Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8560088 (8.2M) [application/octet-stream]
Saving to: ‘/tmp/sleuthkit-java_4.10.2-1_amd64.deb’

/tmp/sleuthkit-java_4.10.2-1_amd64.deb 100%[=========================================================================>]   8.16M  7.54MB/s    in 1.1s 

2023-08-03 11:20:12 (7.54 MB/s) - ‘/tmp/sleuthkit-java_4.10.2-1_amd64.deb’ saved [8560088/8560088]
                                                                                                                                             
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ sudo apt install /tmp/./sleuthkit-java_4.10.2-1_amd64.deb
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'sleuthkit-java' instead of '/tmp/./sleuthkit-java_4.10.2-1_amd64.deb'
The following additional packages will be installed:
  libc3p0-java libsqlite3-dev
Suggested packages:
  liblog4j1.2-java sqlite3-doc
The following NEW packages will be installed:
  libc3p0-java libsqlite3-dev sleuthkit-java
...
```

### Download and unzip autopsy

```text
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ wget -O /tmp/autopsy-4.17.0.zip https://github.com/sleuthkit/autopsy/releases/download/autopsy-4.17.0/autopsy-4.17.0.zip
--2023-08-03 11:22:14--  https://github.com/sleuthkit/autopsy/releases/download/autopsy-4.17.0/autopsy-4.17.0.zip
Resolving github.com (github.com)... 140.82.121.3
Connecting to github.com (github.com)|140.82.121.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
...
Saving to: ‘/tmp/autopsy-4.17.0.zip’

/tmp/autopsy-4.17.0.zip                100%[=========================================================================>]   1.03G  9.10MB/s    in 1m 56s  

2023-08-03 11:24:11 (9.04 MB/s) - ‘/tmp/autopsy-4.17.0.zip’ saved [1101460665/1101460665]
                                                                                                                                                   
┌──(kali㉿kali-blue)-[~/Downloads]
└─$ unzip /tmp/autopsy-4.17.0.zip -d /tmp/
Archive:  /tmp/autopsy-4.17.0.zip
...
  inflating: /tmp/autopsy-4.17.0/unix_setup.sh  

┌──(kali㉿kali-blue)-[~/Downloads]
└─$ cd /tmp
```

### Configure autopsy

```text
┌──(kali㉿kali-blue)-[/tmp]
└─$ cd autopsy-4.17.0 

┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ chmod +x unix_setup.sh
                                                                                                                                            
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ ./unix_setup.sh           
---------------------------------------------
Checking prerequisites and preparing Autopsy:
---------------------------------------------
Checking for PhotoRec...found in /usr/bin
Checking for Java...ERROR: JAVA_HOME environment variable must be defined.

┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")
                                                                                    
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ echo $JAVA_HOME
/usr/lib/jvm/java-17-openjdk-amd64

┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ sudo update-alternatives --config javac
There are 2 choices for the alternative javac (providing /usr/bin/javac).

  Selection    Path                                          Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-17-openjdk-amd64/bin/javac   1711      auto mode
  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/javac   1111      manual mode
  2            /usr/lib/jvm/java-17-openjdk-amd64/bin/javac   1711      manual mode

Press <enter> to keep the current choice[*], or type selection number: 1
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/javac to provide /usr/bin/javac (javac) in manual mode

┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")
                                                                                  
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ echo $JAVA_HOME 
/usr/lib/jvm/java-11-openjdk-amd64                                                                                                                     
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ export JAVA_HOME

┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ ./unix_setup.sh 
---------------------------------------------
Checking prerequisites and preparing Autopsy:
---------------------------------------------
Checking for PhotoRec...found in /usr/bin
Checking for Java...found in /usr/lib/jvm/java-11-openjdk-amd64
Checking for Sleuth Kit Java bindings...ERROR: sleuthkit-4.10.1.jar not found in /usr/share/java/ or /usr/local/share/java/.
Please install the Sleuth Kit Java bindings file.
See https://github.com/sleuthkit/sleuthkit/releases.

┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ mv /usr/share/java/sleuthkit-4.10.2.jar /usr/share/java/sleuthkit-4.10.1.jar

┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ ./unix_setup.sh                             
---------------------------------------------
Checking prerequisites and preparing Autopsy:
---------------------------------------------
Checking for PhotoRec...found in /usr/bin
Checking for Java...found in /usr/lib/jvm/java-11-openjdk-amd64
Checking for Sleuth Kit Java bindings...found in /usr/share/java
Copying sleuthkit-4.10.1.jar into the Autopsy directory...done

Autopsy is now configured. You can execute bin/autopsy to start it
                                                                                                                                                     
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ bin/autopsy
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.netbeans.ProxyURLStreamHandlerFactory (file:/tmp/autopsy-4.17.0/platform/lib/boot.jar) to field java.net.URL.handler
WARNING: Please consider reporting this to the maintainers of org.netbeans.ProxyURLStreamHandlerFactory
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release

(java:4340): Gtk-WARNING **: 11:42:32.073: Unable to locate theme engine in module_path: "adwaita",              
```

### Move it

```text 
┌──(kali㉿kali-blue)-[/tmp/autopsy-4.17.0]
└─$ sudo mv /tmp/autopsy-4.17.0 /opt/

┌──(kali㉿kali-blue)-[/opt]
└─$ ls
autopsy-4.17.0  microsoft

┌──(kali㉿kali-blue)-[/opt]
└─$ sudo ln -s /opt/autopsy-4.17.0/bin/autopsy /usr/local/bin/autopsy

┌──(kali㉿kali-blue)-[/opt]
└─$ chmod +x /usr/local/bin/autopsy
```
     
### Clean up

```text 
┌──(kali㉿kali-blue)-[/tmp]
└─$ rm autopsy-4.17.0.zip sleuthkit-java_4.10.2-1_amd64.deb 
```

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

Run [install_prereqs_ubuntu.sh](https://github.com/sleuthkit/autopsy/blob/develop/linux_macos_install_scripts/install_prereqs_ubuntu.sh):

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
