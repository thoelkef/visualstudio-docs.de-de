---
title: XML-Tools in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 38d933199c85bee3fa85a533f9c61c08bee898ea
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2018
---
# <a name="xml-tools-in-visual-studio"></a>XML-Tools in Visual Studio

*Extensible Markup Language (XML)* ist eine Markupsprache, die ein Format zum Beschreiben von Daten bereitstellt. Dies erleichtert eine präzisere Deklaration von Inhalt und bietet vertrauenswürdigere Suchergebnisse auf verschiedenen Plattformen. Darüber hinaus ermöglicht XML die Trennung von Präsentationsinformationen und Daten. Bei HTML verwenden Sie beispielsweise Tags, um den Browser anzuweisen, dass Daten fett oder kursiv dargestellt werden; bei XML verwenden Sie Tags nur, um Daten zu beschreiben, z. B. den Namen einer Stadt, die Temperatur oder den Luftdruck. In XML werden Stylesheets wie Extensible Stylesheet Language (XSL) und Cascading Style Sheets (CSS) verwendet, um die Daten in einem Browser darzustellen. XML trennt die Daten von den Präsentationsinformationen und dem Prozess. Dadurch können Sie die Daten wie gewünscht anzeigen und verarbeiten, indem Sie verschiedene Stylesheets und Anwendungen anwenden.

XML ist ein Teilsatz von SGML, der für die Bereitstellung über das Internet optimiert wurde. Es wird vom World Wide Web Consortium (W3C) definiert. Diese Standardisierung stellt sicher, dass strukturierte Daten einheitlich und von Anwendungen oder Anbietern unabhängig sind.

XML ist die Grundlage vieler Funktionen von Visual Studio und .NET Framework. Die folgenden Themenliste werden die Tools und Funktionen im Zusammenhang mit XML, die in Visual Studio und .NET Framework bereitgestellt werden.

Weitere Informationen finden Sie unter der <xref:System.Xml?displayProperty=fullName> Dokumentation.

## <a name="in-this-section"></a>In diesem Abschnitt

[Arbeiten mit XML-Daten](../xml-tools/working-with-xml-data.md)  
Erläutert die Rolle von XML in die Möglichkeit, Daten in Visual Studio behandelt werden.

[Debuggen von XSLT](../xml-tools/debugging-xslt.md)  
Bietet Links zu Themen über die Verwendung des Visual Studio-Debuggers zum Debuggen von XSLT.

## <a name="reference"></a>Verweis

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
Macht die [XML-Editor](http://go.microsoft.com/fwlink/?LinkId=228249) Analysestruktur über ["System.Xml.Linq"](http://go.microsoft.com/fwlink/?LinkId=228250) für alle XML-Dokumente.

[Verweise zu XML-Standards](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)  
Bietet Informationen über XML-Technologien, darunter XML, Document Type Definition (DTD), XML Schema Definition Language (XSD) und XSLT.

<xref:System.Xml?displayProperty=fullName>  
Beschreibt die Klassen und andere Elemente, aus denen sich der <xref:System.Xml>-Namespace zusammensetzt, und bietet Links zu ausführlicheren Informationen über jedes Element.

<xref:System.Xml.Serialization?displayProperty=fullName>  
Beschreibt die Klassen und andere Elemente, aus denen sich der <xref:System.Xml.Serialization>-Namespace zusammensetzt, und bietet Links zu ausführlicheren Informationen über jedes Element.

## <a name="related-sections"></a>Verwandte Abschnitte

[XML-Dokumentobjektmodell (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)  
Beschreibt, inwiefern <xref:System.Xml.XmlDocument> und die verbundenen Klassen den Supportspezifikationen gemäß dem W3C Document Object Model (Core) Level 1 und Level 2 Namespace entsprechen.

[Verarbeiten von XML-Daten mit "XmlReader" und "XmlWriter"](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[XSLT Transformations (XSLT-Transformationen)](/dotnet/standard/data/xml/xslt-transformations)  
Beschreibt, wie die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse die XSLT 1.0-Empfehlung implementiert.

[Verarbeiten von XML-Daten mithilfe des XPath-Datenmodells](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
Beschreibt, wie die <xref:System.Xml.XPath.XPathNavigator>-Klasse XML-Daten verarbeiten kann, die in einem <xref:System.Xml.XPath.XPathDocument>- oder einem <xref:System.Xml.XmlDocument>-Objekt gespeichert sind. Die <xref:System.Xml.XPath.XPathNavigator>-Klasse basiert auf dem XQuery 1.0- und XPath 2.0-Datenmodell und kann zum Navigieren und Bearbeiten von XML-Daten verwendet werden.

[XML Schema Object Model (SOM) (XML-Schemaobjektmodell (SOM))](/dotnet/standard/data/xml/xml-schema-object-model-som)  
Beschreibt die Klassen, die zum Erstellen und Manipulieren von XML-Schemas verwendet wurden, indem eine <xref:System.Xml.Schema.XmlSchema>-Klasse bereitgestellt wird, um ein Schema zu laden und zu bearbeiten.