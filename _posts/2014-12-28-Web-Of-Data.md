---
layout: post
title: Web of Data
description: "Describes the Web of Data -- the World-Wide Web as a database of Linked Data"
modified: 2014-12-31
tags: [world wide web, Linked Data, RDF, RDFS, web architecture]
comments: true
image:
  feature: HTML5_sticker.png
---

“The Web is full of intelligent applications, with new innovations coming every
day.”[^27]

But each of those intelligent Web applications is driven by the data available to them. Data that is likely coming from different places in the global information space — accessible usually via a custom API on the server hosting those resources (aka Web of Services). The more consistent the data available to the smart Web application is the better the service and its result will be. But to support an integration of the data from various Web services the semantics of the information delivered by each service has to be available — and there has to be a generalised, formalised way to express the semantic of that data. The focus on a standard that allows Web services to express the semantics of the data they provide also allows for global scalability, openness and decentralisation, which are the key principles of the World-Wide Web. The Semantic Web tries to give a solution for this problem by providing the Resource Description Framework (aka RDF) and related technologies (e.g. RDF schema, SPARQL, OWL, …) for describing, linking and querying the data that a Web service delivers.[^28] But it doesn’t reinvent the wheel; instead the Semantic Web builds upon existing, proven technologies like XML, XML namespaces, XML schemata and the URI to uniquely address resources on the Web:

[^27]: Allemang, D.: Semantic Web for the Working Ontologist, 2nd Edt., Elsevier, 2011, pg. 3
[^28]: Allemang, D.: Semantic Web for the Working Ontologist, 2nd Edt., Elsevier, 2011, pg. 3-12

![](<http://www.w3.org/2001/12/semweb-fin/swlevels.png>)

**Figure 7**: The Semantic Web layers

The RDF as the name implies works on the concept of a resource (aka the subject). A resource could be any thing that has a digital representation and is uniquely addressable in the Internet via an URI (see REST above). Each resource might have a unique set of properties or attributes (aka the predicates). A predicate is usually also expressed via an URI, but could be just a literal in simple cases. The value of a predicate could either be another resource (aka an object identified by its unique URI) or a literal. The combination of those 3 items: subject -\> predicate -\> object/literal is called the RDF triple.[^29]

[^29]: Allemang, D.: Semantic Web for the Working Ontologist, 2nd Edt., Elsevier, 2011, pg. 27-50

![](<http://assets.devx.com/articlefigs/19556.jpg>)

**Figure 8**: The RDF triple

As seen above the RDF usually forms a graph that can be traversed via the predicates starting on the subject. If an object is reached this also has predicates attached that can be walked down. Literal values are the leaves of the whole graph.

Being able to describe the resources is just the first step into a Semantic Web.  In addition there has to be a commonly agreed upon vocabulary for the various predicates of the subjects. This is where the Meta Data initiative of the Dublin Core comes into play. To describe the book from Sir Tim Berners-Lee we can use the following predicates:[^30]

[^30]: DCMI Meta Data Terms: <http://dublincore.org/documents/dcmi-terms/>

-   **title**, for describing the title of the book (URI: <http://purl.org/dc/terms/title>)

-   **creator**, for describing the author of the book (URI: <http://purl.org/dc/elements/1.1/creator>)

-   **created**, for describing the publish date of the book (URI: <http://purl.org/dc/terms/created>)

-   **publisher**, for describing the publisher (URI: <http://purl.org/dc/elements/1.1/publisher>)

-   **identifier**, for describing the ISBN of the book (URI: <http://purl.org/dc/terms/identifier>)

-   **subject**, for describing the genre of the book (URI: <http://purl.org/dc/elements/1.1/subject>)

A RDF representation of the book can be visualized in textual format (assuming the book’s resource address being available at http://www.mybookstore.com/TBL-WeavingWeb):

{% highlight xml %}
<http://www.mybookstore.com/TBL-WeavingWeb> <http://purl.org/dc/terms/title> "Weaving the Web: The Original Design and Ultimate Destiny of the World Wide Web" .
<http://www.mybookstore.com/TBL-WeavingWeb> <http://purl.org/dc/elements/1.1/creator> <http://www.mybookstore.com/authors/TimBernersLee> .
<http://www.mybookstore.com/TBL-WeavingWeb> <http://purl.org/dc/terms/created> "2000" .
<http://www.mybookstore.com/TBL-WeavingWeb> <http://purl.org/dc/elements/1.1/publisher> <http://www.mybookstore.com/publishers/HarperCollins> .
<http://www.mybookstore.com/TBL-WeavingWeb> <http://purl.org/dc/terms/identifier> "978-0062515872" .
<http://www.mybookstore.com/TBL-WeavingWeb> <http://purl.org/dc/elements/1.1/subject> <http://www.mybookstore.com/subjects/ComputerAndInternet> .  
{% endhighlight %}

or as a graph:

![](<../images/RDF%20triple%20-%20Book.png>)

“Just as Semantic Web modeling in RDF is about graphs, Semantic Web modeling in the RDF Schema Language (RDFS) is about sets.”[^31] RDFS is a schema language for RDFS and can be used to describe classes of resources and their relationships.[^32] The OWL Web Ontology Language (aka OWL) allows describing ontologies on the World-Wide Web and also uses RDF as foundation.[^33]

[^31]: Allemang, D.: Semantic Web for the Working Ontologist, 2nd Edt., Elsevier, 2011, pg. 125
[^32]: W3C: RDF Schema 1.1, <http://www.w3.org/TR/rdf-schema/>
[^33]: W3C: OWL Web Ontology Language Reference, <http://www.w3.org/TR/owl-ref/>

As stated before in its original implementation RDF uses XML, XML namespaces and XML schemas heavily; and it builds upon the meta data specification of the Dublin Core project. All of this means the messages that are generated to express the semantic data structures are complicated to read, maintain and understand for humans and needs proper tooling support when working with them.  Although there have been additional standards in the progress that might provide lightweight alternatives — namely the OpenSchema initiative[^34], the microdata idea to extend existing HTML with meta information[^35] as well as the JSON-LD format for Web services.[^36] The OpenSchema initiative provides schema definitions for various data structures that are in use on the Web (e.g. an event, a book, a movie, …) and is commonly used by search engine providers like Google or Yahoo to enhance their search results. The schemas can be used with RDF, microdata or JSON-LD and define property names and data types that are available in each schema. A huge benefit of HTML microdata is that meta information can easily be added to the existing HTML documents that are already available. This might be best fit for already existing (static) HTML documents whereas the JSON-LD format might be of interest for the RESTful Web services that already deliver a representation of a resource. These formats can be easily used with existing systems without having to implement a new RDF representation of the available resources.

[^34]: Organisation of Schemas: <http://schema.org/docs/schemas.html>
[^35]: HTML microdata: <http://www.w3.org/TR/microdata/>
[^36]: JSON-LD 1.0: <http://www.w3.org/TR/json-ld/>
