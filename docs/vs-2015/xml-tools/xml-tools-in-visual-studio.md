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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 313cc11978355942bf6671cc040969c255d7e44d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669349"
---
# <a name="xml-tools-in-visual-studio"></a>XML-Tools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extensible Markup Language (XML) * ist eine Markup Sprache, die ein Format zum Beschreiben von Daten bereitstellt. Dies erleichtert eine präzisere Deklaration von Inhalt und bietet vertrauenswürdigere Suchergebnisse auf verschiedenen Plattformen. Darüber hinaus ermöglicht XML die Trennung von Präsentationsinformationen und Daten. Bei HTML verwenden Sie beispielsweise Tags, um den Browser anzuweisen, dass Daten fett oder kursiv dargestellt werden; bei XML verwenden Sie Tags nur, um Daten zu beschreiben, z. B. den Namen einer Stadt, die Temperatur oder den Luftdruck. In XML werden Stylesheets wie Extensible Stylesheet Language (XSL) und Cascading Style Sheets (CSS) verwendet, um die Daten in einem Browser darzustellen. XML trennt die Daten von den Präsentationsinformationen und dem Prozess. Dadurch können Sie die Daten wie gewünscht anzeigen und verarbeiten, indem Sie verschiedene Stylesheets und Anwendungen anwenden.

 XML ist ein Teilsatz von SGML, der für die Bereitstellung über das Internet optimiert wurde. Es wird vom World Wide Web Consortium (W3C) definiert. Diese Standardisierung stellt sicher, dass strukturierte Daten einheitlich und von Anwendungen oder Anbietern unabhängig sind.

 XML ist die Grundlage vieler Funktionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Im folgenden Thema werden Namen von Tools und Funktionen in Bezug auf XML aufgelistet, die in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bereitgestellt werden.

 Weitere Informationen finden Sie im [XML Developer Center](http://go.microsoft.com/fwlink/?LinkID=100176), das die aktuelle Dokumentation, technische Informationen, Downloads, Newsgroups und andere Ressourcen für XML-Entwickler bereitstellt.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Arbeiten mit XML-Daten](../xml-tools/working-with-xml-data.md) Erläutert die Rolle von XML in der Art und Weise, wie Daten in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] behandelt werden.

 [Buggen von XSLT](../xml-tools/debugging-xslt.md) Enthält Links zu Themen über die Verwendung des Visual Studio-Debuggers zum Debuggen von XSLT.

## <a name="reference"></a>Referenz
 [Microsoft. VisualStudio. XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) macht die Analyse Struktur des [XML-Editors](http://go.microsoft.com/fwlink/?LinkId=228249) über [System. Xml. Linq](http://go.microsoft.com/fwlink/?LinkId=228250) für beliebige XML-Dokumente verfügbar.

 [XML-Standard Referenz](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Bietet Informationen über XML-Technologien, einschließlich XML, Dokumenttyp Definition (DTD), XML Schema Definition Language (XSD) und XSLT.

 <xref:System.Xml?displayProperty=fullName> beschreibt die Klassen und andere Elemente, aus denen der <xref:System.Xml>-Namespace besteht, und bietet Links zu ausführlicheren Informationen zu jedem Element.

 <xref:System.Xml.Serialization?displayProperty=fullName> beschreibt die Klassen und andere Elemente, aus denen der <xref:System.Xml.Serialization>-Namespace besteht, und bietet Links zu ausführlicheren Informationen zu den einzelnen Elementen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [XML-Dokumentobjektmodell (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Beschreibt, wie die <xref:System.Xml.XmlDocument> und die zugehörigen Klassen den W3C-Dokumentobjektmodell (Core) Level 1-und Level 2-Namespace-Unterstützungs Spezifikationen entsprechen.

 [Lesen von XML mit dem "XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) " Beschreibt, wie die <xref:System.Xml.XmlReader> einen nicht zwischengespeicherten, schreibgeschützten Vorwärts Zugriff auf XML-Daten über einen XML-Stream bereitstellt.

 [Schreiben von XML mit dem XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Beschreibt, wie die <xref:System.Xml.XmlWriter> nicht zwischengespeicherte vorwärts-und vorwärts Weise das Erstellen von XML-Streams bietet und Ihnen hilft, XML-Dokumente zu erstellen, die dem W3C-Standard entsprechen.

 [XSLT-Transformationen](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Beschreibt, wie die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse die XSLT 1,0-Empfehlung implementiert.

 [Verarbeiten von XML-Daten mit dem XPath-Datenmodell](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Beschreibt, wie die <xref:System.Xml.XPath.XPathNavigator>-Klasse in einem <xref:System.Xml.XPath.XPathDocument> oder einem <xref:System.Xml.XmlDocument>-Objekt gespeicherte XML-Daten verarbeiten kann. Die <xref:System.Xml.XPath.XPathNavigator>-Klasse basiert auf dem XQuery 1.0- und XPath 2.0-Datenmodell und kann zum Navigieren und Bearbeiten von XML-Daten verwendet werden.

 [XML-Schema Objektmodell (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Beschreibt die Klassen, die zum Erstellen und Bearbeiten von XML-Schemas verwendet werden, indem eine <xref:System.Xml.Schema.XmlSchema> Klasse zum Laden und Bearbeiten eines Schemas bereitgestellt wird.
