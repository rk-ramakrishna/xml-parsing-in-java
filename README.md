# XML Parsing in java

This repository has been created to outline various mechanisms available in java to parse XML documents effectively

Java provides below APIs to parse XML documents.

1. SAX.
2. DOM
3. STAX
4. JAXB


### 1. SAX [Simple API for XML] 
   SAX is Java API for parsing an XML document sequentially from start to end. 
   SAX parser more efficient that DOM, because DOM loads whole document into memory. 
   This benefit becomes bottleneck to use XSLT and XPATH which required entire document to be loaded in memory.
   
   The following code snippet used to parse the XML documents using SAX API.
   XMLReader have various methods for configuring the parser and parsing a document's content. 
   
   SAXParserFactory spf = SAXParserFactory.newInstance();
   spf.setNamespaceAware(true);
   SAXParser sp = spf.newSAXParser();
   XMLReader xmlreader = sp.getXMLReader();
   
#### Drawbacks of SAX:

1. SAX can parse XML documents but cannot create them. 
2. SAX can't be integrate with XPATH & XSLT


### 2. DOM [Document Object Model]
   Document Object Model (DOM) is a Java API for parsing an XML document into an in-memory tree of nodes and for creating an XML document from a node tree. 
   After a DOM parser creates a tree, an application uses the DOM API to navigate over and extract infoset items from the tree's nodes.
   
#### Advantages of DOM:

1. DOM API allows random access of an XML document, where as SAX allowed for sequential access
2. DPM API allows to parse and create XML document, where as SAX allowed to only parse XML document

   However, SAX is advantageous over DOM in that it can parse documents of arbitrary size, whereas the size of documents parsed or created by DOM is limited 
   by the amount of available memory for storing the document's node-based tree structure.   
  
  #####Note: 	
  DOM originated as an object model for the Netscape Navigator 3 and Microsoft Internet Explorer 3 web browsers. 
  Collectively, these implementations are known as DOM Level 0. Because each vendor's DOM implementation was only slightly compatible with the other, 
  the W3C subsequently took charge of DOM's development to promote standardization and has so far released DOM Levels 1, 2, 3, and 4. 
  Java 11 supports the first three DOM levels through its DOM API.
  
  
  The following code snippet used to parse or create the XML documents using DOM API.
  
  DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
  // Parse an XML document into a DOM tree.
  DocumentBuilder parser = DocumentBuilderFactory.newInstance().newDocumentBuilder();
  Document document = parser.parse(new File("Orders.xml"));   
  

### 4. JAXB [Java API for XML Binding]

**What is XML binding in JAXB?**
XML binding is the representation of XML document content as an object in computer memory.
JAXB (Java Architecture for XML Binding) uses annotations to bind XML documents to a java object model.

**What is Unmarshalling [Reading] in JAXB?**
Unmarshalling refers to the process of converting XML data into JAXB-derived Java objects.

**What is marshalling [Writing] in JAXB?**
Marshalling provides a client application the ability to convert a JAXB-derived Java object tree into XML data.

**Differences between JAXB, DOM, SAX**
The Java **DOM and SAX parsing are lower-level APIs to parse XML documents**, **while JAXB is a higher-level API for converting XML elements and attributes to a Java object hierarchy (and vice versa).** Implementations of JAXB may use a DOM or SAX parser behind the scenes to do the actual parsing of the XML input data.
**JAXB uses annotations to bind XML documents to a java object model.**

**What do you mean by high level API of JAXB and low level API of DOM,SAX**
Low level API means we need to write lot of DOM, SAX based java statments to convert the XML documnet to Java. 
High level API means we no need to write lof of java statments to convert the XML documents to Java

**References:**
https://www.javapedia.net/JAXB#qanda1842


**Difference between JAXP and JAXB**

JAXP (Java API for XML Processing) refers to the outdated low-level XML APIs in JavaSE, such as DOM, SAX and STAX.JAXP is programming model [API] provided in JDK to switch between various implementations like DOM, SAX. JAXP is JPA.  
JAXB (Java Architecture for XML Binding) uses annotations to bind XML documents to a java object model.


**Perfomance differences betwen DOM, SAX and JAXB**

Please refer below to findout differences between DOM, SAX and JAXB
https://dzone.com/articles/jaxb-sax-dom-performance

Summary:
1. The peformance times for pure SAX are slightly better than JAXB but only for very large files. 
   Unless you are using very large files the performance differences are not worth worrying about. 
   
2. The progamming model advantages of JAXB win out over the complexitiy of the SAX programming model. 

3. JAXB also provides random accses like DOM does. SAX does not provide this.

4. Performance times look a lot better with Woodstox, if JAXB / StAX is being used.

**please note above perfomance differences are calculate on JDK 6 and above post is a Decade old. We might have more greter perfomance in JDK 8**


  
   





