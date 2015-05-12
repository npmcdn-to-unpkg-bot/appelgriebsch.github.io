---
layout: post
title: Web of Services
description: "Describes the Web of Services -- the World-Wide Web as an application platform"
modified: 2014-11-30
tags: [world wide web, REST, API, JSON, XML, web architecture]
comments: true
image:
  feature: HTML5_sticker.png
---

“Over the years, HTML has become very successful as a tool to put information on the Web that can be employed even without a deep understanding of programming.”[^14]

With the public availability of the first (commercial) web browsers (Netscape Navigator in 1995 and Microsoft Internet Explorer in 1996) the Web becomes more and more important for the general public and businesses around the world. This also opens up new opportunities to do profitable business on the Web (aka e-Commerce). But this also means that the Web has to develop from a graph with nodes containing almost static information into a dynamic platform, in which the web browser on the client site can be seen as a separate application platform. In addition there was a need for the growing online businesses to be able to interoperate with each other on a machine-to-machine level.[^15] The former leads to the development of JavaScript in 1996, a scripting language embedded in the web browser to enable web developers to change the behaviour of web pages on the client site and still the “lingua franca” for cross-platform web application development.[^16] The latter results in the “Service Oriented Architecture” paradigm that enables application services provided by different vendors to talk to each other via a public facing programming interface (aka API). The only requirement for such interoperability to work properly is that each public interface follows some standardised or commonly agreed upon guidelines to be vendor-, platform- as well as language-agnostic. One possible implementation of these concepts are the so-called Web Services, that use the WS\* protocols and standards from the W3C with the extensible markup language (aka XML) and the HTTP protocol at their core.[^17] Like the HTML format XML is originally based on SGML, but instead of formalising markup tags for structuring and styling textual content it is a meta-language allowing everyone to define his or her own markup languages. In this matter it doesn’t dictate what tags are available to structure the information; instead it includes some basic guidelines for creating wellformed and valid documents that uses domain-specific tags, which can be freely defined and structured by the creator of the XML document. Therefore it is better suited in situations where a computer has to parse and evaluate the content of a message (assuming the computer program knows the structure of the message).[^18]

[^14]: Vossen, G.: Unleashing Web 2.0, Elsevier, 2007, pg. 5
[^15]: Vossen, G.: Unleashing Web 2.0, Elsevier, 2007, pg. 5-6, 22-34
[^16]: Kessin, Z.: Programming HTML5 Applications, O’Reilly, 2012, pg. 1-5
[^17]: Josuttis, N.: SOA in practice, O’Reilly, 2007, pg. 1-10, 209-229
[^18]: Taylor, I.: From P2P and Grids to Services on the Web, 2nd Edt., Springer Verlag, 2009, pg. 39-60

Let’s look at a sample XML document that describes the book from Sir Tim Berners-Lee:

{% highlight xml %}
<?xml version="1.0"?>
   <book>
       <title>Weaving the Web: The Original Design and Ultimate Destiny of the World Wide Web</title>
       <author>Sir Tim Berners-Lee</author>
       <isbn>978-0062515872</isbn>
       <genre>Computer and Internet</genre>
       <published>2000</published>
       <publisher>
           <name>HarperCollins</name>
           <url>http://harpercollins...co.uk</url>
       </publisher>
</book>
{% endhighlight %}

This XML snippet is wellformed, which means that it follows the basic guidelines to structure the markup and content of the document — namely it haves matching opening and closing tags and the child elements nested properly. This is the fundamental requirement for an XML message to be readable (and understandable) by a machine. In an additional step the author of the API could also specify an XML schema for each message, which describes the structure of the message with all the possible elements, their ordering, nesting level and data types in detail. By doing so the XML parser program can later verify the content of a retrieved message against the XML schema and check if it is a valid document (related to the schema definition). XML schematas are also expressed in XML format and have been standardised by the W3C.[^19] Being able to create custom markup languages via XML has a huge benefit for machine-to-machine communication and is the basis for integrating Web Services (via the WS\* protocols), but it still has limitations when it comes to figure out the semantics of those XML messages. This is mostly due to the fact that each XML document represents a new markup language and needs a specific XML parser to be understood by the machine; also to distinguish commonly used tag names in an XML document (like ‘\<book\>’ in the example above) the creator has to place them into specific namespaces (aka XML namespaces). But those XML namespaces further complicate the automatic processing of XML documents and increases the necessity to have custom instances of XML parsers for each XML document.[^20]

