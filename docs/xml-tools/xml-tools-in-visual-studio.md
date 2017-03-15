---
title: "XML-Tools in Visual&#160;Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "Klassen [Visual Studio], XML"
  - "CSS, Stylesheets für XML"
  - "Daten [Visual Studio], XML"
  - "Datasets [Visual Basic], XML-Schemas"
  - "Discoverydateien, XML"
  - "Enterprise-Vorlagen, XML und"
  - "Serversteuerelemente, XML und"
  - "SGML, XML"
  - "Stylesheets, Für XML"
  - "Webserversteuerelemente, XML"
  - "Webdienste"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], .NET Framework-Klassen"
  - "XML [Visual Studio], Datenquellen"
  - "XML [Visual Studio], Ressourcen"
  - "XML [Visual Studio], SGML-Beziehung zu"
  - "XML-Schemas"
  - "XMLDataDocument-Klasse"
  - "XSD-Schemas"
  - "XSL"
  - "XSL, Stylesheets"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML-Tools in Visual&#160;Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Extensible Markup Language \(XML\)* ist eine Markupsprache, die ein Format bereitstellt, mit dem Daten beschrieben werden können.  Dies erleichtert eine präzisere Deklaration von Inhalt und bietet vertrauenswürdigere Suchergebnisse auf verschiedenen Plattformen.  Darüber hinaus ermöglicht XML die Trennung von Präsentationsinformationen und Daten.  Bei HTML verwenden Sie beispielsweise Tags, um den Browser anzuweisen, dass Daten fett oder kursiv dargestellt werden; bei XML verwenden Sie Tags nur, um Daten zu beschreiben, z. B. den Namen einer Stadt, die Temperatur oder den Luftdruck.  In XML werden Stylesheets wie Extensible Stylesheet Language \(XSL\) und Cascading Style Sheets \(CSS\) verwendet, um die Daten in einem Browser darzustellen.  XML trennt die Daten von den Präsentationsinformationen und dem Prozess.  Dadurch können Sie die Daten wie gewünscht anzeigen und verarbeiten, indem Sie verschiedene Stylesheets und Anwendungen anwenden.  
  
 XML ist ein Teilsatz von SGML, der für die Bereitstellung über das Internet optimiert wurde.  Es wird vom World Wide Web Consortium \(W3C\) definiert.  Diese Standardisierung stellt sicher, dass strukturierte Daten einheitlich und von Anwendungen oder Anbietern unabhängig sind.  
  
 XML ist die Grundlage vieler Funktionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Im folgenden Thema werden Namen von Tools und Funktionen in Bezug auf XML aufgelistet, die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bereitgestellt werden.  
  
 Weitere Informationen finden Sie im [XML Developer Center](http://go.microsoft.com/fwlink/?LinkID=100176), wo Sie aktuelle Dokumente, technische Informationen, Downloads, Newsgroups und andere Ressourcen für XML\-Entwickler finden können.  
  
## In diesem Abschnitt  
 [Arbeiten mit XML\-Daten](../xml-tools/working-with-xml-data.md)  
 Erläutert die Rolle von XML bei der Behandlung von Daten in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Debugging von XSLT](../xml-tools/debugging-xslt.md)  
 Bietet Links zu Themen über die Verwendung des Visual Studio\-Debuggers zum Debuggen von XSLT.  
  
## Referenz  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Macht die Analysestruktur des [XML\-Editors](http://go.microsoft.com/fwlink/?LinkId=228249) über [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) für alle XML\-Dokumente verfügbar.  
  
 [Referenzen zu XML\-Standards](http://msdn.microsoft.com/de-de/79c78508-c9d0-423a-a00f-672e855de401)  
 Bietet Informationen über XML\-Technologien, darunter XML, Document Type Definition \(DTD\), XML Schema Definition Language \(XSD\) und XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Beschreibt die Klassen und andere Elemente, aus denen sich der <xref:System.Xml>\-Namespace zusammensetzt, und bietet Links zu ausführlicheren Informationen über jedes Element.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Beschreibt die Klassen und andere Elemente, aus denen sich der <xref:System.Xml.Serialization>\-Namespace zusammensetzt, und bietet Links zu ausführlicheren Informationen über jedes Element.  
  
## Verwandte Abschnitte  
 [XML\-Dokumentobjektmodell \(DOM\)](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 Beschreibt, inwiefern <xref:System.Xml.XmlDocument> und die verbundenen Klassen den Supportspezifikationen gemäß dem W3C Document Object Model \(Core\) Level 1 und Level 2 Namespace entsprechen.  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/de-de/3029834c-a27e-4331-b7aa-711924062182)  
 Beschreibt, wie der <xref:System.Xml.XmlReader> nicht zwischengespeicherten, nur weitergeleiteten, schreibgeschützten Zugriff auf XML\-Daten über einen XML\-Stream bietet.  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/de-de/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Beschreibt, wie der <xref:System.Xml.XmlWriter> einen nicht zwischengespeicherten, nur weitergeleiteten Weg bei der Generierung von XML\-Streams bietet und Ihnen dabei hilft, XML\-Dokumente zu erstellen, die dem W3C\-Standard entsprechen.  
  
 [XSLT\-Transformationen](../Topic/XSLT%20Transformations.md)  
 Beschreibt, wie die <xref:System.Xml.Xsl.XslCompiledTransform>\-Klasse die XSLT 1.0\-Empfehlung implementiert.  
  
 [Verarbeiten von XML\-Daten mithilfe des XPath\-Datenmodells](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 Beschreibt, wie die <xref:System.Xml.XPath.XPathNavigator>\-Klasse XML\-Daten verarbeiten kann, die in einem <xref:System.Xml.XPath.XPathDocument>\- oder einem <xref:System.Xml.XmlDocument>\-Objekt gespeichert sind.  Die <xref:System.Xml.XPath.XPathNavigator>\-Klasse basiert auf dem XQuery 1.0\- und XPath 2.0\-Datenmodell und kann zum Navigieren und Bearbeiten von XML\-Daten verwendet werden.  
  
 [XML\-Schemaobjektmodell \(SOM\)](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 Beschreibt die Klassen, die zum Erstellen und Manipulieren von XML\-Schemas verwendet wurden, indem eine <xref:System.Xml.Schema.XmlSchema>\-Klasse bereitgestellt wird, um ein Schema zu laden und zu bearbeiten.