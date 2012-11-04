aSmack - buildsystem for Smack on Android
=========================================

*This repository doesn't contain much code, it's a build environment!*

Tracking trunk can be hard. Doing massive changes on top of trunk can be
near impossible. We are mixing 6 open source projects to provide a working
xmpp library for Android. All trunk-based.

This repository contains a source fetching, patching and building script.
As well as all the minor changes to make an Android version fly.
See the patches/ folder for a detailed list of changes and scripts.

Static Code
===========

**IMPORTANT:** In order to work correctly on Android, you need to register the Providers manually and init some static code blocks before you doing any XMPP activty. *Make sure to call `org.jivesoftware.smackx.ConfigureProviderManager.configureProviderManager()` and `org.jivesoftware.smackx.InitStaticCode.initStaticCode(Context)` prior any XMPP activity*
You could also call `org.jivesoftware.smack.SmackAndroid.init(Context)`, which will call both methods.


Compiled JARs
=============
Can be found [here](https://github.com/Flowdalic/asmack/downloads).
But be aware, they may be *outdated!*

ConnectionConfiguration
=======================
Please use the provided org.jivesoftware.smack.AndroidConnectionConfiguration class if possible to create a new connection.

Compression
===========
In order to enable compressed XMPP streams you have to add [jzlib](http://www.jcraft.com/jzlib/) to your project.

Compiling aSmack
================

1. copy local.properties.example to local.properties and set the Android SDK path (e.g. sdk-location=/opt/android-sdk-update-manager/ on a gentoo system)

2. Run build.bash

aSmack uses a [special fork of smack](https://github.com/Flowdalic/smack). You can read about the results you will get when using one of the various branches provides in the [README](https://github.com/Flowdalic/smack/blob/smack_extended/README.markdown).

Apps that use this fork of aSmack
=================================
- [GTalkSMS](http://code.google.com/p/gtalksms/) uses many features of Smack and XMPP on Android:
    - File Transfer
    - DNS SRV
    - MUC
    - Entity Caps
    - and many more 

- [yaxim](https://github.com/ge0rg/yaxim)
- your app?

Contribution
============

The easiest way to contribute is fork & pull request. You may also ask about
direct project access. Mind that minor changes can be applied to the smack
repository. You'll most likly want to help out on smack, not on aSmack.

Contributors
============

We do not keep a seperate CONTRIBUTORS file, and we discourage @author tags.
However you're free to add your full name to every git commit, and we will
preserver this. Let us know if you've helped on non-technical stuff and we'll
find a way to give you the deserved credit.

Reporting Problems / Debugging
==============================

We always provide source zips. Attach them to the jar in your favorite IDE.
Enable debugging mode (BOSH/XMPPConnection.DEBUG and config.setDebug)
Record a logcat
Remove your credentials (usually a base64 block inside <auth></auth>)

Your issue should contain
1. a logcat
2. a server to reproduce
3. the code you are using (for FOSS project we'll accept reposituroy URLs)

There is no guarantee that we will reply immediatly. But we will try to
investigate the problem.

Contact
=======
Join ##smack @ freenode

Licences / Used libraries
=========================

We only accept Apache and BSD-like licences.
We are currently using code from

 * Apache Harmony (sasl/xml) (Apache Licence)
 * smack (xmpp) (Apache Licence)
 * novell-openldap-jldap (sasl) ( [OpenLDAP Licence][1] )
 * Apache qpid (sasl) (Apache Licence)
 * jbosh (BOSH) (Apache Licence)
 * dnsjava (dns srv lookups) (BSD)
 * custom code (various glue stuff) (WTFPL | BSD | Apache)

This should work for just about every project. Contact us if you have problems
with the licence.

  [1]: http://www.openldap.org/devel/cvsweb.cgi/~checkout~/LICENSE?rev=1.23.2.1&hideattic=1&sortbydate=0  "OpenLDAP Licence"