[^19]: W3C: XML Technology, <http://www.w3.org/standards/xml/>
[^20]: Taylor, I.: From P2P and Grids to Services on the Web, 2nd Edt., Springer Verlag, 2009, pg. 39-60

Another guideline (not a W3C standard though) for implementing such distributed, service-oriented systems is called Representational State Transfer (aka REST) and it builds upon the same fundamental principles that are also driving the World-Wide Web — namely the HTTP protocol, the URI as well as the XML or JSON formats for representing resources. By utilising on and building upon those general Web technologies the RESTful systems are also benefitting from the large-scale experiences and future improvements of them. The idea behind REST is that in the World-Wide Web every resource — that is every thing that can have a digital representation, is available and can be addressed via an unique URI.  This is not limited to virtual things but can also include virtual abstractions of real-world objects. In the latter case you can find usually meta information about the physical object in the World-Wide Web (e.g. a virtual (digital) representation of a place of interest on a map). If you can give every thing a virtual address (an URI) to talk to (via HTTP request/response messages) than you will have to distinguish the kind of actions or capabilities of the object in question. This is usually done via the HTTP verbs in the HTTP request message send by the client and can have the following semantics:[^21]

[^21]: Webber, J.: REST in practice, O’Reilly, 2010, pg. 2-20, pg. 55-92

-   **GET**, for accessing the current representation of the resource

-   **PUT**, for updating an existing resource with the given representation (as part of the HTTP body)

-   **POST**, for creating a new resource (as part of the HTTP body) or executing some specific action on an existing one

-   **DELETE**, for deleting an existing resource

-   **HEAD**, for querying meta information (e.g. available operations on a resource)

The payload of the HTTP messages transferred between client and server is in the HTTP body and can contain different representations of the resource (depending on the expected format the client sends in his request as part of the HTTP message header). In addition to the complex XML representations that are also used in the Web Service scenario the REST approach also offers a more lightweight JSON format that is inherited and directly supported in the JavaScript runtime environment (JSON stands for JavaScript Object Notation). Due to the direct serialization and deserialization support in JavaScript JSON is the recommended data transfer format for RESTful Web applications (Web services following the REST guidelines).[^22]

[^22]: Taylor, I.: From P2P and Grids to Services on the Web, 2nd Edt., Springer Verlag, 2009, pg. 318-322

Let’s look at a sample JSON document that describes the book from Sir Tim Berners-Lee:

{% highlight json %}
{
  "book": {
      "title": "Weaving the Web: The Original Design and Ultimate Destiny of the World Wide Web",
      "author": "Sir Tim Berners-Lee",
      "isbn": "978-0062515872",
      "genre": "Computer and Internet",
      "published": "2000",
      "publisher": {
          "name": "HarperCollins",
          "url": "http://harpercollins...co.uk"
      }
  }
}  
{% endhighlight %}

Compared to the XML message above JSON doesn’t use any tags to markup its content, instead it is a plain-text format that utilises a ‘key: value’ representation for the data of complex objects. Each key is a string representation of an attribute of the object. A value can either contain another object representation or is containing the string representation of the value of the attribute (no other data types supported in the JSON message).  Depending on the richness of support for the various Web technologies you can differentiate 4 levels of styles for RESTful Web applications (according to Richardson[^23]):

[^23]: Webber, J.: REST in practice, O’Reilly, 2010, pg. 18-19, 93-96

-   **Level 0**, every thing is available via a single URL and a single HTTP operation (usually POST). Anything specific to the task or object being addressed is encoded in the payload of the HTTP request message (usually expressed via XML, e.g. SOAP or XML-RPC formatted messages),

