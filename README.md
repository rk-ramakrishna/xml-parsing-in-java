# XML Parsing in java

This repository has been created to outline various mechanisms available in java to parse XML documents effectively

Java provides below APIs to parse XML documents.

1. SAX.

2. DOM
3. STAX


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
  

