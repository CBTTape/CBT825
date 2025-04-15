# CBT825
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 825 is from Raymond Ching and contains his SSL Handshake  *   FILE 825
//*           program.  See member called "README" for details.     *   FILE 825
//*                                                                 *   FILE 825
//*           emails:  "sslhand support" <sslhand@gmail.com>        *   FILE 825
//*                    "Raymond Ching" <rching93@gmail.com>         *   FILE 825
//*                                                                 *   FILE 825
//*     I have written a simple z/OS batch program to perform       *   FILE 825
//*     the first few phases of SSL handshake and print the         *   FILE 825
//*     human readable output into the SYSPRINT DDname. My          *   FILE 825
//*     intention is to write a simple program to diagnose the      *   FILE 825
//*     most common SSL setup issues in z/OS.                       *   FILE 825
//*                                                                 *   FILE 825
//*     Basically, the program is free to execute without any       *   FILE 825
//*     warranty.                                                   *   FILE 825
//*                                                                 *   FILE 825
//*     1. The SSLHAND program in JSSLHAND initiates Secure         *   FILE 825
//*        Socket Layer (SSL) session with the partner SSL          *   FILE 825
//*        server provided in the parameter by sending SSL          *   FILE 825
//*        client hello message.  The server will respond with      *   FILE 825
//*        SSL server hello message containing server               *   FILE 825
//*        certificate and optionally with Certificate request.     *   FILE 825
//*        Following flow diagram is extracted from                 *   FILE 825
//*        http://www.ietf.org/rfc/rfc2246.txt.                     *   FILE 825
//*                                                                 *   FILE 825
//*        ------------------------------------------------------   *   FILE 825
//*           Client                          Server                *   FILE 825
//*                                                                 *   FILE 825
//*           ClientHello       -------->                           *   FILE 825
//*                                           ServerHello           *   FILE 825
//*                                           Certificate*          *   FILE 825
//*                                           ServerKeyExchange*    *   FILE 825
//*                                           CertificateRequest*   *   FILE 825
//*                              <--------    ServerHelloDone       *   FILE 825
//*           ::::::::::                                            *   FILE 825
//*        ------------------------------------------------------   *   FILE 825
//*                                                                 *   FILE 825
//*        The SSLHAND program then formats the content supplied    *   FILE 825
//*        in Certificate and CertificateRequest and prints the     *   FILE 825
//*        output to SYSPRINT DD.  The public certificates found    *   FILE 825
//*        in the Certificate command will print to the SYSPRINT    *   FILE 825
//*        DD in Base64-encoded format for easy transportation.     *   FILE 825
//*        Finally, the SSLHAND program returns and let the         *   FILE 825
//*        TCPIP stack in z/OS to close the TCP/IP socket.          *   FILE 825
//*                                                                 *   FILE 825
//*     2. Program SSLHAND is developed and verified in z/OS        *   FILE 825
//*        v1.6 environment.  Standard z/OS TCPIP API socket        *   FILE 825
//*        call, DFHSMS macros (OPEN, CLOSE, XLATE) are used.       *   FILE 825
//*        Although the program uses AMODE 24 and RMODE 24,         *   FILE 825
//*        ESA/390 machine instructions are used.  This program     *   FILE 825
//*        does not require any external SSL library e.g. IBM       *   FILE 825
//*        z/OS System SSL (GSKSSL).  Only IPv4 is supported.       *   FILE 825
//*                                                                 *   FILE 825
//*     3. To execute the SSLHAND program, you can refer to the     *   FILE 825
//*        JSSLHAND member, amend the JOB and SYSTCPD DD card to    *   FILE 825
//*        suit your executing environment.  For SYSTCPD            *   FILE 825
//*        setting, you can refer to section 'Selecting a Stack     *   FILE 825
//*        When Running Multiple Instances of TCP/IP' in z/OS       *   FILE 825
//*        IBM Communications Server: IP Configuration Guide.       *   FILE 825
//*        The SSL server IP address and TCP port number are        *   FILE 825
//*        supplied as parameter to SSLHAND program in EXEC DD      *   FILE 825
//*        card in the following format:                            *   FILE 825
//*                                                                 *   FILE 825
//*                         PARM='IPv4addr(port_num)'               *   FILE 825
//*           For example,  PARM='123.45.67.89(1414)'               *   FILE 825
//*                                                                 *   FILE 825
//*     4. This program is free to use via JSSLHAND member.         *   FILE 825
//*        Feel free to send email message to                       *   FILE 825
//*        sslhand@gmail.com for any comments.                      *   FILE 825
//*                                                                 *   FILE 825
//*     5. Sample output SYSPRINT DD is attached.                   *   FILE 825
//*                                                                 *   FILE 825
//*     SSLHAND V0.1: 64.233.189.83(443)                            *   FILE 825
//*     Server Hello received                                       *   FILE 825
//*      Version: 3                                                 *   FILE 825
//*      Serial Number:                                             *   FILE 825
//*               1F19F6DE35DD63A142918AD52CC0AB12                  *   FILE 825
//*      Signature Algorithm: sha1RSA                               *   FILE 825
//*      Issuer:                                                    *   FILE 825
//*               C=ZA                                              *   FILE 825
//*               O=Thawte Consulting (Pty) Ltd.                    *   FILE 825
//*               CN=Thawte SGC CA                                  *   FILE 825
//*      Validity:                                                  *   FILE 825
//*               NOT BEFORE=091218000000Z                          *   FILE 825
//*                NOT AFTER=111218235959Z                          *   FILE 825
//*      Subject:                                                   *   FILE 825
//*               C=US                                              *   FILE 825
//*               ST=California                                     *   FILE 825
//*               L=Mountain View                                   *   FILE 825
//*               O=Google Inc                                      *   FILE 825
//*               CN=mail.google.com                                *   FILE 825
//*      Subject Public Key Algorithm: RSA                          *   FILE 825
//*                                                                 *   FILE 825
//*              ----  snip  ----                                   *   FILE 825
//*                                                                 *   FILE 825
```
