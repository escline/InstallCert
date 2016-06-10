InstallCert.java

Java program written by Andreas Sterbenz, and posted on a blog in Oct, 2006:
https://blogs.oracle.com/gc/entry/unable_to_find_valid_certification

Link to Java program in Andreas' blog no longer works, but the source was linked in another blog:
http://nodsw.com/blog/leeland/2006/12/06-no-more-unable-find-valid-certification-path-requested-target

Usage:
Need to compile, first:
javac InstallCert.java

# Access server, and retrieve certificate (accept default certificate 1)
java InstallCert [host]:[port]

# Extract certificate from created jssecacerts keystore
keytool -exportcert -alias [host]-1 -keystore jssecacerts -storepass changeit -file [host].cer

# Import certificate into system keystore
keytool -importcert -alias [host] -keystore [path to system keystore] -storepass changeit -file [host].cer

# Example:
java InstallCert woot.com:443

    Loading KeyStore /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/security/cacerts...
    Opening connection to woot.com:443...
    Starting SSL handshake...

    javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

    <...>

    Server sent 1 certificate(s):

     1 Subject O=Woot Inc, C=US, ST=Texas, L=Carrollton, CN=*.woot.com
       Issuer  CN=SecureTrust CA, O=SecureTrust Corporation, C=US
       sha1    4b 46 ca 6b 83 05 b3 51 ff c6 e7 9c fd b3 9b e3 3f 2e c4 53 
       md5     e8 a5 88 1b d5 67 bb fc 88 cc b1 c5 2b ac c4 7d 

    Enter certificate to add to trusted keystore or 'q' to quit: [1]

[enter]

    [
    [
      Version: V3
      Subject: O=Woot Inc, C=US, ST=Texas, L=Carrollton, CN=*.woot.com
      Signature Algorithm: SHA1withRSA, OID = 1.2.840.113549.1.1.5

    <...>

    Added certificate to keystore 'jssecacerts' using alias 'woot.com-1'

keytool -exportcert -alias woot.com-1 -keystore jssecacerts -storepass changeit -file woot.com.cer

    Certificate stored in file <woot.com.cer>
  
(sudo) keytool -importcert -alias woot.com -keystore /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/security/cacerts -storepass changeit -file woot.com.cer

    Owner: O=Woot Inc, C=US, ST=Texas, L=Carrollton, CN=*.woot.com
    Issuer: CN=SecureTrust CA, O=SecureTrust Corporation, C=US
  
    <...>
  
    Trust this certificate? [no]:
  
yes

    Certificate was added to keystore
