Additional edits were made to Hadoop 0.20.205:
Lines Tagged with [MANUAL] need to be applied to your local machine!

1) Making it OSX friendly:
- setting up the JAVA_HOME

2) Patching with hadoop-snappy, which requires:
 - [MANUAL] Making OS ready for compiling native and JNI stuff:
   - In /Developer/usr/share/autoconf/autom4te.cfg and/or
     /Developer-X.X.X/usr/share/autoconf/autom4te.cfg, change all refs from
       'args: --prepend-include /usr/share/autoconf'
     to
        'args: --prepend-include /Developer/usr/share/autoconf'
   - Make Java header visible:
     In '/System/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home'
     create a include symlink that points to the correct headers, eg
     'sudo ln -s /System/Library/Frameworks/JavaVM.framework/Versions/A/Headers/ include'
 - [MANUAL] Build Snappy (see instructions online)
 - [MANUAL] Build hadoop-snappy (see instructions online or at github electrum/hadoop-snappy)
 - Adding the jar and the native libraries, plus referencing them in the hadoop env.
 - Adding the Snappy code entry in conf/core-site.xml
 - Preventing the java.library.path to be erased in bin/hadoop

##################################################################

For the latest information about Hadoop, please visit our website at:

   http://hadoop.apache.org/core/

and our wiki, at:

   http://wiki.apache.org/hadoop/

This distribution includes cryptographic software.  The country in
which you currently reside may have restrictions on the import,
possession, use, and/or re-export to another country, of
encryption software.  BEFORE using any encryption software, please
check your country's laws, regulations and policies concerning the
import, possession, or use, and re-export of encryption software, to
see if this is permitted.  See <http://www.wassenaar.org/> for more
information.

The U.S. Government Department of Commerce, Bureau of Industry and
Security (BIS), has classified this software as Export Commodity
Control Number (ECCN) 5D002.C.1, which includes information security
software using or performing cryptographic functions with asymmetric
algorithms.  The form and manner of this Apache Software Foundation
distribution makes it eligible for export under the License Exception
ENC Technology Software Unrestricted (TSU) exception (see the BIS
Export Administration Regulations, Section 740.13) for both object
code and source code.

The following provides more details on the included cryptographic
software:
  Hadoop Core uses the SSL libraries from the Jetty project written
by mortbay.org.
