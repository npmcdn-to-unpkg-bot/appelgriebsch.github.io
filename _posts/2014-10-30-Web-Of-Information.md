---
layout: post
title: Web of Information
description: "Describes the Web of Information -- the World-Wide Web as a connected graph of information"
modified: 2014-10-30
tags: [world wide web, information space, graph, hypertext, web architecture]
comments: true
image:
  feature: HTML5_sticker.png
---

In the beginning the Web was mainly used to make information freely available and accessible for everyone with an Internet connection and a web browser installed. It has been invented and first used by Sir Tim Berners-Lee in 1990, who was working at the CERN laboratory in Geneva at the time. He founded the World-Wide Web as a novel mechanism to encode, link and display information that can be easily transferred between a client and a server based on the following existing concepts:

-   **Hypertext**, as a general way to establish links between related information

-   **TCP/IP**, as a protocol to transfer encoded information in a distributed system and as basis for the **HTTP** protocol

-   **SGML**, as a way to represent and encode structured content and as foundation for the **HTML** format

By doing so Sir Tim Berners-Lee solved one of the major issues he faced in his day-to-day job — namely getting different computing systems talk to each other and allow them to share information. Solutions for such problems did indeed exist before, but are either limited to a specific machine/vendor, rely heavily on a central database system and needed adaptations for each new client system that has to be integrated into the existing network. By utilising and building upon commonly agreed standards it makes it easier for Sir Tim Berners-Lee to extend his local network with new machines as well as making various kinds of information accessible to all of them.[^1] Using the Hypertext theory as a foundation for the Web means that it can be seen as a large connected graph containing the web pages or documents as nodes and the links between those web pages as Hypertext links. Taken a look at the whole thing, this will build a huge information space that can be traversed, analysed and searched. This
computer science view of the World-Wide Web makes it possible to build additional services on top of the graph — e.g. search engines like Google, that take the number of links to a web page into account for the relevance of that page.[^2]

[^1]: Berners-Lee, T.: Weaving the Web, Harper-Collins, 2000, pg. 7-51
[^2]: Berners-Lee, T. et al.: Web Science: An Interdisciplinary Approach to Understanding the Web, Communications of the ACM, Vol. 51, No. 7, July 2008, pg. 60-69