-   **Level 1**, every thing is available via its own URL, but still uses a single HTTP operation for interaction. This could be either the POST operation having the specific task to execute on the object in question encoded in the HTTP request body (usually expressed via XML) or the GET operation with specific query parameters on the URL itself,

-   **Level 2**, every thing is available via its own URL and supports different HTTP operations (depending on the capabilities of the resource). In addition to the different HTTP operations the RESTful Web application on Level 2 should also deliver matching (more meaningful) HTTP status codes in the response message (e.g. HTTP status ‘201-Created’ on a successful POST operation to a resource),

-   **Level 3**, introduces ‘Hypermedia as the Engine of Application State’, it builds on Level 2 but enhances it in a way, that each request to a resource on the server will be answered not only with the result of the operation, but will also include a list of Hypertext links, that show how to proceed in the current workflow or can be used to access related resources. By following one of the possible links the client progresses forward in the overall application state and a new set of Hypertext links will be returned by the server.

![](<http://martinfowler.com/articles/images/richardsonMaturityModel/overview.png>)

**Figure 5**: The levels of maturity for RESTful applications

![](<../images/HATEOAS.png>)

**Figure 6**: Hypermedia as the Engine of Application State

The importance of RESTful Web applications has been increased in recent years due to two important developments:

1.  **Rich-Internet Applications**: as more and more applications have been build on the Web there was also the need to provide better, richer user experiences that can compete with those available in desktop applications.  For this purpose the Ajax design pattern has been introduced in 2005 and has been superseded by the Single Page Application design pattern nowadays. The idea behind is the same: instead of having a full round trip to the server every time the user interacts with a web site an asynchronous request is taking place in the background (implemented in JavaScript) and the current web page will be updated in accordance to the result delivered from the server (containing status codes and resource representations in XML or JSON).[^24]

    [^24]: Paulson L.: Building Rich Web Applications with Ajax, IEEE, Oct.  2005, pg. 14-17

2.  **Mobile Web Applications**: With the global availability and public adoption of smart devices (smartphones and tablets) in the last 3-5 years a new market has been established — the market for mobile applications. These applications (which could also be offline-capable Web applications running in browsers of smart devices) are usually being downloaded to the smart device of the user, run locally on the device but loads or sends additional information via a Web service from or to the Internet. This is largely due to the limited capabilities of those devices (in accordance to CPU power and local storage) as well as to the new social communication patterns they make available (e.g. instant messaging, photo- or video sharing, …). So a lot of those novel web applications can be accessed through multiple channels (e.g.  via a desktop browser, via smartphone or tablet) and have to provide the same information in an application that is optimized to the capabilities of the device the user has at hand; something that can only be implemented on a large scale by utilizing Web services for providing the application content.[^25]

    [^25]: Smashing Magazine: The Mobile Web Handbook, Smashing Magazin, 2014, pg. 17-42

    While it is possible to integrate Web services from different vendors and provide a seamless application experience on multiple devices with the concepts introduced by the Web of Services it still doesn’t fit for real-time communication scenarios due to the request/response architectural pattern of the HTTP protocol. The problem is that the client has to be the initiating part of the communication and there is no way for the server to push down information to a client when something happens on the server-side (e.g. a new message arrives in the users inbox). Due to the limitation in the HTTP protocol there have been some workarounds for this:[^26]

[^26]: Webber, J.: REST in practice, O’Reilly, 2010, pg. 185-236

-   **HTTP polling**, the client is periodically asking the server for new status information (e.g. every 3 seconds). The server answers immediately with the current status (either new information available or not). This is the worst alternative to use as it consumes a lot of processing power and network consumption on client and server.

-   **Event-driven updates,** the server creates an event for any changes that occur and provides an URL for the client to receive notifications for specific events (e.g. using the Atom syndication format). The client will open a separate background connection to this notification URL that will be opened for a long time and the server can push down information to the client over it.

In addition to those issues the Web of Services also doesn’t allow to easily integrate and link the information from one source with the information of other services on the Web due to the lack of semantics in the XML and JSON data formats. Any Web service usually defines its own API with the supported data structures that the client has to adapt to. So integrating information from different Web services needs special implementation on the site of the consumer of them.
