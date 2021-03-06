MedlineXmlToDatabase
====================

This is a Java application for loading MEDLINE XML files into a relational database (currently supporting SQL Server and PostgreSQL). The application was designed with two goals in mind:

1. Everything in the XML files needs to go into the database.

2. Any changes in the XML structure that occur over the years should not require changing the program.

The application is run in two phases:

1. During *analysis*, the structure and contents of a large set of XML files is analysed, and a database structure is build to accomodate the data. This is typically done only once a year.

2. During *parse*, all XML files in a folder are parsed and their contents are inserted into the database. This is typically done every time new XML files are available from MEDLINE.

Note that the application works directly of the GZipped XML files, so no need to unzip them.

Features
========
- Supports SQL Server and PostgreSQL
- Scans the XML files to determine the structure of the database needed to hold the data
- All data in the XML files is loaded in the database
- Allows incremental loading of data as it is made available by NLM
- Automatically deletes old versions of citations as revisions are made available

Technology
==========
This is a pure Java application that can only be used through the command line.

System Requirements
============
Requires Java 1.7 or higher, and read access to the database to be scanned.   Java can be downloaded from
<a href="http://www.java.com" target="_blank">http://www.java.com</a>.

Dependencies
============
 * There are no dependencies.

Getting Started
=============== 
1. Download all xml.gz files from MEDLINE (see http://www.nlm.nih.gov/databases/license/license.html for licensing information)

2. Create an ini file according to the example in the iniFileExamples folder, pointing to the folder containing the xml.gz files, and the server and schema where the data should be uploaded

3. Under the [Releases](https://github.com/OHDSI/MedlineXmlToDatabase/releases) tab, download MedlineXmlToDatabase*.zip, and unzip the file. Alternatively, you can download the source code and use the included Ant file to build the Jar file.

4. From the command line, use ```java -jar MedlineXmlToDatabase.jar -analyse -ini <path to ini file``` to create the database structure.

5. From the command line, use ```java -jar MedlineXmlToDatabase.jar -parse -ini <path to ini file``` to load the data from the xml files into the database.

Getting Involved
=============
* Developer questions/comments/feedback: <a href="http://forums.ohdsi.org/c/developers">OHDSI Forum</a>
* We use the <a href="../../issues">GitHub issue tracker</a> for all bugs/issues/enhancements

License
=======
MedlineXmlToDatabase is licensed under Apache License 2.0

Development
===========
MedlineXmlToDatabase was developed in Eclipse. Contributions are welcome.
###Development status
Beta testing

Acknowledgements
===========
Martijn Schuemie is the author of this application.