![](<http://www.expertsupdates.com/ArticleAttachments/seo/web-mining/Figure2.gif>)

**Figure 1**: Web Graph Structure


One of the fundamental design decisions for the Web is that it should be build in a way that it doesn’t rely on a central system to work properly. By doing so it enables and actively supports limitless scalability of the whole network as everyone is free to add additional servers to it without much hassle. This decentralised nature of the World-Wide Web makes it one of the most democratic systems in human history, “where information and power are equally distributed”.[^3] But due to it’s distributed nature it could happen though, that there are dead links on a page — that is: a Hypertext link on a web document that points to a no-longer existing node in the information space. In addition to that with every additional document or page added to the network finding the desired information in the information space will be getting harder, so there was a real need for web services that index all the available pages and documents to make them easier to find. But these eschewals of strict consistency on the one hand and of a centralised entry point into the network on the other hand helps further scaling the World-Wide Web into a global information space.[^4]

[^3]: The Guardian: Two decades on, we must preserve the internet as a tool of democracy, <http://www.theguardian.com/technology/2014/jan/12/web-tool-democracy-tim-berners-lee>
[^4]: Vossen, G.: Unleashing Web 2.0, Elsevier, 2007, pg. 10-22

Another important design decision for the Web is the usage of open, standardised protocols for communication and data encoding. First of all it starts with the TCP/IP protocol — which is the basis for the HTTP protocol on top of it and was already widely used in the beginning of the World-Wide Web; and second it is the HTML document format, that has been published early on and keeps being formalized and standardised by the W3C since the beginning of the 1990s.[^5] Based on its distributed architecture the World-Wide Web needs to support the following functionalities that are common in such systems (among others[^6]):

[^5]: Berners-Lee, T.: Weaving the Web, Harper-Collins, 2000, pg. 7-51
[^6]: Tanenbaum, A.: Distributed Systems, 2nd Edt., Pearson Education, 2007, pg. 5

-   **Access transparency**, that hides the differences in data representations of resources in different computing systems

-   **Location transparency**, that hides the specific location of a resource in the network

-   **Migration transparency**, that hides the fact that a resource has been moved to another location

-   **Replication transparency**, that hides the fact that there are multiple copies of the same resource in the network

-   **Concurrency transparency**, that hides that a resource may be used by multiple users at the same time

Access transparency is needed to hide the differences in data representation between the communicating parties — let’s assume the server uses a different binary representation for data as the client (e.g. big- vs. little-endian encoding, different character encodings, …); transferring data between both systems means that the representation of that data has to be generalised and both systems have to agree upon this common data representation to make the required transformations if necessary. In the World-Wide Web the access transparency is handled via the application-level HTTP protocol, which is based on the TCP/IP data transfer protocol. HTTP itself is a request/response communication protocol, which means that the client has to send a specific request to the server to activate a process on it. That process is responsible to handle the request and returns the answer for that request as a separate response message to the client. The payload of the HTTP message is placed into the HTTP body and is either a textual representation of a resource (e.g. a web page in HTML format) or a BASE64-encoded representation of a binary file (e.g.  an image that is placed on a web page).[^7]

[^7]: Taylor, I.: From P2P and Grids to Services on the Web, 2nd Edt., Springer Verlag, 2009, pg. 81-106

![](<https://cdn.tutsplus.com/net/authors/jeremymcpeak/http1-req-res-details.png>)

**Figure 2**: HTTP request/response message pairs


HTML itself is a markup style language in textual format and as such is a much simpler version of SGML. It uses tags for providing structure and styling of the content in a document — structure is used to classify and arrange the text in the document (e.g. using different headings, paragraphs etc. pp.) whereas styling is used to specify how parts of the content should be rendered on the screen (e.g. using bold, italic, …).[^8]

[^8]: Berners-Lee, T.: HTML, <http://info.cern.ch/hypertext/WWW/MarkUp/MarkUp.html>

Let’s look at a sample HTML document that displays information about the book from Sir Tim Berners-Lee:[^9]

[^9]: data taken from <http://www.amazon.com/Weaving-Web-Original-Ultimate-Destiny/dp/006251587X>

{% highlight html %}
<html>
       <head>
           <title>A book worth reading</title>
       </head>
       <body>
           <h1>Weaving the Web: The Original Design and Ultimate Destiny of the World Wide Web</h1><br>
           <p>by Sir Tim Berners-Lee</p>
           <ul>
               <li>Publisher: HarperCollins</li>
               <li>Genre: Computer and Internet</li>
               <li>Year: 2000</li>
               <li>ISBN: 978-0062515872</li>
           </ul>
           <br>visit the website
               <a href=http://harpercollins...co.uk>here</a>
       </body>
</html>
{% endhighlight %}

Each HTML document starts with the root-tag ‘\<html\>’ and consist of at least the ‘\<head\>’ (containing meta information about the document) and the ‘\<body\>’ (containing the structured content of the document) parts. The HTML standard defines specific tag names for headings (with nested levels: ‘\<h1\>’, ‘\<h2\>’, …), paragraphs (‘\<p\>’) as well as Hypertext links (‘\<a\>’) (among others).[^10]

[^10]: W3C: HTML & CSS, <http://www.w3.org/standards/webdesign/htmlcss>

Location, migration and replication transparency is handled via the URI concept in the Web. URI stands for “Uniform Resource Identifier” and can either be an URL (a “Uniform Resource Locator”) or an URN (a “Uniform Resource Name”) depending on the idea whether a resource has a binary representation and is directly accessible within the network (URL, e.g. HTML representation of the main page of a Web site) or just needs an unique identification mechanism (URN, e.g. the ISBN of a book on the shelf).[^11]

[^11]: Taylor, I.: From P2P and Grids to Services on the Web, 2nd Edt., Springer Verlag, 2009, pg. 83-84

![](<https://cdn.tutsplus.com/net/authors/jeremymcpeak/http1-url-structure.png>)

**Figure 3**: structure of an URL


Behind the scenes the “host” part of an URL is translated to the IP address of the server in the World-Wide Web via a DNS lookup. DNS stands for Domain Name Service and is a separate distributed system that collects and provides addressing information of publicly available servers in the Internet. It is hierarchically structured, starts with the top level domains on it’s roots (e.g.  .com, .org, .de, …) and continues with the other parts of the “host” (aka subdomains, separated by dots) in reverse order (e.g. based on the host in Figure 3: .com -\> domain -\> www). To prevent name clashes for server names the domains and subdomains have to be registered with a local authority (e.g. the DENIC in Germany) before they can be used. This kind of indirection in the access to a resource allows the DNS to point the client to different server IP addresses for the same name lookup to either increase scalability or availability of a resource (if the resource could be easily replicated) or route the client to another address when the resource has been migrated to a different server.[^12]

[^12]: Taylor, I.: From P2P and Grids to Services on the Web, 2nd Edt., Springer Verlag, 2009, pg. 10-11, 108-109

Concurrency transparency is handled by the HTTP protocol. First of all it uses different “verbs” or HTTP methods to classify the kind of action the client requires from the server. Getting read access to a resource on the server is usually signaled via the GET method in the HTTP message and the server responds with the current representation of the resource, if available. Each resource can have different representations (e.g. meta data to an image file on a server as well as the binary representation of the image itself) and the client can ask the server to deliver the required representation via the HTTP GET request message. This is a non-destructive operation as the server will return a “copy” of the resource in the format the client has requested. The resource itself is left untouched on the server (indempotent). The client can on the other hand send new content to the server via the POST operation to signal the server to store or work with the provided content. In addition as the HTTP protocol is stateless by design the server can’t persist information beyond the current session of a client. It is the responsibility of the client instead to provide the server with all the information needed to restore the current status of the web application.[^13]

[^13]: Taylor, I.: From P2P and Grids to Services on the Web, 2nd Edt., Springer Verlag, 2009, pg. 81-106

Based on some simple but general concepts like the **URI**, the **HTTP protocol** and the **HTML format** the whole World-Wide Web idea was created and is a success story for a standardised way to address, receive and interact with resources in a network on global scale. Information about a resource can easily be retrieved and indexed by search engines to allow the resource to be found by possible users. The URI provides an unique name for a resource on the global network, that is human readable, easy to remember and will be translated into the required server address information in the background.

![](<http://www.w3.org/TR/webarch/uri-res-rep.png>)

**Figure 4**: World-Wide Web Architecture


But this simplicity of the fundamental protocols of the World-Wide Web shows some limitations nowadays. Neither is privacy, data protection and data security of the information, that is transferred via the HTTP protocol, part of the original concept nor does it really fits for real-time communication and (live) streaming of content between different parties or has accessibility support built-in. So in it’s initial state it much assumes humans sitting in front of their PC as the receiver of the representation of a resource due to the fact that most of the HTML (and its associated CSS) standard is dealing with how to render content to a screen in the web browser program to be perceived by a human.
