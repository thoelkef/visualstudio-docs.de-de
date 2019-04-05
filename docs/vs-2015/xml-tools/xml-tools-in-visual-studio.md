---
title: XML-Tools
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2812e45460778a3527f55522c6d3fc98285a548d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959783"
---
# <a name="xml-tools-in-visual-studio"></a>XML-Tools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Extensible Markup Language (XML) * ist eine Markupsprache, die ein Format zum Beschreiben von Daten bereitstellt. Dies erleichtert eine präzisere Deklaration von Inhalt und bietet vertrauenswürdigere Suchergebnisse auf verschiedenen Plattformen. Darüber hinaus ermöglicht XML die Trennung von Präsentationsinformationen und Daten. Bei HTML verwenden Sie beispielsweise Tags, um den Browser anzuweisen, dass Daten fett oder kursiv dargestellt werden; bei XML verwenden Sie Tags nur, um Daten zu beschreiben, z. B. den Namen einer Stadt, die Temperatur oder den Luftdruck. In XML werden Stylesheets wie Extensible Stylesheet Language (XSL) und Cascading Style Sheets (CSS) verwendet, um die Daten in einem Browser darzustellen. XML trennt die Daten von den Präsentationsinformationen und dem Prozess. Dadurch können Sie die Daten wie gewünscht anzeigen und verarbeiten, indem Sie verschiedene Stylesheets und Anwendungen anwenden.

 XML ist ein Teilsatz von SGML, der für die Bereitstellung über das Internet optimiert wurde. Es wird vom World Wide Web Consortium (W3C) definiert. Diese Standardisierung stellt sicher, dass strukturierte Daten einheitlich und von Anwendungen oder Anbietern unabhängig sind.

 XML ist die Grundlage vieler Funktionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Im folgenden Thema werden Namen von Tools und Funktionen in Bezug auf XML aufgelistet, die in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bereitgestellt werden.

 Weitere Informationen finden Sie unter den [XML Developer Center](http://go.microsoft.com/fwlink/?LinkID=100176), die die neueste Dokumentation, technische Informationen, Downloads, Newsgroups und andere Ressourcen für XML-Entwickler bietet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Arbeiten mit XML-Daten](../xml-tools/working-with-xml-data.md) behandelt, die die Rolle von XML in die Gruppierung von Daten im erfolgt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Debuggen von XSLT](../xml-tools/debugging-xslt.md) enthält Links zu Themen über die Verwendung von Visual Studio-Debugger zum Debuggen von XSLT.

## <a name="reference"></a>Referenz
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) macht die [XML-Editor](http://go.microsoft.com/fwlink/?LinkId=228249) Analysestruktur über ["System.Xml.Linq"](http://go.microsoft.com/fwlink/?LinkId=228250) für alle XML-Dokumente.

 [Referenzen zu XML-Standards](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) enthält Informationen zu XML-Technologien, einschließlich XML, Dokumenttypdefinition (DTD), XML-Schemadefinitionssprache (XSD) und XSLT.

 <xref:System.Xml?displayProperty=fullName> Beschreibt die Klassen und andere Elemente, aus denen die <xref:System.Xml> Namespace und enthält Links zu ausführlicheren Informationen über jedes Element.

 <xref:System.Xml.Serialization?displayProperty=fullName> Beschreibt die Klassen und andere Elemente, aus denen die <xref:System.Xml.Serialization> Namespace und enthält Links zu ausführlicheren Informationen zu den einzelnen Elementen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [XML-Dokument (DOKUMENTOBJEKTMODELL)](http://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) beschreibt wie der <xref:System.Xml.XmlDocument> und die zugehörigen Klassen mit dem W3C Document Object Model (Core) Level 1 und Level 2 Namespace supportspezifikationen entsprechen.

 [Lesen von XML mit XmlReader](http://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) beschreibt wie der <xref:System.Xml.XmlReader> bietet weitergeleiteten forward only, nur-Lese Zugriff auf XML-Daten über eine XML-Stream.

 [Schreiben von XML mit "XmlWriter"](http://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) beschreibt wie der <xref:System.Xml.XmlWriter> bietet weitergeleiteten, vorwärts-zum Generieren von XML-Streams und hilft, die Sie erstellen die XML-Dokumente, die der W3C-Standard entsprechen.

 [XSLT-Transformationen](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) beschreibt wie der <xref:System.Xml.Xsl.XslCompiledTransform> -Klasse implementiert die Empfehlung zu XSLT 1.0.

 [Exemplarische Vorgehensweise: Verarbeiten von XML-Daten mithilfe des XPath-Datenmodells](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) beschreibt wie der <xref:System.Xml.XPath.XPathNavigator> Klasse kann gespeicherte XML-Daten verarbeiten einer <xref:System.Xml.XPath.XPathDocument> oder <xref:System.Xml.XmlDocument> Objekt. Die <xref:System.Xml.XPath.XPathNavigator>-Klasse basiert auf dem XQuery 1.0- und XPath 2.0-Datenmodell und kann zum Navigieren und Bearbeiten von XML-Daten verwendet werden.

 [XML-Schema Object Model (SOM)](http://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) beschreibt die Klassen, die zum Erstellen und Bearbeiten von XML-Schemas, durch die Bereitstellung einer <xref:System.Xml.Schema.XmlSchema> -Klasse zum Laden und Bearbeiten eines Schemas.
